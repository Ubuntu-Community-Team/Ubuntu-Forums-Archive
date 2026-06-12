---
title: "Routing public subnet"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by funkgui on 2008-01-28
Hi guys, I've got this problem that I'm not able to work out:

I've got a public 8 address subnet that I would like to route from a linux box.

I'm able to set all 5 real address (the others are the net, the broadcast and the router) and redirect to lan machine with port forwarding but the problem is when my internal machine reply using the router gateway masqueraded because the resulting address when going out is always one of the five.

I try to well explain the problem:

I need the router machine to route correctly every ip address port forwarded to internal machine with the right ip so if I route myFirstIp:80 to internal machine the internal machine must reply to request with myFirstIp address, if I ruote mySecondIp:80 to another internal machine this new internal machine must reply to request using mySecondIp address.

Is this possible?

thanx
mARCO

---

### Post by funkgui on 2008-01-30
Hi guys,

maybe I was wrong with the question, in fact after another try with another public subnet I've noticed that with this configuration I do not have the reported problem.

2 NIC:

first one (eth0) attached to WAN and with 5 alias one for every public ip;
second one (eth1) attached to LAN with a single private ip (LAN_IP_ROUTER);

Iptables configured with masquerading active on PUBLIC NIC eth0;
port forwarding 

ex: 
iptables -t nat -A PREROUTING -p tcp --dport 80 -d PUBLIC_IP_1 -i eth0 -j DNAT --to LAN_IP_1:80
iptables -t nat -A PREROUTING -p tcp --dport 80 -d PUBLIC_IP_2 -i eth0 -j DNAT --to LAN_IP_2:80

and LAN_IP_1, LAN_IP_2 configured with gateway address setted to LAN_IP_ROUTER

And this all work fine

mARCO

---

