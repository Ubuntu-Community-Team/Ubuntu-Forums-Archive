---
title: "Gparted error help please"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by antmenj on 2011-02-10
I have just got two new USB sticks.  I tried to use one with Gparted and it crashes it with:

```
======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xc03f0a]
  15: /lib/libparted.so.0(+0x42507) [0xc3b507]
  14: /lib/libparted.so.0(+0x43317) [0xc3c317]
  13: /lib/libparted.so.0(+0x4460c) [0xc3d60c]
  12: /lib/libparted.so.0(+0xf7b1) [0xc087b1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xc0c032]
  10: /lib/libparted.so.0(+0x45fa3) [0xc3efa3]
  9: /lib/libparted.so.0(+0x4619f) [0xc3f19f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xc0ce15]
  7: /usr/sbin/gpartedbin() [0x80901e6]
  6: /usr/sbin/gpartedbin() [0x809fc9b]
  5: /usr/sbin/gpartedbin() [0x80c0532]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0x2bbeb2]
  3: /lib/libglib-2.0.so.0(+0x65def) [0x63fdef]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0x1b296e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x4a6a4e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.

```

Can anyone help me with the meaning of the above?  I'm using lucid i386.  I have tried reformatting it with ubuntu and vi$ta and it seems to work but for some reason not with Gparted.  Could it be faulty?

---

### Post by Linyx on 2011-02-10
Have you Notice it in GUI-Parted...?

I had never used CLI-Parted,but check out the Flash drives in GUI-Parted, is it Missing..?

---

### Post by antmenj on 2011-02-10
What is this guiparted?  I have just looked for it in synaptic and tried installing it from cli without any luck.

At the terminal I did sudo gparted and it crashed with the above error.  I tried two other drives and it did not crash but opened gparted fine.

---

### Post by xtremethegreat1 on 2011-02-10
It happened to me once. I formatted the pen drive with Vista and it makes a different kind of partitioning. Try formatting it with this in the terminal:

sudo mkfs.vfat /dev/sdb1

Make sure only one pen drive is inserted when you're doing this. If this does not work, try this:

sudo mkfs.vfat /dev/sdb

If even this does not work, then your pen drive is in an sdc. Try the two in this order, whichever works first:

sudo mkfs.vfat /dev/sdc1
sudo mkfs.vfat /dev/sdc

Hope that helps. Just lemme know what happens..

---

### Post by srs5694 on 2011-02-10
> **xtremethegreat1 said:**
> It happened to me once. I formatted the pen drive with Vista and it makes a different kind of partitioning. Try formatting it with this in the terminal:

sudo mkfs.vfat /dev/sdb1

Make sure only one pen drive is inserted when you're doing this. If this does not work, try this:

sudo mkfs.vfat /dev/sdb

If even this does not work, then your pen drive is in an sdc. Try the two in this order, whichever works first:

sudo mkfs.vfat /dev/sdc1
sudo mkfs.vfat /dev/sdc

***If you don't know what device file represents your disk, do not use mkfs on ANY device file!!!!!***

Suppose for the sake of argument that the disk device you want to use is /dev/sdc. If you were to follow xtremethegreat's advice, the result would be the destruction of data on /dev/sdb1 and/or /dev/sdb, which could be another USB flash drive, the Linux boot disk, another OS's boot disk, or whatever.

As to the original problem, I suggest more clarity. You say that the disk works with Vista. If so, then it's already ready to use; there's no need to use GParted on it. If you want to re-partition it or create a Linux-specific filesystem on it, then you might try using fdisk to create a fresh partition table. Launch fdisk on the disk (as in "sudo fdisk /dev/sdc" -- but of course you must know the device filename!), type "o", and then type "w" to save your changes. Then try GParted with it. Of course, doing this will render any data already on the disk inaccessible, so do this only if you want to create a blank but usable disk. I'm working from the hypothesis that the disk has a "raw" filesystem on it, with no partition table, and that this is confusing GParted. By writing a fresh Master Boot Record (MBR) partition table using fdisk, this should keep GParted from getting confused, and you'll be able to use GParted to create whatever partitions and filesystems you like. (Alternatively, you could use fdisk to create partitions and mkfs to create filesystems on them.)

---

### Post by JC Cheloven on 2011-02-10
> **antmenj said:**
>  (...)  I have tried reformatting it with ubuntu and vi$ta and it seems to work but for some reason not with Gparted.  Could it be faulty?
I wonder what do you exactly mean. You formatted it with ubuntu? Using what? From nautilus, perhaps?
In that case, you can try the DiskUtility from the Andministration menu. I think it uses the same backend as Nautilus for this task.

BTW, pay attention to srs's advice. You may get into real problem if you blindy run mkfs on a 'random' device. Please check first which device is the right target with (for example) ```
sudo fdisk -l
```

---

### Post by Linyx on 2011-02-11
> **antmenj said:**
> What is this guiparted?  I have just looked for it in synaptic and tried installing it from cli without any luck.

At the terminal I did sudo gparted and it crashed with the above error.  I tried two other drives and it did not crash but opened gparted fine.

I means to say Graphical-Partition-Tool.....Not Command-Line....

---

### Post by xtremethegreat1 on 2011-02-11
> **srs5694 said:**
> ***If you don't know what device file represents your disk, do not use mkfs on ANY device file!!!!!***

Suppose for the sake of argument that the disk device you want to use is /dev/sdc. If you were to follow xtremethegreat's advice, the result would be the destruction of data on /dev/sdb1 and/or /dev/sdb, which could be another USB flash drive, the Linux boot disk, another OS's boot disk, or whatever.

As to the original problem, I suggest more clarity. You say that the disk works with Vista. If so, then it's already ready to use; there's no need to use GParted on it. If you want to re-partition it or create a Linux-specific filesystem on it, then you might try using fdisk to create a fresh partition table. Launch fdisk on the disk (as in "sudo fdisk /dev/sdc" -- but of course you must know the device filename!), type "o", and then type "w" to save your changes. Then try GParted with it. Of course, doing this will render any data already on the disk inaccessible, so do this only if you want to create a blank but usable disk. I'm working from the hypothesis that the disk has a "raw" filesystem on it, with no partition table, and that this is confusing GParted. By writing a fresh Master Boot Record (MBR) partition table using fdisk, this should keep GParted from getting confused, and you'll be able to use GParted to create whatever partitions and filesystems you like. (Alternatively, you could use fdisk to create partitions and mkfs to create filesystems on them.)
@srs5694 Exactly why I asked to make sure that there was only one pen drive inserted while keying in the command..

---

### Post by xtremethegreat1 on 2011-02-11
The problem is with the block size. Vista, by default, formats with a block size that gparted does not support. Gparted (or even parted for that matter), will crash when invoked with that pen drive inserted.

If you have access to a Win XP box, try formatting it with that and it should work just fine.

---

### Post by srs5694 on 2011-02-11
> **xtremethegreat1 said:**
> @srs5694 Exactly why I asked to make sure that there was only one pen drive inserted while keying in the command..

The trouble is that factors other than the number of USB flash drives plugged in will influence the device ID of the target USB flash drive. Of most concern to me in this context is the number of internal hard disks. If the computer has two internal hard disks, then they will probably be /dev/sda and /dev/sdb, and your advice to begin by blindly creating a new filesystem on /dev/sdb1 will overwrite whatever is on /dev/sdb1. In this scenario, chances are /dev/sdb1 holds something valuable. The suggestion to then create a filesystem on /dev/sdb if doing it on /dev/sdb1 "does not work" is even worse, since in this scenario you'd be wiping out the partition table on /dev/sdb, thus creating the need for low-level recovery of *all* the data on that disk, not just on the first partition.

I stand by my advice: ***Never*** use mkfs on a partition or other device unless you're 100% sure what that device is. A "fishing expedition" approach is likely to cause problems -- ***big* **problems! As JC Cheloven points out, fdisk can provide clues about what's on a disk. So can the "df" command (it'll tell you what's currently mounted). There's no need to proceed blind with such operations.

---

### Post by srs5694 on 2011-02-11
> **xtremethegreat1 said:**
> The problem is with the block size. Vista, by default, formats with a block size that gparted does not support. Gparted (or even parted for that matter), will crash when invoked with that pen drive inserted.

If you have access to a Win XP box, try formatting it with that and it should work just fine.

If by "block size" you mean the device's sector size, that's set in the hardware and can't be adjusted by software; that is, it's not a question of a choice made in Vista. The most common sector size today is 512 bytes, although some devices use other sector sizes. GParted does (or did recently; I haven't checked in a few months) have problems with non-512-byte sector sizes, so it is conceivable that this is the problem. If so, Linux should still be able to mount and access the drive just fine, but you'll need to use other tools, such as fdisk and mkfs, to manage the drive's partitions and filesystems.

If by "block size" you mean an allocation block size within the filesystem, I've never before heard the claim that Vista uses settings that cause GParted problems. I just checked, and I was able to resize a Vista-created partition using GParted just fine, so I'm highly skeptical of this claim.

---

### Post by xtremethegreat1 on 2011-02-13
Blocks are different from sectors... Blocks are used for addressing, and their info is stored in the partition header.

---

