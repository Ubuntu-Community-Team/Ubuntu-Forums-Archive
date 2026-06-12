---
title: "Where is the config file for PCMCIA cards?"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by frisket on 2007-03-11
Where is the file in Edgy where I can add details of PCMCIA cards? It's not recognising some of my older cards (that work fine on other distros)

On others distros it was always /etc/pcmcia/config.opts, but in Edgy this file now has totally different stuff in it.

Where has the config file been moved to?

---

### Post by frisket on 2007-03-11
I finally found the undocumented gotcha: there isn't one. pccardctl claims not to need one because it uses hotplug instead of cardctl.

Unfortunately this isn't exctly true: pccard fails to recognise cards that cardctl recognised. 

How and where do I explain to pccard/hotplug what my card is and what to do with it?

---

### Post by frisket on 2007-03-12
A little more accuracy: pccard is failing to recognise that a card has been inserted.
It never gets as far as trying to work out what card it is because it's not even seeing the insertion. Yet some of my old cards *do* trigger it, *and* get recognised. Very weird.

---

