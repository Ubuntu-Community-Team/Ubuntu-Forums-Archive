---
title: "Have to run modprobe every boot for wireless"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by celticbhoy on 2013-09-26
Hi guys (and gals) got what is hopefully a simple problem.
Set up my father in laws old laptop (Acer 3630) with 12.04 and everything was working fine until the other day when he lost his wireless connectivity (not sure if it was the result of an update or something he did) and being a little dippy myself I could not remember how I got the internal Broadcom 4318 modem working originally so followed some instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=2174511") to get it up and running again.
My problem is that although I can get wireless working, it won't survive a reboot. Upon rebooting I need to run 'sudo modprobe b43' to get the wireless to kick in again. I am hoping this is a simple fix.

Any help to sort this out is appreciated.

---

### Post by celticbhoy on 2013-09-26
OK solved - yeah it was a doddle, just adding b43 to the modules list - DOH!

---

