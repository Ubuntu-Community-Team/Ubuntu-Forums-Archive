---
title: "working wireless devices"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by fresnofred on 2010-06-23
I see lots of problems with wireless.  Here is my experience.  For a PC, install an airlink101 super-g PCI card.  For a laptop either an airlink101 model AWLL3026 usb (Zydas chip) or the AWLC4030 or 4130 super-g card (NOT g-card!!).  The PC will work with either the usb device noted above or with the AWLH4030 or 4130 super-g PCI card.  All have atheros chips that work natively, without drivers, with Ubuntu and indeed practically all linux distros.  It took me years to come up with this.  I am sure lots or other cards work but these WILL work for sure.  You can buy them off airlink101 website or used off ebay!  These will solve most if not all Ubuntu wirless problems.

---

### Post by anewguy on 2010-06-23
There is already a [large net page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") with the wireless devices known to work with Ubuntu.  If people would check that, as suggested many times in the forum, some of the wireless posts could be eliminated.  But remember that the biggest problem with wireless is not Ubuntu, but rather the manufacturers not releasing Linux drivers and not making the driver info open source as well.  This leaves a lot of devices without a native driver, though a lot of excellent people have done a LOT of work and made drivers for more of these devices.  There are also "restricted" drivers, meaning they either are not open source or perhaps not free, that sometimes can be activated.  While there are those who would disagree. ndiswrapper is still a very valuable tool in that it allows users with a wireless adapter for which there is no Linux driver to be able to use the Windows drivers in Linux to get the device working.

So yes, wireless can be troubling for the new user, and while I'm not one to normally say "not my fault", in this instance indeed it isn't Ubuntu's fault.  Checking the page for compatibility is strongly recommended for anyone considering purchasing either a wireless adapter or a computer with a built-in wireless adapter when they intend to run Ubuntu/Linux on that hardware.

Most of the time what is lacking is the driver, and there are ways in Linux to get a lot of drivers loaded.  A lot of progress has been made in the restricted drivers, and a lot of adapters can be made to work using ndiswrapper.

Glad you found the solution for yours, and thanks for posting it.

Dave ;)

---

