---
title: "modprobe ndiswrapper hangs system"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by el_ricardo on 2008-02-12
I've been having some difficulty getting wireless working on a friend's laptop. Its a belkin pcmcia device, using the BLKWGNv7 drivers. The drivers install OK, and ndiswrapper sees the device etc etc, but wheni do modprobe ndiswrapper, terminal hangs, and if i put ndiswrapper in to my /etc/modules/ the whole system hangs on boot, and i can't get into the system! (the boot sequence gets up to "loading kernel modules" and then just stops dead)

any help would be great, i feel especially bad because it's not my laptop!

---

### Post by dca on 2008-02-12
I'm not gonna' be much help but if the whole system (everything frozen) hangs during applying ndiswrapper & module to system then it sounds like kernel stack (4k or 8k stack, etc).  If it's just terminal screen then it sounds like a driver issue.  Are you running 64bit or wrong OS driver w/ ndiswrapper?

---

### Post by el_ricardo on 2008-02-12
it doesn't actually crash, just hangs indefinatly, I can still do other stuff if i gave the command from gnome terminal for example, but if it's loaded during boot then i can't do anything else, all i see is a flashing cursor, and no usable system. I had to boot into a live cd to take the ndiswrapper line out of /etc/modules.

I've tried it with all the 32bit drivers on the disk that came with the card (win98, ME, 2000 and XP) and i get the same result every time. For the record it's a belkin F5D7010. Could this be a kernel issue?

---

### Post by dca on 2008-02-12
After digging:
 
[http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)
 
...now if this is correct, I guess it uses the bcm43xx drivers which show up in the restricted drivers area of the System -> Administration ->Restricted Drivers menus...  Make sure they're set to 'Not In Use'...  Mind you, I'm out of my league because I've never had the pleasure of messing about w/ PC-MCIA or USB dongle WiFi devices.  Only PCI, mini-PCI, mini-PCIe, etc, etc...  So, if you click on the above link there, it seems the only thing I can tell you to do is make sure the broadcom wireless drivers are blacklisted on your computer...

---

### Post by el_ricardo on 2008-02-14
yeah i've followed the howto and still no luck, exactly the same problem! i don't think there was any default drivers to blacklist in the first place :(

there must be a solution to this, it's listed as working on the ndiswrapper wiki!

---

### Post by dca on 2008-02-14
The times I've seen ndiswrapper hang when typing 'modprobe -i ndiswrapper' or adding 'ndiswrapper' to your /etc/modules file is when the wrong driver is used.  But if after going through the how-to(s) on installing ndiswrapper and typing 'sudo ndiswrapper -l' lists driver present it should work.  Typing the 'sudo ndiswrapper -l' doesn't yield and 'alternate driver' on the bottom line does it?
 
I have searched a little but the only other thing I've found was:
 
[http://ubuntuhcl.org/pub/reviews.php?product_id=334](http://ubuntuhcl.org/pub/reviews.php?product_id=334)
 
 
For instance, I misdiagnosed a D-Link DWL wifi PCI card for my parent's PC.  The whole time I researched on the web for the drivers (I only had the card, no manual, no CD, etc) I found them, it said it used Marvell chipset.  Come to find out the card was newer and had a Rev.B caveat (Rev A & C = Marvell) which made it have Atheros chipset which was fully compatible w/ MadWifi requiring no ndiswrapper.  The moral of this long story is ndiswrapper did the same exact thing, it would keep hanging.

---

