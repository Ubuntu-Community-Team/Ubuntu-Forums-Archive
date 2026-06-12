---
title: "Using NAT with ubuntu"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by Front187 on 2008-03-03
I have a ubuntu laptop using a wireless connection behind a wireless router.

I have a virtual machine inside my ubuntu laptop (Win XP).  I cannot get WinXP to connect to the internet through the host using NAT.

I am under the impression that using the NAT setting would basically make my laptop act as a router to the virtual machine.  

Under this assumption, in XP, I set the default gateway to 192.168.2.4 (The address of my laptop behind the router) and my gateway to 192.168.2.4.

Obviously this is not right, since my connection doesn't work.

Can anyone give me some hints?  I am still trying to learn the fundamentals of TCP/IP, so please forgive my ignorance.
Here are the relevant device settings
```
eth1      Link encap:Ethernet  HWaddr 00:18:DE:1E:91:1B  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe1e:911b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:14318 errors:32 dropped:3527 overruns:0 frame:0
          TX packets:11879 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21271279 (20.2 MB)  TX bytes:2055480 (1.9 MB)
          Interrupt:17 Base address:0x2000 Memory:8c100000-8c100fff 

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.251.1  Bcast:172.16.251.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

---

