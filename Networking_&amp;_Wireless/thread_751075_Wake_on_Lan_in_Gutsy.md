---
title: "Wake on Lan in Gutsy"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by AkuTenshi on 2008-04-10
Hi, i have set up wake-on-Lan so that it works perfectly from within my local netork, but i cant get it to work past my router (a draytek vigor 2900v). I have the port redirect using NAT, but no luck. Do i need to somehow have it link my MAC address?  Thanks in advance.

---

### Post by mal on 2008-04-10
Some comments that might be of use:

- Not all routers allow the wake on lan "magic" packets to pass through.  If this is the case with your router, I am not aware of a solution.

- I think you would need to forward the wake on lan packet through to the broadcast address (eg 192.168.0.255).

- The mac address needs to be part of the wake on lan packet, but is not part of the port forwarding process.

- You will find a fair bit of information around the web to help with setting up wake on lan arrangements.

Hope this helps.

Mal

---

