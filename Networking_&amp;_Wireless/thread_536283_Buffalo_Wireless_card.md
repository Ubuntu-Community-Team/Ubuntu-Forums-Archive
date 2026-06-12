---
title: "Buffalo Wireless card"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by a_px on 2007-08-27
Hi, I installed Ubuntu on my laptop a few days ago and have spent a few hours trying to get my wireless PC-card to work with no success. Can't find anything on the forums that match my problem. The card is an older 802.11b Buffalo/Melco WLI-PCM-L11GP. I have installed the latest version of Ndiswrapper and loaded the windows driver. The card displays no lights and lspci does not have an entry relating to the card. pccardctl status says "no card". The card works fine under windows and the slot works fine with a wired card.

If the wireless card is in the slot on boot, the pc fails to boot with the message "soft lockup detected on CPU#0!"

Would appreciate any help with this.

Thanks, Alan.

---

### Post by kiloecho7 on 2008-01-06
I've seen the same error message before in a totally unrelated problem.  Going into bios and changing the SATA preference from "AHCI" (or something like that) to "compatibility" mode worked for me.  It's worth a shot for you at least, I'd say.  Hope that helps, sorry I can't get more specific.

kiloecho7

---

