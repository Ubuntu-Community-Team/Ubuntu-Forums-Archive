---
title: "Firestarter with multiple subnets"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by aaronmack on 2007-06-25
I have a dual NIC box with firestarter on it.  The local subnet on the NIC is 10.0.0.x and NAT works with other machines also on that subnet.  I also have the subnets 192.168.0.x and 192.168.1.0 that get routed to that box as their gateway, however firestarter doesn't NAT them, it just ignores them and blocks the packets.  The events do show up on the blocked events list.

I've read a little bit about how to tell firestarter about additional NICs on local subnets, but can't find any info about NAT'ing local traffic from different subnets onto the single NIC.

I can successfully ping all the subnets from Ubuntu, so I do have the routing table configured correctly.  Any ideas?

---

