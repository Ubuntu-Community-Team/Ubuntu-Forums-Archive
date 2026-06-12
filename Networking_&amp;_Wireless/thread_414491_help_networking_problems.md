---
title: "help networking problems"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by bgervasi on 2007-04-19
Hope someone can help me.

I am running ubuntu 6.10 and 2 times a day at the sametime, I loose connection to the lan on the same ip address range.  

eg.  host 172.16.241.30, cannot ping any host on the 172.16.241.0 network, accept one solaris box.  The host can ping others hosts on the 172.16.0.0 range.  The hosts which are not reachable can ping the host 172.16.241.30.  This last for about 40 mins.  I did a nework down and up, and still no resolve.

check cron to see if anything was running during those times, but nothing.

Also disable ipv6, since others say that there could be problems there.

What else can I check?

---

### Post by nautilus on 2007-04-20
IPv6 does not affect IPv4.  they are different protocols.

please provide the output of:

ifconfig

and

route -n

---

### Post by bgervasi on 2007-04-20
eth0      Link encap:Ethernet  HWaddr 00:17:A4:43:9A:DA  
          inet addr:172.16.241.30  Bcast:172.16.241.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211235901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215641991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3951039029 (3.6 GiB)  TX bytes:2548041242 (2.3 GiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1716111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1716111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:916143838 (873.7 MiB)  TX bytes:916143838 (873.7 MiB)
-------------------------------------------------------------------------

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.241.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         172.16.241.1    0.0.0.0         UG        0 0          0 eth0


----------------------------------------------------------------------

---

