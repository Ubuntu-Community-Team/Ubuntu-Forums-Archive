---
title: "ADSL doesn't work"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by Decimatron on 2008-07-05
Hi! I've just installed Ubuntu 7.04, and I have problems with my internet connection (not working at all). The router I have is Huawei HG510 and it's connected to my ethernet card on my mainboard. Any ideas what should I do to make it work?

---

### Post by superprash2003 on 2008-07-05
try this go to system->administration->network and go to your ethernet card properties and set it to DHCP.. if problem still persists go to the terminal and type ifconfig and post output here

---

### Post by Decimatron on 2008-07-05
The wired connection is already set to DHCP. I ran ifconfig but I can't paste it here since I can't write on NTFS partitions, and my nokia n73 seems unable to work on ubuntu as mass storage... :(

---

### Post by Decimatron on 2008-07-05
```
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:C3:3E:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:C3:3E:25  
          inet addr:169.254.5.18  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2664 (2.6 KiB)  TX bytes:2664 (2.6 KiB) 
```

here it is! burned it to a dvd... now what?

---

### Post by superprash2003 on 2008-07-05
try static ip.. what is your router's ip ?? if it is 192.168.1.1 then enter static ip as 192.168.1.10 and gateway as 192.168.1.1 under system->admin->network  eth0 properties ( select Static ip)..

---

