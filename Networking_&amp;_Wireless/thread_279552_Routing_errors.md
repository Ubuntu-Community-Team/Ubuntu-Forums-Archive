---
title: "Routing errors"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by misse- on 2006-10-18
Hi, I'm trying to configure a mini-wan for a shool project but can't get my routers to forward traffic as it seems.

[http://misse.misse.org/routrar.jpg](http://misse.misse.org/routrar.jpg) <-- Here's a picture of the physical setup (note the typo on router 4's host2 ip .118, it's .18)

Host1 = eth1
Host2 = eth2

Every router can ping both of the routers directly connected to eachother, but router1 can't ping router3 by going through router2.

I've tried to change rotuer1s' routing-table by setting .6 as the gw for the network 200.100.50.8, but it doesn't seem to understand that 200.100.50.10 belongs to that network. When I tried to add a route for the host 200.100.50.10, I couldn't edit the netmask of that host, and so it was 255.255.255.255 instead of 255.255.255.252 as intended. Furthermore I've tried to edit the iptables on router2 but no luck. 

ip_forward=1 

Help is much appreciated :).

---

### Post by mips on 2006-10-18
The subnet mask has to be 255.255.255.252.

Post the output of route -n & ifconfig -a for all your boxes. Your diagram makes me dizzy.

Why not just use a classless routing protocol like ospf and forget about static route ?

---

### Post by misse- on 2006-10-18
I'll post everything the next time I get access to the routers (physically unreachable) which probably would be this friday. As to why I've tried static routes; I don't know better :P that's why I'm asking you :)

---

### Post by misse- on 2006-10-20
Router1

eth1: 200.100.50.5
netmask: 255.255.255.252
network: 200.100.50.4
broadcast 200.100.50.7

eth2: 200.100.50.18
netmask: 255.255.255.252
network: 200.100.50.16
broadcast 200.100.50.19

Router 2

eth1: 200.100.50.9
netmask: 255.255.255.252
network: 200.100.50.8
broadcast 200.100.50.11

eth2: 200.100.50.6
netmask: 255.255.255.252
network: 200.100.50.4
broadcast 200.100.50.7

Router 3

eth1: 200.100.50.13
netmask: 255.255.255.252
network: 200.100.50.12
broadcast 200.100.50.15

eth2: 200.100.50.10
netmask: 255.255.255.252
network: 200.100.50.8
broadcast 200.100.50.11

Router 4

eth1: 200.100.50.17
netmask: 255.255.255.252
network: 200.100.50.16
broadcast 200.100.50.19


eth2: 200.100.50.14
netmask: 255.255.255.252
network: 200.100.50.12
broadcast 200.100.50.15

---

### Post by misse- on 2006-10-20
Router1

eth1: 200.100.50.5
netmask: 255.255.255.252
network: 200.100.50.4
broadcast 200.100.50.7

eth2: 200.100.50.18
netmask: 255.255.255.252
network: 200.100.50.16
broadcast 200.100.50.19

Router 2

eth1: 200.100.50.9
netmask: 255.255.255.252
network: 200.100.50.8
broadcast 200.100.50.11

eth2: 200.100.50.6
netmask: 255.255.255.252
network: 200.100.50.4
broadcast 200.100.50.7

Router 3

eth1: 200.100.50.13
netmask: 255.255.255.252
network: 200.100.50.12
broadcast 200.100.50.15

eth2: 200.100.50.10
netmask: 255.255.255.252
network: 200.100.50.8
broadcast 200.100.50.11

Router 4

eth1: 200.100.50.17
netmask: 255.255.255.252
network: 200.100.50.16
broadcast 200.100.50.19


eth2: 200.100.50.14
netmask: 255.255.255.252
network: 200.100.50.12
broadcast 200.100.50.15

--------------------------------------------------------

router 1 route
200.50.100.4 * 255.255.255.252 eth1
200.50.100.16 * 255.255.255.252 eth2

ETC.

A friend tipped me of using routed, but it's not freking in any repository. Does anyone know how to get routed or a good replacement app?

---

