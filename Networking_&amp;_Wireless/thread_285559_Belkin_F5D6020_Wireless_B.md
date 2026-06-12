---
title: "Belkin F5D6020 Wireless B"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by marx2k on 2006-10-27
I spent most of the day to try and get Ubuntu 6.10 to recognize and run my Belkim F5D6020 Wireless B card and in the end, all I really had to do was install Wifi-radar.  It connected me to my wireless gateway which filters by mac address and all is good.  There have been other posts saying that this model of wireless card has been a problem to people so Im wondering if 6.10 fixed this?

---

### Post by marx2k on 2006-11-14
Okay, so the card seems to work OK out of the box (not using WEP) -- But in order to make it work well, I had to first "iwconfig eth1 scan"

Since my router announces its' SSID (not good security), it picks it up with that command.  I take that SSID and enter it into the config for my eth1 card (wireless) under System --> Networking .. at that point I am able to activate the card.  I believe it is a known bug that Networking does not auto-enter this info when it sees the SSID...

At this point the card works OK...and JUST ok because it keeps dropping its' connection intermittently .. this also is a bug I believe.. lots of people seem to be having this problem.  

Everything seems to work GREAT once I install wifi-radar.  Just running it once at every startup and then closing it out once it sees the router seems to keep the connection up without problems.  Not sure why that is, but that seems to be the case.

I would like NOT to have to install wifi-radar in order to have that functionality.

Also, Network Manager does not see my wireless card for some reason.  I don't think it is compatible.

But anyway, this card does seem to work (with some problems) out of the box.

---

