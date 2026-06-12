---
title: "Airport router causing kernel panic (8.10)"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by UncleMilford on 2008-11-11
After days of banging my head against a wall, I have finally pinpointed the kernel panic on my Dell XPS M1530 (running Desktop 8.10) ... it is guaranteed to happen anytime I connect to an apple airport wireless router.  It takes anywhere from 2 minutes to 30 minutes to freeze, and the only way I can prevent it from happening is to turn off wireless support (even if I am not connecting).  As a side note, when I connect my laptop at home (linksys wireless or verizon router) all is good in the world.

ethernet adapter: Marvell Yukon 88E8040
wireless adapter: Intel WiFi 4965AGN

---

### Post by brian.takita on 2008-12-28
I seem to be having the same issue. I have a Dell D820 with Ubuntu 8.10.

---

### Post by brian.takita on 2008-12-28
I created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/311888](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/311888)

---

