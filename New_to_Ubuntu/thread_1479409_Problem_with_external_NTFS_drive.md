---
title: "Problem with external NTFS drive"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Res2216firestar on 2010-05-10
Hi, I recently installed ubuntu 10.04 to my computer when XP failed, and everything's working great so far except for my 250GB WD USB hard drive. It has all the pictures and stuff that I backed up from windows. 

It came preformatted with NTFS and Windows confirmed that while it was working. When I plug it in, it seems to work, and I can read and write to it, but the properties dialog says the filesystem is "msdos", GParted says it has support for NTFS through ntfsprogs, but it says the drive FAT32, and can't find a mount point. I do have ntfs-3g installed. Here's my fstab if anyone can decipher it. My main confusion is that the drive is located at /dev/sdb according to GParted, but fstab makes no mention of it:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2658b5df-d2c7-4cd1-8f1b-5515442f1002 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

What I mainly want to know is if what I wrote to it in Ubuntu is safe, and what I can do to get gparted to work properly with it (I want a partition for my Wii).

---

### Post by The Cog on 2010-05-10
Can you post the output of **sudo fdisk -l** and **sudo blkid** please.

---

### Post by Res2216firestar on 2010-05-10
sudo fdisk -l:
> Disk /dev/sda: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f8b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7120    57186304   83  Linux
/dev/sda2            7120        7302     1463297    5  Extended
/dev/sda5            7120        7302     1463296   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)


sudo blkid:
> /dev/sda1: UUID="38cbba59-c12a-4233-b986-322e44a52cce" TYPE="ext4" 
/dev/sda5: UUID="2658b5df-d2c7-4cd1-8f1b-5515442f1002" TYPE="swap" 
/dev/sdb1: LABEL="My Passport" UUID="B808-895E" TYPE="vfat" 


---

### Post by drdos2006 on 2010-05-10
/dev/sda1: UUID="38cbba59-c12a-4233-b986-322e44a52cce" TYPE="ext4"
/dev/sda5: UUID="2658b5df-d2c7-4cd1-8f1b-5515442f1002" TYPE="swap"
/dev/sdb1: LABEL="My Passport" UUID="B808-895E" TYPE="vfat" 

Your device is /dev/sdb1.
Open up a terminal.
Make a directory.
type : sudo mkdir /media/sdb1
type : sudo cp /etc/fstab /etc/fstab.backup
Edit the fstable.
type : sudo gedit /etc/fstab
Add this to fstab :
# /dev/sdb1
UUID=B808-895E	/media/sdb1	ntfs	defaults 	0	1

Save and close, mount all drives
type : sudo mount -a

regards

---

### Post by Res2216firestar on 2010-05-10
Thanks :D

---

### Post by The Cog on 2010-05-11
Looking at those outputs, I think your drive is FAT, not NTFS. The partition table says it's FAT (type c) rather than NTFS (type 7), and blkid also says it's FAT. I suspect that blkid actually looks at the filesystem rather than the partition table, because it can distinguish between ext3, ext4, jfs etc and they all have the same partition table type of Linux (83).

---

