---
title: "Loopback Interface?"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by chrisch on 2007-10-07
I am just trying to figure out what the loopback interface is.  My web browsing is moving a little slow, like it is going through extra channels to get where it needs to.  I am running Gutsy Beta and under Network tools, Loopback interface is selected vs ethernet interface.  It won't let me keep the etherenet interface selected.

I went into my network settings and removed the roaming checkbox and set my ethernet to dhcp and that seemed to help a bit.

Here is the output of my ifconfig:

chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:CE:71:03  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fece:7103/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10781939 (10.2 MB)  TX bytes:1291087 (1.2 MB)
          Base address:0xdf40 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5673 (5.5 KB)  TX bytes:5673 (5.5 KB)

---

### Post by helgman on 2007-10-08
[Virtual Internet Protocol Network Interface](http://en.wikipedia.org/wiki/Loopback#Virtual_Internet_Protocol_Network_Interface) (Wikipedia)

Regards,
Helgman

---

