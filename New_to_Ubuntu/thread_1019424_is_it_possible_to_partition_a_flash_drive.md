---
title: "is it possible to partition a flash drive"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-23
I would like to create an Ubuntu live flash drive.
However I was wondering if (sense my flash drive is larger than what's needed) I could use the remaining space still as a regular flash drive.

Would I need to set partitions? If so, How?

Thanks for any help

---

### Post by 73ckn797 on 2008-12-23
> **nakama85 said:**
> I would like to create an Ubuntu live flash drive.
However I was wondering if (sense my flash drive is larger than what's needed) I could use the remaining space still as a regular flash drive.

Would I need to set partitions? If so, How?

Thanks for any help

I don't see why you couldn't. If you have "gparted" installed you can just go there and resize the existing partition or completely wipe and create a partition to what ever size you want. If you do not have "gparted" you can boot from the Live CD and use it from there.

That would be: System/Administration/Partition Editor

---

### Post by Hangwire on 2008-12-23
# Insert a 1GB or larger USB flash drive
# Open a terminal window and type sudo su
# Type fdisk -l to list available drives/partitions. Note which device is your flash drive (example: /dev/sda) Throughout this tutorial, replace x with your flash drive letter. For example, if your flash drive is sdb, replace x with b.
# Type umount /dev/sdx1
# Type fdisk /dev/sdx

    * type p to show the existing partition and d to delete it
    * type p again to show any remaining partitions (if partitions exist, repeat the previous step)
    * type n to make a new partition
    * type p for primary partition
    * type 1 to make this the first partition
    * hit enter to use the default 1st cylinder
    * type +700M to set the partition size
    * type a to make this partition active
    * type 1 to select partition 1
    * type t to change the partition filesystem
    * type 6 to select the fat16 file system
    * type n to make another new partition
    * type p for primary partition
    * type 2 to make this the second partition
    * hit enter to use the default cylinder
    * hit enter again to use the default last cylinder
    * type w to write the new partition table

# Type umount /dev/sdx1 to ensure the 1st partition is unmounted
# Type mkfs.vfat -F 16 -n usb /dev/sdx1 to format the first partition
# Type umount /dev/sdx2 to ensure the 2nd partition is unmounted
# Type mkfs.ext2 -b 4096 -L casper-rw /dev/sdx2 to format the second partition


Taken from [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Also, I think the above mentioned way is better :)

---

### Post by 73ckn797 on 2008-12-23
My suggested method is graphical (ie...user friendly) and Hangwire's is command line (CLI) (advanced user friendly). Use whichever you are comfortable with. Both will accomplish the same thing.

No offense to Hangwire.

---

### Post by ajgreeny on 2008-12-23
You certainly can do it; I have done so in the past.  It is no different to any other drive.  Gparted is the easiest way for most.

---

### Post by Hangwire on 2008-12-23
> **73ckn797 said:**
> My suggested method is graphical (ie...user friendly) and Hangwire's is command line (CLI) (advanced user friendly). Use whichever you are comfortable with. Both will accomplish the same thing.

No offense to Hangwire.

None taken.
Like I said, your method is better and easier.

---

### Post by nakama85 on 2008-12-23
great thanks everyone. I will come back and mark this thread as solved once I have set it up and confirmed it works as expected (or hoped)

---

### Post by Captain_tux on 2008-12-23
The principal feature of the January 2009 issue of Linux Format is about installing Linux on a thumb drive.

[http://www.linuxformat.co.uk/modules.php?op=modload&name=NewArchives](http://www.linuxformat.co.uk/modules.php?op=modload&name=NewArchives)

---

