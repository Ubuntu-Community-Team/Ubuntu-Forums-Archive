---
title: "I can't delete from my MP3 player"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by oopsie on 2009-02-10
I just stuck my MP3 player into my PC, intending to copy some files to it. But there wasn't enough room. I tried to delete some of the files on it, but it said it was read only.

I've used this MP3 player many times in windows to copy, move, delete files and no problem. Anyone know why I can't delete from it in Ubuntu?

---

### Post by x33a on 2009-02-10
try deleting the files from the associated software (if any).

---

### Post by oopsie on 2009-02-10
There is no associated software. I just use it as portable storage to move files between windows PCs.

I usually just plug it into my windows PCs, and they see it as a new drive. Then I copy files to or from it, or delete stuff, and carry on.

But, I can't seem to delete from it in Ubuntu.

---

### Post by howefield on 2009-02-10
Try using root privileges, open a terminal and type

```
gksu nautilus
```

Navigate to your mp3 player and see if you can delete now.

---

### Post by oopsie on 2009-02-10
"Error removing file: Read-only file system"

=\

No luck

---

### Post by x33a on 2009-02-10
post the output of:

1. ls -l /media
2. sudo fdisk -l

---

### Post by tarps87 on 2009-02-10
Can you create files on it? Did you unmount it from windows (safely remove)?

---

### Post by oopsie on 2009-02-10
"ls -l /media" gave

total 5
lrwxrwxrwx 1 root root    6 2009-02-08 09:10 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-02-08 09:10 cdrom0
drwx------ 2 me   root 1024 1970-01-01 01:00 disk

"sudo fdisk -l " gave

Disk /dev/sda: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb35350d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3322    26683933+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42bc91a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9591    77039676   83  Linux
/dev/sdb2            9592        9964     2996122+   5  Extended
/dev/sdb5            9592        9964     2996091   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4397e1fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32835   263747106    7  HPFS/NTFS
/dev/sdc2           32836       38913    48821535    5  Extended
/dev/sdc5           32836       38913    48821503+  83  Linux

Disk /dev/sdd: 125 MB, 125682176 bytes
4 heads, 60 sectors/track, 1022 cylinders
Units = cylinders of 240 * 512 = 122880 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?     7790715     8493588    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(7790714, 0, 6)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(8493587, 0, 7)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?     7089665    14880838   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(7089664, 2, 2)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(14880837, 1, 6)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?          11          11           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(10, 2, 54)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(10, 2, 53)
Partition 3 does not end on cylinder boundary.
/dev/sdd4        12023672    12023890       26207+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(12023671, 1, 53)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(12023889, 3, 27)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by oopsie on 2009-02-10
> **tarps87 said:**
> Can you create files on it? Did you unmount it from windows (safely remove)?

Umm, I don't remember. It's been ages since I last used it.

I don't appear to be able to write anything to it.

---

### Post by hansdown on 2009-02-10
Good call tarps87.

If it is not removed safely from a windows machine, problems will happen on other computers. Just hook it back up to the windows box you were using, and "safely" remove it.
Hope this helps oopsie.

---

### Post by oopsie on 2009-02-10
Not really. I don't have windows installed atm =\

I guess this means I should copy everything off it, and reformat it, or something?

---

### Post by x33a on 2009-02-10
looking at ls -l output, only root has all the privileges for /media/disk (assuming this is the pen drive).

1. open a terminal, and type cd /media/disk
2. type ls, decide which files to delete.
3. try sudo rm filename.

---

### Post by tarps87 on 2009-02-10
> **x33a said:**
> looking at ls -l output, only root has all the privileges for /media/disk (assuming this is the pen drive).

1. open a terminal, and type cd /media/disk
2. type ls, decide which files to delete.
3. try sudo rm filename.

Before you try this try and make a backup copy of the data and then try opening a terminal type 
```
cd /media/disk
``` to change the the usb drive and then
```
sudo touch test.txt
```
this should create an empty text file.
(It's easier to remove a new file than recover a deleted one)
Although I suspect that it was not remove correctly so it is still locked by windows. If you can, plug it into any windows pc and safely remove it. If not and if you can copy your data off of it, I would suggest a reformat as currently the drives partition table is a mess. If you decide to reformat you may be able to use gparted if not I can guide you through the command line process

> **hansdown said:**
> Good call tarps87.
Thanks

---

