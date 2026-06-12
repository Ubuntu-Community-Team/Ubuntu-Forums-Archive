---
title: "Inbound connections dropped"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by realalehunter on 2008-11-06
Hi. We have an Ubuntu machine that we use as a file/local web server in the office. Over the past few weeks we have been experiencing problems with connections to it inbound dropping off. We connect to it through ssh and HTTP. When it happens it affeects everyone that is already connected to it and you cannot reconnect to if for a few minutes afterwards by either SSH of HTTP.

When it happens, if you try to connect to it from a machine that hasn't been connected to it for a while it will connect fine. Also while it is down the connection FROM the server seems fine (I can browse the web from it and connect to my computer via ssh even though I cannot connect TO it from my machine).

We have tried upgrading the network card drivers, changing the network card, changing the network cable and sockets.

Nothing unusual shows in any of the log files

Output from ifconfig is
ath0      Link encap:Ethernet  HWaddr 00:1B:11:00:7F:28  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:01:6C:11:DC:9F  
          inet addr:192.168.100.124  Bcast:192.168.103.255  Mask:255.255.248.0
          inet6 addr: fe80::201:6cff:fe11:dc9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3396065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5030105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:733529131 (699.5 MB)  TX bytes:6011348110 (5.5 GB)
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2029143 (1.9 MB)  TX bytes:2029143 (1.9 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-11-00-7F-28-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150500 errors:0 dropped:0 overruns:0 frame:34867
          TX packets:3673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:10904359 (10.3 MB)  TX bytes:168958 (164.9 KB)
          Interrupt:16 


Thanks 
Matt

---

