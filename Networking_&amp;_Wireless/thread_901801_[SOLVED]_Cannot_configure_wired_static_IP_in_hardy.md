---
title: "[SOLVED] Cannot configure wired static IP in hardy heron"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by lum69 on 2008-08-26
Hi,

I am trying to configure a standard wired static ip connection using the graphical network manager. I have disabled roaming mode and entered:

static ip address
ip address: 192.168.1.100
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.1

I am using a linksys router, with dhcp configured starting with address 192.168.1.102

It seems that i can ping another computer on my network, but cannot access web sites or anything else.

the output of ifconfig is the following:

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:c0:45:bd  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fec0:45bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096011 (1.9 MB)  TX bytes:191808 (187.3 KB)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:26:54:12:e0:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:635212 (620.3 KB)  TX bytes:167926 (163.9 KB)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104468 (102.0 KB)  TX bytes:104468 (102.0 KB)


Note:  I have used this same setup with the same router and same ip with older versions of ubuntu with no problems

---

### Post by lum69 on 2008-08-26
nevermind. This works now.

---

