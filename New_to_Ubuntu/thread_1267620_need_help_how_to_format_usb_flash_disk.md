---
title: "need help: how to format usb flash disk"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by aljoriz on 2009-09-15
I wanted to format a flash disk but I don't know how to do it in ubuntu.

---

### Post by k33bz on 2009-09-15
System > Administration > USB Startup Disk Creator

---

### Post by Excedio on 2009-09-15
GParted is also another way to go.

---

### Post by zeroseven0183 on 2009-09-16
> **k33bz said:**
> System > Administration > USB Startup Disk Creator

I didn't know this can be used to format a flash drive. How does it work?

I use Gparted.

---

### Post by 3rdalbum on 2009-09-16
> **k33bz said:**
> System > Administration > USB Startup Disk Creator

Wow, that's either tremendously bad advice or you were getting confused :-)

Gparted is the answer. It's called "Partition Editor" in the Administration menu.

---

### Post by talsemgeest on 2009-09-16
> **zeroseven0183 said:**
> I didn't know this can be used to format a flash drive. How does it work?

I use Gparted.
Select your flash drive from the drop-down list in the main window. If there are no partitions on the drive (it is a grey bar), right click it and select "Create new partition". If there is already a partition on there (some colour other than grey), right click it and select "Format". Choose the filesystem you want to format it to (FAT32 is the usual for flash drives), and click format.

I don't have gparted installed so some of the names might be wrong, but generally it is right.

---

### Post by Geoff918 on 2009-09-16
You can also do this from the CLI (terminal):

Applications -> Accessories -> Terminal

sudo su                    [This sets you as root for the remaining commands]

fdisk -l                     [This retrieves a list of the available partitions--find your USB, maybe something like sdb oh, and that's an -'ELL' after the hypen]

umount /dev/sd??   [Unmounts the inserted flash, insert the appropriate letter/number combination for the sd??]

fdisk /dev/sd??       [Sets the drive as the partition to be acted on]

p                             [selects the active partition on the drive]
d                             [deletes the partition]
p                             [shows any remaining partitions, if any--if so, repeat the delete process until none show]
n                             [selects to create a new partition]
p                             [chooses primary partition]
1                             ["one" makes this the first partition--you can accept the defaults--it will have the full partition unless you create more than one]
a                            [makes the partition active]
q                            [to quit out of fdisk]

mkfs.???? -b 4096 -L [whatever label you want] /dev/sd??          [makes the file system, if you get an error make sure drive is still unmounted. Otherwise, choose ext2, ext3, ext4, or ntfs, fat16, fat32, whatever...so an ext2 drive would be mkfs.ext2 which should be plenty fine for a flash drive]

Remove your drive, and reinsert it.

AND, you're done! Quick and easy.

---

