---
title: "Virtual NICs with different hwaddr - possible or not?"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Roidhun on 2007-05-31
Hi
I have 5 (public) ip-addresses assigned to me via DHCP, based on the NIC hwaddr's. I was wondering whether it would be possible to get them all assigned to the same physical NIC. I envision something like this in /etc/network/interfaces:

    iface eth0:1 dhcp hwaddr xxxxxx
    iface eth0:2 dhcp hwaddr xxxxxx

and so on - I'm sure you get the idea, but will it work?

Regards
Bjarne

---

