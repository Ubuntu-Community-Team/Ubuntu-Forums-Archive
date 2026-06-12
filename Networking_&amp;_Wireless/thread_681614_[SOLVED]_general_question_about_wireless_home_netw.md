---
title: "[SOLVED] general question about wireless home networking"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by erfahren on 2008-01-29
There's something I don't understand about wireless home networking.

If you have a router with a wireless access point are you able to set it up so that the wireless devices (laptop) can connect to the internet *as well as* network with the other computer(s)?

If a desktop is connected to the router by ethernet can it be set up so that a wireless laptop can network with the desktop as well as be able to connect to the internet through the wireless access point?

In other words (see image) - how does the laptop (Computer 2) network with the desktop (Computer 3) through the router *and* be able to connect to the internet. Is the router just able to arrange that?

[IMG]http://img525.imageshack.us/img525/7479/wirelessdiagram1sn7.jpg[/IMG]

It may be a dumb question but I don't have any experience in this. Thanks for any information.

---

### Post by schallstrom on 2008-01-29
In short: Yes, the wireless router is able to arrange this.

Maybe it helps you to think of the wireless router as two devices which are just placed into the same box: a wireless access point, which just handles the transition from wireless ethernet to wired ethernet, and a router. A router is a device, which is able to "look" into the IP packets, make routing decisions based on these addresses and change their source and/or destination addresses if configured to do so. In networking terms one says, a router is a "layer-3 device" because it operates mainly on the IP protocol, which is located at layer 3 of the OSI model. And the router can forward packets from each interface to any other interface it has, i.e. "in any direction".

If you want to read on I would propose [http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)

---

### Post by erfahren on 2008-01-29
> **schallstrom said:**
> In short: Yes, the wireless router is able to arrange this.

Maybe it helps you to think of the wireless router as two devices which are just placed into the same box: a wireless access point, which just handles the transition from wireless ethernet to wired ethernet, and a router. A router is a device, which is able to "look" into the IP packets, make routing decisions based on these addresses and change their source and/or destination addresses if configured to do so. In networking terms one says, a router is a "layer-3 device" because it operates mainly on the IP protocol, which is located at layer 3 of the OSI model. And the router can forward packets from each interface to any other interface it has, i.e. "in any direction".

If you want to read on I would propose [http://en.wikipedia.org/wiki/OSI_model](http://en.wikipedia.org/wiki/OSI_model)
that explained it well - thank you. None of the guides I found went into that very much. 

thanks!

---

