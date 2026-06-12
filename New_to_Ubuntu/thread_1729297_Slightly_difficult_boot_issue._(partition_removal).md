---
title: "Slightly difficult boot issue. (partition removal)"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-14
I have a hard drive with 3 partitions:

The first partition just has the system/boot files for Windows XP (but not Windows itself, just the boot files)

The second partition has the actual Windows installation (the Windows directory, Program Files, etc.)

And the third partition has Ubuntu 10.10 with the ext4 file system.


I want to delete the first and second (Windows) partitions.

Is that going to screw up my Linux installation?  Will I need to do something with GRUB or anything else?

---

### Post by searchfgold6789 on 2011-04-14
> Is that going to screw up my Linux installation?  Will I need to do something with GRUB or anything else?Nope. Just remember to run ```
sudo update-grub
```when you are finished. That's assuming the grub program files are not on either of the partitions you are deleting.

---

### Post by K_45 on 2011-04-14
I'd use GParted to delete both windows partitions, then expand the Ubuntu partition before running the above command.

---

### Post by seawolf167 on 2011-04-14
I'd boot off a LiveCD, fire up GParted, delete both the Windows partitions leaving only Ubuntu. Then resize the Ubuntu partition to take up the entire disk. Once done, restart and see if you deleted GRUB (I don't know what partition you installed it on). If you did, restoring GRUB is pretty easy. Here is a [how-to link]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") (you'll need the LiveCD)

---

### Post by Learning Linux 2011 on 2011-04-15
> **searchfgold6789 said:**
> Nope. Just remember to run ```
sudo update-grub
```when you are finished. That's assuming the grub program files are not on either of the partitions you are deleting.

Would GRUB normally install files on those Windows partitions?  The Windows partitions were there first, then I installed Ubuntu later.

I always thought that GRUB was installed in the Master Boot Record, is that right?
Would it also possibly place files in the first two Windows partitions?

---

### Post by -kg- on 2011-04-15
> **Learning Linux 2011 said:**
> Would GRUB normally install files on those Windows partitions?  The Windows partitions were there first, then I installed Ubuntu later.

I always thought that GRUB was installed in the Master Boot Record, is that right?
Would it also possibly place files in the first two Windows partitions?

In a word, no.  In a normal (not WUBI) installation, GRUB loads a small boot loader into the MBR.  The rest of the files reside in the "/grub" directory, which normally resides on the "/root" partition of your Linux installation, unless you created a separate "/boot" partition, in which case, it will reside there.  It will never install any part of itself into a Windows partition (unless you tell it to, which is highly unlikely...you would know if you told the installer to install it there, and I don't think it can be done).

The only problem I might see is if Ubuntu is loaded on a logical partition, and you deleted a logical partition that was ahead of it.  Since Windows is highly unlikely to have been installed to a logical partition, I would say that you're good to go.

---

