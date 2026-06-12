---
title: "rt61 installed ra0 up but singal strenght 0% while modem is next to r61 card"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by joefie on 2006-10-26
rt61 installed ra0 up but singal strenght 0% while modem is next to r61 card. I have an zyXEL modem which has wifi support and eth support. I'm using that through dhcp (wired) right now, so dhcp should work for wifi to... right???



ra0       Link encap:Ethernet  HWaddr 00:0E:8E:04:6B:86  
          inet6 addr: fe80::20e:8eff:fe04:6b86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29645 (28.9 KiB)  TX bytes:0 (0.0 b)
          Interrupt:1

auto ra0
iface ra0 inet dhcp


is in my network interfaces.

---

