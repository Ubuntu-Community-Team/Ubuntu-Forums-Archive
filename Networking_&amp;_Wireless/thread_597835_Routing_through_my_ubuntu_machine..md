---
title: "Routing *through* my ubuntu machine."
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by paul.drover on 2007-10-30
Ok, I'm not a networking guy. But I have a bunch of spare bit and a little knowledge - a dangerous combination. I have an idea, but I wanted to poll the collective before I started tearing machines apart.

I've my Ubuntu 7.10 accessing the internet through the DSL router supplied by my service provider. It works fabulously (my wife's XP machine is also connected to another port on the same router). I'm also working on reviving several old machines by installing Linux. An internet connection would be handy in assisting the OS installation on these machines as I get to them (I'll be doing only one at a time, so only one extra connection is needed).

The question: Can I insert a second network card (which I have available) into my Ubuntu machine, connect that to the network card in the old machine I'm trying to revive and have my Ubuntu machine serve internet traffic to the old machine? Do I need a special cable for a direct connection? It makes sense to me that I should be able to. Can any one give me an idea of the feasibility, complexity, advisability of such an undertaking?

Thanks all,
Paul.

---

### Post by paul.drover on 2007-10-31
Atypical silence. I guess I'll just try it and see what happens.
Paul.

---

### Post by dmizer on 2007-10-31
you only have two ports on your router?

if you have no spare ports on your router, your best solution will be to purchase a network hub (only slightly more expensive than another network card).  by using a hub instead of a second network card, you'll save yourself the headache of trying to configure internet connection sharing.

here's the howto on internet connection sharing:
[https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

---

### Post by paul.drover on 2007-10-31
Thanks for the info Dmizer. I appreciate that the router solution is likely the easiest one. But I'd like to do the direct connect for two reasons:
1. Pure academics, just to see if I can. There's a mountain there, let's climb it.
2. I have the network cards already. 

So thanks a bunch for the link. It'll be useful.

You wouldn't happen to know if I need a special cable, would you? I'm thinking back to my early days of messing with serial cables and the requisite null modem to connect two machines together. Is there a similar situation with ethernet cables?

Thanks,
Paul.

---

### Post by paul.drover on 2007-10-31
Never mind about the cable question. It was as simple as googling "ethernet pinout". Apparently I will need a "cross-over" cable. Now, where are my wire cutters?
Paul.

---

