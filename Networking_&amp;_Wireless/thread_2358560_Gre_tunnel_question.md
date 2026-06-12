---
title: "Gre tunnel question"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by kelsa on 2017-04-14
Hello,

Perhaps someone can help me understand the ifconfig output from below.  I don't understand how the physical interface, eth1, can show so few drops yet the gre tunnel has so many.  As this is a connectionless tunnel and there is no understanding of drop packets in the network I am thinking it is an issue with packets that are not processed by the application that are in the gre buffer.  They have passed the eth1 buffer but fail to make it to the application.  Any thoughts would be appreciated.

eth1      Link encap:Ethernet  HWaddr 00:50:56:a1:33:44
          inet addr:10.203.132.235  Bcast:10.203.132.255  Mask:255.255.255.224
          inet6 addr: fe80::250:56ff:fea1:3344/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22339914245 errors:0 dropped:15315 overruns:0 frame:0
          TX packets:33710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7177317250655 (7.1 TB)  TX bytes:1416132 (1.4 MB)

gre1      Link encap:Ethernet  HWaddr b6:85:da:9d:5b:e6
          inet6 addr: fe80::b485:daff:fe9d:5be6/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1462  Metric:1
          RX packets:22299386794 errors:0 dropped:7496605552 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6157744898386 (6.1 TB)  TX bytes:680 (680.0 B)

---

