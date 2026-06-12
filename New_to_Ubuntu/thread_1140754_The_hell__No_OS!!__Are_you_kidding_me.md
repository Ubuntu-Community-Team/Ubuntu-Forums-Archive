---
title: "The hell?  No OS?!!?  Are you kidding me??"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by DigiTan on 2009-04-27
Okay, I have two SATA drives.  Same model, same capacity.  The first one has all my files.  The second is new and empty.  I want to clone everything onto the new one.

I ran fdisk, which identified them as /dev/sda (occupied disk), /dev/sdb (empty disk).  To I ran **sudo dd if=/dev/sda of=/dev/sdb** expecting to have it done sometime in the AM tomorrow.  Instead, after about a minute, the PC reset and rebooted saying there was no OS.  I'm pretty sure I didn't get that command backward.  Here's what FDisk is saying:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa89b82a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30820   247561618+   7  HPFS/NTFS
/dev/sda2           30821       34867    32507527+   5  Extended
/dev/sda3   *       34868       36173    10490445   83  Linux
/dev/sda4           36174       38913    22009050   83  Linux
/dev/sda5           30821       31992     9414058+  83  Linux
/dev/sda6           31993       34604    20980858+  83  Linux
/dev/sda7           34605       34867     2112516   82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa89b82a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30820   247561618+   7  HPFS/NTFS
/dev/sdb2           30821       34867    32507527+   5  Extended
/dev/sdb3   *       34868       36173    10490445   83  Linux
/dev/sdb4           36174       38913    22009050   83  Linux
ubuntu@ubuntu:~$ 
```

Clearly, **something** went to sdb, because it used to say it was empty.

So two questions:
One: can I restore sda to some usable state?  And...
Two: what the hell just happened?

---

### Post by DigiTan on 2009-04-28
Question three: where is everybody?...body...body...body...

---

### Post by Kobalt on 2009-04-28
Try to boot your PC using a Live CD, or Live USB, and mount your drives/partitions to see what's in here.

---

### Post by HavocXphere on 2009-04-28
Whatever you do, don't write anything to the disk. Ideally, check whether you're BIOS can lock the drives to read-only until you figure out whats going on.

I'm not really all that familiar with data recovery under linux...but if I had to guess, I'd say the sda drive is flakey/dying.:( Better make backups ASAP.

Also, I've seen the same error when the BIOS battery is flakey and switches the boot drive...but that doesn't explain why it reset's.

---

### Post by DigiTan on 2009-04-28
My hardware flaking out the exact moment I hit this command?  Doesn't seem likely.  Windows, Ubuntu and openSUSE were able to access all this partitions with no problems.

My **fdisk** info above was captured through live CD after the crash.  The partition structure is pretty much the same as how I left it--other than maybe the flags, which I don't remember.

The two things that stick out to me are the disk identifiers being the same.  Maybe this caused some kind of irq or kernel conflict.  Also, partition #5 was mentioned in the error and was the first partition to be left out of sdb.  Incidentally, partition #5 also has my bootloader.

I'm going to try disconnecting sdb in a few hours to see if that makes it bootable.  I can't think of any reasons why sda would have been altered by this.

---

### Post by DigiTan on 2009-04-28
> **DigiTan said:**
> I'm going to try disconnecting sdb in a few hours to see if that makes it bootable.  I can't think of any reasons why sda would have been altered by this.

Tried it an I'm partly back in business.  With the sdb disk removed and the original in it's original SATA channel, the system boots up just like normal.  But with the failed clone plugged in, I can't even get to Grub/Stage2's bootloaders.  I still want to clone the disk so I'll try again.

---

### Post by anjilslaire on 2009-04-28
Try CloneZilla

---

### Post by DigiTan on 2009-04-29
Yeah.  For good measure, I'm also gonna try that Western Digital Lifeguard program and make sure my sdb drive isn't having a firmware fit.

---

### Post by The Cog on 2009-04-29
If you cloned the disk that perfectly, up until the unexplained crash, then you now have two partitions in the machine with the same UUID. Maybe it's trying to boot the unfinished clone. This could explain the problems with booting. Using the live CD to edit /boot/grub/menu.lst to specify by device instead of by UUID might help.

---

### Post by Hospadar on 2009-04-29
What happens if you just unplug sdb?

---

### Post by The Cog on 2009-04-29
> **Hospadar said:**
> What happens if you just unplug sdb?
See post #6

Another possiblle explanation is that with the second disk in, GRUB searches the partially copied disk for stage 2. So after a succesful copy and then removing sda, you may find that sdb boots fine.

---

