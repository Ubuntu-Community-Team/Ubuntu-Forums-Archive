---
title: "need a PCMCIA ethernet card suggestion"
date: 2004-12-17
forum: Networking &amp; Wireless
---

### Post by negativ on 2004-12-17
I need a suggestion on a PCMCIA ethernet card that the default ubuntu warty distribution detects correctly right out of the box without getting upgraded packages during the install.

I recently killed the onboard ethernet on my laptop (don't ask) and decided to reinstall warty on the laptop.   I need to be able to get it online without having to go online first in order to get it working (if that makes sense).

---

### Post by spartas on 2004-12-17
I use a linksys WPC11 card (It's only a 802.11b card though if you're wondering).  It's based off the Intersil chipset, which is recognized in a default installation of Ubuntu. You may want to look into other linksys cards if you need 54Mbps.  You're probably best off either waiting for more people to reply or searching the internet for wireless cards that are debian compaitble.

---

### Post by Smash on 2004-12-18
I use a Digicom Palladio Wawe, in Italy costs max 40€.
It use a "orinoco" module.

---

### Post by Dan on 2004-12-18
Cisco Aironet 350 card. Works straight out of the box. IMHO the best WiFi card you can get.

---

### Post by king20878 on 2005-01-03
I picked up the AT&T Plug&Share 54Mbps Wireless Notebook Adapter (6700G) over the weekend, plugged it in and it just worked.  It appears to use an Atheros chipset as Ubuntu happily loaded the madwifi modules for me.  I haven't explored all of the card's features, but it is connecting to my AP in managed mode without a hitch.

I've seen this card on sale a lot of places.

First time I've ever had wireless working so painlessly in Linux.   =D>

---

### Post by jahLux on 2005-04-01
For what its worth - I have been struggling with a D-Link DWL-650 PCMCIA 2.4GHz card that 'just works' under Win-XP [multi-boot Sony Vaio PCG-F540K ].

Still can't get it to be even recognized on boot-up - much less to 'work' under [UBUNTU/KUBUNTU Hoary 2.6.10-5] ! 

Avoid this card at all costs - it does NOT work under SuSE 9.3 Pro or MEPIS 3.3 either!

CAVEAT EMPTOR . . . . . !

---

### Post by uberlinux on 2005-04-15
another vote for a aironet 350 (cisco)  I recompiled my kernel three times for an orinoco gold under hoary with no luck, it worked but wouldnt go into monitor mode

---

