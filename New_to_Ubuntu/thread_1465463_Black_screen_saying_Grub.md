---
title: "Black screen saying Grub"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by matt5692 on 2010-04-29
Hi I am completely new to linux but need it for a masters degree i am starting in september.

I have attempted to dual boot my home made pc with windows xp on one partition and ubuntu on the second.

I have completed the ubuntu install but when I reboot I get a black screen that simply says 'GRUB' and I cannot do anything.

Help please!!!!

---

### Post by computerguts on 2010-04-29
sounds like a partition error between windows a linux, are you able to access the grub book menu? 

It is the menu that gives you the choice to chose between operating systems. If you are go to the first ubuntu operating system selection and press e to edit and select intgid, the press enter to boot.

---

### Post by Julek on 2010-06-04
I have exacly the same problem, dual boot win xp and ubuntu 10.04 when i reboot i also have black screen with "GRUB". Now i boot ubuntu from supergrub disk, but it is not a solution. Please help

---

### Post by anewguy on 2010-06-04
Something to try, but no guarantees:

Boot up from the LiveCD you installed from (the try Ubuntu without changing your computer option)

open a terminal window (applications/accessories/terminal)

type:

sudo update-grub <press enter>

When that finishes, try rebooting and see if you get to the Grub menu.  If so, try selecting Ubuntu and see what happens.

Dave ;)

---

### Post by Julek on 2010-06-06
So i did what u want and thats what happed

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

so i mount my ubuntu partition in this way:

```
sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sdb2 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
```

and again update-grub:

```
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done

```

but after restart the problem still appears.
Any ideas?

---

### Post by anewguy on 2010-06-06
Boot from the LiveCD again.  Then start up the partition manager and check for partitions on your drive as it looks like it can't read the table at boot.  If you can't get at the partition manager, do the following:

- open a terminal window

- type:

sudo parted <press enter>

- when the prompt comes up, type:

print <press enter>  This will list known partitions

quit <press enter>  Exit parted


Please post the output of either or both of these back here.

Dave ;)

---

### Post by Julek on 2010-06-06
Here:

```
ubuntu@ubuntu:~$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA ST3120213A (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  16.2GB  16.2GB  primary  ntfs         boot
 2      16.2GB  19.4GB  3249MB  primary  ntfs
 3      19.4GB  120GB   101GB   primary  ntfs


```

```

(parted) print                                                           
Model: ATA SAMSUNG SP0411N (scsi)
Disk /dev/sdb: 40.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  32.4GB  32.4GB  primary  ntfs
 2      32.4GB  38.9GB  6440MB  primary  ext4
 3      38.9GB  40.1GB  1168MB  primary  linux-swap(v1)

```

---

### Post by aeiah on 2010-06-06
if you can boot into ubuntu using the super grub disk, then you can do the update-grub command on your actual operating system instead of within a livecd environment. often simpler than mounting and chrooting etc.

---

### Post by Julek on 2010-06-06
i update grub straight from ubuntu many times, before posting here but efect is the same black screen with word GRUB

---

### Post by eriktheblu on 2010-06-06
Julek, check the boot priority of your BIOS. Make the 40GB drive boot first (before the 120 GB).

---

### Post by Julek on 2010-06-06
It's working now! thanks a lot :D

So i change the boot sequence in bios and i install grub on second hard disk, and after reboot i can see grub menu and both system starts normally. Thanks again.

---

