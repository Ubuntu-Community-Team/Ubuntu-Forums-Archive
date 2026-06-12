---
title: "Kernel panic with orinoco_cs and 7.10"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by indyrob on 2007-10-21
I installed Gutsy on my laptop.  Boots fine. 

Plugging in my Linksys WPC11 v.3 wireless card (PrismII, uses orinoco_cs) causes an immediate kernel panic.  No good. 

I'm pretty sure the problem is related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149997") in orinoco_cs.c.

Could someone help me out with a fix, such as showing me how to apply the patch from linked thread above?  Any help is appreciated!

---

