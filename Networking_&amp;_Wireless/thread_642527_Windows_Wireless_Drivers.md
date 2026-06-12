---
title: "Windows Wireless Drivers"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by YodaMstr on 2007-12-16
Alright, I've read a couple of threads on this and apparently I need some specific help because nothing's helping me along. :P

Anyways, I have a Vista/Ubuntu dual-boot.  On Vista, I looked through my list of drivers and found out I have a WLAN 1390 Mini-card.  Unless that's not what I honestly have and the driver's just loaded for whatever reason.  So, is there a way to check on Ubuntu?  But on to my main problem.  Wireless won't work on Ubuntu.  It can't find any network no matter what I try.  I went through the list of supported wireless cards, and the 1390 isn't supported out of the box.  So, with some help, I got the ndiswrapper files and such set up.  From there, I was told to go to System -> Admin -> Windows Wireless Drivers.

So...I'm there.......and have no clue what to do.  Where would I pull the driver file from?  Any help?  It'd be greatly appreciated.

---

### Post by spd106 on 2007-12-16
I would prefer to steer you toward the bcm43xx driver, which can be installed quite easily bt following the steps in the wiki guide at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

The alternative, Ndiswrapper, is also quite thoroughly  documented at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you want to continue with ndiswrapper what you need are the .inf and .sys files from the Windows partition or download the latest driver file from the Dell? website and extract those files from it. The [ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/") website will provide some links to known working driver files too.

---

