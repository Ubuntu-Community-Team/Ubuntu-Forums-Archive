---
title: "mount fat32 drives"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by mdysonr on 2009-01-23
I've installed Xubuntu 8.10  on my computer but i cant mount fat32 drives, i need the permission to the read and write on that drives

sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcca6ceef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+   c  W95 FAT32 (LBA)
/dev/sda2            1403       10011    69151792+   f  W95 Ext'd (LBA)
/dev/sda5            1403        9206    62685598+   c  W95 FAT32 (LBA)
/dev/sda6            9207        9970     6136798+  83  Linux
/dev/sda7            9971       10011      329301   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4852f6b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+   c  W95 FAT32 (LBA)

---

### Post by t4ggs on 2009-01-23
install the software called "Disk Manager" is in the repositories, i use it for ntfs partitions and it works really well...

---

### Post by billgoldberg on 2009-01-23
> **mdysonr said:**
> I've installed Xubuntu 8.10  on my computer but i cant mount fat32 drives, i need the permission to the read and write on that drives

sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcca6ceef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+   c  W95 FAT32 (LBA)
/dev/sda2            1403       10011    69151792+   f  W95 Ext'd (LBA)
/dev/sda5            1403        9206    62685598+   c  W95 FAT32 (LBA)
/dev/sda6            9207        9970     6136798+  83  Linux
/dev/sda7            9971       10011      329301   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4852f6b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+   c  W95 FAT32 (LBA)

Open up your terminal (system -> accessories -> terminal).

Enter this:

```
sudo mkdir /media/drive1
```

This will create a directory in /media for your drive to be mounted on.

Here I called it "drive1", but you can call it anything you want.

Then do this:

```
sudo mount /dev/sda1 /media/drive1
```

This tells the pc to mount /dev/sda1 (aka your first fat32 parition) to the newly created folder in /media.


Repeat for drives sda2 and sda5. But make sure to create a different folders for them in /media.

You only need to make those folders in /media once.

In the future you can just just the mount command.

---

### Post by mdysonr on 2009-01-23
its works thanks

---

### Post by timcredible on 2009-01-23
usually when you can't mount a fat16 or fat32 drive read/write it's because there's errors on the drive.  try running dosfsck on it and see if it works normally after that.

---

