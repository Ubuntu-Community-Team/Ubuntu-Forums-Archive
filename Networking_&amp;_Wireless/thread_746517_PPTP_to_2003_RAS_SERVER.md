---
title: "PPTP to 2003 RAS SERVER"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by opteron180 on 2008-04-05
Hi,
I ma using Ubuntu 7.01 and I am able to establish a PPTP VPN connection to 2003 RAS server, however, I am not able to access remote resources and ping IP.

IFCONFIG log:
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.1.51  P-t-P:192.168.1.50  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:4188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3230722 (3.0 MB)  TX bytes:988711 (965.5 KB)

As you can see, the subnet mask is incorrect. Will it be a problem? If so, how to change it?
Thanks.

---

