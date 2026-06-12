---
title: "Yet another Broadcom 4318 issue"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by sonofskywalker3 on 2008-04-16
I have a compaq presario v2000 model v2570nr. I am running kubuntu 7.10 gutsy, x64 edition. i have been working on this for 3 days and have finally made some progress but now i'm stumped again. using adept manager i was able to download and install the restricted drivers for the card, using the bcm43xx-fwcutter package. after that i was finally able to enable my wireless card. it now detects all the local area networks, but i cannot connect to any of them. any unsecured network shows good signal then starts to connect, but it gets to 28% and then hangs for about a minute, before saying the network could not be connected to. any ideas?

---

### Post by dstew on 2008-04-16
The native driver + firmware doesn't always work well, hence the continued use of ndiswrapper. That is the next thing to try, I think. See [this HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29#head-b0e306f00ab3b4adea24f483a5dd5bf05fbdaf08") if you want to try it.

---

