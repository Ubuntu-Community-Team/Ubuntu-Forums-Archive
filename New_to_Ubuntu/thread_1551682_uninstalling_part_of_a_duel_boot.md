---
title: "uninstalling part of a duel boot"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-08-12
how do i erase the ubuntu 10.04 from the harddrive?

---

### Post by cj.surrusco on 2010-08-12
Start up a partition manager in Windows and delete the Ubuntu partition. Then boot to the Windows disk and reinstall the bootloader if necessary.

---

### Post by ornothaloapq on 2010-08-12
is that obvious or is there more steps a beginner would need to know?

---

### Post by jeffymarts on 2010-08-12
Ok, so the thing is that you have to actually manually delete the Ubuntu partition that's installed. That's not as simple as it sounds though because that's where the MBR (Master Boot Record: Thingie that loads the OS's if you weren't aware.) resides and if that's deleted... well, it's not good. So follow this tutorial ([http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)) to delete the partition with Ubuntu in it without getting rid of the MBR.

---

### Post by earthpigg on 2010-08-12
> **ornothaloapq said:**
> is that obvious or is there more steps a beginner would need to know?

as always with partitions, have solid backups in place first.

other than that, not really. maybe verify that your windows disk works beforehand. it may be safer to install the windows bootloader and verify that it works *before* deleting the ubuntu partition... but, as long as you have solid backups, it really doesn't make a difference.

---

### Post by jeffymarts on 2010-08-12
What cj.surrusco said works too, but I think this way is easier if you're a noob. I had to do a similar thing when I first started using Ubuntu and at that time I didn't have much knowledge about computers but that tutorial explained what I needed to know.

---

### Post by cj.surrusco on 2010-08-12
> **jeffymarts said:**
> Ok, so the thing is that you have to actually manually delete the Ubuntu partition that's installed. That's not as simple as it sounds though because that's where the MBR (Master Boot Record: Thingie that loads the OS's if you weren't aware.) resides and if that's deleted... well, it's not good. So follow this tutorial ([http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)) to delete the partition with Ubuntu in it without getting rid of the MBR.

I don't think he would want the grub bootloader without Ubuntu, just Windows. It would be hard to edit without a Ubuntu partition and he is probably better off with the Windows bootloader. 

The only difficult part may be reinstalling the Windows bootloader. For Vista or 7 it is easy, just boot to the CD and choose to fix it automatically. With XP, you have to login to the recovery console and execute 'fixmbr' and 'fixboot'.

---

