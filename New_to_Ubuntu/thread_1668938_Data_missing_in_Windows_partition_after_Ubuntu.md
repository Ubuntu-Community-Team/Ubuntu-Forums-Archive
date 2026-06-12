---
title: "Data missing in Windows partition after Ubuntu"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by alabhya on 2011-01-17
I recently installed Ubuntu 10.10 on my system, dual boot with Windows 7.

I have 2 drives for Windows (C,D) and 2 for ubuntu (/,swap) and recovery.

The contents of "Downloads" folder of Windows (C;\Users\..\Downloads) have gone missing. 
I had last accessed that folder from ubuntu to copy some data to the ubuntu partition.
Also,i tried opening one of the files there with wine.

Later i booted into windows and saw that the folder content was missing.

So has it been moved somewhere or deleted?

---

### Post by wilee-nilee on 2011-01-17
Install gparted in Ubuntu from the software center or run in the terminal.
sudo apt-get install gparted

Open gparted and take a screen shot of it and post it, using the paper clip in the reply panel to upload the image then click on it to place it in a reply.

I don't think your supposed to have wine run that way I'm not surprised something is amiss. Wine is for running in ubuntu with downloads to ubuntu, I believe.

---

### Post by diablo75 on 2011-01-17
Never saw that happen before.  Are you sure you didn't move the data instead of copy it?  Can you not just copy the data back from the Ubuntu side?

Also, a better way to show us your partition layout is to open a terminal, type the following:

```
sudo fdisk -l
```

and copy/paste the output of that command back here in the forum.

---

### Post by sanderd17 on 2011-01-17
Maybe you don't suspend to disk, but if you did, that could be the cause.

If you suspend an OS to disk, the OS expects that nothing is changes when it is fired up again. If you use 2 OSes, you can't suspend.

---

### Post by alabhya on 2011-01-17
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14        1303    10360832    7  HPFS/NTFS
/dev/sda3            1303       18865   141064192    7  HPFS/NTFS
/dev/sda4           18866       60801   336850889+   f  W95 Ext'd (LBA)
/dev/sda5           18866       25090    50000000   83  Linux
/dev/sda6           25090       25339     1999872   82  Linux swap / Solaris
/dev/sda7           25339       60801   284850689    7  HPFS/NTFS



And the data is missing even if i browse through ubuntu..
dont remember me deleting it either..

---

### Post by Rubi1200 on 2011-01-17
From what I have read, you need to be careful with NTFS and Linux as permissions can get messed up.

This is not the first time I have seen this happen. If you want to share data between Windows and Ubuntu use a separate partition and format it to FAT32.

In this case, the only two things I can think of are to enable viewing system files and see if the stuff "disappeared" somewhere or try a System Restore in Windows though I cannot guarantee that will work.

You might also want to look in the Wine folders on Ubuntu, especially any hidden (starts with .) files in your home directory (Ctrl + H).

---

