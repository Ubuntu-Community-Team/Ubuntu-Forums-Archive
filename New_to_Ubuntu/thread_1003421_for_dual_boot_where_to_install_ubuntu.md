---
title: "for dual boot: where to install ubuntu"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-12-06
hi,

i have a pc in which 50Gb out of 80GB of it is occupied by windows. Then i have an extended partition of 30GB. The memory occupancy is as follows..

C:\   50GB   NTFS (windows)
D:\   30GB   extended partition NTFS

I want to install Intrepid Ibex in that PC(with dual boot). what should i do.. I dont want to install it with wubi;).. i want to learn about partitions

1. should i delete the D:\ and install ubuntu in it.. or 
2. can i leave D:\ as such as an extended partition and install ubuntu in it.or
3. should i delete D:\ and make it a primay partition and then install ubuntu in it.

or suggest me any good method.

---

### Post by Kevbert on 2008-12-06
Welcome to Ubuntu.
What version of Windows do you have ?
Delete D:\.
Select manual install when you get to the partitioning part. Make a swap file twice your RAM memory size (for using when hibernating) in the unused space (but not more than 4Gb if you have loads of memory).
Use the rest of the unused space formatted ext3 and a mount point of /
The Ubuntu bootloader will overwrite the Windows one and add an option to boot Windows.
Good luck.

---

### Post by luckydeveloper on 2008-12-06
> **Kevbert said:**
> Welcome to Ubuntu.
What version of Windows do you have ?
Delete D:\.
Select manual install when you get to the partitioning part. Make a swap file twice your RAM memory size (for using when hibernating) in the unused space (but not more than 4Gb if you have loads of memory).
Use the rest of the unused space formatted ext3 and a mount point of /
The Ubuntu bootloader will overwrite the Windows one and add an option to boot Windows.
Good luck.

i did it. ubuntu boots well. but windows is not booting. i get the grub menu correctly. but when i choose windows, it is not booting. it simply restarts my pc when i choose windows from grub.

what could be the problem.. please help

---

### Post by luckydeveloper on 2008-12-06
here's my output for   sudo fdisk -l

```
~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        9413    24410767+  83  Linux
/dev/sda3            9414        9730     2546302+   5  Extended
/dev/sda5            9414        9730     2546271   82  Linux swap / Solaris

```

guys, please help

---

### Post by luckydeveloper on 2008-12-06
what could be the problem...

---

### Post by lovelyvik293 on 2008-12-06
please post your /boot/grub/menu.lst file.

---

### Post by luckydeveloper on 2008-12-06
> **lovelyvik293 said:**
> please post your /boot/grub/menu.lst file.
here it is.. 

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
# kopt=root=UUID=c8d0bb45-a318-43fb-ad8e-e7467776d99a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c8d0bb45-a318-43fb-ad8e-e7467776d99a

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c8d0bb45-a318-43fb-ad8e-e7467776d99a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c8d0bb45-a318-43fb-ad8e-e7467776d99a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c8d0bb45-a318-43fb-ad8e-e7467776d99a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c8d0bb45-a318-43fb-ad8e-e7467776d99a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c8d0bb45-a318-43fb-ad8e-e7467776d99a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by lovelyvik293 on 2008-12-06
According to your menu.lst the windows xp must boot.
if there is any error at the boot time of windows xp?

---

### Post by lovelyvik293 on 2008-12-06
Here is my menu.lst working fine.

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
# kopt=root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=65f5af4e-c7f7-4a10-ae4d-b141ae68767b ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
#XP 
title		Windows Machine
root		(hd0,0)
makeactive
chainloader	+1
```

---

### Post by luckydeveloper on 2008-12-06
the problem still exists... i cannot solve it.. please help. 

editing the menu.lst file didn't solve it.

any other way to solve my problem?

---

### Post by lovelyvik293 on 2008-12-06
you can install the grub again on the ubuntu or can install the MBR again on windows followed by the grub installation on ubuntu.

---

### Post by Kevbert on 2008-12-06
Are you using XP or Vista ?

---

### Post by luckydeveloper on 2008-12-06
Windows XP

---

### Post by caljohnsmith on 2008-12-06
Your problem is most likely that you accidentally installed Grub to the boot sector of your Windows partition; that would cause you to reload the Grub menu when you boot XP, just like you are seeing. How about booting your Windows Install CD, go to the "recovery console" and run:
```
fixboot
```
And that should fix the problem. If not, let me know exactly what happens when you boot Windows again from Grub.

---

