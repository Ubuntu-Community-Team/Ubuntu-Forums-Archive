---
title: "Can not connect to certain sites through VPN"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by Hooloovoo on 2008-01-02
Hi everyone!

When I connect with my VPN created in network-manager I can not reach certain sites (such as thepiratebay.org). Most sites such as google however work without any problem. I can successfully ping to all sites and the same VPN work just fine in window.

This is the output from route -n:

Kernel IP routing table
Destination     Gateway         Genmask            Flags Metric Ref    Use Iface
83.233.183.2    192.168.0.1   255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     0.0.0.0           255.255.255.0    U        0      0        0 eth0
0.0.0.0            0.0.0.0           0.0.0.0               U       0      0        0  ppp0

and this is from ifconfig:

eth0      Link encap:Ethernet  HWaddr 66:77:44:22:33:11
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:446521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:285509245 (272.2 MB)  TX bytes:237398780 (226.4 MB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:25944 (25.3 KB)  TX bytes:25944 (25.3 KB)

ppp0   Link encap:Point-to-Point Protocol
          inet addr:83.233.183.119  P-t-P:83.233.183.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:115139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:36541669 (34.8 MB)  TX bytes:45032875 (42.9 MB)

Please help me with this annoying problem!

---

