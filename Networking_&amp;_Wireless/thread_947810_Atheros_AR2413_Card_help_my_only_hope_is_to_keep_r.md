---
title: "Atheros AR2413 Card help: my only hope is to keep reposting!!!"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by TheSmokingGNU on 2008-10-14
I am running a dual boot of XP home edition, and ubuntu 5.2.4 I believe. anyway, I have a Belkin Wireless G Desktop card that is recognized as an Atheros AR2413 card, and I need to get a wireless signal. How do I do that? I am kind of a n00b at this sort of thing, at least with linux. Thanks in advance,
Darren

---

### Post by PMahoney on 2008-10-14
Download the latest madwifi drivers from madwifi.org (should be 0.9.4) then follow the how-to on the following link.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

From a quick review, earlier drivers didn't work well with your specific card, but hopefully this will help some.

P

---

### Post by wirelessmonkey on 2008-10-14
Which version of Ubuntu are you really using? If it is 5.0.4 as I suspect, it may be easier for you to just upgrade to 8.04.  If you'd rather not, you'll probably need to start by updating your kernel, wireless-tools, and PCMCIA utils.  Since 5.0.4 is no longer supported, you'll have to do these all from source, for which you'd best be prepared to spend some time if you're not familiar with doing so already.

Best of Luck

---

### Post by TheSmokingGNU on 2008-10-15
holy crap... an actual reply... and it's useful too! :) thanks people

---

