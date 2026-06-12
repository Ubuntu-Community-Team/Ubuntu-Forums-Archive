---
title: "Reroute all traffic to IP through remove server using iptables"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by alimovz on 2013-11-26
I have a private network 192.168.0.0/24

I have a router (192.168.0.1) between the network and the Internet running iptables.

I need, using iptables, to route all traffic coming out of the private network to 38.92.15.88(Remote Server) through 18.22.54.178(Test Box). Please see the diagram below.

[http://postimg.org/image/dehwvndg7/](http://postimg.org/image/dehwvndg7/)

How can I do that without having to set up a VPN on test box? I essentially want to make test box my router's gateway to Remote Server.

Another important question is how would I configure 18.22.54.178(Test Box)?

Thank you.

---

