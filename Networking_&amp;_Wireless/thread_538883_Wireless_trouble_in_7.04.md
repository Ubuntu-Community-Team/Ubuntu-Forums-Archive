---
title: "Wireless trouble in 7.04"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by sharmar on 2007-08-30
The wireless works on windows but not on ubuntu 7.04. The wired internet does work though on ubuntu. So it does connect to the router but is not picking the wireless connection.  Please help me with this.

 ON  ifconfig I get this.

eth0      Link encap:Ethernet  HWaddr 00:16:D3:A7:1F:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:D3:A7:1F:48  
          inet addr:169.254.5.150  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1204 (1.1 KiB)  TX bytes:1204 (1.1 KiB)

---

### Post by bmartin on 2007-08-31
Your wireless device isn't being detected at all. If it's a USB wireless stick, what is the output of **lsusb**? Otherwise, what is the output of **lspci**?

---

