---
title: "wlan:avahi"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by merlin666 on 2008-02-07
This concerns a laptop with 64bit gutsy (7.10) and integrated broadcomm wireless card. The wireless worked fine years ago with 64-bit Fedora and also more recently with older versions of ubuntu. I have cleaned out and re-installed ndiswrapper a few times following various documentation sources, but cannot get rid of the avahi device. Any suggestions?

rolf@ubuntu:~$ ndiswrapper -l
netbc564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


rolf@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:15:5F:EB  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe15:5feb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1826518 (1.7 MB)  TX bytes:397029 (387.7 KB)
          Interrupt:23 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:8C:F9:E7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:d0000000-d0002000 

wlan0:ava Link encap:Ethernet  HWaddr 00:90:4B:8C:F9:E7  
          inet addr:169.254.11.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Memory:d0000000-d0002000

---

### Post by samaricsm on 2008-02-08
I think you are stuck with it.  The 169.254.x.x is part of the zeroconf, or multicast DNS protocol.  From what I can tell, Ubuntu uses it to locate services.  I did not configure for it when I built my firewall and the update manager stopped working.

---

