---
title: "Wireless working, dsl not"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by glethro on 2008-08-30
I have my system set up on an Acer 8920, i got the sound and everything working but today i noticed that i cant connect to the internet by cord.

my wireless is working fine and connects without a problem but i cant get it working using my Ethernet ...

i know the port is active cuz it works fine with vista (Dual boot).

furthermore when i type in ifconfig -a i get no mention of eth0.. 


user@user-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 B)  TX bytes:800 (800.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:c4:23:19  
          inet addr:10.0.1.2  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1136 (1.1 KB)  TX bytes:6576 (6.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-C4-23-19-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

