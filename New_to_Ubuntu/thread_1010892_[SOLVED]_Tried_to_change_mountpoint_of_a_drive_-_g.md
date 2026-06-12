---
title: "[SOLVED] Tried to change mountpoint of a drive - got in trouble."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by karlsomewhat14 on 2008-12-14
Today, out of curiosity, I tried to change the mountpoint of my Windows drive. I did this through the properties dialog box that you can access once the drive is mounted and is showing an icon on the desktop.
Problem is, I seem to have hit enter once I was done typing the new mountpoint, and thought it did nothing (but it did do something - inserted a new line character as far as I can tell)

Now, when I go to the places menu and try to mount it, I get a lovely error message about the newline character in the mountpoint.
Searched the forums a bit, and managed to manually mount it. Problem is, the icon doesn't appear on the desktop for some reason, and the drive has disappeared from my places menu as well.

Any chance I could be pointed to the proper config file to change the mountpoint back to normal?

---

### Post by Michael.Godawski on 2008-12-14
ok,

let's have a look on your drives and partitions:

```
sudo fdisk -l
cat /etc/fstab
```

Please post output here.

---

### Post by karlsomewhat14 on 2008-12-14
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3623d90a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5875    47190906    7  HPFS/NTFS
/dev/sda2           17761       19027    10177177+  83  Linux
/dev/sda3            5876       17760    95466262+  83  Linux
/dev/sda4           19028       19457     3453975   82  Linux swap / Solaris

Partition table entries are not in disk order
```

The Windows drive isn't, and hasn't been in my fstab though - it's not something I use often enough to bother automatically mounting it.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=45f93654-7204-4b62-ad8a-4bde98b099bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=93440d5a-f9e5-40d3-930d-34c7dfec4723 /home           ext3    relatime        0       2
# /dev/sda4
UUID=4dfd3582-94da-4ec9-9540-16ee433264a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by drs305 on 2008-12-14
An easy way to fix it would be to add a line in fstab for your windows partition. I prefer UUIDs (which you can get for sda1 by running the 'sudo blkid' command) but here it is for /dev/sda1:

```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Add this line to the bottom of your fstab file. This assumes the mountpoint /media/windows exists. If it doesn't, create it or change the mountpoint to whatever you wish:
```

/dev/sda1 /media/windows ntfs auto,users,uid=1000,umask=027,utf8 0 0

```
Save the file, then run:
```

sudo mount -a

```
If you do not see any messages after running this command the partition was successfully mounted.

By mounting it to /media you should once again see it on your Desktop. If you don't want it mounted automatically, change *auto* to *noauto*

---

### Post by karlsomewhat14 on 2008-12-14
Not sure how, but I managed to fix it without extensive editing of any files...
Mounting it through command line, and trying to unmount through command line (umount gave an error message about /etc/mtab) somehow got the icon back on my desktop, and from there I was able to revert the mountpoint to normal.
And then simply restarting X let me mount and unmount it regularly again.

Thanks for the advice, drs305, I'm going to go ahead and add it to fstab so that I don't inadvertently break it again.

---

