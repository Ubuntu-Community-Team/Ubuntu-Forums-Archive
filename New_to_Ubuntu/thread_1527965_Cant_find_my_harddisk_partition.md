---
title: "Cant find my harddisk partition"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Punkbyz on 2010-07-10
Hi, i am totally new to ubuntu. When i was Installing Ubuntu I completely destroyed all the previous windows partitions and made some new ones. i allocated 10 GB to root, 10 GB to home , 512 MB as swap memory. I partioned around 60 GB as FAT, but it does not appear in My computer as it would in Windows.

---

### Post by thehipho on 2010-07-10
Look in the upper left menu in PLaces>Removable Media: look for your fat32 there.

AND did you mean to completely lose your Windose partitions?

---

### Post by patchwork on 2010-07-10
Just to be sure the partition was created correctly, open a terminal and enter
```
sudo fdisk -l
```

This will list the partititions and their filesystems.  Your 60GB FAT should be listed in the output.

---

### Post by Punkbyz on 2010-07-10
Yes its listed. But how do i access it?

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe54fe54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          63      498688   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2              63        9730    77649921    5  Extended
/dev/sda5              63        1279     9764864   83  Linux
/dev/sda6            1279        2494     9764864   83  Linux
[U][B]/dev/sda7            2494        9730    58118144    b  W95 FAT32
[/B][/U]

---

### Post by patchwork on 2010-07-10
Let's first try to manually mount the partition

First, create the mount point by creating a directory where you'd like to access the partition.  (In my example, I will be accessing the partition from /media/FAT)

```
sudo mkdir /media/FAT
```

Next, mount the partition to the mount point
```
sudo mount -t vfat /dev/sda7 /media/FAT
```

The partition should now be accessible through /media/FAT


To have the drive accessible on startup, it will need to be added to the /etc/fstab file.  More on this after you can manually access your partition.

---

### Post by Punkbyz on 2010-07-10
Ok i Got that. I can Access Fat through /media.
Now the next part?

---

### Post by patchwork on 2010-07-10
Open the /etc/fstab for editing:
```
gksu gedit /etc/fstab
```

Check to see if the partition is listed in file (if it is, it should be automatically mounting at startup)

Assuming it's not in the file, add the line```

/dev/sda7 /media/FAT vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
to the file.

Save the file, and issue```
sudo mount -a
``` to mount all the partitions in your fstab

More information can be found in the [community documentation]("https://help.ubuntu.com/community/Fstab")

---

### Post by Punkbyz on 2010-07-10
theres some thing about sda7: should i delete it and replace it withthe code you gave?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d5f2ad50-1a90-4e64-a03a-53c3fa869a23 /home           ext3    defaults        0       2
[COLOR=Black]***_/dev/sda7       /windows        vfat    utf8,umask=007,gid=46 0       1_***[/COLOR]
# swap was on /dev/sda1 during installation
UUID=f6f25d2c-ed12-4637-bf4e-736a0f8c1b12 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by patchwork on 2010-07-10
Before replacing the entry, make a backup of the current fstab (just in case things don't work out as planned)

```
sudo cp /etc/fstab /etc/fstab.backup
```
Once you have backed up your fstab, you can safely replace the existing line with the suggested line above (originally from the community documentation).

---

### Post by Punkbyz on 2010-07-10
Hey thanks. it worked fine.

---

