---
title: "WPC300N + Ndis = time out problem after an hour"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by sapincher on 2008-05-03
My computer has a WPC300N Linksys router, and the drivers that Linksys has are awful. In windows, they make the card use about 50% of the processor in bursts for no reason at all. Broadcom has compatible drivers called bcmwl5.inf and BCMWL5.SYS. 

I have Ubuntu installed while I work out some kinks in my hard drive partitioning that make it impossible to boot windows, and I would like to have the wireless working properly. When I load the bcmwl5.inf file into ndiswrapper, the wireless card works perfectly for an hour or so. It even shows that it has full 802.11n transfer speeds (though I haven't tested it out).

However, after that short period of working perfectly, the wireless card just cuts off all network transmissions. I can still see the network name in Wicd and it still shows that I am connected to my delightfully unsecured wireless network(with even a dBm signal strength rating), but I can not do anything involving the network, such as internet or even pinging the router. This problem goes right away the second I reinstall the bcmwl5.inf driver into ndiswrapper again and reconnect to the network. But, then I only have just another hour of connectivity.

What are your takes on this situation?

---

### Post by sapincher on 2008-05-10
Can I bump this, because I am still having the same problem. I really need an answer...

---

### Post by sapincher on 2008-05-11
Whatever, I am just going to have to buy a new card, I guess. I've gone through at least seven different drivers for the card and three versions of Ndiswrapper. I am absolutely positive the card is not defective. 

Thank you for your wonderful help.

---

