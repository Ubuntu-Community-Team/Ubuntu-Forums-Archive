---
title: "Moving installation"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-01-17
I want to move my Linux installation...

Current situation:
HD1 (internal 250 gb):
   Grub in the MBR
   Windows XP
   Windows Vista
   Ubuntu

HD2:
One empty external usb harddrive.

Situation to be:
HD1 (internal):
Vista Loader in the MBR
FreeBSD
Windows XP
Windows Vista

HD2 (external USB):
Ubuntu (Grub on the USB drive)




Is there any way I can move my entire Ubuntu install to the external HD and make it bootable (so that I don't have to reinstall)?

---

### Post by talsemgeest on 2009-01-17
It would be easiest to just copy the entire hard drive (depending on if the external hard drive is big enough). You can copy sda to sdb using this command: ```
dd if=/dev/sda of=/dev/sdb
```

Just make sure you get the disk numbers correct, post the output of {code]sudo fdisk -l[/code] if you are not sure.

---

### Post by northern lights on 2009-01-17
> **WitchCraft said:**
> 
Situation to be:
HD1 (internal):
Vista Loader in the MBR
FreeBSD
Windows XP
Windows Vista

HD2 (external USB):
Ubuntu (Grub on the USB drive)
In the above scenario, only Vista will be bootable. You'd need to have a GRUB in the MBR chainloading Vista Loader on the Vista partition and another GRUB on the external HDD.

---

### Post by WitchCraft on 2009-01-17
> **northern lights said:**
> In the above scenario, only Vista will be bootable. You'd need to have a GRUB in the MBR chainloading Vista Loader on the Vista partition and another GRUB on the external HDD.

Initially yes, then you boot into Vista, and add the other operating systems to the bootloader, then restart.
Afterwards, everything will be bootable. 
Vista loader works just fine.

---

### Post by WitchCraft on 2009-01-17
> **talsemgeest said:**
> It would be easiest to just copy the entire hard drive (depending on if the external hard drive is big enough). You can copy sda to sdb using this command: ```
dd if=/dev/sda of=/dev/sdb
```

Just make sure you get the disk numbers correct, post the output of {code]sudo fdisk -l[/code] if you are not sure.

Unfortunately, destination < source.

---

### Post by boof1988 on 2009-01-17
> **WitchCraft said:**
> Unfortunately, destination < source.

One option, if there is a lot of "free space" in the partitions, is to use a partition editor to shrink the partitions before copying.

This can take a lot of time.  Backup important data first.

This may work if there's enough free space.

---

### Post by talsemgeest on 2009-01-17
> **WitchCraft said:**
> Unfortunately, destination < source.
Ok, thats just fine. It just means that you have to run two commands. Can you please run ```
sudo fdisk -l
``` first, so I can put the right device numbers into the code?

Anyway, here are the two types of commands you would have to run. Also, you would have to create a new partition on the external hdd first for this to work. ```
dd if=/dev/sda of=/dev/sdb bs=512 count=1
dd if=/dev/sda1 of /dev/sdb1
```

The first command will copy the bootsector onto the new drive (from sda to sdb). The second command will copy all the data from sda1 to sdb1.

---

### Post by WitchCraft on 2009-01-17
```

all:~# fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e07da

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/hda2            7013       14721    61921280    7  HPFS/NTFS
/dev/hda3           14722       30070   123290842+  83  Linux
/dev/hda4           30071       30401     2658757+   5  Extended
/dev/hda5           30071       30401     2658726   82  Linux swap / Solaris
all:~# 

```

```

hda1 XP:    53.7 GB total, 26.7 GB used, 27.0 GB free
hda2 Vista  59.1 GB total, 33.5 GB used, 25.6 GB free
hda3 Linux 115.7 GB total, 37.9 GB used, 77.8 GB free
hda4/5 bs/swap

```

---

### Post by logos34 on 2009-01-17
> **WitchCraft said:**
> 
```

hda1 XP:    53.7 GB total, 26.7 GB used, 27.0 GB free
hda2 Vista  59.1 GB total, 33.5 GB used, 25.6 GB free
hda3 Linux 115.7 GB total, 37.9 GB used, 77.8 GB free
hda4/5 bs/swap

```

like boof1988 said, you need to shrink down those partitions so that they'll fit on the new drive (how big is it anyway?).  Use Vista's disk utilities for vista and maybe xp, then if necessary shrink ubuntu / using Gparted on the ubuntu live cd (SYstem>admin>partition editor).

Then use the dd command to copy one partition at a time.

---

### Post by talsemgeest on 2009-01-17
> **WitchCraft said:**
> ```

all:~# fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e07da

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/hda2            7013       14721    61921280    7  HPFS/NTFS
/dev/hda3           14722       30070   123290842+  83  Linux
/dev/hda4           30071       30401     2658757+   5  Extended
/dev/hda5           30071       30401     2658726   82  Linux swap / Solaris
all:~# 

```

```

hda1 XP:    53.7 GB total, 26.7 GB used, 27.0 GB free
hda2 Vista  59.1 GB total, 33.5 GB used, 25.6 GB free
hda3 Linux 115.7 GB total, 37.9 GB used, 77.8 GB free
hda4/5 bs/swap

```
Ok, you should have run it with the external drive plugged in. I am just going to assume that the external hard drive is hdb, and the ubuntu partition on the external hdd is hdb1.

```
dd if=/dev/hda of=/dev/hdb bs=512 count=1
dd if=/dev/hda3 of /dev/hdb1
```

Of course, if the external hard drive is different, just change the drive in the command.

---

### Post by talsemgeest on 2009-01-17
> **WitchCraft said:**
> I want to move my Linux installation... Is there any way I can move my entire Ubuntu install to the external HD and make it bootable (so that I don't have to reinstall)?

> **logos34 said:**
> like boof1988 said, you need to shrink down those partitions so that they'll fit on the new drive (how big is it anyway?).  Use Vista's disk utilities for vista and maybe xp, then if necessary shrink ubuntu / using Gparted on the ubuntu live cd (SYstem>admin>partition editor).

Then use the dd command to copy one partition at a time.
I believe the OP only wants to copy the ubuntu partition, not the windows partitions.

---

### Post by logos34 on 2009-01-17
> **talsemgeest said:**
> I believe the OP only wants to copy the ubuntu partition, not the windows partitions.

yep, I see now.  misread it.

nm

---

### Post by WitchCraft on 2009-01-17
> **talsemgeest said:**
> Ok, you should have run it with the external drive plugged in. 

I assumed so, but I just needed to search it first...

```

all:~# fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e07da

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/hda2            7013       14721    61921280    7  HPFS/NTFS
/dev/hda3           14722       30070   123290842+  83  Linux
/dev/hda4           30071       30401     2658757+   5  Extended
/dev/hda5           30071       30401     2658726   82  Linux swap / Solaris

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd296e65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sda2            2933        7296    35053120    7  HPFS/NTFS
all:~# 

```
sda1: 22.5 GB
sda2: 33.4 GB
----------------
total: 55.9 GB  

The USB drive is a 60 GB one.

---

### Post by WitchCraft on 2009-01-17
> **logos34 said:**
> yep, I see now.  misread it.

nm


Yes, I only want to copy the ubuntu partition. 
(but shouldn't that include swap etc. ?)
Then I still need to install Grub in the USB-disc bootsector somewhere...

---

### Post by talsemgeest on 2009-01-17
> **WitchCraft said:**
> I assumed so, but I just needed to search it first...

```

all:~# fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e07da

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/hda2            7013       14721    61921280    7  HPFS/NTFS
/dev/hda3           14722       30070   123290842+  83  Linux
/dev/hda4           30071       30401     2658757+   5  Extended
/dev/hda5           30071       30401     2658726   82  Linux swap / Solaris

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd296e65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sda2            2933        7296    35053120    7  HPFS/NTFS
all:~# 

```
sda1: 22.5 GB
sda2: 33.4 GB
----------------
total: 55.9 GB  

The USB drive is a 60 GB one.
Ok, unfortunately, 120GB of data will not fit onto a 60GB HDD. As long as there is less than 60BGB of actual data on the ubuntu partition, this is what you will have to do:

1. Boot off the ubuntu live cd.
2. Fire up the partition editor.
3. Shrink the ubuntu partition to less than 55GB.
4 Delete the two ntfs partitions on the usb hdd.
5. Create a new ext3 partition on the usb hdd bigger than 55GB but less than 57 GB.
6. Create a swap partition at the end of the usb hdd of no more than 2GB.
7. Apply the changes.
8. Boot back up into ubuntu and run these commands:

```
dd if=/dev/hda of=/dev/sda bs=512 count=1
dd if=/dev/hda3 of /dev/sda1
```

---

### Post by WitchCraft on 2009-01-17
> **talsemgeest said:**
> Ok, unfortunately, 120GB of data will not fit onto a 60GB HDD. As long as there is less than 60BGB of actual data on the ubuntu partition, this is what you will have to do:

1. Boot off the ubuntu live cd.
2. Fire up the partition editor.
3. Shrink the ubuntu partition to less than 55GB.
4 Delete the two ntfs partitions on the usb hdd.
5. Create a new ext3 partition on the usb hdd bigger than 55GB but less than 57 GB.
6. Create a swap partition at the end of the usb hdd of no more than 2GB.
7. Apply the changes.
8. Boot back up into ubuntu and run these commands:

```
dd if=/dev/hda of=/dev/sda bs=512 count=1
dd if=/dev/hda3 of /dev/sda1
```

OK, just one question before i start doing that:

Is it (more or less) safe to assume that I don't have to make a backup of my esteemed data before i start shrinking partitions?

---

### Post by talsemgeest on 2009-01-17
> **WitchCraft said:**
> OK, just one question before i start doing that:

Is it (more or less) safe to assume that I don't have to make a backup of my esteemed data before i start shrinking partitions?
As long as you don't have any powercuts while you are shrinking, or get so impatient that you just restart, yeah, it is safe to assume that your data will be safe. Just know that nothing is 100% foolproof.

---

