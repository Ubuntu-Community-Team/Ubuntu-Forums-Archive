---
title: "[SOLVED] Grub Error 21 - Help!"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-30
So I just got a new harddrive for this old Compaq Armada m300 I've had laying around and it does not support booting from USB nor does it have a CD drive, so to installed Xubuntu to it I used a USB to IDE adapter on my main laptop that runs Ubuntu 8.10

How ever since I finished my main laptop (the one running Ubuntu) is now getting "Error 21" after the grub menu when I turn it on... Did installing Xubuntu on a serperate HDD some how mess up my main HDD?... In any event can I correct this error with out reformatting? Right now I am using the Xubuntu live CD on my laptop to post this... help please!

~Jeff

---

### Post by caljohnsmith on 2008-12-30
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by beastrace91 on 2008-12-30
Results.txt: ```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hda
 => Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________

fdisk -lu /dev/hda:
Note: sector size is 2048 (not 512)

Disk /dev/hda: 570 MB, 570589184 bytes
255 heads, 63 sectors/track, 17 cylinders, total 278608 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Disk identifier: 0x00000000


sfdisk -V /dev/hda:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/hda: unrecognized partition table type

sfdisk: no partition table present.

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe5541869

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   224829674   112414806   83  Linux
/dev/sda2       224829675   234436544     4803435    5  Extended
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="59f86560-0b02-42ab-97d9-3f5cc5e5089b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5d3bb299-6104-44fe-b374-c8e059d271a1" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=59f86560-0b02-42ab-97d9-3f5cc5e5089b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=59f86560-0b02-42ab-97d9-3f5cc5e5089b

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
uuid		59f86560-0b02-42ab-97d9-3f5cc5e5089b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59f86560-0b02-42ab-97d9-3f5cc5e5089b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		59f86560-0b02-42ab-97d9-3f5cc5e5089b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59f86560-0b02-42ab-97d9-3f5cc5e5089b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		59f86560-0b02-42ab-97d9-3f5cc5e5089b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59f86560-0b02-42ab-97d9-3f5cc5e5089b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		59f86560-0b02-42ab-97d9-3f5cc5e5089b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59f86560-0b02-42ab-97d9-3f5cc5e5089b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		59f86560-0b02-42ab-97d9-3f5cc5e5089b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=59f86560-0b02-42ab-97d9-3f5cc5e5089b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5d3bb299-6104-44fe-b374-c8e059d271a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23792
drwxr-xr-x  3 root root    4096 2008-12-20 04:46 .
drwxr-xr-x 20 root root    4096 2008-12-20 04:46 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 04:46 grub
-rw-r--r--  1 root root 8196388 2008-12-20 04:07 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8195999 2008-12-20 04:46 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 04:46 .
drwxr-xr-x 3 root root   4096 2008-12-20 04:46 ..
-rw-r--r-- 1 root root    197 2008-12-20 03:35 default
-rw-r--r-- 1 root root     15 2008-12-20 03:35 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 03:35 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 03:35 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 03:35 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 03:35 jfs_stage1_5
-rw-r--r-- 1 root root   4792 2008-12-20 04:46 menu.lst
-rw-r--r-- 1 root root   4310 2008-12-20 04:46 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-20 03:35 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 03:35 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 03:35 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 03:35 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 03:35 xfs_stage1_5

=============================== StdErr Messages: ===============================

Disk /dev/hda doesn't contain a valid partition table

```

Is there hope? I googled Grub Error 21 and saw that it is linked to a boot config mess up, did the Xubuntu live disc mess something up on my laptop when I installed it to that other HDD?

In any event hope that results.txt helps!

~Jeff

~Jeff

---

### Post by beastrace91 on 2008-12-31
Anyone have any idea please? I really need to get this working... not having a computer is killing me 

~Jeff

---

### Post by beastrace91 on 2008-12-31
Wow so I found something explaining exactly what happened to me... [http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)

So any ideas how I can correct this issue (meaning reinstalling grub) to my laptop with out that external HDD? I left it at my parents house and I am at home for the evening :( I have a live CD (what I am using to post right now) if that helps...

~Jeff

---

### Post by eagle416 on 2008-12-31
if you have a functional second computer, you can make a Super Grub Disk, which you can use to reinstall Grub, or at least boot into whatever OS you want.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by beastrace91 on 2008-12-31
I do not currently have a second computer (or blank CDs lying around...) How ever some google savy lead me to [this thread](http://ubuntuforums.org/showthread.php?t=224351) trying that now to see if it works. *crosses fingers*

~Jeff

---

### Post by eagle416 on 2008-12-31
you can put Super Grub Disk on a USB memory stick.

One thing you might want to search for is reinstalling grub from the live cd. It can be done, I just don't remember exactly how.

---

### Post by beastrace91 on 2008-12-31
Yep reinstalling grub from a live CD worked like a charm. (It is what the thread I linked to above said to do)

TBA this is the first issue like this I have ever had with *buntu and it is kinda disappointing... I am obviously not the first one for this to happen to and I hope maybe something can be done to prevent it from happening again. (I am not much for code but I doubt it can be hard to fix, I mean just leave the grub files on the main HDD alone when installing?...)

~Jeff

---

