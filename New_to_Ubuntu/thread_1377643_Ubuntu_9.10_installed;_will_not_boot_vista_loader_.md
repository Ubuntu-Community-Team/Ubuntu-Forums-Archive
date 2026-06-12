---
title: "Ubuntu 9.10 installed; will not boot vista loader from cd"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by v1tal1 on 2010-01-10
My hdd is partitioned and ubuntu is on the first partition--the other partition is free.  I put in the vista disk and it will not boot from cd.  I tried a few things, but I'm kind of newb here.  Any help is much appreciated.  I've read through 100 threads on here, but none seem to contain a solution to my unique problem.  I'm a total rtard I guess.

---

### Post by Mrent on 2010-01-10
Check the boot order of your hardware in your BIOS.  Make sure your optical media is placed before your hard drive in boot priority. Also, it is possible your Vista disk is not bootable (this happened to me with the Vista upgrade disk).

---

### Post by warfacegod on 2010-01-10
You can access the BIOS with Esc button or one of the F keys. Sometimes Delete works it depends on the manufacturer.

---

### Post by kansasnoob on 2010-01-10
Generally look at pages 3 & 4 of this guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=3)

You'll see that they create no new partition for Vista at all. The area you're installing Vista to should be unformatted and unpartitioned.

**Note: the steps in that guide regarding grub are outdated.** Fresh installs of 9.10 use the grub2 bootloader. Look here about how to reinstall grub2 to the mbr:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Oops! missed this, "I put in the vista disk and it will not boot from cd."

---

### Post by v1tal1 on 2010-01-10
> **Mrent said:**
> Check the boot order of your hardware in your BIOS.  Make sure your optical media is placed before your hard drive in boot priority. Also, it is possible your **Vista disk is not b**ootable (this happened to me with the Vista upgrade disk).

I think that may be the problem.  I already assured cd was 1st boot priority.  The disk is my recovery dvd and appears to not be bootable.  I think it only loads if it reads an existing copy of vista on the hdd.  damn.  Well, thanks for the help.  My neighbor has an actual new vista loader disk.  I'll try that.

---

### Post by v1tal1 on 2010-01-10
> **kansasnoob said:**
> Generally look at pages 3 & 4 of this guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=3)

You'll see that they create no new partition for Vista at all. The area you're installing Vista to should be unformatted and unpartitioned.

**Note: the steps in that guide regarding grub are outdated.** Fresh installs of 9.10 use the grub2 bootloader. Look here about how to reinstall grub2 to the mbr:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Oops! missed this, "I put in the vista disk and it will not boot from cd."

Thanks for the info, but I think my disk being a recovery cd/dvd is the problem.

---

