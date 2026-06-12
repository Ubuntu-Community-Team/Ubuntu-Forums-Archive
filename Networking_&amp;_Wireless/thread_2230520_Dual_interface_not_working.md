---
title: "Dual interface not working"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by deees2 on 2014-06-19
If I do following config it works but as I need to shift ip from eth0.125 to eth1 they don't work in screen as I cannot putty into the machine after setup ..screenshot attached any guidance?

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:56:8c:1f:80
          inet addr:10.209.96.40  Bcast:10.209.96.127  Mask:255.255.255.128
          inet6 addr: fe80::250:56ff:fe8c:1f80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:335269 (335.2 KB)  TX bytes:98402 (98.4 KB)
          Interrupt:18 Base address:0x2000


eth1      Link encap:Ethernet  HWaddr 00:50:56:8c:2b:8e
          inet6 addr: fe80::250:56ff:fe8c:2b8e/64 Scope:Link

 


          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120 (120.0 B)  TX bytes:71082 (71.0 KB)


eth0.125  Link encap:Ethernet  HWaddr 00:50:56:8c:1f:80
          inet addr:10.5.125.1  Bcast:10.5.125.127  Mask:255.255.255.128
          inet6 addr: fe80::250:56ff:fe8c:1f80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:9476 (9.4 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

