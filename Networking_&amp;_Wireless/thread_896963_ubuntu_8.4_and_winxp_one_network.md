---
title: "ubuntu 8.4 and winxp one network"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by hobbyhall on 2008-08-21
hi! sorry for my bad eng.
i have 2 PC on first PC i have a ubuntu 8.4 and this PC have 2 eth cards - first for internet and second for other PC
other PC have WIN XP, but i can't configuring network for my win xp PC

eth0      Link encap:Ethernet  HWaddr 00:08:54:0f:77:d5  
          inet addr:84.237.223.26  Bcast:84.237.223.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe0f:77d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3899007 (3.7 MB)  TX bytes:469406 (458.4 KB)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:0d:87:b1:04:66  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:feb1:466/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73950 (72.2 KB)  TX bytes:1728 (1.6 KB)
          Interrupt:11 Base adeth2      Link encap:Ethernet  HWaddr 00:80:ad:71:18:ef  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fe71:18ef/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30505 (29.7 KB)  TX bytes:2064 (2.0 KB)
          Interrupt:11 Base address:0xc400 dress:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52800 (51.5 KB)  TX bytes:52800 (51.5 KB)

where is problem?

P.S
I using linux first time- just don't mad! :) and tell me all info
thanks for helping and sorry for BAD eng

---

### Post by Iowan on 2008-08-21
If you want to share the internet connection, [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") may be helpful.  
Does the Windows box have an IP address?
(Yes) What is it?  
      Can it **ping** the Ubuntu box?
      Is it in the 192.168.0.XXX subnet?
(No)  Is it DHCP address?

---

### Post by hobbyhall on 2008-08-22
windows have ip 192.168.0.2, mask 255.255.255.0, gateway 192.168.0.1

---

