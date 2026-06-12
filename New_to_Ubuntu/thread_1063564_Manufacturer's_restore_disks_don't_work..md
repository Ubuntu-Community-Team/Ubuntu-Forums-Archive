---
title: "Manufacturer's restore disks don't work."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by David R. Ingham on 2009-02-08
In installing Ubuntu, I wiped out µS Windows and its partition.  When I received "Restore" discs from Gateway and tried to restore Win., they hung up while trying to load files (light blue window).  Is there a way to fix that by reformatting with the Ubuntu install disk?

---

### Post by Shazaam on 2009-02-08
The restore disk(s) might be looking for a factory "Restore/Recovery" partition (separate from the Windows partition) that it relies on to do it's work. Did you delete the Restore partition?

---

### Post by Kellemora on 2009-02-08
Hi David

HOW MANY Discs did they send you?

MOST OEM Restore Disks are ONE DISK, because it uses the EXISTING D Drive for the Restore Information.

OEM FULL INSTALL Disks are often 3 or more CDs or a DVD.
AND they install ALL the GARBAGE the computer came with too that takes hours to delete and erase.

If you are familiar with a local REAL Computer Store, MOST will be happy to burn you an Install disk for FREE that is completely FREE of ALL the GARBAGE.........
Just make sure you ask for the CORRECT flavor of Windows that you were using!  Eg:  XP-Home, XP-Pro, XP-MCE, XP-Pro-MCE, etc.
YOUR Existing License and Code IS VALID for this reinstall!  But it will only work on the Flavor of XP you had previously.

I really doubt if you will find a Real Computer shop with Vista, unless you BUY a New Install package.  They would recommend you UPGRADE to XP-Pro and pay the 100 bucks for the license if you don't have one already from an older computer.
If you want XP-Home, they may have a few waste licenses laying from from those who upgraded to XP-Pro from Home, which they might also give you for free.  Never know unless you ask!

Good Luck

TTUL
Gary

---

### Post by David R. Ingham on 2009-02-08
They sent two DVDs and a CD.  Only the CD is able to lift itself up by its own bootstraps.
At one point, the only thing that worked was letting Ubuntu take the whole disk.

---

### Post by David R. Ingham on 2009-02-10
A support person gave me a link to GWscan.  I was hoping that would do it, but the only write option is to write zeroes, and I am not sure that is worth trying.  It didn't find any problems.

---

### Post by johnjohn2 on 2009-02-10
Why don't you just try to format the whole drive through the ubuntu live cd

The disks may then work, or just bin the discs and stick with ubuntu.

:guitar:

---

### Post by Kellemora on 2009-02-10
HI David

Are you SURE it hung up?????

The reason I ask is the last time I installed from OEM Manufacturer Disks it spent like 40 minutes writing the files to Drive D before there was any user input to have to enter or any changes on the screen at all.

Well, there was a row of dots at the bottom, but it was lower than my screen was displaying.  Figured that out some time later after I installed the video drivers and had to reinstall some more things.

TTUL
Gary

---

### Post by David R. Ingham on 2009-02-10
I ran GWscan and selected long erase with all zeroes.  It did now re-install Windows.  Perhaps the way it was partitioned confused the installer but when it saw all zeroes it knew what to do.
Yes, I suppose if I had selected the right partition option in the Ubuntu installer that would have done it too.
Now I have to re-install Ubuntu.

---

