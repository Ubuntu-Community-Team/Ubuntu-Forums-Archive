---
title: "Bonding - transfer rate"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by idefixgallier on 2007-08-21
Hi!

I enabled bonding with 2 100 Mbit cards, connected to a hp procurve switch
- both ports are trunked

The result is a nearly doubled transfer-rate from the server, but still 100 Mbit
to the server (thats not what I want, because this is a backup server and it needs
"incoming" transfer rate)

Can anyone give me a hint please?

lg
Martin

---

### Post by nodows on 2007-08-21
I'm having trouble figuring out your post.  Do you have two nics bonded
on the server side or the client side?  And if its on the server side like I
would hope if you're only putting 100Mbit into it from the  client side then
that would explain it.  However if you either have 1)multiple machines on
the client side to send info to the server or 2) another client with bonded 100
Mbit nics to send info at that rate (which by the way is not really achievable
from a regular hard drive), then it might just be that your switch is kinda cheap
or broken (maybe doens't support more than 100Mbit in both directions/? who knows)

I've seen some switches refuse to send the same amount of data two different
directions--I think due to these new "smart" switches that think they know where
to send traffic.  If you've got an older "dumber" one you could try that, or get out 
a gigabit one and just go gigbit on all sides.

---

### Post by netztier on 2007-08-22
> **idefixgallier said:**
> Hi!

I enabled bonding with 2 100 Mbit cards, connected to a hp procurve switch
- both ports are trunked

The result is a nearly doubled transfer-rate from the server, but still 100 Mbit
to the server (thats not what I want, because this is a backup server and it needs
"incoming" transfer rate)

Can anyone give me a hint please?

lg
Martin

That's normal and the way switches (normally) implement link bundling. A link bundle of n 100mbps links is not a n00mbps link, but n times a 100mbps link. Like an Autobahn with the same speed limit, but more lanes.

When the switch sends an Ethernet frame out of the aggregated port, it has to determine which link to actually use. 

Normally, it will pick some of the last bits of the source and destination MAC address of the frame,  XOR them and then modulo-divide by the number of links present in the bundle (I think that's the algorithm, but I'd have to look it up). In any case, the result is a binary number that represents the link number to use. If there's two links, one bit is used, with four links it's two, with four to eight links its three bits etc.

So you're probably not going to see more than 100mbps for any single connection *to* that server. If you have multiple connections to that server, you're probably going to see more than 100mbps in *total* (but not for any *individual* connection - provided that the MAC-Address based XOR-calculation results in a different value for each connection.

The fact that the server can send out at 2x100mbps might be due to the server doing round-robin distribution instead of calculating per MAC-address pair. The Linux bonding driver has some capabilites that you won't find in an Ethernet switch.

Two advices I can give you:
[LIST]
[*] make sure to use multiple simultaneous connections to that server in a way that the switch's MAC-address based link distribution mechanism can be effective
[*] for a handful of $ or &#8364;, get a gigabit interface for the backup server (only if your LAN switch has Gigabit ports, of course). This is by far the most simple and straightforward solution without complexity issues.
[COLOR="Gray"][*] check if the switch can be configured to do round-robin distribution on the link bundle - although I doubt that this is possible.[/COLOR]
[/LIST]

best regards

Marc

---

### Post by idefixgallier on 2007-08-24
Hi!

Thank you for your replies

@nodows 

I have bonded two NIC's at the server side and I test from an
"real" 1000Mbit Nic

@Netztier
Thats what I am "afraid" of, the problem is, I only have 2 
Gbit Ports at the Procurve and I don't wanted to buy another
hardware for that so bonding with the existing devices seems
a good solution

lg
Martin

---

### Post by netztier on 2007-08-24
> **idefixgallier said:**
> Hi!
Thats what I am "afraid" of, the problem is, I only have 2 
Gbit Ports at the Procurve and I don't wanted to buy another
hardware for that so bonding with the existing devices seems
a good solution


I don't think you can modifiy the traffic distribution behaviour for a link bundle on a HP Procurve - I started to look around and found something that applies to the 2600 series switches. I don't know what model you actuall have, but I think this will be similar for all ProCurve products.

See Page 26 of this document: [ftp://ftp.hp.com/pub/networking/software/Mgmt-Oct2005-59906023-Chap12.pdf](ftp://ftp.hp.com/pub/networking/software/Mgmt-Oct2005-59906023-Chap12.pdf)
[SIZE="1"](found on: [http://www.hp.com/rnd/support/manuals/2650_6108.htm](http://www.hp.com/rnd/support/manuals/2650_6108.htm))[/SIZE]

[INDENT]> [SIZE="1"]**Outbound Traffic Distribution Across Trunked Links**

Both trunk group options (LACP and Trunk) use source-destination address pairs (SA/DA) for distributing outbound traffic over trunked links. SA/DA (source address/destination address) causes the switch to distribute outbound traffic to the links within the trunk group on the basis of source/destination address pairs. 

That is, the switch sends traffic from the same source address to the same destination address through the same trunked link, and sends traffic from the same source address to a different destination address through a different link, depending on the rotation of path assignments among the links in the trunk. 

Likewise, the switch distributes traffic for the same destination address but from different source addresses through different links. Because the amount of traffic coming from or going to various nodes in a network can vary widely, it is possible for one link in a trunk group to be fully utilized while others in the same trunk have unused bandwidth capacity even though the address assignments are evenly distributed across the links in a trunk. 

In actual networking environments, this is rarely a problem. However, if it becomes a problem, you can use the ProCurve Manager Plus network management software to quickly and easily identify the sources of heavy traffic (top talkers) and make adjustments to improve performance.

Broadcasts, multicasts, and floods from different source addresses are distributed evenly across the  links. As links are added or deleted, the switch redistributes traffic across the trunk group. For  example, in figure 12-12 showing a three-port trunk, traffic could be assigned as shown in table 12-6.
...
[/SIZE][/INDENT]

---

