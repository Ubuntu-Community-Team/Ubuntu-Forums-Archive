---
title: "2 Hard Drives"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Foxfire on 2008-12-27
I have to hard Drives in my computer I want one just for storage like Pictures Videos ect   how do i go about doing this?

---

### Post by Elfy on 2008-12-27
You can add it to fstab -http://ubuntuforums.org/showthread.php?t=283131

Basically you need to create a folder in /media or /mnt for the drive to mount into and then add a line in your fstab file to mount it on boot.

If you need some help then post the results of these here

```
sudo fdisk -l
cat /etc/fstab
blkid
```

---

### Post by tubasoldier on 2008-12-27
you don't have to put it under /media or /mnt
It can go anywhere as long as you have permissions to it.
You can mount it in your /home/user/ directory or wherever you like.
The key to using it is simply having the permissions to read and write to it.

---

### Post by Foxfire on 2008-12-27
noname-desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30c930c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8155    65504013+   7  HPFS/NTFS
/dev/sda2            8156       24263   129387510    5  Extended
/dev/sda3           24264       24321      465885   82  Linux swap / Solaris
/dev/sda5            8156       24263   129387478+  83  Linux

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3649    29310561   83  Linux
noname-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=dd596dd6-612a-4511-bd5c-8560a9615fc8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=7f43608d-25c6-4918-9b47-092c364d5fc8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
noname-desktop:~$ blkid

---

### Post by Elfy on 2008-12-27
If blkid failed can you run it with sudo please

---

### Post by Foxfire on 2008-12-27
/dev/sda1: UUID="5CBCE589BCE55DD0" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="7f43608d-25c6-4918-9b47-092c364d5fc8" 
/dev/sda5: UUID="dd596dd6-612a-4511-bd5c-8560a9615fc8" TYPE="ext3" 
/dev/sdb1: UUID="17efe9bc-3f0b-434a-aabd-52a8a38d5b46" TYPE="ext3"

---

### Post by Elfy on 2008-12-28
You can, as tubasoldier said, mount them anywhere you like, but I shall work with /mnt - if you want then to show on the desktop change ALL /mnt to /media.

Change disk1 and disk2 to anything you wish - but remember to amend the fstab lines as well.

```
sudo mkdir /mnt/disk1 /mnt/disk2
sudo cp /etc/fstab /etc/fstab.2812
```

```
gksudo gedit /etc/fstab
```

Add these lines for the ext3 drive

```
#/dev/sdb1
UUID=17efe9bc-3f0b-434a-aabd-52a8a38d5b46 /mnt/disk1 ext3 user 0 2
```

Add these lines for the NTFS drive

```
#/dev/sda1
UUID=5CBCE589BCE55DD0 /mnt/disk2 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

Save and close gedit, then run

```
sudo mount -a
```

Which will mount the new drives for you to use. If you don't appear to have permissions to write to the ext3 disk then do this, change user to your username

```
sudo chown user.user /media/disk1
sudo chmod 770 /media/disk1
sudo chown user.user /media/disk2
sudo chmod 770 /media/disk2
```

---

### Post by Elfy on 2008-12-28
<snip>

---

