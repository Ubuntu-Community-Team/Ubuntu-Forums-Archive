---
title: "Wireless Card Freezes System"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by Anaea on 2006-08-08
I've just installed Dapper on a Toshiba Satellite A45-S121.  I tried setting up my wireless card as my default network connection during the install, but that didn't work out, which I expected, so I have the ethernet connection functional as the standard connection.  I still want the wireless working, though, but I've run into a rather annoying problem.

If my wireless card is pushed into its slot, even though the leds indicating that it's connected to the computer do not light up, my system is prone to freeze.

If I push the card into the slot when it wasn't already, the system freezes immediately.

If I open the network configuration and try to activate the wireless or go into the properties, the system freezes immediately.

This is a hard freeze, the mouse and keyboard don't respond at all, I get nowhere with ctrl-alt-bksp, and waiting doesn't get me anywhere either.

I have a Belkin F5D7010 v2 which, according to a thread I found three freezes ago and didn't get bookmarked, is supported by Ubuntu and, if memory serves, doesn't require ndiswrapper.

My only theory at this point has to do with the fact that looking at top, I'm consistently using about 234488k of 239484k in my memory.  My swap is active, but I'm only using 18796k of 489972k.  Is it possible that I'm just maxing out my memory by adding the network card to it, or is there something else going on?  Either way, I could really use some help on this one.

---

### Post by Anaea on 2006-08-09
Update: The memory dump idea seems increasinly less likely since I can install new programs without a hitch.  It's been a couple days now and the onyl freezes I've had were directly tied to the wireless card in one of the ways I described above.  The card works fine in Windows, as it always has.  Under system->networking I have a wireless (ath0) connection listed only when I boot the system with the card in, otherwise only the ethernet connection is listed, so *something* is going on.  Any ideas?

---

