---
title: "REPOST - Multiple Internet Connections"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by Boomgawd on 2005-04-16
Setup :

eth0 Link encap:Ethernet HWaddr 00:02:55:70:C8:C1
inet addr:192.168.0.101 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::202:55ff:fe70:c8c1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:52066356 errors:0 dropped:0 overruns:0 frame:0
TX packets:41438257 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3425001706 (3.1 GiB) TX bytes:1917211049 (1.7 GiB)

eth1 Link encap:Ethernet HWaddr 00:02:55:8B6:99
inet6 addr: fe80::202:55ff:fe8b:d699/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:12038030 errors:375 dropped:0 overruns:0 frame:375
TX packets:12725205 errors:0 dropped:0 overruns:0 carrier:0
collisions:117632 txqueuelen:1000
RX bytes:306665308 (292.4 MiB) TX bytes:4062338458 (3.7 GiB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:561412 errors:0 dropped:0 overruns:0 frame:0
TX packets:561412 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:43715633 (41.6 MiB) TX bytes:43715633 (41.6 MiB)

ppp0 Link encap:Point-to-Point Protocol
inet addr:216.239.81.84 P-t-P:216.239.80.244 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1492 Metric:1
RX packets:12032920 errors:0 dropped:0 overruns:0 frame:0
TX packets:12720138 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:41633568 (39.7 MiB) TX bytes:3782338650 (3.5 GiB)


Eth0 is local router with 5meg cable service - FAST but capped.
Eth1 is DSL 3 meg service, NO CAP not as fast.

I want azureus (port 49187) to use the DSL (Eth1) and everything else to use CABLE/ROUTER (Eth0)...

Right now traffic is default via DSL gateway.. I use firestarter as a firewall. I've been researching ROUTE2 and IPTABLES but its stumping me..

I would even be happy leaving the DSL as the default gateway but finding some way to point Firefox at the Router gateway..

Any help would be appreciated.

Boom.

-- Sorry for the re-post. Please delete the thread in Laptop --

---

### Post by soul_rebel on 2005-04-16
[http://lartc.org/](http://lartc.org/)

You'll need some reading I think. :)

---

### Post by aimaz on 2005-04-24
Routing by port number isn't easy, you have to use iptables and iproute2.
I am currently trying to do a similar thing but had no luck so far I have been reading this [http://linux-ip.net/html/adv-multi-internet.html](http://linux-ip.net/html/adv-multi-internet.html) hopefully you'll have more luck than I've had so far.

---

### Post by notch on 2006-10-10
I am also trying to get Azureus to use a seperate internet connection and have been unable to find a way.

I have tried messing with all the bind options but nothing seems to work.

---

### Post by mips on 2006-10-10
Stupid suggestion, i dont play around with firewalls much. Why not allow port 49187 on the one interface and block all other ports. On the second interface you do the opposite, block port 49187 and allow all other ports.

---

