---
title: "Atheros 5007EG - Works sometimes"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by spinnelein on 2008-04-07
I've got Gutsy set up on my Acer laptop with a 5007EG card. I set up wicd and ndiswrapper, and it works like a dream... sometimes.

Sometimes on boot, wicd works perfectly, and sometimes it shows "No wireless networks found" and doesn't even see the card.

ifconfig shows wlan0, and if I reboot enough times, it works again.

Any ideas?

---

### Post by DXM31 on 2008-04-07
I have the same card and never to ndiswrapper to work, so your doing better than I did.
I went with madwifi, it works great and never drops.

---

### Post by kutjara on 2008-04-07
> **spinnelein said:**
> I've got Gutsy set up on my Acer laptop with a 5007EG card. I set up wicd and ndiswrapper, and it works like a dream... sometimes.

Sometimes on boot, wicd works perfectly, and sometimes it shows "No wireless networks found" and doesn't even see the card.

ifconfig shows wlan0, and if I reboot enough times, it works again.

Any ideas?

Like the first respondant, I use madwifi. There's even a prepatched and  ready-to-go madwifi driver available for download from the madwifi site. Follow the instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=669267](http://ubuntuforums.org/showthread.php?t=669267)

They worked for me perfectly, and my Aspire 4351's  5007EG card never gives me any trouble. The instructions are for Gutsy, but I used them with Hardy, and they work just as well.

Ndiswrapper never worked for me with this card.

---

