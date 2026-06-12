---
title: "Network inside a network"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by crazy_fox on 2006-10-12
Greetings..

I have a network inside another network. To go into more detail, i bought a router/modem (not using its modem capabilities) and i have connected 3 computers on it. Then i have the forth slot connect to the other lans slot, that takes me to the the other router.

Now, if i set the default gateway of one of the computers to see the other lans gateway, i can connect to WAN, but if i use our lans router as a gateway, i can see the other 2 computers of my lan.

What i wish to do though is to use be able to use both WAN, and my LAN at the same tame.. is this possible?

Thanks in advance..

---

### Post by Ben Armston on 2006-10-12
The way I would do it would be to set up all of the computers on the LAN to have the router/modem as the default gateway and then set the router/modem to have the other router as its default gateway. You should be able to change the default gateway on the router/modem through whatever interface it provides.

---

### Post by crazy_fox on 2006-10-12
Yeah, i saw the interface of setting up the gateway of the router..

It had three fields, Gateway, destination, and netmask.. Is that right?
What would destination be if so?

---

