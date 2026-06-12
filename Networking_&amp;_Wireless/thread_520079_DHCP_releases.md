---
title: "DHCP releases"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-08-07
Is a DHCP server supposed to stop processing data from a client once the client's IP has been released?

For example, if DHCP Server Y grants Client X an IP, and Client X releases that IP at some point, should Server Y continue processing data from that host anyway?

(I guess the question could also be reworded as: Does a DHCP server check its Clients table before routing data from the WAN.)

I would assume so, because otherwise how would it know what MAC address to use?

Right now I'm messing around with MAC addresses and DHCP leases on my Linksys router and checking to see what does or doesn't alter the router's DHCP clients table. Right now it seems that I released the DHCP lease on the router (it doesn't show on the table) but my computer can still access the Internet fine.

I'm wondering if the table the admin panel shows isn't just really delayed, because it seems to change for nothing.

---

### Post by kidders on 2007-08-08
Hi there,

> **B-Con said:**
> I guess the question could also be reworded as: Does a DHCP server check its Clients table before routing data from the WAN.DHCP has absolutely nothing to do with routing ... perhaps you are confusing it with something else. Although it has other uses, DHCP is chiefly a protocol used to distribute network configuration information. Packet routing is managed using a different, unrelated set of protocols.

To answer your question though, if a DHCP server were to stop processing requests from a client that had released its lease, there would be no way for it to re-acquire an address later.

---

### Post by B-Con on 2007-08-08
Oh, OK. Since the router has to keep a record of all the active DHCP releases, I wondered if it verified the source address of a host against that table before it processed a packet. Apparantly not, thanks.

---

### Post by kidders on 2007-08-08
Ah I see...

That seems like an odd sort of a thing for a manufacturer to do, since it would make networks administered by their products incredibly inflexible, without really achieving anything useful. Having said that, your particular router may well have such a facility ... the best thing to do is take a quick look at your manual ... but I doubt it.

---

