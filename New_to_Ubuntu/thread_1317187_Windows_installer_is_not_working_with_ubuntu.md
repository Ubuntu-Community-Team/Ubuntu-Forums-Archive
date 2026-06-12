---
title: "Windows installer is not working with ubuntu"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by dilantha on 2009-11-06
Hi,
  I have a problem with installing windows when ubuntu is already installed in my machine. Windows installer did not work when ubuntu is there. First i thought it might be a problem with the windows CD.But after removing ubuntu and re formatting that partition in to NTFS format that it worked really fine.This is a big problem for me.because when ever i want to reinstall windows i have to remove ubuntu first and then install both windows and  ubuntu :( . If any one can help with me in this it would be a great help.THanks..

---

### Post by wrgb2 on 2009-11-06
When you installed Ubuntu, did you let it format the entire disk as ext3 or ext4?

---

### Post by ajgreeny on 2009-11-06
The problem is that windows can not see any ext3 formatted disks, so as far as the windows installer was concerned, you did not have a disk, or any disk space, to install windows to.

To overcome this you need to shrink your ubuntu partition using the live ubuntu CD and either make the empty space into an ntfs partition, or just leave it unallocated, though I seem to remember others saying that unallocated space that had once been ext3 was still not recognised by windows.

---

### Post by dilantha on 2009-11-08
> **wrgb2 said:**
> When you installed Ubuntu, did you let it format the entire disk as ext3 or ext4?

No. I installed ubuntu in a separate partition.Size is around 20 GB.Except that partition all the other partitions partitions are NTFS..but unless i remove ubuntu and made that 20 GB partition NTFS, windows installer didn't work..What can be the issue??.

---

### Post by dilantha on 2009-11-08
> **ajgreeny said:**
> The problem is that windows can not see any ext3 formatted disks, so as far as the windows installer was concerned, you did not have a disk, or any disk space, to install windows to.

To overcome this you need to shrink your ubuntu partition using the live ubuntu CD and either make the empty space into an ntfs partition, or just leave it unallocated, though I seem to remember others saying that unallocated space that had once been ext3 was still not recognised by windows.


THanks for your reply..That means do i have to remove ubuntu when ever i want to install windows again?

---

### Post by ajgreeny on 2009-11-08
No you shouldn't have to remove Ubuntu, but you will need to shrink its partition or windows will not see the disk space.  It needs unallocated or ntfs/vfat formatted partitions to able to work on the disk in the first place.

Windows is totally blind to the ext file systems used most commonly by linux distros.  For this reason you can not use the windows installer to shrink the existing ext filesystem on the disk, but must do it as a separate activity.

I see, however, that you already have separate partitions form the OSs, so I am rather baffled about why the windows install CD can not do its stuff, unless what you have is a recovery CD for windows as originally installed, as I understand that occasionally these demand a hard disk of exactly the same size as was used originally.  If that is the case, then, yes, you may have to remove ubuntu, install windows and then reinstall ubuntu.

---

