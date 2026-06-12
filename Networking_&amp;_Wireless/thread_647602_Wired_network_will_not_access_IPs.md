---
title: "Wired network will not access IPs"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by garrett218 on 2007-12-22
I have a dual boot of XP and Ubuntu running now and have come across a strange issue.  I am able to resolve URLs through pinging and using a browser but anytime I try to ping an IP address it does not work.  Possibly connected to this is the the Synaptic Package Manager and Update Manager do not seem to be connecting as I am unable to retrieve new packages.  Has anyone heard of this issue before?  I am using Fios and DHCP.  Here are the results from ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:19:DB:66:05:4F  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe66:54f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3848675 (3.6 MB)  TX bytes:262046 (255.9 KB)
          Interrupt:21 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:19:DB:D1:87:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

