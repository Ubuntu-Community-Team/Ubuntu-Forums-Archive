---
title: "Ubuntu 6.06, Thinkpad T43, packet loss"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by yves on 2006-10-01
I have a T43 Thinkpad that dual boots Ubuntu 6.06 and Windows XP. I'm trying to switch to Ubuntu only, but loosing 35% of my network packets with Ubuntu doesn't help while loosing none with XP.

I know the wifi device is using the atheros chipset. Seems like I'm not the only one experiencing this, but I can't get my hand on the final solution. I had the same problem with 5.10 btw.

Any pointers ?

---

### Post by yves on 2006-10-05
Well, thanks to that post : [http://www.ubuntuforums.org/showthread.php?t=168141](http://www.ubuntuforums.org/showthread.php?t=168141)

I found the solution to my problem.  I have a DLINK access point, and I had to put both, the Basic rates and Tx rates to 11 Mbps.  Funny this bug never showed while using WinXP though.

---

