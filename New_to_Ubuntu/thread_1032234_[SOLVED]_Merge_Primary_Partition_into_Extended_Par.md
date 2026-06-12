---
title: "[SOLVED] Merge Primary Partition into Extended Partition"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by opticyclic on 2009-01-06
Is it possible to merge or move an existing partition, that contains an Ubuntu installation, into an extended partition?

I started off with 160 GB Vista installation split into 2 primary partitions
80 GB Windows/Programs etc
80 GB Documents etc

I then resized and installed Ubuntu in a new primary partition and a Swap partition in its own primary partition.
This gave me
40 GB Vista Windows/Programs etc
40 GB Vista Documents etc
73 GB Ubuntu
7 GB Linux-Swap

I now want to install another distro alongside but I have run out of primary partitions.

I deleted the Swap partition and added an extended partition with a couple of logical partitions inside (see attached)
40 GB Vista Windows/Programs etc
40 GB Vista Documents etc
19.5 GB Ubuntu
42.5 GB Extended
     - 25 GB Space for new distro
     - 17.5 GB Space for Ubuntu
7 GB Free space (previously Linux-Swap)

Is it possible to merge the Ubuntu partition into the extended partition and still boot it?
Or maybe copy all the files and replace all references to sda3 with sda6 (not sure which files these would be in)?


I have 4 GB RAM, which makes 3.5 GB addressable, so it is debatable whether I need a Swap partition or not.
However, I'm also considering a /home partition as well and in the future I might add other distros as well so my partition table might end up like:
40 GB Vista Windows/Programs etc
40 GB Vista Documents etc
40 GB Extended 1
     - Logical 1
     - Logical 2
40 GB Extended 2
     - Logical 1
     - Logical 2

which is part of the reason I'm asking about merge/move.
The other reason is that I don't have the all the installation disks with me and for the next few months I only have low bandwidth access so I can't download it again.

---

### Post by Big_astur on 2009-01-06
Can't you just add the SWAP inside the extended partition?

Sorry didn't read the last part :D

---

### Post by caljohnsmith on 2009-01-06
It is possible to convert a primary partition into a logical partition, and it looks like it could work in your case since your Ubuntu partition is physically next to the extended partition. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```
And we can work from there if you want.

---

### Post by opticyclic on 2009-01-06
```
me@my-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b85059c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   167782859    41945715    7  HPFS/NTFS
/dev/sda3       167782860   208748609    20482875   83  Linux
/dev/sda4       208748610   297893294    44572342+   5  Extended
/dev/sda5       208748673   261184769    26218048+  83  Linux
/dev/sda6       261184833   297893294    18354231   83  Linux
me@my-laptop:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 83891367, Id= 7, bootable
/dev/sda2 : start= 83891430, size= 83891430, Id= 7
/dev/sda3 : start=167782860, size= 40965750, Id=83
/dev/sda4 : start=208748610, size= 89144685, Id= 5
/dev/sda5 : start=208748673, size= 52436097, Id=83
/dev/sda6 : start=261184833, size= 36708462, Id=83

```

---

### Post by caljohnsmith on 2009-01-06
OK, how about first shrinking the sda2 NTFS partition by the smallest amount that you can with gparted (you only have to shrink it 63 sectors, but gparted will make you shrink it more than that), and then post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```
And we can work from there.

---

### Post by opticyclic on 2009-01-06
The minimum it would let me shrink it by was 5 MiB.
```
me@my-laptop:~$ sudo fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b85059c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   167766794    41937682+   7  HPFS/NTFS
/dev/sda3       167782860   208748609    20482875   83  Linux
/dev/sda4       208748610   297893294    44572342+   5  Extended
/dev/sda5       208748673   261184769    26218048+  83  Linux
/dev/sda6       261184833   297893294    18354231   83  Linux
me@my-laptop:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 83891367, Id= 7, bootable
/dev/sda2 : start= 83891430, size= 83875365, Id= 7
/dev/sda3 : start=167782860, size= 40965750, Id=83
/dev/sda4 : start=208748610, size= 89144685, Id= 5
/dev/sda5 : start=208748673, size= 52436097, Id=83
/dev/sda6 : start=261184833, size= 36708462, Id=83
```

---

### Post by caljohnsmith on 2009-01-06
OK, please download the attached "partition_table.txt" file to your desktop, and then do:
```
sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt
```
That will produce a lot of output including a few warnings, so don't be alarmed, but please post the output. Next reboot to your Live CD, and post the output of:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda
```
And also do:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
sudo mount /dev/sda5 /mnt
cat /mnt/etc/fstab
cat /mnt/boot/grub/menu.lst
sudo blkid -c /dev/null

```
Please post the output of all the above commands, and we can work from there.

---

### Post by opticyclic on 2009-01-06
I haven't got my LiveCD on me, so I'll have to do the second part in about an hours time and post the rest then.

```
me@my-laptop:~$ sudo sfdisk --force /dev/sda < ~/Desktop/partition_table.txt

Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   5221    5222-  41945683+   7  HPFS/NTFS
/dev/sda2       5222   10442    5221   41937682+   7  HPFS/NTFS
/dev/sda3      10444   12993    2550   20482875   83  Linux
/dev/sda4      12994   18542    5549   44572342+   5  Extended
/dev/sda5      12994+  16257    3264-  26218048+  83  Linux
/dev/sda6      16258+  18542    2285-  18354231   83  Linux
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  83891429   83891367   7  HPFS/NTFS
/dev/sda2      83891430 167766794   83875365   7  HPFS/NTFS
/dev/sda3     167782797 297893294  130110498   5  Extended
/dev/sda4             0         -          0   0  Empty
/dev/sda5     167782860 208748609   40965750  83  Linux
/dev/sda6     208748673 261184769   52436097  83  Linux
/dev/sda7     261184833 297893294   36708462  83  Linux
Warning: partition 3 does not start at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```


It looks like you just manually created a partition table that we then forced onto the system.
How did you work out what it should be?
Can you post a link to this subject?

---

### Post by caljohnsmith on 2009-01-06
It looks like everything went as planned, so once you have a chance to boot your Live CD and reinstall Grub, that might be all you have to do to get the drive booting OK again. Be sure to post the output of all the commands from my previous post though so we can check your fstab and menu.lst too in order to make sure they will work with the new partition arrangement. 
[QUOTE=opticyclic]It looks like you just manually created a partition table that we then forced onto the system.
How did you work out what it should be?
Can you post a link to this subject?[/QUOTE]
That's exactly right, we manually changed your partition table. :) It was possible to make the sda3 Ubuntu partition into a logical partition (now it's sda5), because you resized the sda2 partition to make room for the extended partition to start after the sda2 partition. Since we weren't actually resizing or physically moving any partitions (only the extended partition, which is just a conceptual container for the logical partitions), that's why manually changing the partition table is a valid approach to convert the primary partition into a logical one. And sorry, I don't have any links on what we did, because I learned the basic technique of using sfdisk to manually modify the partition table from forum member meierfra. It mostly takes some knowledge of how primary and logical partitions are set up and structured in order to make it work. Anyway, let me know once you can boot the Live CD and we can go from there.

---

### Post by opticyclic on 2009-01-06
Thanks for explaining.

We now have:
```
 
mint@mint ~ $ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b85059c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   167766794    41937682+   7  HPFS/NTFS
/dev/sda3       167782797   297893294    65055249    5  Extended
/dev/sda5       167782860   208748609    20482875   83  Linux
/dev/sda6       208748673   261184769    26218048+  83  Linux
/dev/sda7       261184833   297893294    18354231   83  Linux

```

I'm a little concerned with this warning here.
```

mint@mint ~ $ sudo sfdisk -d /dev/sda
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 83891367, Id= 7, bootable
/dev/sda2 : start= 83891430, size= 83875365, Id= 7
/dev/sda3 : start=167782797, size=130110498, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=167782860, size= 40965750, Id=83
/dev/sda6 : start=208748673, size= 52436097, Id=83
/dev/sda7 : start=261184833, size= 36708462, Id=83

```
```

mint@mint ~ $ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
mint@mint ~ $ sudo mount /dev/sda5 /mnt
mint@mint ~ $ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=f11fbbee-816b-4882-85bd-733c646ed612 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```

mint@mint ~ $ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		79dec3e4-ad3d-4607-bb63-92b6cbc8ae12
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		79dec3e4-ad3d-4607-bb63-92b6cbc8ae12
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		79dec3e4-ad3d-4607-bb63-92b6cbc8ae12
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		79dec3e4-ad3d-4607-bb63-92b6cbc8ae12
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		79dec3e4-ad3d-4607-bb63-92b6cbc8ae12
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

```

mint@mint ~ $ sudo blkid -c /dev/null
/dev/sda1: UUID="B470A4F870A4C28A" LABEL="VISTA" TYPE="ntfs" 
/dev/sda2: UUID="379668F91241225B" LABEL="VISTA_DOCS" TYPE="ntfs" 
/dev/sda5: UUID="79dec3e4-ad3d-4607-bb63-92b6cbc8ae12" TYPE="ext3" 
/dev/sda6: LABEL="UE" UUID="aa32e442-2a81-47e7-91d6-21136ba9812c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="MINT" UUID="101f424d-2948-4def-a974-521d06f5588f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
mint@mint ~ $
```

---

### Post by caljohnsmith on 2009-01-06
Did the Grub commands you ran say they completed successfully? Also, I made your sda3 extended partition start 63 sectors before the new sda5 linux partition, which is normally where the extended partition starts if the sda5 partition is on a cylinder boundary; it looks like your original sda3 linux partition was slightly off, so that's why sfdisk gives that warning. As far as I know you shouldn't have to be concerned about it though, because all modern OSes uses LBA (Logical Block Addressing) rather than CHS (Cylinders, Heads, Sectors), so it is not necessary for a partition to start/stop exactly on a cylinder boundary. Also, I've found that it depends on which partitioning program you use as to what geometry (CHS) is originally used to create the partition table, and if you use a different partitioning program that uses a different geometry after that, you can get those types of geometry warnings like you did anyway.

Since both your fstab and menu.lst use UUIDs, it looks like you should be all set and able to boot again (assuming the Grub commands ran successfully). I notice you are missing a swap partition or swap file, so you might want to make one at some point. One small thing to correct would be the reference to "sda3" in your fstab, and also your missing swap partition, so how about doing:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/etc/fstab
```
Don't worry if the first mount command returns an error, that means you probably still have sda5 mounted on /mnt. Once you open fstab, change sda3 to sda5, and comment out the swap partition line:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/[COLOR="Red"]sda5[/COLOR]
UUID=79dec3e4-ad3d-4607-bb63-92b6cbc8ae12 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
[COLOR="Red"]#[/COLOR]UUID=f11fbbee-816b-4882-85bd-733c646ed612 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Then reboot, and let me know what happens or if you have any problems. We can work from there.

---

### Post by opticyclic on 2009-01-06
Quality!
Thanks for that.

I just have to resize a bit now using GParted and everything will be perfect :)

---

### Post by caljohnsmith on 2009-01-06
> **opticyclic said:**
> Quality!
Thanks for that.

I just have to resize a bit now using GParted and everything will be perfect :)
So did you confirm you can boot Ubuntu OK? If so, cheers and have fun trying new distros. :)

---

