---
title: "ndiswrapper error"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by rubyzolom on 2007-03-13
ok, so i've been trying to get my laptop connected to the internet via wireless card, but i keep running into the same error: 

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

i've been following the instructions from here: [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

but i keep getting the same exact error on the part where it asks you to enter "sudo modprobe ndiswrapper".  I got rid of the older ndiswrapper and only have 1.8 on here, and i even reinstalled that about 5-6 times.  i am trying to install a driver called C22C (found it on driverguide.com) and i've gone into the windows xp folder to use the TIACXLN.INF for the previous steps.  it seems that i've tried just about everything, so i need your help dearly.  thank you in advance.

---

### Post by SactoBob on 2007-03-14
That is the error message I got with a couple of cards that were unsupported by ndiswrapper.  I could not find a driver that worked, and finally bought a card that did work easily. (money well spent).

If ndiswrapper will not take a driver for your card, and there is no native driver, you may have to face that the card will not work under Linux.  Have you done a search for other users of that card with ndiswrapper, or checked ndiswrappers list of cards that have worked?  You could try some other versions of your Win drivers.

Don't feel bad, I spent a couple of weeks trying to make two cards work that was not going to work.  (Anybody looking for a Pre-N card that works great with Windows?)

Bob

---

