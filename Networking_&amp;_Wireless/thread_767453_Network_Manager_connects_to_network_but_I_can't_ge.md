---
title: "Network Manager connects to network but I can't get to the internet (7.10)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by SigmaHog on 2008-04-25
I've been trying to figure this out for a week. I can connect on other wireless networks but not my own at home. I'm just at a loss at what to do!

ifconfig output is this:

eth0 Link encap:Ethernet HWaddr 00:15:C5:15:CF:76
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:22

eth1 Link encap:Ethernet HWaddr 00:16:CE:5E:E1:CD
inet addr:192.168.1.159 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::216:ceff:fe5e:e1cd/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:150 errors:0 dropped:683 overruns:0 frame:0
TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:19275 (18.8 KB) TX bytes:8445 (8.2 KB)
Interrupt:4 Base address:0x8000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by superprash2003 on 2008-04-25
are you able to see your network?is this the ifconfig output when you are connected to your network?

---

