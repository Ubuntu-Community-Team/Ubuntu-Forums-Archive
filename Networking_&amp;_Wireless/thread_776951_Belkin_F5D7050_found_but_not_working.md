---
title: "Belkin F5D7050 found but not working"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by chrisdudeperson on 2008-05-01
Hey guys,

I have a Belkin F5D7050v3 which is plugged into my Ubuntu 8.04 machine. It seems that that linux won't find any networks on it.
Yesterday i did a bit of foruming to see what was wrong with my belkin F5D7050. I found out that linux knows that my Belkin F5D7050 was there and recognised because i did an lsusb and these were the results:

Bus 001 Device 007: ID 04f2:0200 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 06f2:0011 Emine Technology Co. 
Bus 001 Device 003: ID 050d:705a Belkin Components 
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub 
Bus 001 Device 001: ID 0000:0000 


I was then told to do a ifconfig and these were the results:

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:304 errors:0 dropped:0 overruns:0 frame:0
TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:15200 (14.8 KB) TX bytes:15200 (14.8 KB)

wlan0 Link encap:Ethernet HWaddr 00:17:3f:ad:79:c8 
inet6 addr: fe80::217:3fff:fead:79c8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:782 errors:0 dropped:0 overruns:0 frame:0
TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:57346 (56.0 KB) TX bytes:100386 (98.0 KB)

wlan0:avahi Link encap:Ethernet HWaddr 00:17:3f:ad:79:c8 
inet addr:169.254.8.105 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1


According to one user my ifconfig was not right.


Can anyone help?

Thanks
Chris

---

### Post by chrisdudeperson on 2008-05-01
any ideas?

---

