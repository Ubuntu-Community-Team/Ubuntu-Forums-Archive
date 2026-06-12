---
title: "Grub 17"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Raouf on 2008-12-06
I have Dual Boot Ubuntu and Vista
I viewed many pages with this error but I can't fixed it

This is the output of sudo fdisk -lu
```
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf20ff20f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280    7  HPFS/NTFS
/dev/sda2        62926605   390716864   163895130    f  W95 Ext'd (LBA)
/dev/sda5        62926668   122993639    30033486    7  HPFS/NTFS
/dev/sda6       122993703   327790259   102398278+   7  HPFS/NTFS
/dev/sda7       327790323   386813069    29511373+  83  Linux
/dev/sda8       386813133   390716864     1951866   82  Linux swap / Solaris

```

This is what my menu.lst looks like
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thx for assistance

---

### Post by Elfy on 2008-12-06
Can you post the result of

```
sudo blkid
```

and all of the menu.lst file please

---

### Post by Raouf on 2008-12-06
Menu.lst
```
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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9b56bbd3-6c15-4880-8a61-0e0dac4db40a

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
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
 This is what shown after sudo blkid
```
/dev/sda1: UUID="C088E04288E03894" LABEL="Vista OS" TYPE="ntfs" 
/dev/sda5: UUID="E2548A225489F995" LABEL="Stor" TYPE="ntfs" 
/dev/sda6: UUID="70828EC0828E8A74" LABEL="Multimedia" TYPE="ntfs" 
/dev/sda7: UUID="9b56bbd3-6c15-4880-8a61-0e0dac4db40a" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="0b27a9dd-117e-45e3-a64b-f46f6e01f863" 
/dev/loop0: TYPE="squashfs" 

```

---

### Post by Elfy on 2008-12-06
Well that all looks ok, from a terminal try and reinstall grub - information to do so is here

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

Your root is likely to be hd0,6 - but use the response the find command gives you.

---

### Post by Raouf on 2008-12-06
I also get Grub Error 17, I tried many things but nothing works with me

This is the output of sudo fdisk -lu
```
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf20ff20f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280    7  HPFS/NTFS
/dev/sda2        62926605   390716864   163895130    f  W95 Ext'd (LBA)
/dev/sda5        62926668   122993639    30033486    7  HPFS/NTFS
/dev/sda6       122993703   327790259   102398278+   7  HPFS/NTFS
/dev/sda7       327790323   386813069    29511373+  83  Linux
/dev/sda8       386813133   390716864     1951866   82  Linux swap / Solaris

```


Menu.lst
```
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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9b56bbd3-6c15-4880-8a61-0e0dac4db40a

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
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9b56bbd3-6c15-4880-8a61-0e0dac4db40a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		9b56bbd3-6c15-4880-8a61-0e0dac4db40a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
 This is what shown after sudo blkid
```
/dev/sda1: UUID="C088E04288E03894" LABEL="Vista OS" TYPE="ntfs" 
/dev/sda5: UUID="E2548A225489F995" LABEL="Stor" TYPE="ntfs" 
/dev/sda6: UUID="70828EC0828E8A74" LABEL="Multimedia" TYPE="ntfs" 
/dev/sda7: UUID="9b56bbd3-6c15-4880-8a61-0e0dac4db40a" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="0b27a9dd-117e-45e3-a64b-f46f6e01f863" 
/dev/loop0: TYPE="squashfs" 

```

---

### Post by Raouf on 2008-12-06
hey forestpixie,
I get Stuck at Setup (hd0,7)

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,7)/boot/grub/stage2
/boot/grub/menu.lst"... failed

```

anyway thx for assistance

---

### Post by Raouf on 2008-12-06
I ges stuck at Setup (hd0)
```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,7)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

```
thx for assistance
- Raouf

---

### Post by Elfy on 2008-12-06
Can you boot the livecd and run these commands

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sda7 /mnt/tmp
```

Once that has done run these and post the outputs

```
ls /mnt/tmp/boot/
ls /mnt/tmp/boot/grub
```

---

### Post by unutbu on 2008-12-06
Please post the output of 
```
sudo fdisk -l
```
Also, what did you type before "setup (hd0)"?

was it 
```

sudo grub
grub> root (hd0,7)
grub> setup (hd0)
```?

---

### Post by caljohnsmith on 2008-12-06
Unutbu, unfortunately Raouf sort of has three threads going, here are the other two:

[http://ubuntuforums.org/showthread.php?p=6317955#post6317955](http://ubuntuforums.org/showthread.php?p=6317955#post6317955)
[http://ubuntuforums.org/showthread.php?t=1003402](http://ubuntuforums.org/showthread.php?t=1003402)

From that thread he got the following output of "sudo fdisk -lu":
```
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf20ff20f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280    7  HPFS/NTFS
/dev/sda2        62926605   390716864   163895130    f  W95 Ext'd (LBA)
/dev/sda5        62926668   122993639    30033486    7  HPFS/NTFS
/dev/sda6       122993703   327790259   102398278+   7  HPFS/NTFS
/dev/sda7       327790323   386813069    29511373+  83  Linux
/dev/sda8       386813133   390716864     1951866   82  Linux swap / Solari
```
So it looks like he has a problem with his partition table, which is why he is getting that strange Grub error 12 when running the Grub commands. Unutbu, I don't want to intrude, so I'll politely step out here and let you help him check/correct his partition table if you want; or let me know if you want any input. :)

---

### Post by meierfra. on 2008-12-06
> omitting empty partition (5)


That's your problem. Boot from the Ubuntu Live CD, open  a terminal and type 


```
 sudo sfdisk -d /dev/sda |  sudo sfdisk --force  /dev/sda
```

If this does  not cure your problem, come back here and we will have to have a closer look at your setup.

---

### Post by Raouf on 2008-12-07
by the way I played with Super Grub Disk, yeah it's fixed now but really I don't what SGD do in fixing

```
raouf@Raouf:~$ ls /mnt/tmp/boot/
abi-2.6.27-7-generic         memtest86+.bin
abi-2.6.27-9-generic         System.map-2.6.27-7-generic
config-2.6.27-7-generic      System.map-2.6.27-9-generic
config-2.6.27-9-generic      vmcoreinfo-2.6.27-7-generic
grub                         vmcoreinfo-2.6.27-9-generic
initrd.img-2.6.27-7-generic  vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-9-generic  vmlinuz-2.6.27-9-generic

```

```
raouf@Raouf:~$ ls /mnt/tmp/boot/grub
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2

```

---

### Post by Raouf on 2008-12-07
by the way it was fixed right now using Super Grub Disk, fix Linux and Windows, I don't know what happen but it's fixed

This what comes with in normal Linux (not Live)
sudo sfdisk -d /dev/sda |  sudo sfdisk --force  /dev/sda

```
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   3916-   3917-  31457280    7  HPFS/NTFS
/dev/sda2       3917   24320   20404  163895130    f  W95 Ext'd (LBA)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       3917+   7655    3739-  30033486    7  HPFS/NTFS
/dev/sda6       7656+  20403   12748- 102398278+   7  HPFS/NTFS
/dev/sda7      20404+  24077    3674-  29511373+  83  Linux
/dev/sda8      24078+  24320     243-   1951866   82  Linux swap / Solaris
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048  62916607   62914560   7  HPFS/NTFS
/dev/sda2      62926605 390716864  327790260   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5      62926668 122993639   60066972   7  HPFS/NTFS
/dev/sda6     122993703 327790259  204796557   7  HPFS/NTFS
/dev/sda7     327790323 386813069   59022747  83  Linux
/dev/sda8     386813133 390716864    3903732  82  Linux swap / Solaris
Warning: partition 1 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Device or resource busy
The command to re-read the partition table failed
Reboot your system now, before using mkfs

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```

---

### Post by meierfra. on 2008-12-07
> This what comes with in normal Linux (not Live)
...

That was exactly what should come out. Just run "sudo fdisk -lu"again and you will see that  "omitting empty partition (5)"  no longer appears.

---

### Post by bapoumba on 2008-12-07
Posts from other threads moved in here.

---

### Post by kansasnoob on 2008-12-07
I love to watch meierfra and caljohnsmith work.

They're both amazing!

Many kudos to you both!

---

