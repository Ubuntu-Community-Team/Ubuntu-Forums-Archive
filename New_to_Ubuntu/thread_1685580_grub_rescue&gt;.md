---
title: "grub rescue&gt;"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by zoocrew on 2011-02-10
OK so I did something pretty stupid: I replaced my hard drive and installed Ubuntu 10.10 on my netbook. I’ve played with it for a few months and decided I didn’t like it (Can’t stream net flix, can’t tether my cell phone with PDA net, and can’t run my on-line training required from work). So I decided to put windows back on- I never partitioned the drive. The only thing I had around was an old Gateway recovery disc with Windows XP Media center 2005. I booted the disc and it looked like it was loading and then stopped. There was some kind of odd message box with a long string of numbers(?) and an ok button I then selected. Now all get is:

error: unknown filesystem
grub rescue>

How do I fix my netbook?

---

### Post by wojox on 2011-02-12
If you want Windows installed you need to purchase a CD. Then you can load it and it will run and install.

---

### Post by tednix on 2011-02-12
You need the Windows disc that came with your netbook.  Windows OEM discs are "tied" to a particular motherboard and since Windows 2005 didn't ship with your netbook it almost certainly won't install.
Also make sure that the HD is formatted to something that Windows can recognize eg FAT32 or NTFS before trying to install.  Maybe using gParted from a Ubuntu live cd could do the formatting.
One last suggestion replace the present HD with the original drive since it had Windows already running.

---

### Post by billcecil on 2011-02-12
Windows is easy. Buy the disk, and install. no more problems.

---

### Post by drs305 on 2011-02-12
If you are getting the Grub rescue prompt and have a *bootable* CD inserted, make sure the BIOS is looking at the CD first. If it isn't, the system will try to boot from the MBR, which still points to the Ubuntu partition. You said it looked like it tried to boot the CD. If that fails, the BIOS might revert to it's second choice - the hard drive. Make sure the CD is clean, and you might check to make sure the CD drive works with some other CD just to make sure it's not a CD drive problem.

If you have a bootable *and working * CD and have the BIOS point to the CD first, and you won't get the 'grub rescue' prompt.

---

