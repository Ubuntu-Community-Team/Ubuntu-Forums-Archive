---
title: "Convert Logical Partition to Primary"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by probev on 2010-04-19
Hi:

I had to replace my hard drive and the new hard drive is twice as big. In my original configuration, I had dual boot (XP and Ubuntu 9.10 64-bit). Ubuntu was initially installed on an extended partition. With the new drive, I'd like to seperate my windows and my ubuntu partitions. The problems is I have close to 150 GB unused space and here is the out put of the fdisk:

```
root@probev-lnx:~# fdisk -ul

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe0c6372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   105177554    52588746    7  HPFS/NTFS
/dev/sda2       105177555   308383739   101603092+   f  W95 Ext'd (LBA)
/dev/sda4       616751415   625137344     4192965   82  Linux swap / Solaris
/dev/sda5       105177618   252509669    73666026    7  HPFS/NTFS
/dev/sda6       252509733   308383739    27937003+  83  Linux

```The question I have is how can I move /dev/sda6 outside the extended /dev/sda2 and utilize the unallocated 150 GB:

1. Without loosing any data
2. Being able to still boot out of my Ubuntu

I'd appreciate your help!!!

---

### Post by carl4926 on 2010-04-19
That's messy, you need to rip it up and start again.

---

### Post by probev on 2010-04-19
> **carl4926 said:**
> That's messy, you need to rip it up and start again.

Ohhhh, don't say that :(

My swap is on diff primary partition. I can recreate /dev/sda5 (Windows D: drive)...

Just want to avoid reinstalling ubuntu. I have MANY customization done already.

Would appreciate any help.

---

### Post by probev on 2010-04-19
> **carl4926 said:**
> That's messy, you need to rip it up and start again.

Can't I copy my Linux partition to the unallocated space and tell ubuntu to boot from there?

---

### Post by friv_livs on 2010-04-19
Are you willing to let your computer be unusable for 24 hours?

If yes:

Do you have a parted magic CD? If not, go [HTML]http://sourceforge.net/projects/partedmagic/[/HTML], download the .zip, unpack the .zip for the.iso, burn the .iso to CD.

Then boot the parted magic disk, open gparted or partition editor, and set the following tasks, in this order:

1. click /dev/sda2, right click->extend/grow->left click, and move the right edge of the graphical bar all the way right.

2. click /dev/sda6, right click->extend/grow->left click, and move the right edge of the graphical bar all the way right.

This will keep the linux partition intact.

Otherwise, you need to do a back-up and reinstall to change logical to primary.

---

### Post by louieb on 2010-04-19
friv_livs  suggestion is good - if it were mine - that what I would do. Actually should go pretty fast - growing a partition to the left usually does.

Just a bit of info:  **sfdisk** can change a logical partition into a primary one or a primary partition into a logical one.  

Using sfdisk is dangerous - if you have never used - its best to practice on a disk  you can loose everything on or practice in a virtual machine  such as Virtualbox.

[sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

### Post by srs5694 on 2010-04-19
I'd do it a different way: Create a new partition in the currently-unallocated space and [convert it into a /home filesystem.](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/) This will give you the advantages of a separate /home directory, such as an ability to completely wipe out and reinstall Ubuntu (or even move to another distribution) without affecting your user data.

That said, the layout that will result won't be quite ideal. Most importantly, you'll have a big NTFS partition between your /home and your root (/) partitions, which will degrade performance. (You've got a similar problem now with your swap and root (/) partitions.) Another issue is that your root (/) partition will be a bit on the big side -- 27GB or so. (5-20GB is about right these days for an installation with a separate /home partition, depending on how much software you install.) IMHO, though, these problems are both minor enough that it's better to just live with them than to completely reinstall or risk trashing your system with the amount of filesystem copying and moving that you'd need to do to fix these problems.

---

### Post by probev on 2010-04-19
So, here is what I did and it worked great (all of this was run with Ubuntu LiveCD).

1. Out of the unallocated space I created an ext4 partition - /dev/sda3 (Primary)
2. Did dd from the linux partition to the new partition - dd if=/dev/sda6 of=/dev/sda3
3. resize2fs the new partition
4. Mounted the new partition - /media/sda3
5. Reinstalled the Grub2
6. Dropped the original partition
7. Resized /dev/sda3 and now all ext4 partitions are consecutive, right after the NTFS partitions. No gaps. Someone mentioned that it is not good to have gaps.
7. Reboot and everything works great

One thing I noticed is that after dd the UUID of the original and the new partition is the same. If it is not we got to make sure that we update it.

Again, I used clonezilla to take a full disk image before I started anything and after I was done I just finished with the disk image after everything was implemented.

Here is my new fdisk -ul

```
root@my-lnx:/home/probev# fdisk -ul

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe0c6372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   105177554    52588746    7  HPFS/NTFS
/dev/sda2       105177555   252509669    73666057+   f  W95 Ext'd (LBA)
/dev/sda3       252509670   616751414   182120872+  83  Linux
/dev/sda4       616751415   625137344     4192965   82  Linux swap / Solaris
/dev/sda5       105177618   252509669    73666026    7  HPFS/NTFS
```

Hope this would help others in the forum.

---

