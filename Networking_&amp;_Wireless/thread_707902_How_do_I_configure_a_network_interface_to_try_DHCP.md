---
title: "How do I configure a network interface to try DHCP first?"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by SwordAngel on 2008-02-25
I am building my own Gutsy miniserver at home and will move it to be co-located at a data centre.

At home, I have a router, so the Gutsy machine gets its TCP/IP settings from the router's DHCP server. It appears, however, that the data centre will not have a DHCP server and that I would need to configure the network interface to static IP, subnet mask, gateway, and dns information.

To make the transition smoother, I am considering to configure the network interface to try DHCP first, and then set to some specific TCP/IP settings if and only if DHCP fails. Is that possible? How would I do that?

Alternatively, is it possible for the network interface to simultaneously use two sets of TCP/IP settings?

Sorry if I sound crazy. My networking knowledge is getting fuzzier everyday.

Thanks.

---

### Post by Iowan on 2008-02-25
My networking knowledge seems to be getting fuzzier, too.  I remember reading about "aliasing", but I don't remember if the interface could have two addresses in the same subnet (I don't think so...).

---

### Post by SwordAngel on 2008-02-26
> **Iowan said:**
> My networking knowledge seems to be getting fuzzier, too.  I remember reading about "aliasing", but I don't remember if the interface could have two addresses in the same subnet (I don't think so...).

Thanks Iowan. Googling 'network interface alias' turned up some good hints.
Now the only thing that remains is how adding the dns server addresses, which does not seem to be doable from the /etc/network/interfaces file.

---

