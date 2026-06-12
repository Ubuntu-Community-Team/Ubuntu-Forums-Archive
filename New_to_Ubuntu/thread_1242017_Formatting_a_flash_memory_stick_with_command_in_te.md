---
title: "Formatting a flash memory stick with command in terminal."
date: 2009-08-16
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-08-16
My Windows died on me and I'm currently using a live CD to access the data on my drive. My flash drive is full of crap and I just want to wipe it clean.

In a nutshell:

[LIST=1]
[*]Using terminal, List all of my connected devices (so I can use the E:/ bla bla adress to format)
[*]Using terminal FORMAT completely the flash stick, using the previous thing aquired.
[*]Copy the files found on my dead windows partitions to a windows comptabile flash drive.
[/LIST]

please help thx

---

### Post by llamabr on 2009-08-16
1. Using terminal, List all of my connected devices (so I can use the E:/ bla bla adress to format)

```
df -h  
```

will tell you all the mount points.  Connected devices?  maybe 

```
lsusb
```

   2. Using terminal FORMAT completely the flash stick, using the previous thing aquired.

Depends on how you want to format it.  
```
mkfs           mkfs.cramfs    mkfs.ext3      mkfs.ext4dev   mkfs.msdos     mkfs.vfat
mkfs.bfs       mkfs.ext2      mkfs.ext4      mkfs.minix     mkfs.reiserfs  
```

Any of those will do.

   3. Copy the files found on my dead windows partitions to a windows comptabile flash drive.

If it's mounted, just use the cp command

---

### Post by Rocket2DMn on 2009-08-16
From a LiveCD, you shouldn't need to do stuff from the terminal.  GParted is available on the LiveCD from System->Administration->Partition Editor.  Then you can copy your files in nautilus.

However, here are the terminal directions:

To view drives and partitions:
```
sudo fdisk -l
```
To format the device, first unmount it:
```
sudo umount /dev/sdb1
sudo mkfs -t <fstype> /dev/sdb1
```
(where sdb1 is the partition you want to format).

To copy the files, unplug the device and plug it back in so that it automounts (probably to /media/disk).  Now copy:
```
sudo cp -r /path/to/directory/to/content /media/disk
```
That will recursively copy the directory given to the device mounted at /media/disk.

---

### Post by colau on 2009-08-17
> **papuccino1 said:**
> My Windows died on me and I'm currently using a live CD to access the data on my drive. My flash drive is full of crap and I just want to wipe it clean.

In a nutshell:

[LIST=1]
[*]Using terminal, List all of my connected devices (so I can use the E:/ bla bla adress to format)
[*]Using terminal FORMAT completely the flash stick, using the previous thing aquired.
[*]Copy the files found on my dead windows partitions to a windows comptabile flash drive.
[/LIST]

please help thx
If the flash device = /dev/sdb1
To have a fat32 format:
```

mkfs.vfat /dev/sdb1

```

---

