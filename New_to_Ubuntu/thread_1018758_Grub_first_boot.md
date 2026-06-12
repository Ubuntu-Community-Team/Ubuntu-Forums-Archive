---
title: "Grub first boot"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Lethithan on 2008-12-22
First time with linux, I've installed Ubuntu, Now when I try boot it I get a command line
GRUB>

Tried playing around to get it to boot, want to know what commands I need or if I should be seeing this screen. I would have expected it to go straight to a login screen.

---

### Post by caljohnsmith on 2008-12-22
Did you install Ubuntu inside of Windows using Wubi? Do you have the Ubuntu Live CD (install CD) that you can boot? If so, how about booting that, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by hexanol on 2008-12-22
You should not see this screen. I think that means grub can't find it's configuration file on the designated partition. On the grub command line, try this command
```
*grub>* find /boot/grub/menu.lst
```
If you get an error, then the grub configuration file is missing. Else, grub has been setup incorrectly. But in any way, I find it weird.

EDIT: And if you do find a file named menu.lst in the /boot/grub/ directory, enter this command
```
configfile (hdX,Y)/boot/grub/menu.lst
```
where X and Y are the number given as a result of the find command you just entered.

---

### Post by Lethithan on 2008-12-22
File reads as

> Grub is installed in the MBR of /dev/sda and looks on boot drive #3 in partition #1 for its boot files.
No boot loader is installed in the MBR of /dev/sdb
Grub is installed in the MBR of /dev/sdc and looks at sector 24063 of the same hard drive for the stage2 file., but no stage2 files can be found at this location

sda1:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type

sda2:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type

sda3:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type

sdc1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /etc/fstab /boot

sdc2:
    File system:  Extended Partition

sdc5:
    File system:  swap


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a1f36d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000    7  HPFS/NTFS
/dev/sda2       204802048   409602047   102400000    7  HPFS/NTFS
/dev/sda3       409602048  1953544191   771971072    7  HPFS/NTFS

Warning: partition 3 extends past end of disk


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


Warning: partition 3 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.


Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   374796449   187398193+  83  Linux
/dev/sdc2       374796450   390716864     7960207+   5  Extended
/dev/sdc5       374796513   390716864     7960176   82  Linux swap / Solaris

Warning: partition 3 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

/dev/sdc1: UUID="4ac18af2-c30d-4adb-bbcd-2cf77a253761" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="78d7b149-5499-4ff3-b7f4-f38b6a8740ef" 
/dev/loop0: TYPE="squashfs" 

sdc1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=4ac18af2-c30d-4adb-bbcd-2cf77a253761 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=78d7b149-5499-4ff3-b7f4-f38b6a8740ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdc1/boot

total 12804
drwxr-xr-x  2 root root    4096 2008-12-23 04:40 .
drwxr-xr-x 20 root root    4096 2008-12-23 04:40 ..
-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic
-rw-r--r--  1 root root 8645004 2008-12-23 04:40 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

StdErr Messages 

boot_info_script.txt: line 136: [: -lt: unary operator expected
boot_info_script.txt: line 136: [: -lt: unary operator expected
boot_info_script.txt: line 136: [: -lt: unary operator expected
Disk /dev/sdb doesn't contain a valid partition table
me type
/dev/sda3: unknown volume type

as to Hexanol, I'll get back to you soon about that.

---

### Post by Lethithan on 2008-12-22
Error 15: file not found o.O

---

### Post by caljohnsmith on 2008-12-22
OK, I think I see part of the complication; you have Windows in a RAID setup it appears. But fortunately you have Ubuntu on a non-RAIDed drive it looks like, so ideally it would be best if you were to install Grub to the MBR of your Ubuntu sdc drive and boot the sdc drive directly on start up. Can you set your BIOS to boot the Ubuntu sdc drive on start up? Also, your sdc1 Ubuntu partition does not have Grub installed. How about reinstalling Ubuntu to the sdc drive, but when you get to the final step in the installation process, click the "advanced" button, and specify to have Grub installed to /dev/sdc. Then you should be able to boot the sdc Ubuntu drive OK. It would be good to restore a Windows MBR to your RAID drives, but first see if you can get the Ubuntu sdc drive booting OK. We can work from there if you want.

---

### Post by Lethithan on 2008-12-22
Heres hoping.....
With the MBR I need the Windows disc for that right?

I was trying to avoid the boot manager getting onto my windows discs but didn't realise it did it automatically.....
And yeah I was going to switch between them through the bios.

---

### Post by caljohnsmith on 2008-12-22
> **Lethithan said:**
> Heres hoping.....
With the MBR I need the Windows disc for that right?

I was trying to avoid the boot manager getting onto my windows discs but didn't realise it did it automatically.....
And yeah I was going to switch between them through the bios.
Fortunately you don't have to have a Windows Install CD to reinstall a Windows MBR; it is possible to install a Windows equivalent MBR from the Ubuntu Live CD by doing:
```
sudo lilo -M  /dev/sda mbr
```
Let me know how that goes. :)

---

### Post by Lethithan on 2008-12-22
There we go, Ubuntu's working, thanks mate.
Just another quick question
Can I get Ubuntu to recognize the NTFS/RAID of my Windows, or vice visa to make it easier to transfer files?

---

### Post by kansasnoob on 2008-12-22
> **caljohnsmith said:**
> Fortunately you don't have to have a Windows Install CD to reinstall a Windows MBR; it is possible to install a Windows equivalent MBR from the Ubuntu Live CD by doing:
```
sudo lilo -M  /dev/sda mbr
```
Let me know how that goes. :)

You rock! Happy holidays!

---

### Post by caljohnsmith on 2008-12-22
> **Lethithan said:**
> There we go, Ubuntu's working, thanks mate.
Just another quick question
Can I get Ubuntu to recognize the NTFS/RAID of my Windows, or vice visa to make it easier to transfer files?
Great, glad to hear that worked. I don't have much experience with RAID, but I've heard of people in the forums using the package "mdadm" in order to recognize RAID setups. Anyway, cheers and good luck with it. :)
[QUOTE=kansasnoob]
You rock! Happy holidays![/QUOTE]
Happy holidays to you too, kansasnoob. Hope it isn't too cold and snowy in Kansas right now, although I would imagine that could be the case. :)

---

### Post by meierfra. on 2008-12-22
> boot_info_script.txt: line 136: [: -lt: unary operator expected
boot_info_script.txt: line 136: [: -lt: unary operator expected
boot_info_script.txt: line 136: [: -lt: unary operator expected

Lethithan, I'm the author  of the script  "boot_info_script.txt". I think I fixed the bug which caused the above errors. 

 If you have some time, could you follow the instruction from post 2 again  and post the new "RESULT.txt" (if you still have the file "RESULT.txt" on your desktop from the last time, delete it first)


Thanks

---

### Post by kansasnoob on 2008-12-22
> **meierfra. said:**
> Lethithan, I'm the author  of the script  "boot_info_script.txt". I think I fixed the bug which caused the above errors. 

 If you have some time, could you follow the instruction from post 2 again  and post the new "RESULT.txt" (if you still have the file "RESULT.txt" on your desktop from the last time, delete it first)


Thanks

And a happy, happy holiday to you!

Both you and caljohnsmith blow my mind!

You've both helped many, many people get past booting problems that were far beyond my capability!

---

### Post by Lethithan on 2008-12-23
I ran it again

> Lilo is installed in the MBR of /dev/sda
No boot loader is installed in the MBR of /dev/sdb
Grub is installed in the MBR of /dev/sdc and looks on the same drive in partition #1 for its boot files.
Windows is installed in the MBR of /dev/sdd

sda1:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type

sda2:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type

sda3:
    File system:  
    Mounting failed:  
mount: you must specify the filesystem type

sdc1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2:
    File system:  Extended Partition

sdc5:
    File system:  swap

sdd1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdd1 starts at sector 63.
    Operating System: 
    Boot files/directories present: 

sdd2:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdd2 starts at sector 238597380.
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a1f36d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000    7  HPFS/NTFS
/dev/sda2       204802048   409602047   102400000    7  HPFS/NTFS
/dev/sda3       409602048  1953544191   771971072    7  HPFS/NTFS

Warning: partition 3 extends past end of disk


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


Warning: partition 3 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.


Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   374796449   187398193+  83  Linux
/dev/sdc2       374796450   390716864     7960207+   5  Extended
/dev/sdc5       374796513   390716864     7960176   82  Linux swap / Solaris

Warning: partition 3 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.
/dev/sdc: OK


Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c6e2a8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   238597379   119298658+   7  HPFS/NTFS
/dev/sdd2       238597380   488392064   124897342+   7  HPFS/NTFS

Warning: partition 3 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.
/dev/sdc: OK
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sdd: OK

/dev/sdc1: UUID="da5e5633-af4a-44d7-9620-a84d3c3b6a6d" TYPE="ext3" 
/dev/sdc5: UUID="78d7b149-5499-4ff3-b7f4-f38b6a8740ef" TYPE="swap" 
/dev/sdd1: UUID="E4D4B65AD4B62EA4" LABEL="Data1" TYPE="ntfs" 
/dev/sdd2: UUID="B860BA8360BA47C0" LABEL="Data2" TYPE="ntfs" 

sdc1/boot/grub/menu.lst

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=da5e5633-af4a-44d7-9620-a84d3c3b6a6d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=da5e5633-af4a-44d7-9620-a84d3c3b6a6d

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
uuid		da5e5633-af4a-44d7-9620-a84d3c3b6a6d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=da5e5633-af4a-44d7-9620-a84d3c3b6a6d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		da5e5633-af4a-44d7-9620-a84d3c3b6a6d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=da5e5633-af4a-44d7-9620-a84d3c3b6a6d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		da5e5633-af4a-44d7-9620-a84d3c3b6a6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=da5e5633-af4a-44d7-9620-a84d3c3b6a6d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		da5e5633-af4a-44d7-9620-a84d3c3b6a6d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=da5e5633-af4a-44d7-9620-a84d3c3b6a6d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		da5e5633-af4a-44d7-9620-a84d3c3b6a6d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sdc1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=da5e5633-af4a-44d7-9620-a84d3c3b6a6d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=78d7b149-5499-4ff3-b7f4-f38b6a8740ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sdc1/boot

total 25512
drwxr-xr-x  3 root root    4096 2008-12-23 06:51 .
drwxr-xr-x 21 root root    4096 2008-12-23 16:30 ..
-rw-r--r--  1 root root  503560 2008-11-05 07:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-21 10:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root     512 2008-12-23 06:04 boot.0800
-rw-r--r--  1 root root   85316 2008-11-05 07:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-21 10:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-23 06:50 grub
-rw-r--r--  1 root root 8661080 2008-12-23 06:50 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8660389 2008-12-23 06:51 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-12 06:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-05 07:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-21 10:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-05 07:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-21 10:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-05 07:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-21 10:30 vmlinuz-2.6.27-9-generic

sdc1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-23 06:50 .
drwxr-xr-x 3 root root   4096 2008-12-23 06:51 ..
-rw-r--r-- 1 root root    197 2008-12-23 05:56 default
-rw-r--r-- 1 root root     45 2008-12-23 05:56 device.map
-rw-r--r-- 1 root root   8108 2008-12-23 05:56 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-23 05:56 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-23 05:57 installed-version
-rw-r--r-- 1 root root   8712 2008-12-23 05:56 jfs_stage1_5
-rw-r--r-- 1 root root   4792 2008-12-23 06:50 menu.lst
-rw-r--r-- 1 root root   4708 2008-12-23 06:50 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-23 05:56 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-23 05:56 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-23 05:56 stage1
-rw-r--r-- 1 root root 121460 2008-12-23 05:57 stage2
-rw-r--r-- 1 root root   9556 2008-12-23 05:56 xfs_stage1_5

StdErr Messages 

Disk /dev/sdb doesn't contain a valid partition table
me type
/dev/sda3: unknown volume type

Hope this helps you

---

### Post by meierfra. on 2008-12-23
Thank you very much! The bug seems to be fixed. Although there is still something strange going on. If you have some time could you post the output of

```
sudo sfdisk -sV
```

I'll promise, this will be last  request.


Thanks again for your help.

---

### Post by Lethithan on 2008-12-23
There we are

> /dev/sda: 488386584
Warning: partition 3 extends past end of disk
/dev/sdb: 488386584

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.


---

### Post by Elfy on 2008-12-23
meierfra. - that is a very useful script :)

---

### Post by meierfra. on 2008-12-23
[QUOTE=Lethithan]There we are[/QUOTE]

Thanks.


[QUOTE=forestpixie]meierfra. - that is a very useful script[/QUOTE]
Thanks. I only have little programing experience, this is my very first bash script and it has been a slow learning process. So every word of encouragement is appreciated.

You are welcome to use it in your own posts.

---

