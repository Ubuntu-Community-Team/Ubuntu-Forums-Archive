---
title: "ethernet"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by pramodmmuraly on 2009-03-12
hai
i m using hardy right now.when i m giving ifconfig -a command result is

eth0      Link encap:Ethernet  HWaddr 00:16:E6:97:D9:AF  
          inet addr:192.168.1.216  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe97:d9af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20471366 (19.5 MiB)  TX bytes:4034397 (3.8 MiB)
          Interrupt:177 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2234380 (2.1 MiB)  TX bytes:2234380 (2.1 MiB)

eth1     Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

can any one tell what this eth1 means.there is no entry for it in /etc/network/interface files.
plz help me.
plus tell me the command for getting details of this.

---

