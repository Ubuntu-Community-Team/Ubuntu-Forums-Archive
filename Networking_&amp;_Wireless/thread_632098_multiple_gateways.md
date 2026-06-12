---
title: "multiple gateways"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by mudcow007 on 2007-12-05
Hello all

is it possible to have more than one gateway on the one nic?

im looking at the interfaces file coudl i just add another gateway underneath of the other gateway?

basically like this:

192.168.0.30           ip address
255.255.255.0         Subnet
192.168.0.32          Gateway
192.168.0.33          Gateway


Thanks

---

### Post by jonallport on 2007-12-05
There's no problem with having multiple gateways, you just need to decide how to use them.  Are they for fail-over, load balancing, agregation, are there different services available through each one?

You may need to use 'route add 0.0.0.0 gw W.X.Y.Z metric N' in /etc/rc.local rather than using /etc/networking/interfaces.

Without knowing what you're tring to achieve it's difficult to advise.

Typically I would expect see multiple gateways on the 'head-end' network of a multi-site setup. i.e. .32 is a router connected to (an)other site(s), .33 is a router to the ISP.  In this scenario I would pick ONE of them to be my default route and sort the rest out in the routing tables of THAT router.  Otherwise you have to put static routing tables on each client - yawn!

Please post more and I'll endevour to help.

---

