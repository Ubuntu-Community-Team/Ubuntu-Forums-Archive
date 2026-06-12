---
title: "Broadcom BCM5751: Internet and local fails after 30 minutes"
date: 2013-12-16
forum: Networking &amp; Wireless
---

### Post by tomasvdmeer on 2013-12-16
Hi uys and some girls i think...

i have a problem since the release of Xubuntu 13.04

I can connect to the network and internet but it disconnect after 30 minutes.

we tried new cables, reset of the modem and things like that.

we have the problem on all 13.04 machines @ home (all with same gear)

Hope one can help us with it

also xubuntu thinks my machine is a laptop? should it be a power issue?

eth0 = Broadcom BCM5751
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:05:9f:7b:c0  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:5ff:fe9f:7bc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41838879 (41.8 MB)  TX bytes:2280241 (2.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:261268 (261.2 KB)  TX bytes:261268 (261.2 KB)



---

### Post by praseodym on 2013-12-16
Any time filter active in your router?

---

