---
title: "Need Help With WPA"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by iwarp62 on 2007-04-22
Hello,

I just did a clean install of feisty on my notebook. It's an Acer Aspire 3610 with the Broadcom 4318 wireless card. I've been messing around trying to get the card going for a day now.

If I use the bcm43xx-fwcutter method, the card works but it is stuck at 11Mb/s and the signal strength is weak. But it works with wpa security. If I use the ndiswrapper method the card works beautifully on any unsecured network but it refuses to connect with wpa.

Right now I'm using bcm43xx-fwcutter method which I guess is the lesser of two evils. I was wondering if anyone could help me getting wpa working with ndiswrapper though as I want to get the full wireless g speed. Perhaps this is some kind of bug?? Has anyone else experienced and fixed this?

Thank you, All help is appreciated.

---

### Post by iwarp62 on 2007-04-22
Ok, I finally got this fixed. Yay! I ended up downloading the latest ndiswrapper from sorceforge and compiling myself using the wiki. I'm fairly confident this should be filed as a bug in launchpad but I really have no idea what I'm doing. I don't know what caused the bug.

---

### Post by jarrett on 2007-04-22
Had the same issue and installing ndiswrapper 1.42 worked wonders for me too!

Thanks mate!

---

