---
title: "Wired Connection Greyed Out"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by Jexel on 2008-07-22
I have a p5b-deluxe wifi mobo and it has two ethernet ports.

Marvell Yukon 88E8056 Gigabit Ethernet Controller
Marvell Yukon 88E8001 Gigabit Ethernet Controller

Network manager shows the two wired options however they are both greyed out and do not allow me to select them. What do I need to do to get it working?

---

### Post by Jexel on 2008-07-23
bump?

---

### Post by lisati on 2008-07-23
Do you have anything plugged into the adapters? One possibility is that the network manager thinks that there's nothing there to connect with.

---

### Post by Jexel on 2008-07-23
yes i've tried connecting to both ports but i get nothing, no lights nothing.

It's really weird I can't get this work under vista either...HOWEVER, when i tried using a live cd during the "boot up" process, the lights on one of the lan ports was flashing. I checked my router and it detected the connection.

---

### Post by Rentius on 2009-05-22
I'm having the same trouble with 9.04 x64. 

I have a Via rhine II and DM9601 USB ethernet card and both are greyed out. 

I installed Jaunty yesterday and it worked fine, after turning on this morning couldn't connect. When I try and remake the DSL connection in Network manager it doesn't save. I've also tried sudo pppoeconf and still doesn't work

Booting through Windows finds all connections working, thus enabling this post

I'm 1 day new to Linux so all help appreciated

---

### Post by Rentius on 2009-05-22
Further googling found others suggesting the following information may be needed so here it is:

ipconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:0b:2f:1d:ee:68  
          inet6 addr: fe80::20b:2fff:fe1d:ee68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13824 (13.8 KB)  TX bytes:12647 (12.6 KB)
          Interrupt:23 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:60:6e:02:03:83  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr d6:f6:83:17:48:aa  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.92.160.220  P-t-P:117.92.160.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8724 (8.7 KB)  TX bytes:7940 (7.9 KB)

ifconfig, Ispci and Ismod all produced empty text files

---

### Post by Rentius on 2009-05-22
My poor windows oriented brain is struggling.......

I still have all devices greyed out in network manager. Clicking on connection information yields, 

"Error displaying connection information:

No valid active connections found!"

regardless it seems Firefox works and I can access repository.

:o ????

---

### Post by superprash2003 on 2009-05-23
do you get any " your device is unmanaged" error?

---

### Post by Rentius on 2009-05-23
> **superprash2003 said:**
> do you get any " your device is unmanaged" error?
No, It's quite baffling to me, the devices are greyed out and it claims no valid active connections but I haven't had that error reported. At the same time the connection works despite no DSL connection being present in the manager?!?

---

