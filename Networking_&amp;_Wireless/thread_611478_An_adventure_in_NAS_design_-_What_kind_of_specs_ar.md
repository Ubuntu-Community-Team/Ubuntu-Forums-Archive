---
title: "An adventure in NAS design - What kind of specs are necessary?"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by jafoca on 2007-11-13
I want to build a nas box that will function as: 
network storage
light HTTP server
light FTP server
pass through router with ip blocking etc.
Partially redundant

I want this box to run gigabit ethernet, at least on the subnet side.  10/100 is clearly fine on the WAN side since... well the internet sux.

This box will serve as multimedia storage and backup of critical files for a few clients, 3 or so probably, rarely more than one concurrently.

I am planning on running some version of Gutsy 7.10 headless on this machine.  I would like to do X forwarding over SSH a bit maybe.  The machine will be always on in my closet.



The most major constraint I have is that I would like the computer to consume as little energy as possible.  I have looked into GEODE and VIA options, but geodes seem unreliable in terms of *nix and VIA concerns me that it might not be capable of saturating the gigabit network if needed.

Thanks!

---

### Post by abubin on 2007-11-13
get a NAS that already have those features build-in. The price will come to around the same as you do your own. Plus the power consumption on these small NAS will be much more lower. These NAS comes with RAID5 for brands like buffalo and qsnap.

The only thing these NAS doesn't have is X desktop. Which I do not understand why you need them for a headless server.

The router part can be done from your adsl router (if you have one).

---

### Post by jafoca on 2007-11-13
I want the x desktop because it will be my only full time nix box, and I want to mess with it sometimes.

Additionally, my router can not perform all of the advanced functions for routing that I want because it is limited in memory / processor power....

Believe me I have looked into that.

---

