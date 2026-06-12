---
title: "Serious partitioning problem!"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by checkm8 on 2010-12-05
Hi,

I installed ubuntu 10.10 on top of windows 7. Now my computer boots straight into ubuntu 10.10 and I cannot even boot to windows 7. Please help. The following might help you:

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4febc8b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          14       38767   292968750    7  HPFS/NTFS
/dev/sda3           38768       64602   195306985+   5  Extended
/dev/sda5           38768       39800     7809448+  82  Linux swap / Solaris
/dev/sda6           39801       64602   187497472   83  Linux


Any solutions? Also, grub doesnt even show up. So there are no options to boot to windows.

---

### Post by Mark Phelps on 2010-12-06
Did you allow the Ubuntu installer to shrink the Win7 OS partition to make room for Ubuntu? IF so, you likely got a corrupted WIn7 OS partition as a result.

When in Win7, you SHOULD have used the Backup feature to create and burn a Win7 Repair CD.  You could be using that now to repair your Win7 bootloader.

Since you probably did NOT do that, go to the link below, download the proper Win7 CD image, and burn that to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot from that and run Startup Repair three times -- that's right, three times.  That should restore Win7 boot capability.

---

### Post by dexeqex on 2010-12-06
When I upgraded to grub2 my menu stopped appearing.  Holding down the left shift button on boot brought it back.

---

