---
title: "Trunking/Bonding Wireless and Wired NIC"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by benpage26 on 2008-05-18
Hi,

I have heard of a technique called trunking or bonding, that enables multiple NICs to act as one, for failover / speed increases.   I don't know much about it other then the fact that it seems useful / interesting.

How useful/possible would it be to use this technique to join my wired NIC and my wireless card, they both connect to the same router, but at the moment i can only use one at a time.  Surely this would provide increase QOS control and such?  Anyone have any ideas?

Ben

---

### Post by SpaceTeddy on 2008-05-18
ethernet bonding only works on point-to-point connections, not on broadcast mediums. So, you can hook up two network card to a switch and then configure BOTH so they BOTH know that the two network cards act as one. 

For you, running two cables from your box to the router would work (if your router supports that feature, that is), but a wireless connection is ALWAYS a broadcast medium, this makeing it impossible to bond it together with anything else - because it is no point-to-point connection. 

in other words - i don't think your setup is possible.
please correct me if i am wrong :)

---

### Post by misha680 on 2008-12-17
So how would you combine bandwidth from a wireless and wired NIC that both have Internet access? It seems this should be possible...

Misha

---

