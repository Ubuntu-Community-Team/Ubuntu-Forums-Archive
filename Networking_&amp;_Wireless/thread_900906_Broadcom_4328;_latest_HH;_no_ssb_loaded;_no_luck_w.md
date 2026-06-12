---
title: "Broadcom 4328; latest HH; no ssb loaded; no luck with ndiswrapper so far"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by smuikas on 2008-08-25
So, here's a rundown of my issue:

I've got a brand spankin' new dell 1525, with the integraded broadcom 4328. Nothing came up on install, so I thought I'd try ndiswrapper. Well, ndiswrapper tells me hardware found, driver installed (bcmwl5). Running the latest stable HH release 64bit.

ndiswrapper is loaded in lsmod.
ssb, etc, all the problem modules mentioned in other howtos were never ever loaded. So that can't be the problem.

But even with ndiswrapper loaded and saying everything is a-ok, I can't access my wlan. 

iwconfig lists no wireless connections available, and ifconfig only lists my eth0. 

I've tried the crappy b43-fwcutter crap, and it doesn't work either. Any help would be much appreciated. I'm not really that much of a *nix nub, and I'm at a complete loss (I've compiled my own kernels before from scratch, used a dell csx500 for a few years running fluxbox). PLEASE :)

---

### Post by jpeddicord on 2008-08-25
Moved to Networking & Wireless. Tutorials & Tips is **not** a support forum.

---

