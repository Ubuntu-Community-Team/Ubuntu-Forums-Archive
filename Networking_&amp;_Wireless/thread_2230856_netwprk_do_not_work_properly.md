---
title: "netwprk do not work properly"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by monika4 on 2014-06-21
Hi guys, there are problems with a network on my PC with xubuntu. When using firefox there is connection, then after some time there is no connection (I don't know if that depends on time or on internet sites). To get it back I need to disconnect and connect again. Any idea what's wrong? Thanks a lot. Here is the output:

monika@soliton:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:81:d7:53:39  
          inet addr:138.251.31.55  Bcast:138.251.31.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fed7:5339/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1197050 errors:0 dropped:2942 overruns:0 frame:0
          TX packets:57298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202955873 (202.9 MB)  TX bytes:8038505 (8.0 MB)
          Interrupt:16 Memory:fbae0000-fbb00000 

eth1      Link encap:Ethernet  HWaddr 00:e0:81:d7:53:3a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107171 (107.1 KB)  TX bytes:7786 (7.7 KB)
          Interrupt:17 Memory:fb9e0000-fba00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1040436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1040436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720082495 (720.0 MB)  TX bytes:720082495 (720.0 MB)

---

### Post by TheFu on 2014-06-21
R U directly connected to the internet?  Ouch!  A router really would be a good idea from a security standpoint.

Troubleshooting sometimes-working network connections is hard.
* simplify
* test
Then
* simplify
* retest
then
* simplify more
* retest again
repeat until the root cause is determined.
So .. if you are using wifi - stop it. Use only wired ethernet.  Sometimes it is easiest to rule out other system issues - use iostat, top, netstat to determine what is really slowing down. It may NOT be the network. Heck, your IP could be under DDoS attack.

---

### Post by monika4 on 2014-06-21
thanks a lot for the answer, but what to do? there is no wifi at all here. What to check andf how? It\s interrupted when I for example open a new webpage, before it was hanging on [www.comsol.de](www.comsol.de), later when I opened yourube.com... I need to disconnect and connect again and then it works.

---

### Post by TheFu on 2014-06-21
Seems like DNS is the issue, but can't really tell from the information provided.

[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) will get you started on troubleshooting, but it would be best to rule out other programs slowing the system down. When this happens, close all browsers, disable any BT traffic THEN do the testing.

Are you running any ad blockers?  Antivirus?  Javascript protection?  Ghostery?  If not, consider it - to prevent every ad network in the world from making your PC slower.  If so, disable them and test again.... simplify.

---

