---
title: "Networking stops every few minutes"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by jrjazzman on 2006-10-13
It seems that when I'm running aMule, networking just stops, as in I can't even ping my default gateway:

~$ ping 10.1.10.1
PING 10.1.10.1 (10.1.10.1) 56(84) bytes of data.
From 10.1.10.155 icmp_seq=16 Destination Host Unreachable
From 10.1.10.155 icmp_seq=19 Destination Host Unreachable


A quick ifdown/ifup fixes the problem, but as you can imagine it's quite annoying to have to do this every few minutes.  Any ideas what could cause this?  I'm running dapper.

thanks

---

