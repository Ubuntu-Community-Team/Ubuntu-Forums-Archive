---
title: "BCM4311 and HP NX7400"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by Icoo on 2006-09-30
I own a HP NX7400 and I installed Ubuntu onto it...as you suspect wireless is not working...lspci says I have a Broadcom 4311 Wireless Chip (I'm sure, it is not a Intel one!). Now I have tryed this guide in hope of installing it (BCM43xx):

[BCM43XX Guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")

But no luck, now I'm looking for a ndiswrapper guide that actually works...has anyone expireience with the chip or the laptop...has anyone put it to work?

---

### Post by beercz on 2006-10-06
I have a nx7400 laptop as well.  My wireless worked straight out of the box.  But the only problem I have is that ACPI is quite working correctly.

Have you got the right kernel installed?

Try uname -a to find out.  The output of the command on my pc is:

> Linux ianpc 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

See this [thread, message #4 by dietkinnie]("http://www.ubuntuforums.org/showthread.php?t=246827&highlight=nx7400").

Good luck!

---

