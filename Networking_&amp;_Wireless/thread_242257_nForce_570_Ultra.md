---
title: "nForce 570 Ultra"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by ckasprzak on 2006-08-23
Does anyone have this chipset and have they gotten their integrated nic to work properly with Drapper ?

System instals w/out a hitch just no network connectivity.

Got the same thing with another distro, is there anyway.

---

### Post by Original Brownster on 2006-08-23
Hi, 
[Check this thread]("http://www.ubuntuforums.org/showthread.php?t=231330"), it explains a problem found when dual booting windows with this chipset, at least initially.
If I get the jist of it, there is a kernel module in ubuntu for this chipset called 'forcedeth' HOWEVER windows leaves the chip in an unusable state, then forces a reset when you go back into windows, the linux driver does not force the reset (at least the one in the install, which when you do the update it should cure this problem).

The work around seems to be, disconnect the power cables and the network cable to the pc and leave it for x minutes before re-connecting and booting into linux. Assuming this works, you can update your system and this will download the latest driver.

from the thread 
quote:
My problem went away when I got the first big batch updates from security
that updated forcedeth from version 0.48 to 0.54 which is the 2 versions mentioned in this post.
unquote.

[this thread]("http://www.ubuntuforums.org/showthread.php?t=231330")


> **ckasprzak said:**
> Does anyone have this chipset and have they gotten their integrated nic to work properly with Drapper ?

System instals w/out a hitch just no network connectivity.

Got the same thing with another distro, is there anyway.

---

### Post by ckasprzak on 2006-08-24
Thanks I'll give this a try when I get home!!!

---

