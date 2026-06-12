---
title: "Wifi adpater list"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by Endow on 2006-08-27
Okay so I'm going to buy a new adapter.Is there some sort of list I can check of wifi adapters automatically suported by Dapper Drake?

---

### Post by funchords on 2006-08-27
[WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Hope this helps.

---

### Post by Endow on 2006-08-28
I'm thinking about buying a DLink adapter but I dunno which to choose.Does any of you have a suggestion?

What is the best DLink adapater (that works out of the box on Ubuntu)???

If you have a non-dlink suggestion it's okay too.What's important is that is good quality and it's USB

---

### Post by Endow on 2006-08-28
PS:That list is very incomplete.My last DLink adapter (-120+) IS supported "out of the box" by Dapper Drake (it wasn't by older versions) and isn't on that list.

Isn't there a more up to date list (Dapper Drake list)?

---

### Post by funchords on 2006-08-28
The D-Link DWL-G520 should do that.  What kind of Wireless Access Point do you have?

That list was updated today.  The last updater is listed at the bottom.  Perhaps he'll add yours.

---

### Post by Melcar on 2006-08-28
In my quest to get wireless working on my new laptop I have played around from the integrated wireless chip to several Linksys and D-Link adapters and even an old no-name adapter I found in the garage.  All where recognized inmediately (some did requiere drivers to actually work) and to my surprised worked without incident.  The problems started when I re-enabled WPA on my network, so I whent back to WEP and those pesky MAC filters.  I'm happily using my integrated Broadcom chip at the moment (only had to use fwcutter and networkmanager).  I conclude that in fact most wireless adapters do work, but WPA support is still shaky.

---

### Post by Endow on 2006-08-29
Funchords:aren't there any good USB solutions?Other brand perhaps?

---

### Post by funchords on 2006-08-29
I'm not the right guy to ask.  

So far, I've only tried a Hawking HWU54G.  As Melcar said, it was fine unless I wanted WPA.  Then I had to compile drivers and supplicants to get mine to work.

---

### Post by Endow on 2006-09-01
I ended up talking with a fellow Ubuntu user who happens to work at a store near my house.I bought a Sitecom WL-113 usb wifi adapter and I had out of the box funcionality with no strings attached at least so far...

It was cheap too (granted I never heard of Sitecom before but hey it serves my [current] needs...)

---

