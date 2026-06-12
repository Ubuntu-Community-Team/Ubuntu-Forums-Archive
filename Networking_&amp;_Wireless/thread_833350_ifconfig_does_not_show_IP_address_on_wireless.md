---
title: "ifconfig does not show IP address on wireless"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by hadaxu on 2008-06-18
Hi everyone,

ifconfig does not show wireless ip address on my Thinkpad X61. Is that a problem? Is there another solution? Thanks.

Here is what I got:

wifi0     Link encap:UNSPEC  HWaddr 00-1C-23-4A-6C-6B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:423583 errors:0 dropped:0 overruns:0 frame:123650
          TX packets:13238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:69178417 (65.9 MB)  TX bytes:1857783 (1.7 MB)
          Interrupt:21

---

### Post by pytheas22 on 2008-06-18
It's only a problem if your Internet connection is not working, but I gather that it does since you didn't mention it.  Are you able to browse websites?  If so, it's probably just some problem with ifconfig being unable to get the IP address properly.  If you can't browse websites, please post the output of lscpi so we can figure out which kind of wireless card you have and how to solve the problem.

---

