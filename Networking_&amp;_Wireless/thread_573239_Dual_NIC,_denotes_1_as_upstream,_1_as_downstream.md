---
title: "Dual NIC, denotes 1 as upstream, 1 as downstream?"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by Oshaka on 2007-10-11
Hello

I have currently 2 NICs in one of my servers. They each have an WAN IP , which both IP's are on the same network and use the same gateway. 

I can ping both and can ping from both. 

But... When I run say, Iptraf it shows eth0 as only outgoing packets and eth1 only shows incoming packets. 


What can I do to fix this? I want to have both running full-duplex and both being able to send in/out to their specific IP

---

### Post by kryliss on 2007-10-12
Check to see that only one of the interfaces has a gateway setup, otherwise it might be "confusing" the system.

---

