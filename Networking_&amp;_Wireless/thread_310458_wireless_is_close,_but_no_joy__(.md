---
title: "wireless is close, but no joy  :("
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by radnor on 2006-12-01
Hello to all!

I have a Compaq 1700T laptop, Dlink 524 router and a dlink pcmcia card g530.  

I can "see" the signal from my router.  While wired, I can see the MAC address of my card.  But, if I remove the cat5, no net...

How do I tell it to use the wireless VS wired?

TIA,
Radnor

---

### Post by FrodoB on 2006-12-02
Publish the outputs from:

lspci                if the device is Card Bus, PCMCIA or PCI

lsusb               if the device is a USB adapter

iwconfig

---

