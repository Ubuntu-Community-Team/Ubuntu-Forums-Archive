---
title: "D-link G510 works with 2.6.17-10, but not with 2.6.17-11....?d-link,G510,"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by OldGaf on 2007-02-19
As the subject implies, the card worked "out-of-the -box" with 2.6.17-10. Then I upgraded my Nvidia drivers which seems to require 2.6.17-11. Now, I can still see the card and it says it is activated, but I can not get an IP.  ](*,) 

Anyone got any idea's?

---

### Post by teaker1s on 2007-02-20
[http://www.ubuntuforums.org/showthread.php?t=358004]("http://www.ubuntuforums.org/showthread.php?t=358004")

---

### Post by OldGaf on 2007-02-20
OK, I got my D-Link DWL-G510 (Atheros chipset) to work again under 2.6.17.11. It seems that 2.6.17.10 had built in madwifi support in the restricted modules that are eather missing or are broken in -11.

The solution was to get the MADWIFI driver and compile it under -11. 
It is very simple to do, just follow these instructions.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If you do not have an Atheros chipset, try ndiswrapper (NOT the one in the repos....... get 1.37 and compile it.) Here is a simple set of instructions.

**NOTE: At this time 1.37 is the latest ndiswrapper. You will also have to change the Winblows driver for the one that matches your card.

[http://www.ubuntuforums.org/showthread.php?t=342558](http://www.ubuntuforums.org/showthread.php?t=342558)

BTW...... This is a BIG pi$$ off and a pain in the @$$ to have to do. This should have been picked up on before the release of -11.

---

### Post by gradedcheese on 2007-02-20
If you were not previously using ndiswrapper, **do not** 'solve' this problem by installing it!  Instead, identify what real driver you were using before and get a new version of it (for the -11 ABI) or compile a new version.  You should always avoid ndiswrapper at any cost, unless it's the only thing that supports your interface to begin with.

---

