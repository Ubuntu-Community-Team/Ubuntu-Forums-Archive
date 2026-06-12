---
title: "Tranparent Packet Inpector"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by xcalie on 2008-07-31
Hi all,
I am wanting to setup a Transparent packet inspector and firewall that will act in between a switch and main xDSL router.
The whole network will be on the same range, and will roughly look like this

[CENTER]|*Internet*|
|
|
|*xDSL Router*|
10.1.1.1
|
|
|*Packet Inspector*|
|
|
|*Network Switch*|
|
|
|*Computers*|[/CENTER]

I am hoping that since the whole network is in the same subnet range, i should be able to use the
/etc/sysctl.conf
(Uncomment) #net.ipv4.conf.default.forwarding=1

And set the interfaces on the Packet Inspector as the IP range, and i should not have to setup the PC's behind the switch as using this as a gateway.
I am hoping to get this box to be able to slip in between the router and switch and just watch traffic without having to change gateway addresses.

Any comments or help is greatly appreciated!

---

