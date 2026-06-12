---
title: "intel pro wireless 2200 stays off in bios"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by rudeboyskunk on 2008-04-14
Ok, this is a problem I cannot seem to find anywhere else.

I just bought a Dell Latitude D610 laptop, which has an internal Intel PRO Wireless 2200BG wireless card.  I can see it under the device listing, however, it does not show up when I do iwconfig or in Network Manager.

I looked at it in my BIOS, and it was switched to "off."  I switched it to "on," and then booted into Ubuntu.  It still did not show up, and when I restarted my computer to look at it in BIOS again, it was once again switched to "off."  I've switched it to "on" several times, and then do "save/exit" and it still reverts to "off."  What am I doing wrong?

Hitting Fn/F2 does not turn it on either.

---

### Post by dstew on 2008-04-14
It could be that Ubuntu is resetting the card. Linux does not use BIOS programs after the boot phase, so perhaps there is something resetting the card, and the next time the BIOS comes up, the card is off.

What is the listing in lspci? If the card appears, but iwconfig doesn't show a network device, it might be there is no driver for the card.

---

### Post by rudeboyskunk on 2008-04-14
Okay, after one of several tries, it was working and staying in the on position.  After restarting many times just to test, it's still working.

So, magic I guess?  Anyway, everything works fine on it.

---

