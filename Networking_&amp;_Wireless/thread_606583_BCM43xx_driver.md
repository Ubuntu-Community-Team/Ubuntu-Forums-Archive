---
title: "BCM43xx driver"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by RedPenguin on 2007-11-08
I am trying to use the BCM43XX driver with my Broadcom wireless card.

I have a light on my wireless card when the PC access it, and it turns on.

It starts out saying:

"Unsupported 80211 core revision 13"

Then

"Invalid PHY Revision 3"

Then repeats these messages over and over:

"MAC Suspend Failure" and "FATAL ERROR: BCM43XX_IRQ_XMIT_ERROR".

Is my card not supported or something?

I tried using ndiswrapper and it installed the Windows driver bcmwl6.inf but wouldn't activate the card.

---

### Post by spd106 on 2007-11-09
It's quite likely that you are correct. You may have to wait for the next release to use the bcm43xx driver.

In the mean time you should be able to use ndiswrapper, just make sure that you blacklist the the bcm43xx driver first. Any good ndiswrapper guide will tell you how to do this. Basically you add 'blacklist bcm43xx' to the /etc/modprobe.d/blacklist file.

---

