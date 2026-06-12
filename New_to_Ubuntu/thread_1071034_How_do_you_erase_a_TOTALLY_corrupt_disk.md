---
title: "How do you erase a TOTALLY corrupt disk?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by DigiTan on 2009-02-15
I recently cloned a hard drive.  I installed WinXP SP3 but apparently left an anti-virus on.  Now when I try to boot, Chkdisk comes on basically saying the file record is totally corrupt.

Luckily, I have everything backed up.  But this disk is so corrupted, neither WinXP nor Live CD can read, write, or boot off it normally.  The only exception is when I use CTRL+ALT+F1 to force Ubuntu into safe mode (which is how I'm here now).  Anytime to try to execute a command involving this disk, the console hangs endlessly.  Even...

sudo dd if=/dev/zero of=/dev/sdb

...has no effect on it.  Fdisk and Gparted can't view it, and ntfsfix says only Chkdisk can fix it.


What the hell is going on here?  All I want is to wipe out this drive and start over.  How do I set this thing back to all-zeros?

---

### Post by hansdown on 2009-02-15
Hi DigiTan.

Dban works wonders.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by Matsukaze on 2009-02-15
You can use the disk maker's diagnostic software, such as Seagate's Seatools or Western Digital's Data Lifeguard, to wipe the disk and also to check for problems with the disk hardware.

---

### Post by Michaelg14 on 2009-02-15
I would boot to a live CD and use gparted to delete the partition and start over.

---

### Post by Rolcol on 2009-02-15
Data corruption shouldn't block you from completely overwriting it with zeros.  I suspect you could have a case of hard drive failure.

---

### Post by DigiTan on 2009-02-17
Yeah, it looks like it's a defective disk.  SeaTools was able to detect the disk's stats, spin up the drive, and perform a track zero erase.  But all tests and other erase modes failed.  So it looks like it's RMA time.

I'll probably burn a DBAN boot disc as well, seeing as it could be useful later.

---

### Post by handy on 2009-02-18
There has been a spate of bad firmware in Seagate drives for some months.

---

### Post by DigiTan on 2009-02-19
Yep.  Unfortunately, I didn't read the consumer reports until after all this started going down.  Namely, I have the Barracuda 7200.10--which has a better reputation than the 7200.11, but clearly has its own set of issues.  It's a damn shame, because for the first 24 hours, it was noticeably faster than my current Western Digital drives.  ...Which are good enough to begin with.

Luckily, everything was mirrored onto redundant backups before-hand.  I'll have to put off my first Ubuntu install for a while, but no data was lost in the ordeal.

---

