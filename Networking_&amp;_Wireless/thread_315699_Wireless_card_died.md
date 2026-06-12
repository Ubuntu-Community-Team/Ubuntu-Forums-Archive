---
title: "Wireless card died"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by Elvish Legion on 2006-12-09
Well I was at work earlier and I was having trouble connecting, no biggie it happens a lot, but when I get home and boot my laptop back up I notice my wireless card is no longer 'there'...

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:36:8A:B1:7E  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe8a:b17e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2513718 (2.3 MiB)  TX bytes:379442 (370.5 KiB)
          Interrupt:66 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Its not even being detected anymore...

---

