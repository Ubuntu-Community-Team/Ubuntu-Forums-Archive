---
title: "ifconfig counters not working?"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by fhriley on 2014-08-06
I just built a router and installed it with Ubuntu Server 14.04 LTS. It has two NICs in it, one for the internal network and one for the external (internet) network. I'd like to monitor external interface usage, but the ifconfig counters are always 0. The internal interface counters work fine. According to lspci, the external interface is a Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10) and in ifconfig it is device p3p1. Other than the counters, it works fine. How do I get the counters working on this device?

---

### Post by fhriley on 2014-08-06
Finally figured out the correct Google query to find an answer. It's fixed in kernel 3.14. Ubuntu 14.04 installs kernel 3.13.

The original bug report: [http://www.spinics.net/lists/netdev/msg245544.html](http://www.spinics.net/lists/netdev/msg245544.html)
Thread stating when it was fixed: [https://bbs.archlinux.org/viewtopic.php?id=166555](https://bbs.archlinux.org/viewtopic.php?id=166555)

---

