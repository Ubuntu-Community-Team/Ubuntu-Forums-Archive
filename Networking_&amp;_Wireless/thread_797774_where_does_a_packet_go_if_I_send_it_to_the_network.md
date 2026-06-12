---
title: "where does a packet go if I send it to the network address?"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by CrazyGuy123 on 2008-05-17
If I send a packet to thge network address (ie. send a packet to 192.168.0.0 in a network with subnet mask 255.255.0.0), where will the packet go?

Does it get sent to the default gateway?  Does it get broadcasted to the whole subnet?

---

### Post by lemming465 on 2008-05-17
> **CrazyGuy123 said:**
> If I send a packet to the network address..
I'm not sure it even leaves your PC.  There shouldn't be any ARP response to identify an ethernet destination for it.
> Does it get sent to the default gateway?
No, only stuff which lacks a local route gets sent to the default gateway. Anything on the local subnet would be sent directly.

> Does it get broadcast to the whole subnet?
No, for that you need the address with all ones in the host part, e.g. 192.168.255.255 for a /16.

---

### Post by CrazyGuy123 on 2008-05-19
Cool thx.

I thought I'd try it, and it appears as if Linux treats the network address in exactly the same way as the broadcast address.  (ie. it sends packets with the IP header pointing to that address and the MAC header pointing to broadcast)

It seems odd that by design both the "all zeros" and "all ones" host addresses have the same effect.  I guess one must have some additional special purpose, otherwise it could just be used like any other address.  I'd be very interested in a more information if anyone knows the real reason.

Anyway - thats solved the problem for me.  A filter at my ISP blocks all packets to my netblock broadcast address, so now I can use the "all zeros" address instead.

---

### Post by lemming465 on 2008-05-19
Originally the all zeroes address was the broadcast address.  I don't recall offhand which internet RFC switched it to all ones.  Yes, some systems still treat both as broadcasts.

---

