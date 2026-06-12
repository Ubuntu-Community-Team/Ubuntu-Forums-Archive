---
title: "Dropped network connection"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by aztektum on 2008-06-23
When I plug in my Sprint/HTC Mogul WinMo device to USB to charge, Hardy dumps my already established network link (on my desktop or laptop).

Never had this problem in Gutsy. I'd rather not have it now.

---

### Post by aztektum on 2008-07-25
Simply for posterity, in case anyone has the same issue, I figured it out:

Go into Settings on the Win Mo device, tap the Connections tab, tap USB to PC. Uncheck the Enable advanced network functionality

With it checked it puts the phone in RNDIS mode which Ubuntu then attempts to use as a network advice. Unchecked it's in PPP mode.

---

