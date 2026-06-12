---
title: "New USB HD Found, but not mountable"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-12-12
I have a new USB HD I received yesterday.  It came unformatted so I plugged it in and I see USB drive showing up.  Also, it comes up as /dev/sdd.  The problem is when I use QT Parted and create a FAT32 partition, the drive suddenly disappears from the Computer view, although still accessible via FDisk.

I feel pretty dumb, but can someone tell me what's going on?  When the drive is blank...I can see it, but not mount it.  When I place a partition on it, it disappears from the computer view.  I even created the partition and used QTParted to format the drive and make it active, still not seen or accessible.  Obviously I am missing somthing in the process...

Any help is greatly appreciated

Here is a screen print from my fdisk -l:

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006a2a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14593   117218241    b  W95 FAT32

---

### Post by TJCIB on 2008-12-12
```
mkdir /mnt/harddrive
sudo mount -t vfat /dev/sdd1 /mnt/harddrive
```

*edit*
If you want a desktop icon to appear, you should make your mount point /media/harddrive and change the next command also

---

