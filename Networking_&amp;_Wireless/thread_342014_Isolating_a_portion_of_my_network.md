---
title: "Isolating a portion of my network"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by pbaehr on 2007-01-19
I have seven or eight computers in my network. Currently, they are all connected to one router which is connected to a cable modem. Some of the computers pass through a switch, others have a direct hookup to the router. Still others are wireless. Some of them run Windows, some of them run Ubuntu.

Ultimately, I want to split this into two functional networks which cannot communicate with one another, but share an access point to the internet. So, basically Network A would not be able to see Network B, but both would be able to access the internet through one main router.

Do any network gurus have any thoughts on how I can accomplish this? Is this something that can be solved with configuration of the existing network or does it require additional hardware?

Let me know if you have a suggestion or a resource you can point me to to help me get started. Thanks!

---

### Post by Iowan on 2007-01-19
Sounds like something the router *should* be able to handle.  Mine is a '486 dial-up router running [FREESCO]("http://www.freesco.org/") - which can handle up to 10 subnets.  The easiest way to split subnets on FREESCO would be to use multiple ethernet cards.  IIRC, it (FREESCO) could even serve as DHCP server for these subnets.  If your router has multiple ports, I suspect it could do the same.

---

### Post by mips on 2007-01-19
Turn a PC with 3 NICs into a router.

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Adapt the above to your needs.

---

### Post by pbaehr on 2007-01-19
So I assume from the replies that subnetting would accomplish what I want to do? I've never set up a network in a way that *prohibits* computers from seeing each other. In fact, I always aim to do the exact opposite.

---

### Post by mips on 2007-01-19
> **pbaehr said:**
> So I assume from the replies that subnetting would accomplish what I want to do? I've never set up a network in a way that *prohibits* computers from seeing each other. In fact, I always aim to do the exact opposite.

Yes.

---

### Post by koenn on 2007-01-19
> **pbaehr said:**
> So I assume from the replies that subnetting would accomplish what I want to do? I've never set up a network in a way that *prohibits* computers from seeing each other. In fact, I always aim to do the exact opposite.

subnetting will create 2 separate networks. That's the start. 
computers on different networks (or subnets) can not communicate to each other, unless there's a router to provide a route between the networks. Considering internet as yet another network, there are several scenario's:

1- your router has 3 interfaces 
That would be 1 WAN interface (connect to internet) and 2 (or more) LAN interfaces - 1 for each local network you want to connect.
In this scenario, the router will probably provide routes to each network, allowing both LANs (subnets) to access internet, but also allow communication between the LANs. 
That's not what you want. You would have to configure the router so that no route exists between LAN A  and LAN B.
This scenario is what you'd expect from a "rea"l router, but it is probably not the case for a "home" router. 
Consider this : each computer would need a default 'gateway' in its own network. With 2 networks, your router needs 2 IP addresses ( not counting the IP address on the internet side) to be able to be the gateway for 2 separate networks. If it doesn't support this, it does not have 2 LAN interfaces. 

2- your router has 2 interfaces.
that is : 1 WAN, 1 LAN. you may see 4 or more LAN ports, but these you should regard as if it was a 4 (or more) ports hub or switch connected to 1 LAN interface of the router
You can only provide 1 gateway address (to multiple computers) - so you can connect no more than 1 network to it.
The workaround here would be to replace the router with a 3-way router, either something you buy or something you build out of an old computer with 3 network cards.
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)

This puts you back in scenario 1 and you need to delete the route between LAN A and B, or (if the router is a linux box) set iptables rules to block communication between LAN A and LAN B


3- 2 interfaces, but 3 networks.
(this works in theory and on some routers, but not necesarilly on the one you have).
the WAN interface connects to the internet.
You have 1 LAN interface (possibly with multiple ports and/ or a switch attached)? Remember that all of those ports are considerd ports on a switch or hub, so no route exists between them. You could connect 2 subnets (i.e. some computers with IP addresses from network A, some others with IP addresses from network B) to the same switch, and they would not be able to talk to each other (eg a ping would return "network unreachable)
now, if your router supports it, you can set 2 different ip addresses to the 1 LAN interface
allowing the router to be a gateway (i.e. router) for both LANs : both LANs will be able to connect to the internet, but can not reach each other - unless your router by default adds an additional route between the 2 IP addresses on the same interface; this is something you should check. 

Welcome to the world of networking  :-)
So, if you can figure out which scenario applies to your situation, you can design a sollution accordingly.

---

### Post by pbaehr on 2007-01-22
Koenn,

Thanks for taking the time to write such a detailed response. It's extremely helpful.

From what you've written it sounds like I'll need a more involved router. My setup currently falls under the second example you provided. Maybe if I can find enough spare parts laying around I'll build a router. I've never administered something more complicated than your basic run of the mill Linksys or Netgear router so it will be an adventure, I'm sure.

Good to know I can come here for more help if I need it though. Thanks, again!

---

### Post by koenn on 2007-01-22
Building a router is not as hard as it looks - the biggest part is to get a computer working with 3 network cards (but should be easier now that hardware recognition is more advanced) and figure out which is which (where to plug in LAN A, where to plug the internet connection, etc). The routing is very basic, linux solves most or all of it by itself. iptables, should you want or need it, is not too hard to configure once you understand how it works. 

And in the process, you'll learn the basics of how networking works. 
Have fun.

---

### Post by mips on 2007-01-22
If your are uptight about security have a look at OpenBSD with Packet Filter etc. Firewall Builder gives you a nice and easy configuration ool.

---

