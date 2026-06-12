---
title: "&quot;Just works&quot; card finally!"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Phreaker on 2008-09-22
Today I bought my first wireless card for my desktop, since I wanted to get away from all the cables, running around my home.
I got the Linksys WUSB54GR and installed it on my Vista.
But when I booted from an Ubuntu 8.04.1 livecd, my card just worked!
Trust me, It was hard to believe. Right now I am surfing from at an almost maximum signal rate and it is running without any problems.

I don't know, if it's from it's proprietary technology, but it picks up excellent speed and signal.

I think it's running a ralink chipset,I am not sure how to find that out

I get only this line from lsusb:
[B]
Bus 008 Device 002: ID 13b1:0023 Linksys 
[/B]

---

### Post by panhandle on 2008-09-22
Yes, this NIC does run a Ralink chipset--RT73.

Good news for you as well, the WUSB54GR is also detected by a number of other *NIX flavors, including Fedora, OpenBSD and BackTrack,to name just a few.

---

### Post by liquidfunk on 2008-09-22
I struggled with that card when I first used it in 7.04.

---

### Post by Phreaker on 2008-09-30
From what I understood, in some of the newer kernels the module is included, so if you install something more up to date (e.g. *buntu 7.10), it would run "out of the box"

---

