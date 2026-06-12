---
title: "KERNEL PANIC Mount: you must specify filesystem type"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by abicash on 2009-08-19
Hi 
I am running Intrepid
This is after I changed usplash in /etc/splashy folder (to get a Mac look:confused:)
Somehow the system got corrupt.
Now i cant get through.

I booted from a Live-Cd

Here is fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=ba1b21e2-0285-4526-b08b-dbd8c27b5f32 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ffb57ebf-a695-472c-8690-83799784b08a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Here is 
```
sudo fdisk -l /dev/sdb6
```

```

Disk /dev/sdb6: 10.4 GB, 10487199744 bytes
255 heads, 63 sectors/track, 1274 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb6 doesn't contain a valid partition table

```

I also tried 

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb6
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdb6 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb6 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb6: 208475/1269056 files (0.6% non-contiguous), 2357644/2560351 blocks

```

One thing i noticed is that in Places folder when i right click on the Linux partition i see it as ext3 whereas everywhere else its ext2


Anything can be done to save the installation?

---

### Post by Penguin Guy on 2009-08-19
```
Disk /dev/sdb6: 10.4 GB, 10487199744 bytes
255 heads, 63 sectors/track, 1274 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: [COLOR="Red"]0x00000000[/COLOR]

[COLOR="Red"]Disk /dev/sdb6 doesn't contain a valid partition table[/COLOR]
```
That's bad, firstly it looks like you'll need to run some sort of fsck command (luckily I haven't had much experience with this) and secondly since every device is assigned a random identifier (anyone correct me if I'm wrong), the chance that your disk identifier is supposed to be 0x00000000 is 1/4294967295 (not very high).

---

### Post by abicash on 2009-08-19
Hello Penguin Guy

Thanks for replying

I don't think that should be THE problem..
I have another computer running the same specs and i just checked on it and it too has the same disk identifier

```
Disk identifier: 0x00000000

Disk /dev/sda13 doesn't contain a valid partition table
```

and it is working good!!!

I replaced the items in the /etc/splashy folder with my custom themes and configure.xml files and that triggered all this!!

I have replaced the original contents of these but no joy!

Thanks and regards

---

### Post by sdennie on 2009-08-19
fdisk is meant to run on disks and not partitions so, that explains the strange error message.  The problem you are likely seeing is that you've not built the initramfs properly after installing a new bootsplash.  If the initramfs image doesn't have the kernel modules for the filesystems or disk controllers, those are the type of boot errors you will get.  You can probably fix it by booting into a different kernel (or a chroot from a livecd) and running:

```

sudo update-initramfs -c -k 2.6.xx-yy

```

Where xx-yy is the version of the kernel you've broken.  However, this may not work now that you've ignored the "WARNING!!!  Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage." message.  Always unmount a partition before trying to fsck it.

---

### Post by fela on 2009-08-19
Yes, I think it's definitely a dud initramfs. Either that or something is seriously messed up with your harddisk. But I think it's more likely a dud initramfs.

---

