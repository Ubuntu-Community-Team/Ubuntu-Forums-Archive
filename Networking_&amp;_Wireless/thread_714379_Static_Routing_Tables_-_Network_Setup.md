---
title: "Static Routing Tables - Network Setup"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by hooper82 on 2008-03-03
Hi guys/girls,

I'm trying to setup a ubuntu 6.06 server box as a router between some subnets.

My network atm - 

Internt
  |
  |
  |
PPPOE (DHCP)
pfSence Firewall
192.168.30.1
  |
  |
  |
Core Network (192.168.30.0)
  |
  |
  |
eth0-192.168.30.2
==========Ubuntu Router==============
eth1-192.168.39.1                                        eth2-192.168.38.1
  |                                                                           |
  |                                                                           |
  |                                                                           |
Network 1 (192.168.39.0)                               Network 2 (192.168.38.0)



The Ubuntu router has 3 NIC's -
eth0 - 192.168.30.2
eth1 - 192.168.39.1
eth2 - 192.168.38.1

What should the routing table be on the ubuntu router?

I thought that I'd have to add routes on eth0 pointing to the  networks 1 and 2, like -
route add -net 192.168.39.0 netmask 255.255.255.0 gw 192.168.39.1 eth0
but you do that, and it spits out - SIOCADDRT: Network is unreachable

I must have missed something somewhere...can anyone help?

---

### Post by schmildo on 2008-03-03
If you're pinging from eth0 to a network attached to eth1, you'll need a route that goes in both directions  otherwise you wont get a response from the ping. You may have to staticly specify another route going the other way.

I'm not yet familiar with linux routing so I can't check your syntax unfortunately.

route add -net 192.168.30.0 netmask 255.255.255.0 dev eth0
route add -net 192.168.39.0 netmask 255.255.255.0 dev eth1
route add -net 192.168.38.0 netmask 255.255.255.0 dev eth2


I've grabbed this from the man page of route:
route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
	      adds a route to the network 192.56.76.x via "eth0". The Class  C
	      netmask modifier is not really necessary here because 192.* is a
	      Class C IP address. The word "dev" can be omitted here.

... and I understand 'via' to be "that's where the target network is located", and not applying a rule to an inbound interface like I think you might be trying. At a guess the above three commands might work, but not give you the control you want. I 'think' iptables is what you are looking for.

I'm sorry my answer isn't very neat; I'm not well versed in linux routing... yet. (still studying)

*Oh and I might be on the wrong track, but notice that i've removed the gateway parameter and changed eth0 to eth1.*

---

