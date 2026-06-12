---
title: "Windows Wireless Driver"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2008-04-21
I have a Linksys internal wireless network card installed on a PCI slot.  I have it working under ubuntu and windows (ubuntu gets 10% better reception somehow).  It took me many difficult hours on several days to get it to work but I have a hint that most people fail to mention.  When you are using the windows wireless driver GUI all the how-to's point out that you must find the .INF file to feed to it.  None of the How-To's I have found mention that It is also critical that the .SYS file is in the same dir.  Otherwise it will report that you have an invalid driver.  So the >INF file is fed to the little program, but the .SYS file (of the same name usually) must be in the same folder!

---

