---
title: "How to choose a wireless network automatically?"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by mmcmonster on 2007-09-13
I have a desktop computer with a wireless card in my family room.  When the system boots up, it will typically automatically find my wireless router and get it's IP address.  Occasionally it gets a bit confused and doesn't get an IP address from my router.

The problem, I think, is that the computer detects 2 other wireless networks in the area and can't figure out which one to join.  Is there a way to tell it that I always want to get an IP address from a particular network, if it is available?

---

### Post by Zorael on 2007-09-13
I don't think there is (at present) any way to set up network priorities, but of course, you *can* tell it to always (and only) connect to one ESSID. It would ignore the other one.

(The setting for which should be in your network settings for your wireless interface, or alternatively, in /etc/network/interfaces.)

---

