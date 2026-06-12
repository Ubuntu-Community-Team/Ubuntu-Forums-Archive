---
title: "another noob who needs help getting wireless to work"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by cypher604 on 2007-02-26
Hello! 
I'm new to linux and need help getting the wireless to work on my laptop (Acer Aspire 1414WLCi). 

No wireless cards show up in the networking dialog found in administration. Only shows my wired and modem connections.

"lspci" brings up the wireless card information: 
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

this is what I get for "ifconfig":
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:6F:63:3C  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe6f:633c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1991858 (1.8 MiB)  TX bytes:249733 (243.8 KiB)
          Interrupt:6 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

Thank you all in advance!

---

### Post by Metaljaz on 2007-02-27
when you type lspci from the terminal window was listed for network controller? You listed the information for ethernet controller.

---

