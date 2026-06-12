---
title: "how to create a wifi network?"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2006-07-25
Hi,

I am using a Apple Powerbook (TiBook), and I want to create a wifi network, so that other people can join it (ultimately, I want to share my internet connection with people on the wifi network).

How can I create a wifi network?

Max.

---

### Post by Ares Drake on 2006-07-25
Hey,
the best and easiest way is to go for a wireless router. It creates a wifi network and shares your internet connection. Those wifi routers cost about 50€.
To create a wifi network **without** such a router, you would need to get your wireless network card in your Powerbook to act as access point (wich only works with special drivers) and install some routing software / ip table rules. And besides, the other people on your network could only use the internet as long as your own Powerbook was powered on.

So its well worth the money to get a dedicated wifi router, many of them are linux powered as well.

---

### Post by davidmaxwaterman on 2006-07-25
> **Ares Drake said:**
> Hey,
the best and easiest way is to go for a wireless router. It creates a wifi network and shares your internet connection. Those wifi routers cost about 50€.
To create a wifi network **without** such a router, you would need to get your wireless network card in your Powerbook to act as access point (wich only works with special drivers) and install some routing software / ip table rules. And besides, the other people on your network could only use the internet as long as your own Powerbook was powered on.

So its well worth the money to get a dedicated wifi router, many of them are linux powered as well.

OK, so some additional info is necessary.

Yes, a dedicated router would be ideal, but they're not available in my country yet (China) for the access I want to use (CDMA).

In the meantime, we have the PCMCIA card and use it with my laptop to connect to the internet. I had thought it would be a simple matter to share the CDMA connection via my wifi card, since it's trivial with OS X, but it seems not to be.

I have firestarter installed which can do the routing/etc for me, but I need to be able to create the wifi network so that others can join it.

Any ideas? I was looking into hostapd (host access point daemon), but I haven't gotten anywhere with it yet. Perhaps it doesn't work with my Powerbook's wifi card...but I haven't tried very hard, since I've been too busy.

---

### Post by Ares Drake on 2006-07-26
Hostap is definetely able to deliver what you want. You can find it's site here: [http://hostap.epitest.fi/](http://hostap.epitest.fi/)
However it only works with Prism chipset based network cards and as far as I know, Apple uses Broadcom based ones. So you would probably need another USB or PCMCIA WLAN Card with Prism chipset to get hostap running.

---

