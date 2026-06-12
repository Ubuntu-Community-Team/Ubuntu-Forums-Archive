---
title: "What does this mean? &quot;fsck /dev/sdb&quot; results"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by zer010 on 2009-09-13
I'm running a live session.  I have put in another HD.  Not sure if it's ok or not.  I've been trying to reinstall Ubuntu a couple of times. At first i narrowed the problems down to a bad stick o' RAM. (Add-on pieces are comming from a found pc.)  My HD light is always on after I introduced the "new" HD.  I did some looking and found the "fsck" command, and sda comes up clean. sdb however.... well, it's right here:

ubuntu@ubuntu:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

sdb, if I remember correctly, is unallocated free space.  That shouldn't interfere with an installation should it?  I figured I'd partition it later, as it's going to be my distro test HD.

Any help, is greatly appreciated! Thanks!

---

### Post by scragar on 2009-09-13
If the drive is unalocated then use fdisk or Gparted to set it up, fsck can't check any file systems if there are none on the drive.(And fsck stands for **f**ile **s**ystems **c**hec**k**)

---

### Post by Sgt-Slyde on 2009-09-13
I believe /dev/sda is drive 0 (first hard drive) and /dev/sdb is drive 1 (second hard drive).  Partitions on the drives are usually identified as /dev/sda1, /dev/sda2, etc.  If there is no data you want to save on the new hard drive you're trying to add, try one of the partitioning tools to reestablish the partitions.  Otherwise, if you're wanting to keep the data I'd recommend some disk recovery tools (e.g. Hiren's Boot Disk) to rebuild the partition tables and recover the data, since your system doesn't seem to be able to read it as-is.

---

### Post by zer010 on 2009-09-13
I'm about to re-install again so I'm not worried about data loss.  I was just wondering if the fsck results looked like something was physically wrong with the drive.  Anything someone can tell me about my HD light staying on? Even during this live session, it's still on. Just a steady light, no flashing.

---

### Post by earthpigg on 2009-09-13
badblocks is what you want to use to check for physical defects :D

> man badblocks

---

