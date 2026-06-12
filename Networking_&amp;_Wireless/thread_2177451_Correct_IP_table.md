---
title: "Correct IP table"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by aasalem10 on 2013-09-28
Me as many others using Ubuntu 12.04 PC that has multiple interfaces.  USB (huawei dongle 1550), wireless card, and rj45 socket for wired connections. And of course we expect network/internet connection to work on any interface.   

current netsta  (huawei dongle)
alaa-a-salem@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination                    Gateway             Genmask                  Flags      MSS      Window    irtt      Iface
0.0.0.0                        10.64.64.64            0.0.0.0                      UG          0             0            0      ppp0
10.64.64.64                 0.0.0.0                   255.255.255.255        UH          0              0            0     ppp0
169.254.0.0                 0.0.0.0                   255.255.0.0               U             0             0           0      ppp0
alaa-a-salem@ubuntu:~$ 

alaa-a-salem@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 17:01:55 UTC 2013 i686 athlon i386 GNU/Linux
alaa-a-salem@ubuntu:~$ 

Is there a simple way for PC users to ensure that routing table is correct and tightly configured for save usage.
[http://ghgghgghghgg.wordpress.com/](http://ghgghgghghgg.wordpress.com/)

---

