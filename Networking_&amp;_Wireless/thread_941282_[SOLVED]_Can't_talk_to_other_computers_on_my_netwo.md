---
title: "[SOLVED] Can't talk to other computers on my network"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by Harbard on 2008-10-07
I am trying to set up a BBS (Citadel/ux) on my home network.  I have successfully changed my systems to a static IP.  Now I am unable to connect to the computer running the BBS and I can not connect to my main computer from that one.  Nor can I ping my router...but I still have internet access.

```
dan@dan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:e1:ee:7a  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:11:d8:ef:67:17  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feef:6717/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7411499 (7.0 MB)  TX bytes:1157180 (1.1 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24644 (24.0 KB)  TX bytes:24644 (24.0 KB)
```

```
dan@dan-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

The ip address of the computer I am trying to connect to is 192.168.1.102, and my router is 192.168.1.1 

I have no firewalls running on the computers (my router has a built in firewall)

I should be able to type 192.168.1.102:8080 into my browser and connect to my BBS.


Any ideas?

---

### Post by cariboo on 2008-10-08
From the looks of it you have 2 network cards in your computer, eth0 and eth1. They both have the same ip address, that is your problem you have to change one of the ip addresses or disable one of the nics for your system to work properly.

Jim

---

### Post by Harbard on 2008-10-08
Thank you very much.  That has resolved my problem.  I am not sure why though.  eth0 was not connected to anything.  Even incorrectly configured it should not have affected anything else on the network.:confused:  Still, it's all shiny now.

Thanks!

---

