---
title: "routing through network interfaces"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Ev1L on 2008-08-20
Hi,
is it possible to force the routing through different network interfaces on the same machine?

In my specific case I have 2 physical interfaces eth1 (on internal network) and eth2 (on external network).
I created a virtual interface ifb0 and what I want is:

eth1 -> ifb0 -> eth2

instead of

eth1 -> eth2


Thanks

---

### Post by ilrudie on 2008-08-20
you can use the route command to force packets destined for a specific network (or all networks not otherwise specified) through a particular interface or gateway.

man route add

Its important to know that the route command is temporary in ubuntu and most *nix implementations.  when you reboot the routes will be gone.  to make them permanent add the routes to the proper stanza in /etc/network/interfaces using the up <routeing command> syntax.  For more info see man interfaces.

---

### Post by Ev1L on 2008-08-20
i tried with route, but i found only that i can define a gateway for all packets towards a network. it is not what i want because:
- i expected to do it without using IP on the virtual device, as the "tc" command does
- imagine i have a target network A. when i add a rule to route a packet for A to ifb0, then i need a rule to route the packet (still with destination A) to eth1, but i will have one destination and two rules (i tried, it loops)

keeping searching around i believe i could solve the problem with iptables, but i find only sparse information, in particular i can't find how to tell "forward all to interface ifb0"

---

### Post by ilrudie on 2008-08-20
So you have a virtual interface that doesn't talk on any networks?  Why?  What are you trying to accomplish?  Normally when people make a virtual interface it is bound to a physical interface it just answers to a different ip.  Id assumed that ifb0 just sat on eth2 and talked on his network.

---

### Post by Ev1L on 2008-08-20
ok, maybe starting from the beginning with the whole story could help (but it's a quite complicated scenario):
1 - i need to emulate network impairments on incoming traffic and i did this with "ts", which wants to create a virtual interface (ifb0) and insert impairments between eth1 and ifb0
2 - i need to measure such impairments (on RTP) with a monitor i have, which relies on SIP to detect ip:port
3 - i have openser+rtpproxy which change SDP for outgoing packets
4 - i have 2 real interfaces, one on local net, the other on outside world

so i use tc and the traffic goes:
eth1 -> ifb0 -> openser -> eth2 and it's ok.

the problem is that i would need now to do in the other direction:
eth1 <- ifb0 <- openser <- eth2
instead with tc i can't address from eth2 the same interface (overrides the other settings), without it skips directly from openser to eth1

i believe this could be done with iptables, because route is based on ip, while i rely on devices (right?)

unfortunately it's not an application layer problem (for which i would ask for help on openser forum), but low layer

---

### Post by ilrudie on 2008-08-20
I have never tried to set something like this up.  It seems like the openser forum might be a good place to ask about this as they probably set up simliar stuff.  ipfilters and tc seem like they should both be able to do this.  Seems like you should be able to set up different rules for inbound and outbound traffic with tc.  good luck.

---

### Post by bala.linux on 2009-03-18
> **Ev1L said:**
> ok, maybe starting from the beginning with the whole story could help (but it's a quite complicated scenario):
1 - i need to emulate network impairments on incoming traffic and i did this with "ts", which wants to create a virtual interface (ifb0) and insert impairments between eth1 and ifb0
2 - i need to measure such impairments (on RTP) with a monitor i have, which relies on SIP to detect ip:port
3 - i have openser+rtpproxy which change SDP for outgoing packets
4 - i have 2 real interfaces, one on local net, the other on outside world

so i use tc and the traffic goes:
eth1 -> ifb0 -> openser -> eth2 and it's ok.

the problem is that i would need now to do in the other direction:
eth1 <- ifb0 <- openser <- eth2
instead with tc i can't address from eth2 the same interface (overrides the other settings), without it skips directly from openser to eth1

i believe this could be done with iptables, because route is based on ip, while i rely on devices (right?)

unfortunately it's not an application layer problem (for which i would ask for help on openser forum), but low layer

I am also trying to forward my local traffic to different interfaces. 

Local -> VIP1 -> VIP2 -> ETH0

VIP1 - 192.168.20.1
VIP2 - 192.168.10.1
ETH0 - 59.x.x.x


I want to forward all my local traffic to pass through 2 virtual ips of different subnets and then to go out through eth0.

Could you please help me ?

Regards,
Bala

---

### Post by Ev1L on 2009-03-18
> **bala.linux said:**
> I am also trying to forward my local traffic to different interfaces. 

Local -> VIP1 -> VIP2 -> ETH0

VIP1 - 192.168.20.1
VIP2 - 192.168.10.1
ETH0 - 59.x.x.x


I want to forward all my local traffic to pass through 2 virtual ips of different subnets and then to go out through eth0.

Could you please help me ?

Regards,
Bala
if you want to do that in both directions, you are stuck at my same point :)

---

### Post by bala.linux on 2009-03-18
I want to do it in one direction but needs to get the reply for my request :)

I have used mark and different routing tables and tried to achieve the one direction. But got some arp message on both VLAN2 and ETH0. How did you setup for the one direction ?


Regards,
Bala

---

### Post by Ev1L on 2009-03-18
for one direction i used one of the tc examples on forwarding, creating a virtual ifb0
it was on some kind of wiki i guess, but it was over 6 months ago...

---

### Post by bala.linux on 2009-03-19
> **Ev1L said:**
> for one direction i used one of the tc examples on forwarding, creating a virtual ifb0
it was on some kind of wiki i guess, but it was over 6 months ago...

If you could remember its link or any pointer towards the solution would be a great help !


Regards,
Bala

---

### Post by Ev1L on 2009-03-19
[http://www.linuxfoundation.org/en/Net:Netem](http://www.linuxfoundation.org/en/Net:Netem)

look in the faq: How can I use netem on incoming traffic?

i started from that example

---

### Post by bala.linux on 2009-03-19
Thanks...
I need to forward my locally generated traffic to IFB...I am using marking and then forward to IFB...but it does not get routed to eth0...I need to verify it again ...

---

