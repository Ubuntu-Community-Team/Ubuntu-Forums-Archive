---
title: "Can't mount external HardDrive"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by SalsaShark on 2009-04-16
So I need to back up my files and I've been having trouble with my external harddrive for awhile now.  I want to use it for both Linux and Windows, so I've got it formatted in FAT32.  It used to auto-mount but it was only readable, now it doesn't even automount saying that the computer cannot read FAT32 file systems.  Any idea what the problem is?

---

### Post by bobmatino17 on 2009-04-16
did it say it cant read FAT32? because it has to at least read it to tell what FS it is. If it was say ext3 on Windows, it would say the drive wasnt formatted. So it should be able to read it at least. And second, did *you* format it with FAT32? Because sometimes the manufacturer doesnt have formatted properly.

---

### Post by SalsaShark on 2009-04-16
Yeah, I get an pop-up that explicitely says:
"Cannot Mount Volume
The volume uses the FAT32 file system which is not supported by your system."

---

### Post by taurus on 2009-04-16
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by SalsaShark on 2009-04-16
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fcc211e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       14365   105146364    6  FAT16
/dev/sda3           14366       14607     1943865   82  Linux swap / Solaris
/dev/sda4           14608       30401   126865305   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)

---

### Post by taurus on 2009-04-16
What happens when you try to mount it by hand from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by bobmatino17 on 2009-04-16
is your external hdd 80GB? because sdb is common for external drives.

---

### Post by SalsaShark on 2009-04-16
Hmm, I guess it mounted... Thanks.  So I'm going to have to do that every time eh?

---

### Post by halitech on 2009-04-16
you can look here: [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

and scroll to the bottom and edit fstab so it mounts everytime on boot

---

