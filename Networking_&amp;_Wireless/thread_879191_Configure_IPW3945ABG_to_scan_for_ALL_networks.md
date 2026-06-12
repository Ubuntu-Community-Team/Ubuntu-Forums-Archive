---
title: "Configure IPW3945ABG to scan for ALL networks?"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by luisjorge on 2008-08-03
Hello everyone! I was wondering if there's a way to configure the my wireless card, an Intel Prowireless 3945abg, to scan for all available networks: a, b and g, or if this is configured by default. I ask this, because I've noticed that I used to find more wireless networks when I used windows that now with ubuntu. I haven't had any problems with my wireless connection, but I would still like to be able to find any possible wifi spot.

Thanks very much in advance!

Luis Jorge.

---

### Post by FuturePilot on 2008-08-03
There's some issues with the iwl3945 driver at the moment. The driver doesn't support scan_capa = 0x0 which means it can't see any hidden networks which is probably why you're not seeing many networks. I have that same card in my laptop and right now it only sees my network, but with my Atheros card in my other laptop I can usually see 2-3 other networks.

---

