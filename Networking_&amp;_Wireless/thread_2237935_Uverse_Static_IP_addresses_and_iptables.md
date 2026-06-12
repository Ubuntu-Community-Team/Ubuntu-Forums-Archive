---
title: "Uverse Static IP addresses and iptables"
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2014-08-04
I have ATT Uverse and a block of static IPs. The router ATT requires you to use cannot do IP mapping (IP forwarding) the only thing it can do is port forwarding. It does allow you to configure a router behind the router. 

I have configured iptables to do one to one NAT. it appears to work from outside the network. Below is an edited version of the iptables save.

> *nat
:PREROUTING ACCEPT [460:32156]
:INPUT ACCEPT [473:32964]
:OUTPUT ACCEPT [200:13810]
:POSTROUTING ACCEPT [14:830]
-A PREROUTING -d x.y.z.97/32 -j DNAT --to-destination 192.168.1.1
-A PREROUTING -d x.y.z.98/32 -j DNAT --to-destination 192.168.1.2
-A PREROUTING -d x.y.z.99/32 -j DNAT --to-destination 192.168.1.3
-A PREROUTING -d x.y.z.99/32 -j DNAT --to-destination 192.168.1.3
-A PREROUTING -d x.y.z.100/32 -j DNAT --to-destination 192.168.1.103
-A PREROUTING -d x.y.z.101/32 -j DNAT --to-destination 192.168.1.71
-A POSTROUTING -s 192.168.1.1/32 -j SNAT --to-source x.y.z.97
-A POSTROUTING -s 192.168.1.1/32 -j SNAT --to-source x.y.z.97
-A POSTROUTING -s 192.168.1.1/32 -j SNAT --to-source x.y.z.97
-A POSTROUTING -s 192.168.1.2/32 -j SNAT --to-source x.y.z.98
-A POSTROUTING -s 192.168.1.3/32 -j SNAT --to-source x.y.z.99
-A POSTROUTING -s 192.168.1.103/32 -j SNAT --to-source x.y.z.100
-A POSTROUTING -s 192.168.1.71/32 -j SNAT --to-source x.y.z.101
-A POSTROUTING -o eth4 -j MASQUERADE
COMMIT

What I can't get to work is for the machines inside the network to access the webserver on these machines. I can ping them using either IP address, I can log in using ssh but I can't access the webserver on them or other services. They just hang. I would like users to be able to access these services using the same url both in the office and outside it.

I know I am missing something here but I stumped for the moment.

---

