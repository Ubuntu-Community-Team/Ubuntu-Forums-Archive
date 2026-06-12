---
title: "Realtek 8139 problem"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by tommaddox on 2006-10-08
Hi !
I am having a problem with my ubuntu 6.06 DD. My network interface driver seems to work fine, but once in a time it breakes. Any application trying to use the network interface seems to hang (eg. ifconfig eth0 -up , ssh). 

The lspci reports:
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lsmod|grep 8139 reports:
8139too                26880  0
8139cp                 22528  0
mii                     5888  2 8139too,8139cp

Is my problem caused by that I have both modules 8139too and 8139cp loaded on the same time? And if this is a problem how to solve it? And what is 'mii' ?

Thanks in advance.
BR
Tommaddox

---

### Post by mips on 2006-10-08
Tried searching fo 8139 here ?  There are many posts on the issue.

---

### Post by tommaddox on 2006-10-08
Hi! Yes I did search this forum. But what I am looking for, is what is the role of each of those modules, and if I am right that they should not be loaded at once. Anyway I tried doing notthing abou it and my ubuntu is running for 4 hours and nothing happens with network. Kind of strange isn't it ?

---

