---
title: "Microsoft MN-720 not working with bcm43xx drivers"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by meheheh on 2007-07-25
Maybe I lied when I said "not working".

It's semi-working, but without the regular blinking pattern seen in WIndows XP when not connected to a network, and will not connect to a network. It can detect networks and signal strengths though.

Anyone have any idea? I've tried various firmwares, including one cut out of the driver with bcm43xx-fwcutter. They all provide either a non-functional wifi connection or one that's only good as a wifi finder.

If anyone has a solution to this I'd be very grateful.
Also, because someone will probably ask this: the output of lspci is
06:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)

---

### Post by BrownCoat78 on 2007-10-28
I have the same problem. But I notice that that only occurs if the PCMCIA card is inserted during startup. If I plug the card in AFTER I've powered up and logged in, it functions normally. I did not have this issue with feisty, only with gutsy.

---

