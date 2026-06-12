---
title: "Mounting drives"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-12-28
Hey guys,

I'm having some trouble mounting all of my hard disks after my upgrade to 9.10.

Here is my Fdisk:
```
roman@roman-htpc:~$ sudo fdisk -l
[sudo] password for roman: 
Sorry, try again.
[sudo] password for roman: 

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27929e80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460      182401  1453416615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584      182401  1452420553+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121600   976751968+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f14f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      121601   976752000   83  Linux
roman@roman-htpc:~$ 

```

here is the output when I try to mount:
```
roman@roman-htpc:~$ sudo mount /dev/sdb1 /mnt/sdb
mount: special device /dev/sdb1 does not exist
roman@roman-htpc:~$ sudo mount /dev/sdb /mnt/sdb
mount: unknown filesystem type 'nvidia_raid_member'
roman@roman-htpc:~$ sudo mount /dev/sdc /mnt/sdc
mount: unknown filesystem type 'nvidia_raid_member'

```

here is my Fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=01e51a52-dd53-4ca6-a858-770f74233a45 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=2c63dab7-a06d-4caa-8951-5eff6c71d49a /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=05eb887e-8347-4109-8f2e-a85a2cc4851c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda6 /mnt/sda xfs defaults 0 3
/dev/sdb1 /mnt/sdb ext4 defaults 0 3
/dev/sdc1 /mnt/sdc ext4 defaults 0 3


none /proc/bus/usb usbfs auto,devmode=0666 0 0




```

basically I would like to mount /dev/sdb to /mnt/sdb and /dev/sdc to /mnt/sdc

anyone have any idea what i'm doing wrong? any help would be very appreciated. 

Thanks everyone.

---

### Post by mapes12 on 2009-12-29
To access/mount my other partitons/drives I create a directory in the filesystem then mount to that directory like this:

```
sudo mkdir /HDD2
```
# creates a folder in the filesystem folder called HDD2

```
sudo mount /dev/sdb1 /HDD2
```
# mounts the 2nd HDD Linux partition to the file system via the above directory

The above is for mounting the first partition on my second HDD.

---

### Post by Archer Troy on 2009-12-29
I do that, same thing. here is what it says:
```
roman@roman-htpc:~$ sudo mkdir /mnt/sdb
[sudo] password for roman: 
roman@roman-htpc:~$ sudo mkdir /mnt/sdc
roman@roman-htpc:~$ sudo mount /dev/sdc1 /sdc
mount: mount point /sdc does not exist
roman@roman-htpc:~$ sudo mount /dev/sdc1 /mnt/sdc
mount: special device /dev/sdc1 does not exist
roman@roman-htpc:~$ 

```

---

### Post by Muttley99 on 2009-12-29
> **Archer Troy said:**
> I do that, same thing. here is what it says:
```
roman@roman-htpc:~$ sudo mkdir /mnt/sdb
[sudo] password for roman: 
roman@roman-htpc:~$ sudo mkdir /mnt/sdc
roman@roman-htpc:~$ sudo mount /dev/sdc1 /sdc
mount: mount point /sdc does not exist
roman@roman-htpc:~$ sudo mount /dev/sdc1 /mnt/sdc
mount: special device /dev/sdc1 does not exist
roman@roman-htpc:~$ 

```

You've made two mount points; /mnt/sdc & /mnt/sdb 
But you need to be explicit in your mount command;
you tried to mount /dev/sdc1 at mount point /sdc - this doesn't exist!
try;

[HTML]sudo mount /dev/sdc1 /mnt/sdc[/HTML]

---

### Post by Archer Troy on 2009-12-29
Thanks for the reply, but I did do that already. i Just made both of the mount points first:
```

roman@roman-htpc:~$ sudo mkdir /mnt/sdb
[sudo] password for roman: 
roman@roman-htpc:~$ sudo mkdir /mnt/sdc
roman@roman-htpc:~$ sudo mount /dev/sdc1 /sdc
mount: mount point /sdc does not exist
**roman@roman-htpc:~$ sudo mount /dev/sdc1 /mnt/sdc**
mount: special device /dev/sdc1 does not exist
roman@roman-htpc:~$
```

---

### Post by Muttley99 on 2009-12-29
Sorry I missed that!

You could try;

[HTML]sudo blkid[/HTML]

find the UUID for the device you want to mount i.e. UUID="23488-3284.....
then;

[HTML]sudo mount UUID=(the code without abbreviation marks) /mnt/sdc[/HTML]

---

### Post by Archer Troy on 2009-12-29
well that brings up a whole new set of questions...

This is what i get:

```
roman@roman-htpc:~$ sudo blkid
[sudo] password for roman: 
/dev/sda1: UUID="01e51a52-dd53-4ca6-a858-770f74233a45" TYPE="ext3" 
/dev/sda5: UUID="05eb887e-8347-4109-8f2e-a85a2cc4851c" TYPE="swap" 
/dev/sda6: UUID="2c63dab7-a06d-4caa-8951-5eff6c71d49a" TYPE="xfs" 
/dev/sdb: TYPE="nvidia_raid_member" 
/dev/sdc: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_bbcbfebb1: UUID="6a537afc-328a-429b-9c55-919c9d9b1425" TYPE="ext4" 
roman@roman-htpc:~$ 

```

i have absolutely no idea what nvidia raid member is, nor the mapper. any idea what is going on.

---

### Post by Muttley99 on 2009-12-29
Looks like you have a raid setup?

Well I don't use raid myself and haven't used it for some years. I'm guessing; you have a software raid setup using UUID="6a537afc-328a-429b-9c55-919c9d9b1425"

Have you tried mounting the above UUID? 

I wish I could help you further but I have little knowledge of Raid!

---

### Post by falconindy on 2009-12-29
/dev/mapper/nvidia_bbcbfebb1 (not /dev/sdc1) is the device you want to mount. no need to fool around with UUIDs.

---

### Post by Archer Troy on 2009-12-29
Alright well thats progress..

i mounted dev/mapper/nvidia_bbcbfebb1
but i only get 1 of my two hard disks mounted.

so basically:

sda - mounted to sda
dev/mapper/nvidia_bbcbfebb1 (which is actually my sdc) - mounted to sdc

im still missing my last hard drive (sdb)

anyone now whats going on?

also, i never setup a RAID. don't know how that happened...

---

### Post by Muttley99 on 2009-12-29
Check your BIOS to see how it recognises your drives.

---

### Post by Archer Troy on 2009-12-29
I believe that everything is recognized properly
Sata 1 - 1.5 tb
Sata 3 - 1 tb
Sata 4 - 1 tb

is there any way to remove the raid device?

---

### Post by Muttley99 on 2009-12-29
Have a look at 

[HTML]/boot/grub/device.map
[/HTML]

There's a command for repopulating this (i've forgotten!)

Check with the experts before doing this!

---

### Post by Archer Troy on 2009-12-29
thanks for all of your help so far.

here is device.map:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

---

### Post by Muttley99 on 2009-12-30
If your booting from sda! and all you have is data on these drives;
You could try commenting these drives out in your fstab,

[HTML]#/dev/sdb1 /mnt/sdb ext4 defaults 0 3
#/dev/sdc1 /mnt/sdc ext4 defaults 0 3[/HTML]

then try mounting them manually!

---

