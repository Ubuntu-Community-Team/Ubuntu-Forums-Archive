---
title: "Cant get Ubuntu 10.10 to boot off USB"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by CyborgGold on 2011-03-11
I used the Universal USB Installer from pendrivelinux.com to download and install a copy of Ubuntu 10.10 to a 4GB thumb drive I had laying around.  I have used the same program/process to do a live Mint boot without any issues.  When I try to boot from the USB I get an error that the computer can not boot from device, and I get a command prompt.

I have tried a few different distros without any success, any ideas on what I am screwing up?  I am currently running Win7 on an HP G60, with a dual boot containing BackTrack 4.  I would love to try out a few different distros, since BT4 is more of a hardcore user distro.

Thanks in advance to anybody that tries to help!

---

### Post by fabricator4 on 2011-03-11
> **CyborgGold said:**
> I used the Universal USB Installer from pendrivelinux.com to download and install a copy of Ubuntu 10.10 to a 4GB thumb drive I had laying around.  I have used the same program/process to do a live Mint boot without any issues.  When I try to boot from the USB I get an error that the computer can not boot from device, and I get a command prompt.

I have tried a few different distros without any success, any ideas on what I am screwing up?  I am currently running Win7 on an HP G60, with a dual boot containing BackTrack 4.  I would love to try out a few different distros, since BT4 is more of a hardcore user distro.

Burn the LiveCD to a CD and you should be able to boot it easily. After booting you can then install 10.10 to the USB drive.  4GB is a little tight for a full install, you won't have much more than 1/2 Gb left, if that, and no swap partition.  An 8 GB drive would work well however.

An alternative would be to make an extra partition on your hard drive that you load different distros onto to try.  It's a better way to gauge how they will work, since USB booting and USB writes in general can be quite slow.

If you're re-arranging your hard drive, consider making separate partition that mounts as /home.  This would work with any distro, and means your /home data and settings would be the same no matter which distro or which device you booted off.

Chris.

---

### Post by Scooter85 on 2011-03-11
fabricator 4 is correct that 4 gig is tight, but I have 10.10 on one and have added all the files I need right now,  no problems. (except system freezes if in firefox I lock the scroll pad so my cursor doesn't go flying with thumb gestures. then I have to reboot. all else seems fine, day four.

---

