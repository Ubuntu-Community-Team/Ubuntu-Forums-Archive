---
title: "moved fstab from media directory"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by wqd3tried on 2009-02-12
Hello all, this may not even be a problem.
I have recently tried Ubuntu and Xubuntu, and as my PC is old (circa 2002) installed Xubuntu. 
This was fine until a hard drive problem. I had to use older smaller drives. I was following a guide to getting a second internal hard drive to auto mount at boot up, and put a renamed copy of fstab on the desktop. Part way through I decided to stop and moved my modified fstab file out of the "media" directory to the desktop but now cannot move the original back!

All the above moves were using File Manager. 
I also tried using the terminal with "cp" and "mv" commands but got only "file not found" errors.
I know there is another fstab file in etc directory, so does my cock-up matter? I have not re booted since.

Also, how do you get out of the "manual" in the terminal?

---

### Post by sisco311 on 2009-02-12
please post:
```
cat /etc/fstab
```
```
ls -al /media
```
```
ls -al ~/Desktop
```

```
sudo fdisk -l
```and
```
sudo blkid
```

> Also, how do you get out of the "manual" in the terminal?press "q" ;)

---

### Post by scragar on 2009-02-12
The one in /etc is the only one that matters as far as I know, anything else will just be an extra copy.

To exit a man page use **q**, same goes for anything piped to less.

---

### Post by wqd3tried on 2009-02-12
Wow, speedy service! 
Still have'nt re-booted.

> **sisco311 said:**
> 

press "q" ;)
Doh!

Outputs:
me-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8910e5ab-f06d-4d2d-9bbc-1197942bb46f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a90c8324-56d3-491e-9dd0-c089fea0e646 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

me-desktop:~$ ls -al /media
total 24
drwxr-xr-x  6 root root 4096 2009-02-12 10:06 .
drwxr-xr-x 21 root root 4096 2009-02-08 23:24 ..
lrwxrwxrwx  1 root root    6 2009-02-08 16:48 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-02-08 16:48 cdrom0
drwxr-xr-x  2 root root 4096 2009-02-08 16:48 cdrom1
drwxr-xr-x  2 root root 4096 2009-02-12 10:06 dee
lrwxrwxrwx  1 root root    7 2009-02-08 16:48 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2009-02-08 16:48 floppy0
-rw-r--r--  1 root root    0 2009-02-12 09:26 .hal-mtab

me-desktop:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5ef8825

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         200     1606468+   c  W95 FAT32 (LBA)
/dev/sda2             201         321      971932+  83  Linux
/dev/sda3            1200        1240      329332+  82  Linux swap / Solaris
/dev/sda4             322        1199     7052535    5  Extended
/dev/sda5             322        1155     6699073+  83  Linux
/dev/sda6            1156        1199      353398+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf038fbc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         784     6297448+   b  W95 FAT32

me-desktop:~$ sudo blkid
/dev/sda1: UUID="304E-16F7" TYPE="vfat" LABEL="^OE" 
/dev/sda2: UUID="7cbb341a-e31c-44c4-b6de-9670ca75dffd" TYPE="ext2" 
/dev/sda3: TYPE="swap" UUID="d85c5bc8-34e7-4e0a-bfbb-0be83a922829" 
/dev/sda5: UUID="8910e5ab-f06d-4d2d-9bbc-1197942bb46f" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="a90c8324-56d3-491e-9dd0-c089fea0e646" 
/dev/sdb1: UUID="3566-16F0" TYPE="vfat"

I'm using a dual boot setup with windows 98 in the tiny partition and some of it's applications installed on the second drive.

Thanks.

---

### Post by sisco311 on 2009-02-12
Sorry for the delay. (I'm in the middle of home renovation, bah :) )

sda1 is probably the windows partition
sda5 is the current ubuntu / (root) partition
sda6 is the swap partition

sda2 is an ext2 partition,  probably an old linux installation.
sda3 is a swap partition

sdb1 is probably the data partition.

First you have to create a mount point for the partitions.
(an empty directory, usually in /media)

```
sudo mkdir /media/windows
sudo mkdir /media/data
```

Then an fstab entry:

```
UUID=<uuid of the partition> /mount/point type options 0 0
```

To backup then edit the fstab:
```
sudo cp /etc/fstab /etc/fstab-old
gksu mousepad /etc/fstab
```

In your case add this lines:
```
UUID=304E-16F7 /media/windows vfat defaults,dmask=002,fmask=113,gid=46 0 0
UUID=3566-16F0 /media/data vfat defaults,dmask=002,fmask=113,gid=46 0 0
```

Mount the partitions:
```
sudo mount -a
```

---

### Post by wqd3tried on 2009-02-12
A slight delay for free help is OK with me.

An update on the situation:
Well, it still works after shutdown and restart, so scragar must be right about the version I moved being a copy. This also implies I must edit the fstab file in /etc but I am going to leave it for today. I want to work out what I did wrong with the cp and mv commands in the terminal. It's a bit awkward to be able to move files in one direction only.

I am pretty sure sdb1 is the second hard drive, currently with windows files and fat32. 
I am curious about the sda2 ext2 partition. I had previously installed Ubuntu 6, but when I decided to swap to Xubuntu, re-formatted the whole drive from DOS - or so I thought - before re-installing windows, then Xubuntu from a Live CD. Surely this would have removed existing partitions? Certainly the DOS fdisk reported one 10Gb partition after formatting. Not an important issue for me today, but I would like to know. 

Thanks again for the help.

---

### Post by scragar on 2009-02-12
> **wqd3tried said:**
> A slight delay for free help is OK with me.

An update on the situation:
Well, it still works after shutdown and restart, so scragar must be right about the version I moved being a copy. This also implies I must edit the fstab file in /etc but I am going to leave it for today. I want to work out what I did wrong with the cp and mv commands in the terminal. It's a bit awkward to be able to move files in one direction only.

I am pretty sure sdb1 is the second hard drive, currently with windows files and fat32. 
I am curious about the sda2 ext2 partition. I had previously installed Ubuntu 6, but when I decided to swap to Xubuntu, re-formatted the whole drive from DOS - or so I thought - before re-installing windows, then Xubuntu from a Live CD. Surely this would have removed existing partitions? Certainly the DOS fdisk reported one 10Gb partition after formatting. Not an important issue for me today, but I would like to know. 

Thanks again for the help.

The abreviations are quite easy to work out, **sd** is a hard drive, **a** is first hard drive, **b** is the second HD...
And the number is simply a partition number, so 1 is first partition, 2 is second partition... But your partition numbers might jump about a bit, most ubuntu settups go 1, 4, 5 - since 3 is the extended partition, I've no idea where 2 has gone though...

---

### Post by wqd3tried on 2009-02-13
Thanks to scragar for the tips and sisco311 for the walk through of fstab modification. 
It seems an odd thing to say, but there is almost too much information out there! Apart from this forum and the community documentation, a number of other sites have guides to this sort of operation and I was getting bogged down. 
It then occured to me to check for available software, and I have downloaded and used PySDM, so now have the use of the second hard drive which I wanted.
I am still left with the mystery of my failed terminal usage, but at least I don't have an un-useable machine and no internet access! A more leisurely return to command line use is now possible - I was pretty confident with DOS in ancient times, so it isn't too intimidating.

---

