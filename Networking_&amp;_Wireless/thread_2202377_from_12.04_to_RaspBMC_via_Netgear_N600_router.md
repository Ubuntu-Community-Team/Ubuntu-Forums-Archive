---
title: "from 12.04 to RaspBMC via Netgear N600 router"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2014-01-28
I cannot reach the Netgear N600 (WNDR-3400 v.2) webgui. The hardware is pc to router to Raspberry PI. The NetMgr in 12.04 is "Wired connection 1" with

IP is 10.42.0.1
Subnet is 255.255.255.0
GW is 0.0.0.0
DNS is 0.0.0.0

All else is stock or default configs.

Trying both 192.168.0.1 and 192.168.1.1 returns nothing.

pi@raspbmc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:27:eb:30:fb:f7  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba27:ebff:fe30:fbf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64242 (62.7 KiB)  TX bytes:89540 (87.4 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3860 (3.7 KiB)  TX bytes:3860 (3.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:b6:b1:50  
          inet addr:192.168.1.84  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:821f:2ff:feb6:b150/64 Scope:Global
          inet6 addr: fe80::821f:2ff:feb6:b150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14999 errors:0 dropped:73 overruns:0 frame:0
          TX packets:2097 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2116813 (2.0 MiB)  TX bytes:416162 (406.4 KiB)

The RaspBMC says it is internet connected at IP 192.168.1.84 but the Weather applet cannot find the location or temperature, which means that it's not on the 'net but reports it is. Also the time is off by about 15 minutes.

---

### Post by Iowan on 2014-01-28
From which machine are you trying to reach the Netgear? Looks like **raspbmc** has addresses for both interfaces - but what is the PC using?
If it's 10.42.0.1, then both machines are trying to use that address.

---

### Post by Mark_in_Hollywood on 2014-01-29
A strange circumstance. When the wifi is connected to this computer I have 'net access. When wifi is disconnected I can ssh into the Raspberry PI, I cannot figure how to have both, although I'm certain it must be possible from what I've read at forums.

Here is the terminal output for the PI's route -n

pi@raspbmc:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

pi@raspbmc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:27:eb:30:fb:f7  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ba27:ebff:fe30:fbf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14658 errors:0 dropped:1 overruns:0 frame:0
          TX packets:102851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1405262 (1.3 MiB)  TX bytes:7917404 (7.5 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:29153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8448613 (8.0 MiB)  TX bytes:8448613 (8.0 MiB)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:b6:b1:50  
          inet addr:192.168.1.84  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:821f:2ff:feb6:b150/64 Scope:Global
          inet6 addr: fe80::821f:2ff:feb6:b150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1556234 errors:0 dropped:1582 overruns:0 frame:0
          TX packets:83911 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:143250487 (136.6 MiB)  TX bytes:10184993 (9.7 MiB)

and here is the computer's wifi network info - this is with the wifi adapter connected. Note no eth0 IP address.

mark@Lexington:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2314648 (2.3 MB)  TX bytes:198129 (198.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:838433 (838.4 KB)  TX bytes:838433 (838.4 KB)

wlan0     Link encap:Ethernet  HWaddr 90:f6:52:0c:2d:a4  
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:bdbf:4420:bc16:f0d4:791b:45d4/64 Scope:Global
          inet6 addr: 2602:306:bdbf:4420:92f6:52ff:fe0c:2da4/64 Scope:Global
          inet6 addr: fe80::92f6:52ff:fe0c:2da4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:363885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:296419610 (296.4 MB)  TX bytes:29735801 (29.7 MB)

---

