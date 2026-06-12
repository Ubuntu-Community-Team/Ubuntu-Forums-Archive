---
title: "Random Crashes when Connected to Large Wi-fi Network"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by Cris987 on 2008-01-14
This may be related to other random crashes reported on Gutsy. I have commented in another thread (AMD 64 Random Freezes) but I think I have isolated my own problem and thus should report it as a separate bug.

I 'm running Gutsy on Inspiron 1501 (not pre-installed). Specs are Sempron 3400+, 1g RAM, and ATI Xpress 1150 256MB integrated graphics. 

It runs fine with Ethernet internet or in a small wi-fi network. However, when I'm connected in a large wi-fi network (e.g University), my laptop freezes every 15-30 min - a complete freeze - no response to any keys whatsoever. 

I use ndiswrapper to run my Dell 1390 802.11g Mini Wireless Card.

I'm going to revert back to the given driver and see if things improve tomo.

---

### Post by tgalati4 on 2008-01-15
I assume that this is a removeable card.  Next time it freezes, immediately pull it out.  If it is extensively warm, then it could be a heat issue locking up the DSP.  It could be the noisey RF environment that is causing the card to work overtime and get hot.  Don't know of a solution other than to get another card, preferable one that uses a native Linux driver.

---

### Post by Cris987 on 2008-01-15
It's a laptop, so I don't think it will be easy removing the wireless card.

I stopped using ndiswrapper today, but used the native driver that came with gutsy forr broadcom 43xx. 

No crash yet, but I keep getting disconnected inside a classroom of 15-20 laptops. Note that this did not occur back in feisty.

---

### Post by tgalati4 on 2008-01-16
Sometimes you can reset the wireless card by removing the battery from the laptop for an hour or so.  Then try it again.  Also, try running a Feisty Live CD and see if you get more reliable connectivity in the classroom.  Sometimes the antenna connection inside the laptop gets loose from its card connection causing signal drops.  Sometimes the antenna wire wears out from routing through the hinge of the laptop.  So we need to narrow down a hardware issue vs a driver/software issue.

---

### Post by Cris987 on 2008-01-17
I'll try removing the battery now. 

Unfortunately, I don't have the Feisty Live CD with me, so I wont be able to try that...

---

### Post by Cris987 on 2008-01-18
I tried removing the battery for an hour + ... no help.

One thing I've noticed though : I don't think it has much to do with a large wi-fi network. It has more to do with having other laptops (running wi-fi presumerably) close to me. 

I had no trouble connecting to my hotel's wi-fi network when I'm the only one in the room, but I keep getting disconnected when 2 others are using their laptops.

---

