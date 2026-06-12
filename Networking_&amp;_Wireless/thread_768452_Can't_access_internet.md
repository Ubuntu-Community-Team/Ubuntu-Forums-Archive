---
title: "Can't access internet"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by d525sn on 2008-04-26
Hi, Using an ethernet connection at university my computer recognises thats its plugged in but can't actually get onto the internet - the ifconfig data is below - if anyone has any suggestions that would be excellent. I've played around with varios settings o no avail - does anyone know what the correct ones are - thanks for your help

ifconfig 
eth0 Link encap:Ethernet HWaddr 00:12:3F0:BC:A1 
inet addr:129.234.180.52 Bcast:129.234.180.255 Mask:255.255.255.0 
inet6 addr: fe80::212:3fff:fed0:bca1/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:313 errors:0 dropped:0 overruns:0 frame:0 
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:39533 (38.6 KB) TX bytes:2272 (2.2 KB) 
Interrupt:19 

eth1 Link encap:Ethernet HWaddr 00:12:F0:61:E8:1F 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
Interrupt:17 Base address:0x6000 Memory:dfdfd000-dfdfdfff 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by FrankT-Qc on 2009-04-21
Could you post your routes ?

---

### Post by jimv on 2009-04-22
What university?  I ask so I can check their website to see if there are any special instructions for connecting.

---

