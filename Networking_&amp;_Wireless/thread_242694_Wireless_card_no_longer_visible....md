---
title: "Wireless card no longer visible..."
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by SFDD on 2006-08-24
I have a fresh install of 6.06 that I've been trying to get going with wireless. (Dell 8500 with the notorious Broadcom mess of a card.) I had this working before, but that last update killed my xserver and I was one of the ones who reinstalled too quickly before the fix was available. Anyway...

I had it working today sporadically with the BCM43xx option, but it wasn't working as well as I had it working before with ndiswrapper. So I decided to try that again. After following one too many tutorials that didn't work, all of a sudden the card is no longer visible in the Networking control panel. 

The last line of my lspic output does show it:
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

ifconfig shows:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Any ideas on what happened or how I can fix it? Thanks!

---

