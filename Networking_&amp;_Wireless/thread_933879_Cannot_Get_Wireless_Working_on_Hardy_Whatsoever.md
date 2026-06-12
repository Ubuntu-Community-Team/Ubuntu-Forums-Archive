---
title: "Cannot Get Wireless Working on Hardy Whatsoever"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Giovanni Gale on 2008-09-29
I've been trying to get either my Broadcom Wireless Card 4311 Rev 2 (in both Vista and Linux, it sometimes isn't detected by my computer and sometimes it is) or my Netopia Wireless USB Card (Ralink RT 2570) working in Hardy Heron with no avail. I've tried to follow the guides I've found for both fwcutter and ndiswrapper, but nothing has made either one connect to the network.

They both show up as detecting the wireless network and have a signal, but when I try and connect it keeps asking me again and again for the WEP key and never connects.


Hopefully someone can help me out with this. And if possible, help me remove some of the stuff I installed trying to fix the problem.

---

### Post by superprash2003 on 2008-09-30
in your terminal type lshw -C network and post output here

---

### Post by Another Monkey on 2008-09-30
Disable WEP.  Does it connect now?

Consider ditching WEP and moving to WPA if you can, as WEP is not secure.

---

### Post by Giovanni Gale on 2008-10-01
I was able to get my wireless USB card connecting to the internet after changing to WPA encryption (internal Broadcom card hasn't started in Linux for the last 2 days, only in Vista, so I can't check it).


However, if I go more than 10 feet from the router, the signal drops from 95%+ to under 30%. And web pages take 30sec+ to load... -_-"


Besides this, thanks for your help people! I am at least 1 step closer to my goal now... :D

---

### Post by Ayuthia on 2008-10-01
Can you still post what superprash2003 requested in post #2?  I would like to see what driver it is trying to use.

Also, have you been able to get your system updated?  The current kernel should work better with your card if it is using the b43 driver.  I am guessing that you are using the b43 driver only based on the signal issues that you are having.

---

