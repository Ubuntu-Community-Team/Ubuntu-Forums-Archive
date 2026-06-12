---
title: "Running XBMC via a Raspberry PI Network to Ubuntu"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-10-24
Ubuntu not seeing the HDHomeRun TV tuner on the network. I want to make all the hardware and software play nicely together.

Devices: Ubuntu 12.04, RaspBMC, router, SiliconDust HDHomerun TV dual tuner.

Software: Ubuntu with XBMC, HDHomerun config_gui, Raspberry PI with RaspBMC.



Raspberry PI's ifconfig

pi@raspbmc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:27:eb:30:fb:f7  
          inet addr:10.42.0.14  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba27:ebff:fe30:fbf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2254635 (2.1 MiB)  TX bytes:619008 (604.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229331 (223.9 KiB)  TX bytes:229331 (223.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:b6:b1:50  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:821f:2ff:feb6:b150/64 Scope:Global
          inet6 addr: fe80::821f:2ff:feb6:b150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:286088 errors:0 dropped:288328 overruns:0 frame:0
          TX packets:36159 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36316730 (34.6 MiB)  TX bytes:7376086 (7.0 MiB)

Ubuntu's ifconfig:

mark@Lexington:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38398 (38.3 KB)  TX bytes:26890 (26.8 KB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:349938 (349.9 KB)  TX bytes:349938 (349.9 KB)

wlan0     Link encap:Ethernet  HWaddr 90:f6:52:0c:2d:a4  
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:92f6:52ff:fe0c:2da4/64 Scope:Global
          inet6 addr: fe80::92f6:52ff:fe0c:2da4/64 Scope:Link
          inet6 addr: 2602:306:bdbf:4420:9478:5f2e:7d64:fb2d/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:190524783 (190.5 MB)  TX bytes:17976489 (17.9 MB)

---

