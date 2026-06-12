---
title: "Belkin F5D9010 in 7.10"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by khufi on 2007-10-20
Hi, I've been trying for days to get this card to work, following every tutorial I can find, trying to bring my limited linux-knowledge to bear on it, etc., and I can't do it. 

I'm running a standard Gateway ML6230 with an up-to-date installation of ubuntu 7.10. Everything is working great, except for the wireless internet situation. I've got the F5D9010 card in the slot, and a Belkin F5D7230-4 for my wireless router.

As far as I can tell, the computer simply isn't recognizing the card. I've tried ndiswrapper with the suggested drivers. The card shows the power light on, but the wireless light doesn't come on at all except during the boot process.

Any ideas?

---

### Post by khufi on 2007-10-20
perhaps it would help to mention that everything seems to be fine until i get to the point of trying

ndiswrapper -l

and the expected output is something like:

    * Make sure it has installed correctly:
      Quote:
      ndiswrapper -l

    * The output should yield something like this:
      Quote:
      rt2500usb : driver installed
      device (13B1:000D) present (alternate driver: rt2500usb)

but mine says the part about the driver being installed, but nothing about the device being present.

---

