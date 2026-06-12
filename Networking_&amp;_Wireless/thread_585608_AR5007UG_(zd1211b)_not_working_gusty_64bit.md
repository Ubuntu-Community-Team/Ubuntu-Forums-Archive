---
title: "AR5007UG (zd1211b) not working gusty 64bit"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by apamatos on 2007-10-21
I posted here sometime ago about this problem but got no answers. I'm continuing my attempts to solve the issue - Drivers and USB zydas port are detected but no interface is connected and it does not work.

I'm trying ndiswrapper, that also didn't work. Then I realized that I'm using the 64bit version of linux and that drivers and installed vista are 32bits (I really don't know about the zydas driver shipping with gusty but...). I believe now that this may be the problem, so I'm trying to solve this first.

I can't  find the 64bit drivers. I found one link that seems to be dead. can anyone provide a good link to a zd1211b 64bit driver? - could be windows to work with ndiswrapper.

Or any suggestion???

Thanks in advance
AP:confused:

---

### Post by felixdzerzhinsky on 2007-10-25
I think you are in the same boat as me. That card is not supported in the 2.6.23 kernel. So we have to upgrade to that kernel. I would like to find a reliable, complete, not contradictory document on how to install the 2.6.23 kernel the Ubuntu way using .oldconfig.

[http://linuxwireless.org/en/users/Drivers/zd1211rw](http://linuxwireless.org/en/users/Drivers/zd1211rw)

Or is there an easier way?

---

