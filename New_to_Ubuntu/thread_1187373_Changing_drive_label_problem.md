---
title: "Changing drive label problem"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-14
How do I go about doing this because I've tried doing it from the storage device manager and I get a weird result.

Look at the attached screenshot.
The name is set to Spare but it's like morphed together with my old label which was "Dont delete". And I have no idea where the Q and S came from.

What can I do to clean this weird mess up and label them properly?

---

### Post by Gp. on 2009-06-15
Anybody :(

---

### Post by egalvan on 2009-06-15
Show us the output of 

```
fdisk -l
```

and the content of your fstab file

```
gedit /etc/fstab
```


Please wrap "code tags" around fstab output.

---

### Post by Gp. on 2009-06-15
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71e0c9c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47187   379029546   83  Linux
/dev/sda2           47188       48641    11679255    5  Extended
/dev/sda5           47188       48641    11679223+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08dc855c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4deeea85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS

```

And

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=3d5a164e-acf0-4d9f-be63-ec5343a0eb3b  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=832012d8-8b57-40b9-be8b-bba50c3d1a56  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
none                                       /proc/bus/usb   usbfs        devgid=46,devmode=664       0  0  
/dev/sdb1                                  /media/Spare    ntfs         defaults                    0  0  
/dev/sdc1                                  /media/Storage  ntfs         defaults                    0  0  
```

---

### Post by WorldTripping on 2009-06-15
You can use 'mtools' to rename FAT32 and 'ntfsprogs' for NTFS partitions.

They are in the repositories.

More here:
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

Cheers.

---

### Post by louieb on 2009-06-15
Open up Gparted and check the label column. Wonder if the partition label is "dont delete".

Newer versions of Gparted  can change the label of most types of partitions. 

The version in Jaunty is recent and has that feature. I use a  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") when I want to run Gparted.

---

### Post by egalvan on 2009-06-15
I forgot to ask for this... please post output of

```
sudo blkid
```

---

### Post by Gp. on 2009-06-16
```
/dev/sda1: UUID="3d5a164e-acf0-4d9f-be63-ec5343a0eb3b" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="832012d8-8b57-40b9-be8b-bba50c3d1a56" 
/dev/sdb1: UUID="1038B12D38B11328" LABEL="Spare [DONT DELETE]" TYPE="ntfs" 
/dev/sdc1: UUID="D47C5CAE7C5C8D5C" LABEL="TB [DONT DELETE]" TYPE="ntfs" 
```

Also how do I install gparted?
Is it available in the repositories?

sudo apt-get install gparted?

---

### Post by billgoldberg on 2009-06-16
> **Gp. said:**
> ```
/dev/sda1: UUID="3d5a164e-acf0-4d9f-be63-ec5343a0eb3b" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="832012d8-8b57-40b9-be8b-bba50c3d1a56" 
/dev/sdb1: UUID="1038B12D38B11328" LABEL="Spare [DONT DELETE]" TYPE="ntfs" 
/dev/sdc1: UUID="D47C5CAE7C5C8D5C" LABEL="TB [DONT DELETE]" TYPE="ntfs" 
```

Also how do I install gparted?
Is it available in the repositories?

sudo apt-get install gparted?

Yes, but it could be installed by default also.

---

### Post by snakeman21 on 2009-06-16
Gparted is really easy, just make sure you click the drop-down menu in the upper right corner and select the drive you want to change the label on.  Then, right-click the primary partition and select "unmount".  Right-click it again and click "label".  Change the label to you heart's content and click Apply.  

Gparted can also resize, add, and delete partitions, and format them to different filesystems.

---

### Post by Gp. on 2009-06-20
Did this, but the Label option is blanked out and I get this...

---

### Post by Gp. on 2009-06-20
> **WorldTripping said:**
> You can use 'mtools' to rename FAT32 and 'ntfsprogs' for NTFS partitions.

They are in the repositories.

More here:
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

Cheers.

Did this, but it says:
Ubuntu caches the drive's label so to see full affects of the change it is not enough just to umount and mount it again, the you should umount, remove, put back, mount again.

What does it mean to remove, put back?
The label shows up as what I want it to show up as, but after mounting, it's not shown graphically like that.

---

