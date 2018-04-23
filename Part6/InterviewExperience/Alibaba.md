#Alibaba
---

一面

* 说一下你怎么学习安卓的？
* 项目中遇到哪些问题，如何解决的？
* Android事件分发机制？
* 三级缓存底层实现？
* HashMap底层实现，hashCode如何对应bucket?
* Java的垃圾回收机制，引用计数法两个对象互相引用如何解决？
* 用过的开源框架的源码分析
* Acticity的生命周期，Activity异常退出该如何处理？
* tcp和udp的区别，tcp如何保证可靠的，丢包如何处理？

二面：

* 标号1-n的n个人首尾相接，1到3报数，报到3的退出，求最后一个人的标号
* 给定一个字符串，求第一个不重复的字符 abbcad -> c


面试者：陶程

Python实现（标号1-n的n个人首尾相接，1到3报数，报到3的退出，求最后一个人的标号）


```
# coding=utf-8
#!/usr/bin/env python
import sys
import random


def run(n, mark, last, positionNum, loopDepth):
    leftNum = n
    for i in range(1, n+1):
        if mark[i-1] == 0:
            leftNum -= 1
            continue
        elif positionNum == 2:
            mark[i-1] = 0
            positionNum = 0
            leftNum -= 1
        else:
            last = i
            positionNum += 1
    if leftNum > 1:
        loopDepth += 1
        run(n, mark, last, positionNum, loopDepth)
    else:
        print "mark:{}, last:{}, depth:{}".format(mark, last, loopDepth)
        print "last number is: {}".format(last)


def getLastDiv3(n):
    mark = [1] * n
    last = 1
    positionNum = 0
    loopDepth = 1
    print 'N: {}'.format(n)
    run(n, mark, last, positionNum, loopDepth)


if __name__ == "__main__":
    if len(sys.argv) > 1:
        total = int(sys.argv[1])
    else:
        sys.exit('Need param N!')
    getLastDiv3(total)
```
