---
title: "Can't get PCMCIA ethernet card to work on desktop"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by mikebai1990 on 2006-08-20
Hey guys, just joined the forum. I just installed Ubuntu on a gateway all-in-one desktop (quite old). It doesn't have a ethernet port, but it has a PCMCIA slot. I have a 3Com Cardbus 3CCFE575CT PCMCIA card, and I was trying to get it to work. After I plug this in, I get this from dmesg: "pcmcia_socket0: cardbus cards are not supported." I've done a lot of searching around, and there are others who have used this card without any problems. When I go into the "networking" all I see is a ppp modem, no ethernet modem detected.

Since this is a desktop, I was wondering if maybe Ubuntu automatically disables PCMCIA services on desktops because it is usually seen more on laptops?

If more information is needed, I'll glady post it.

Thanks for helping out a newb!

---

### Post by anjin on 2007-08-19
I had a similar problem and I fixed it by changing my PC Card configuration in BIOS to "Cardbus/16-bit".

You might want to look in your BIOS to see if there is anything there like that.

---

