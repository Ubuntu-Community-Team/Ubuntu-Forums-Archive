---
title: "Atheros -Working but invalid connection"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Gailen on 2008-08-30
Hi.

I'm a novice Ubuntu user and I'm experiencing quite a wird issue with my Wireless ATheros Card.

I installed Ubuntu 8.04 Hardy Heron in my Samsung R60Plus laptop, featuring a Pentium Dual Core T2370 processor, 2 GB of DDR2-667 RAM, an integrated Radeon Xpress X1250 (experienced some issues trying to load the graphic interface but they're already solved) and so on. Everything works fine here, except for the integrated WIreless card, and Atheros AR5007EG.

I tried using ndiswrapper and the Windows XP 32 bit drivers, but they didn't work at all. Then I tried the MADWIFI drivers, but I misused them and had to reinstall Ubuntu to try a clean installation, as generic Ubuntu drivers wouldn't load. Now, I finally got the full support for the card installing first the Madiwifi drivers for the card and then the Madwifi HAL.

Now the card seems to work as it recognizes all the wireless connections around, but I can't get it connected to the Internet, as when I connect to my home WIfi, with a WEP encryptation, this happens:

With the "automatic" mode enabled, it keeps me asking the WEP pass (pretty complicated and I cannot get it saved by the computer) regularly, but not connecting. EDIT-Okay, this was an issue due to the password, as I configured it as a WEP passphrase instead of an ASCII WEP. But now, when it finally connects to the net, it inmediately disconnects for it. The same for an unencypted connection

No I've noticed another issue: after sometime LAN-connected, the Wireless connection dissapears from the system and the network control, but the Privative Drivers windows shows that WiFi drivers are correctly loaded

So I come here asking you for help.

THank you very much for all the answers

---

### Post by Gailen on 2008-08-30
Anyone?

Okay, the first problem was solved.

I only had to change the WEP ASCII key for the Hexadecimal one and now voila! it connected

The moderator can close this post

---

