---
title: "Fix windows xp, dual booting, don't want to lose ubuntu"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by WhatAreHackers on 2011-02-22
Missing some files for windows xp boot up... won't explain how... anyway to recover windows but prevent the loss of ubuntu?

---

### Post by mikewhatever on 2011-02-22
How is Ubuntu supposed to be involved in recovering Windows?

---

### Post by WhatAreHackers on 2011-02-22
> **mikewhatever said:**
> How is Ubuntu supposed to be involved in recovering Windows?

idk, i heard if i use the windows xp cd, it'll erase my mbr(guessing it would rid of ubuntu or something) or i might be wrong, better safe than sorry?

---

### Post by SEisch on 2011-02-22
If you use the Windows installation CD to completely reinstall Windows, it most likely will rewrite everything on the hard drive.  If you use it to repair, you may be able to replace the missing files.  You might also try checking on the Windows XP forums.  They may have a little more info on this.

---

### Post by mikewhatever on 2011-02-22
MBR is the first sector (512 bytes) on the hdd (not sure in what way it's yours:confused:). Recovering Windows will overwrite that sector, but Ubuntu will remain on its own partition.

---

### Post by irishjay1 on 2011-02-22
First put the cd in. Start the computer and press an fn key. I dont know which to press,all computers are different. It will ask from were you want to boot. Press CD-ROM drive. The CD will set up. After a couple minutes it will be finished. Then select the old windows partition and download the new windows over it. It will keep Ubuntu.:)

---

### Post by SE7EN-LOCSTA on 2011-02-22
allright, let me try to see if i can help.

if you are trying to 'repair' or 'reinstall' windows xp to the same location of your existing windows xp, without losing the ability to boot back into ubuntu, then you will have to get a program to use after your operation.

repair/reinstall windows xp, making sure not to use space used by ubuntu. this WILL overwrite the MBR on your hard drive, and replace it with a winxp boot that will not recognise ubuntu.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)    you either want super gub disc 1 (if you have an older version of ubuntu) super grub disc 2 (for newer versions of ubuntu)  or you can use rescatux. you will have to boot into the disc/usb drive after you finalise your windows xp operations. there is some howto's on how to do this, youll want to read those and get your boot disc together before you start your winxp reparations.

there is also supposed to be a way to reboot into a ubuntu live cd after windows rewrites the mbr and use a repair option, however i had 0 luck with doing so, it would always tell me grub was not installed (could have been due to lack of internet at time or me just missing something obvious)

---

### Post by Ben Page on 2011-02-23
This guy has it all explained

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Just repair your XP and then follow the instructions in the link (note: You'll need the Ubuntu Live CD).

---

