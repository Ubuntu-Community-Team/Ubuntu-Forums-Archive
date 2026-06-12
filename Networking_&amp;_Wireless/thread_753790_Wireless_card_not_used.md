---
title: "Wireless card not used"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by dchurch on 2008-04-13
Hi all,

I have a Netgear pcmcia card (which is 'N') in my laptop that seems to be detected, it's in the hardware list, and when I use ndiswrapper with the .inf file it says that the driver is installed.

The problem is that when I attempt to connect to my router it tries to connect using the internal wireless - which is not compatible with my router.

How can I specify that I want it to use the pcmcia card and not the internal one?

---

### Post by chili555 on 2008-04-13
> it tries to connect using the internal wireless - which is not compatible with my router.How so? I never heard of a modern router that was incompatible with a modern wireless card. Are you trying to make sure you connect with an "N" capable connection? If you can figure out which card is which interface, eth2 or wlan0 etc. you can amend the */etc/network/interfaces* file to comment out the line *auto wlan0* or whichever interface you don't want to start automatically.

---

