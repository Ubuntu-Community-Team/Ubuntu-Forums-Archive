---
title: "Problems duel booting - partitioning error. 8.10"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by danny h on 2008-12-18
Whenever I try to install 8.10 off a live cd, i get up to the partitioning stage, and straight away get an error, and it sends me back to the partitioning menu. However, now I dont have the choice to use the slider with how much space I want to allocate each - instead I am faced with a 'prepare partitions' page, and if i try to click forward i get 'no root file system is defined'

any ideas?

---

### Post by danny h on 2008-12-18
and heres what sudo fdisk -l says:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75cace1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6272    50379808+   7  HPFS/NTFS
/dev/sda2            6273        9729    27768352+   7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-12-18
Please also post the output of:
```
sudo sfdisk -luS
sudo parted /dev/sda print
```
And we can work from there if you want.

---

### Post by danny h on 2008-12-18
thanks for the quick reply!

ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 100759679  100759617   7  HPFS/NTFS
/dev/sda2     100759680 156296384   55536705   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA Hitachi HTS54168 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  51.6GB  51.6GB  primary  ntfs         boot 
 2      51.6GB  80.0GB  28.4GB  primary  ntfs

---

### Post by caljohnsmith on 2008-12-18
Looks like your partition table is OK, so how about first setting up your partitions prior to using the Ubuntu Installer, and see if that helps. Just open System > Admin > Partition Editor, and then you'll need to make at least two partitions for Ubuntu: one for the main Ubuntu install which will be mounted on "/" or root during the installation, and also a swap partition. But first you need to shrink one of your NTFS partitions to make room for Ubuntu, and once that is done, I would recommend making an "extended" partition with that space, and within the extended partition you can create logical partitions for Ubuntu and swap; you can also create any additional logical partitions you might want for your personal documents, etc. You can format the Ubuntu partition to use the ext3 file system, and the swap partition is just formatted as "swap". Generally the swap partition should be twice your RAM size, but you don't usually need a swap partition greater than 4 GB even if you have > 2 GB of RAM. How about trying to set up your partitions manually, and then let me know if the Ubuntu installer still has problems.

---

### Post by kansasnoob on 2008-12-18
If this is Vista I highly recommend using Vista's own partition tools:

[http://www.bleepingcomputer.com/tutorials/tutorial133.html](http://www.bleepingcomputer.com/tutorials/tutorial133.html)

---

### Post by danny h on 2008-12-18
woops!

i misunderstood the post, clicked 'create new partition' , and wiped my harddrive clean. xp is gone, along with everything else.

biggest mistake ever :(

---

### Post by caljohnsmith on 2008-12-18
> **danny h said:**
> woops!

i misunderstood the post, clicked 'create new partition' , and wiped my harddrive clean. xp is gone, along with everything else.

biggest mistake ever :(
OK, if you don't do anything else, there's a possibility we can recover your Windows partition. When you made the new partition, did you format it? How about posting the new output of:
```
sudo fdisk -lu

```

---

### Post by bodhi.zazen on 2008-12-18
You can likely recover your windows partitions with test disk (assuming you did not format).

If you did you may be able to recover some data with photorec.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

both are in the Ubuntu repos and you can "install" them while running the live CD

---

