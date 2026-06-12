---
title: "multi IP router setup on Ubuntu."
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by tomkk on 2013-09-10
Ok, I know that for some this might sound ridculisly simple but:

I've got a internet connection where service provider provided a block of IP's with additional WAN address. I'm connected via adsl pppoe passthrough modem and hot ppp0 interface with WAN IP. For ilustration purposes lets say that:
WAN: 1.1.1.1
ip range: 4.4.4.0 / 28
(so)
network: 4.4.4.0
gateway 4.4.4.1
some addresses 4.4.4.2 - 6
broadcast: 4.4.4.7

I've created eth0:1 - 6 interfaces with 4.4.4.1 - 6 addresses to have multiple virtual machines hanging on those. Now question is: how to resolve routing ? Am I right to assume that I only need to provide a routing entry for eth0:1 (with IP 4.4.4.1) which is a gateway for this network to pump everything through ppp0 (and other interfaces would automagically pump everything through this interface since those would be provided with gateway IP address of this card) ? If so I'm a bit puzzled on how to perform that - options are "ip" or "iptables" or even crude networks and providing gateway for eth0:1 being ppp0 ???? I'm clueless now.

---

