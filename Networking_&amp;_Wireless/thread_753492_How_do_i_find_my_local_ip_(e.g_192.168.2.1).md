---
title: "How do i find my local ip (e.g 192.168.2.1)"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by nappymonster on 2008-04-12
Hi all, How do i find out my local ip, such as 192.168.2.1 in ubuntu?

---

### Post by chili555 on 2008-04-12
Open a terminal and type ifconfig. Here's an example:```
chili@LAPTOP60:~/DriverInstall$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:D2:C2:1B:8D  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10647 errors:45 dropped:436 overruns:0 frame:0
          TX packets:8723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12517076 (11.9 MB)  TX bytes:1012542 (988.8 KB)
          Interrupt:21 Base address:0xc000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5188 (5.0 KB)  TX bytes:5188 (5.0 KB)

```My IP is 192.168.1.102.

---

