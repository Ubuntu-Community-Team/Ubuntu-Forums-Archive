---
title: "Changing default boot partition"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by dahornor on 2010-02-20
I am running UNR dual-boot (Win 7 Starter) on a Toshiba NB 205.  Really liking the clean interface, especially that Firefox plays very nicely with Ubuntu in full screen mode, as compared with Windows.

I would like to make the UNR partition the DEFAULT boot partition so that I don't have to babysit the machine and choose UNR each time I need to restart.

This seems like a fairly easy thing to do.  

Suggestions?

Thanks!

---

### Post by x33a on 2010-02-20
While you can change the option manually, the easiest way would be to install startupmanager. Install it and use it to change the default boot.

---

### Post by dahornor on 2010-02-20
Thank you.  Startupmanager does let me choose Unix, but nothing happens differently at startup.  I still get the usual "Choose which OS" stuff.  Maybe the only way to do this is to install UNR as the only OS?

---

### Post by x33a on 2010-02-21
What timeout have you set for booting into the default os?

---

### Post by dahornor on 2010-02-22
It's not really a timing issue.  It's a matter of which OS is the default:  Win 7 or UNR.  I can't find a way to make UNR the default, so every time I reboot I have to choose UNR.

---

### Post by x33a on 2010-02-22
That means it boots by default into windows 7? anyways, try to modify grub manually, take a look here:

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by dahornor on 2010-02-22
Yes, it boots by defrault into Windows 7.  I will check out the link you posted.  Thanks!

---

