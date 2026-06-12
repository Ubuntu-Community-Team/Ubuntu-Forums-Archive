---
title: "Help me about PPTP VPN server"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Usta_AsH on 2008-08-30
Hi, I did everything nicely.
Client can connect to VPN server. Connection accepts. But the problem is, client cannot connect to internet but client can ping  to client's ip address and server ip adress not another ip address else. my ifconfig is:

eth0 Link encap:Ethernet HWaddr 00:06:5B:5E:10:8D
inet addr:207.10.234.175 Bcast:207.10.239.255 Mask:255.255.248.0
inet6 addr: fe80::206:5bff:fe5e:108d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:394300 errors:0 dropped:0 overruns:1 frame:0
TX packets:3139 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:27426894 (26.1 MiB) TX bytes:547112 (534.2 KiB)
Interrupt:11 Base address:0x4c00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:340 errors:0 dropped:0 overruns:0 frame:0
TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:193256 (188.7 KiB) TX bytes:193256 (188.7 KiB)

I also another real wan ip address(it is dedicated server) which is 207.10.234.176.

What should I write to localip and remoteip?

---

