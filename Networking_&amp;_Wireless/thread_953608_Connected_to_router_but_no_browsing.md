---
title: "Connected to router but no browsing"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by faisal892 on 2008-10-20
Hi all,

I have asked this question but got no solution therefore asking again.

I just upgraded from Ubuntu 8.04 to Ubuntu 8.1. Problem is that my internet was working fine before I upgraded but after upgraded to Ubuntu8.1 I can not browse internet though my laptop is connected through wireless to router. The same is the case when I connected my laptop through wire to router. It shows me as connected but no browsing.

Here is output of ifconfig


faisal@faisal-laptop:~$ ifconfig

eth0 Link encap:Ethernet HWaddr 00:1b:38:91:87:6a 

UP BROADCAST MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Interrupt:16 Base address:0x1000 



lo Link encap:Local Loopback 

inet addr:127.0.0.1 Mask:255.0.0.0

inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:246 errors:0 dropped:0 overruns:0 frame:0

TX packets:246 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0 

RX bytes:15416 (15.4 KB) TX bytes:15416 (15.4 KB)



wlan1 Link encap:Ethernet HWaddr 00:1a:73:c3:c2:da 

inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0

UP BROADCAST RUNNING MULTICAST MTU:576 Metric:1

RX packets:9 errors:0 dropped:0 overruns:0 frame:0

TX packets:13 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:2088 (2.0 KB) TX bytes:2018 (2.0 KB)



wmaster0 Link encap:UNSPEC HWaddr 00-1A-73-C3-C2-DA-00-00-00-00-00-00-00-00-00-00 

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)



faisal@faisal-laptop:~$


Please if any body could help.

Faisal.

---

