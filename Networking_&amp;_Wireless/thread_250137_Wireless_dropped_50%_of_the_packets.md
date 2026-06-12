---
title: "Wireless dropped 50% of the packets"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by hego on 2006-09-03
Hi,

I having a trouble with my wireless (ipw3945), I discover that my wireless connection is dropping a lot of packets:

eth1      Link encap:Ethernet  HWaddr 00:13:02:60:71:09
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe60:7109/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40114 errors:10 **dropped:9392** overruns:0 frame:0
          TX packets:6701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6170095 (5.8 MiB)  TX bytes:999849 (976.4 KiB)
          Interrupt:185 Base address:0xe000 Memory:8a000000-8a000fff

This is causing that my connection via wireless is very SLOW. 

This is my system information:

Laptop: HP Pavilion dv5000t
OS:     Ubuntu 6.06
Kernel: 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
Router: linksys BEFW11S4 V.2

I'm using WEP (64) as a security.

This problem doesn't happen if I use Windows.

I was thinking to upgrade the ipw3945 and ieee80211 to the current version but I couldn't find any good document on how to do that.

---

