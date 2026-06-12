---
title: "New kernels won't load in GRUB."
date: 2009-04-18
forum: New to Ubuntu
---

### Post by morellib on 2009-04-18
I recently have a problem getting my GRUB to stop putting out error 18 by adding a new partition specifically for the GRUB files with the help of this website: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Unfortunately, since my fix, new kernel versions no longer show up in the GRUB list. 

I am currently using 2,6,27-13-generic

2.6.27-14-generic has been available for at least 2 weeks now and my GRUB refuses to update with it. My start-up manager insists that it's my default version. I don't have it limiting the number of grub files that I have and I've tried manually updating the GRUB again and it still won't work. I've included my menu.lst in case I somehow ruined a part of that and that's how I got myself into this mess. 

I'd really appreciate it if anyone would be able to help out. 

Thanks

---

### Post by adult swim on 2009-04-18
so you added a new partition for /boot to fix your error 18?

---

### Post by morellib on 2009-04-18
Yeah, that part worked like a charm. I followed all of the instructions on this particular page: [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

I stopped following instructions after it began telling me how to set it up so I could have multiple instances of linux on my computer. I'm happy with just ubuntu. (I keep a small windows partition for times that I absolutely can't use ubuntu for something, which are becoming fewer and fewer).

---

### Post by adult swim on 2009-04-18
if you have the above as your menu.lst and it is not showing up i would guess that you have have not set up grub to look into your new /boot partition.  can you post the output of ```
sudo fdisk -l
``` and do you know which partition you have /boot on?

---

### Post by morellib on 2009-04-19
Here's the output of sudo fdisk -l:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4826    38756812+   7  HPFS/NTFS
/dev/sda2            4865       14593    78148192+  83  Linux
/dev/sda3            4827        4864      305235   83  Linux

Partition table entries are not in disk order

```

I believe that my /boot is in /dev/sda3, if that's what you were asking...

---

### Post by adult swim on 2009-04-19
alright just to be sure run these commands,
```
sudo grub

find /boot/grub/stage1
``` then copy and paste what that find command returns here.  to exit that grub prompt enter in ```
quit
```

---

### Post by morellib on 2009-04-19
Here's the output:

```
grub> find /boot/grub/stage1
 (hd0,1)

```

---

### Post by meierfra. on 2009-04-19
Did you create an "fstab" entry for your boot partition? Please post the output of

```

cat /etc/fstab
ls -l /boot
cat /boot/grub/menu.lst
sudo mount /dev/sda3 /mnt
ls -l /mnt
cat /mnt/grub/menu.lst
```

---

### Post by morellib on 2009-04-20
There's a lot here, and it appears that I lost some of it before I copied it all and pasted it... but here ya go:

```
-rw-r--r-- 1 root root  508385 2009-04-01 18:46 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  508317 2009-02-05 05:54 abi-2.6.27-12-generic
-rw-r--r-- 1 root root  508371 2009-02-26 03:54 abi-2.6.27-13-generic
-rw-r--r-- 1 root root  508371 2009-04-15 16:26 abi-2.6.27-14-generic
-rw-r--r-- 1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r-- 1 root root   91358 2008-11-21 08:46 config-2.6.27-10-generic
-rw-r--r-- 1 root root   91358 2009-04-01 18:46 config-2.6.27-11-generic
-rw-r--r-- 1 root root   91358 2009-02-05 05:54 config-2.6.27-12-generic
-rw-r--r-- 1 root root   96573 2009-02-26 03:54 config-2.6.27-13-generic
-rw-r--r-- 1 root root   96573 2009-04-15 16:26 config-2.6.27-14-generic
-rw-r--r-- 1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x 3 root root    4096 2009-04-18 01:40 grub
-rw-r--r-- 1 root root 8126500 2008-12-07 08:26 initrd.img-2.6.27-10-generic
-rw-r--r-- 1 root root 8131263 2009-04-07 12:22 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 8130463 2009-02-16 11:20 initrd.img-2.6.27-12-generic
-rw-r--r-- 1 root root 8131129 2009-03-03 09:56 initrd.img-2.6.27-13-generic
-rw-r--r-- 1 root root 8134457 2009-04-16 01:14 initrd.img-2.6.27-14-generic
-rw-r--r-- 1 root root 8125457 2008-11-29 09:29 initrd.img-2.6.27-9-generic
-rw-r--r-- 1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r-- 1 root root 1029828 2008-11-21 08:46 System.map-2.6.27-10-generic
-rw-r--r-- 1 root root 1031799 2009-04-01 18:46 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1032334 2009-02-05 05:54 System.map-2.6.27-12-generic
-rw-r--r-- 1 root root 1032976 2009-02-26 03:54 System.map-2.6.27-13-generic
-rw-r--r-- 1 root root 1032976 2009-04-15 16:26 System.map-2.6.27-14-generic
-rw-r--r-- 1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r-- 1 root root    1074 2008-11-21 08:48 vmcoreinfo-2.6.27-10-generic
-rw-r--r-- 1 root root    1074 2009-04-01 18:48 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root    1074 2009-02-05 05:55 vmcoreinfo-2.6.27-12-generic
-rw-r--r-- 1 root root    1074 2009-02-26 03:55 vmcoreinfo-2.6.27-13-generic
-rw-r--r-- 1 root root    1074 2009-04-15 16:28 vmcoreinfo-2.6.27-14-generic
-rw-r--r-- 1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r-- 1 root root 2247280 2008-11-21 08:46 vmlinuz-2.6.27-10-generic
-rw-r--r-- 1 root root 2249232 2009-04-01 18:46 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 2251152 2009-02-05 05:54 vmlinuz-2.6.27-12-generic
-rw-r--r-- 1 root root 2251376 2009-02-26 03:54 vmlinuz-2.6.27-13-generic
-rw-r--r-- 1 root root 2251504 2009-04-15 16:26 vmlinuz-2.6.27-14-generic
-rw-r--r-- 1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic
bdmorelli@bdmorelli-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro

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
# howmany=8

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

bdmorelli@bdmorelli-laptop:~$ sudo mount /dev/sda3 /mnt
[sudo] password for bdmorelli: 
bdmorelli@bdmorelli-laptop:~$ ls -l /mnt
total 59054
-rw-r--r-- 1 root root  507990 2009-03-13 12:56 abi-2.6.27-10-generic
-rw-r--r-- 1 root root  508385 2009-03-13 12:56 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  508317 2009-03-13 12:56 abi-2.6.27-12-generic
-rw-r--r-- 1 root root  508371 2009-03-13 12:56 abi-2.6.27-13-generic
-rw-r--r-- 1 root root  507665 2009-03-13 12:56 abi-2.6.27-9-generic
-rw-r--r-- 1 root root   91358 2009-03-13 12:56 config-2.6.27-10-generic
-rw-r--r-- 1 root root   91358 2009-03-13 12:56 config-2.6.27-11-generic
-rw-r--r-- 1 root root   91358 2009-03-13 12:56 config-2.6.27-12-generic
-rw-r--r-- 1 root root   96573 2009-03-13 12:56 config-2.6.27-13-generic
-rw-r--r-- 1 root root   91364 2009-03-13 12:56 config-2.6.27-9-generic
drwxr-xr-x 3 root root    1024 2009-03-13 13:20 grub
-rw-r--r-- 1 root root 8126500 2009-03-13 12:56 initrd.img-2.6.27-10-generic
-rw-r--r-- 1 root root 8129913 2009-03-13 12:56 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 8130463 2009-03-13 12:56 initrd.img-2.6.27-12-generic
-rw-r--r-- 1 root root 8131129 2009-03-13 12:56 initrd.img-2.6.27-13-generic
-rw-r--r-- 1 root root 8125457 2009-03-13 12:56 initrd.img-2.6.27-9-generic
drwx------ 2 root root   12288 2009-03-13 12:40 lost+found
-rw-r--r-- 1 root root  124152 2009-03-13 12:56 memtest86+.bin
-rw-r--r-- 1 root root 1029828 2009-03-13 12:56 System.map-2.6.27-10-generic
-rw-r--r-- 1 root root 1031799 2009-03-13 12:56 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1032334 2009-03-13 12:56 System.map-2.6.27-12-generic
-rw-r--r-- 1 root root 1032976 2009-03-13 12:56 System.map-2.6.27-13-generic
-rw-r--r-- 1 root root 1029585 2009-03-13 12:56 System.map-2.6.27-9-generic
-rw-r--r-- 1 root root    1074 2009-03-13 12:56 vmcoreinfo-2.6.27-10-generic
-rw-r--r-- 1 root root    1074 2009-03-13 12:56 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root    1074 2009-03-13 12:56 vmcoreinfo-2.6.27-12-generic
-rw-r--r-- 1 root root    1074 2009-03-13 12:56 vmcoreinfo-2.6.27-13-generic
-rw-r--r-- 1 root root    1073 2009-03-13 12:56 vmcoreinfo-2.6.27-9-generic
-rw-r--r-- 1 root root 2247280 2009-03-13 12:56 vmlinuz-2.6.27-10-generic
-rw-r--r-- 1 root root 2248912 2009-03-13 12:56 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 2251152 2009-03-13 12:56 vmlinuz-2.6.27-12-generic
-rw-r--r-- 1 root root 2251376 2009-03-13 12:56 vmlinuz-2.6.27-13-generic
-rw-r--r-- 1 root root 2244304 2009-03-13 12:56 vmlinuz-2.6.27-9-generic
bdmorelli@bdmorelli-laptop:~$ cat /mnt/grub/menu.lst
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
# kopt=root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# howmany=5

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

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by meierfra. on 2009-04-20
Yes. the "cat /etc/fstab" part got cut of.  So could you post the output of

```
cat /etc/fstab
```


From the rest of the information it seems very likely that your boot partition does not appear in "fstab".


You do have the new kernel:

> -rw-r--r-- 1 root root 8134457 2009-04-16 01:14 initrd.img-2.6.27-14-generic


but its in folder  "/boot" of  your Ubuntu partition and not on your boot partition.  

The new kernel is also on menu.lst


> title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic

but its on the wrong wrong menu.lst.

So work through  the instruction from Hermanzone again and make sure to complete each step. If you would like  I can write up detailed instructions tailored to your setup, but I'm out of time for today.

---

### Post by morellib on 2009-04-20
Sorry about that, here's the part that got cut:

```
bdmorelli@bdmorelli-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb /boot		ext3	defaults, errors=remount-ro 0	    1
# /dev/sda2
UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I'll do my best to work through the instructions again, although I thought I'd followed them very carefully. If you don't mind tailoring them a bit I'd greatly appreciate it, but take your time. Thanks so much for all your help so far.

---

### Post by meierfra. on 2009-04-20
> # /dev/sda3
UUID=5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb /boot		ext3	defaults, errors=remount-ro 0	    1



Now I'm confused. Your boot partition does seem to be mounted all ready.

Could you post the output of

```
mount
sudo blkid 
```

---

### Post by morellib on 2009-04-20
I looked back through those instructions and thought I followed everything to the letter... I don't understand what I did to get myself into this mess haha.

Here's the output:

```
bdmorelli@bdmorelli-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bdmorelli/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bdmorelli)
bdmorelli@bdmorelli-laptop:~$ sudo blkid
[sudo] password for bdmorelli: 
/dev/sda1: UUID="240C6BF90C6BC480" TYPE="ntfs" 
/dev/sda2: UUID="8a0526ab-5cd6-4b30-9411-eeb5050e8b73" TYPE="ext3" 
/dev/sda3: UUID="5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb" TYPE="ext3" SEC_TYPE="ext2" 

```

---

### Post by meierfra. on 2009-04-20
For some reason /dev/sda3 does not get mounted, even though it is listed in /etc/fstab. 
Try

```
sudo mount -a
mount | grep sda3
```

Does the first line of code give you an error message?
Does the second line produce any output?

---

### Post by meierfra. on 2009-04-20
Ignore my previous message. I know what the problem is:

> UUID=5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb /boot		ext3	defaults, errors=remount-ro 0	    1

Its the space  between "defaults," and "error"

So change 

```
defaults, errors=remount-ro

```


to

```
defaults,errors=remount-ro

```

Now follow the instruction from hermanzone again (so that the new kernel  and intitrd gets copied to the boot partition and  menu.lst  on your boot partition contains the new kernel)

---

### Post by morellib on 2009-04-21
Ok, I'm sure this is going to sound completely stupid, and you'll for sure think that I am for not getting it, but I edited the /etc/fstab as you told me to, which went just fine. Now I'm doing this off my LiveCD and I can't get it to work again like I did the first time. I keep getting hung up on pulling things up, it won't let me run the code I'm trying to put it:

```
Sudo cp -r /media/ubuntu/boot/* /media/boot/
```

I can't figure out why either. It's driving me crazy because I got it to work without a hitch the last time I did all of this...

---

### Post by morellib on 2009-04-21
Let me go ahead and change my statement, I don't think it's working because my drives aren't mounting for some reason... I've put a hundred time:

```
sudo mount -t ext3 /dev/sda3/media/boot
```

and

```
sudo mount -t ext3 /dev/sda2/media/ubuntu
```

but it seems that the output I get every time is:

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

Instead of an actual mounting... I made the mount points, I just can't figure out what I've done wrong...

---

### Post by morellib on 2009-04-21
Nevermind. I am a prize idiot. I'm going through the hermanzone instructions again now. Please disregard the previous posts.

---

### Post by morellib on 2009-04-21
Ok, everything worked perfectly. I'm on the new version of the kernel. 

Clearly I have issue with following instructions to the letter. The problem I had in the earlier posts (I'm sure you've noticed) is that I was either adding spaces where they weren't supposed to be (the initial problem) or not putting them in when clearly they were required (the problem of a few posts ago). 

Thank you very much, meierfra., and adult swim. Both of you were a great help and were very patient with my mess and lack of abilities. 

I really appreciate it!

---

### Post by meierfra. on 2009-04-21
> Ok, everything worked perfectly. 

Great. Have fun with Ubuntu.

---

### Post by morellib on 2009-04-29
Ok, so actually, now that I've fixed the error 18 problem, this is going to be absurd, but I've got error 15 now that I've upgraded to 9.04 Jaunty. Everything was going fine with the upgrade and then I get this error message when I restart. I also recall seeing a new kernel version 2.6.28-11 or something along the way but now it's vanished without a trace. I apologize for breaking my system again...

---

### Post by meierfra. on 2009-04-29
I have seen various cases where the new kernel did not get install. That usually can be fixed by running "apt-get install dist-upgrade" after "chrooting" into your ubuntu partition. But before we get into the details, let's check out your system:

Boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by morellib on 2009-04-29
Here what's in the RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,513,687    77,513,625   7 HPFS/NTFS
/dev/sda2          78,140,160   234,436,544   156,296,385  83 Linux
/dev/sda3          77,529,690    78,140,159       610,470  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="240C6BF90C6BC480" TYPE="ntfs" 
/dev/sda2: UUID="8a0526ab-5cd6-4b30-9411-eeb5050e8b73" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro

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
# howmany=8

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb /boot		ext3	defaults,errors=remount-ro 0	    1
# /dev/sda2
UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  49.2GB: boot/grub/menu.lst
  43.9GB: boot/grub/stage2
  44.0GB: boot/initrd.img-2.6.27-10-generic
  62.9GB: boot/initrd.img-2.6.27-11-generic
  44.0GB: boot/initrd.img-2.6.27-12-generic
 119.9GB: boot/initrd.img-2.6.27-13-generic
  50.3GB: boot/initrd.img-2.6.27-14-generic
  43.9GB: boot/initrd.img-2.6.27-9-generic
  44.0GB: boot/vmlinuz-2.6.27-10-generic
  61.6GB: boot/vmlinuz-2.6.27-11-generic
  44.0GB: boot/vmlinuz-2.6.27-12-generic
 119.4GB: boot/vmlinuz-2.6.27-13-generic
  55.9GB: boot/vmlinuz-2.6.27-14-generic
  43.9GB: boot/vmlinuz-2.6.27-9-generic

============================= sda3/grub/menu.lst: =============================

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
# kopt=root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# howmany=8

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


  39.9GB: grub/menu.lst
  39.9GB: grub/stage2
  39.7GB: initrd.img-2.6.27-13-generic
  39.7GB: initrd.img-2.6.28-11-generic
  39.7GB: vmlinuz-2.6.27-13-generic
  39.6GB: vmlinuz-2.6.28-11-generic
```

I apologize for it taking so long, I had to create a new Live CD as my Intrepid one has recently developed a large scratch in the back. 

Thanks again for all your help. Let me know if there's anything else you need.

---

### Post by meierfra. on 2009-04-29
You do have the new kernel:

>  39.7GB: initrd.img-2.6.28-11-generic

 39.6GB: vmlinuz-2.6.28-11-generic

but it does not appear on menu.lst.

The missing kernel on menu.lst does not explain the Grub error 15. Do you get Error 15 before the grub menu appears, or when you pick Ubuntu at the Grub menu?
What version LiveCD are you using? Ubuntu 8.10?

Try this:
Boot from the Ubuntu Live CD, open a terminal and type

```
sudo /mount /dev/sda3 /mnt
gksudo gedit /mnt/grub/menu.lst
```


Add the following to menu.lst just after the line "## ## End Default Options ##" :

title		Ubuntu 9.04  kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet



Save the file.

Back in the terminal:


```
sudo grub-install --root-directory=/mnt --recheck /dev/sda
```


Reboot. If you are able to boot into Ubuntu I suggest to update your system:


```
sudo apt-get update
sudo apt-get dist-upgrade
sudo update-grub
```

If you were not able to boot into Ubuntu, describe exactly what happens during boot up.

---

### Post by morellib on 2009-04-29
Ok, I did all that you asked, it did not boot me directly into ubuntu. Instead I am sitting here looking at a grub command line. 

```
[ Minimal BASH-like line editing is supported. For the first word, 
TAB lists possible command completions. Anywhere else TAB lists the 
possible completions of a device/filename.  ]


grub>



```


That's pretty much what it looks like. 

Any ideas?

---

### Post by meierfra. on 2009-04-30
That's strange.  Before you  tried  my suggestions, did the grub menu appear at boot up?

Try booting into Ubuntu from the Grub prompt at boot up:

```

find /boot/grub/menu.lst

root (hd0,2)

kernel /vmlinuz-2.6.28-11-generic root=/dev/sda2 ro

initrd /initrd.img-2.6.28-11-generic

boot

```

Was this successful? Post the  output of these commands.

Could you run the boot_info_script and post the "RESULTS.txt" again?  (If you were able to boot into Ubuntu, run the script from Ubuntu, otherwise use the LiveCD)

> I had to create a new Live CD as my Intrepid 

Is it an Intrepid LiveCD? Or Jaunty?

---

### Post by morellib on 2009-04-30
Ok, so I've got some stuff to report here. First off, I was able to boot into Ubuntu with the new set of instructions you gave me. The only output I thought was odd, actually the only output I got was from the first line I put in. The output from "find /boot/grub/menu.lst" was:

```
hd(0,1)
```

Here are the results of the new RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,513,687    77,513,625   7 HPFS/NTFS
/dev/sda2          78,140,160   234,436,544   156,296,385  83 Linux
/dev/sda3          77,529,690    78,140,159       610,470  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="240C6BF90C6BC480" TYPE="ntfs" 
/dev/sda2: UUID="8a0526ab-5cd6-4b30-9411-eeb5050e8b73" TYPE="ext3" 
/dev/sda3: UUID="5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /boot type ext3 (rw,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bdmorelli/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bdmorelli)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# howmany=8

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5f709b9d-1fc3-4815-a10b-0a9d38ac7bdb /boot		ext3	defaults,errors=remount-ro 0	    1
# /dev/sda2
UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  40.2GB: boot/grub/menu.lst
  40.2GB: boot/grub/stage2
  40.1GB: boot/initrd.img-2.6.27-13-generic
  40.0GB: boot/initrd.img-2.6.28-11-generic
  40.0GB: boot/vmlinuz-2.6.27-13-generic
  40.0GB: boot/vmlinuz-2.6.28-11-generic
  40.0GB: initrd.img
  40.0GB: vmlinuz

============================= sda3/grub/menu.lst: =============================

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
# kopt=root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# howmany=8

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.28-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-13-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-12-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-10-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=8a0526ab-5cd6-4b30-9411-eeb5050e8b73 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


  39.7GB: boot/grub/stage2
  39.9GB: grub/menu.lst
  39.9GB: grub/stage2
  39.7GB: initrd.img-2.6.27-13-generic
  39.7GB: initrd.img-2.6.28-11-generic
  39.7GB: vmlinuz-2.6.27-13-generic
  39.6GB: vmlinuz-2.6.28-11-generic
```

Last, but not least, I restarted the computer and it made me go through the instructions you had listed for me to use in your last post to boot into ubuntu. My grub loader isn't loading at all. And in answer to your question, no, this is the first time (well, second time since I rebooted to see if the problem had been fixed) that a grub command line has ever appeared for me. 

Oh, and I created a new LiveCD, and it's a Jaunty Ubuntu LiveCD. 

Let me know if you need anything else.

---

### Post by meierfra. on 2009-04-30
> First off, I was able to boot into Ubuntu with the new set of instructions you gave me. 
Good.  That means you don't have any serious problems and it shouldn't  take much longer to fix your problem.

> The only output I thought was odd, actually the only output I got was from the first line I put in. 
That's normal.

> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

"grub-install"  wrote the wrong paths to the mbr.     It should just be "/grub/stage2" and "/grub/menu.lst". (My fault, I should have given you a different command)

But now that you are able to boot into Ubuntu, this should be easy to fix.
Open a terminal in Ubuntu and type:

```
sudo grub-install --recheck /dev/sda
sudo apt-get update
sudo apt-get dist-upgrade
sudo update-grub

```

---

### Post by morellib on 2009-05-01
You are absolutely brilliant. 

Everything works perfectly, I can't thank you enough!

The only things I'd like to do with my awesome ubuntu machine now is figure out how to shut the beep off when shutting down/restarting and change my login password (So my wife-to-be can use my computer as well.)

Thank you so much for saving me from another huge headache!

---

### Post by Didius Falco on 2009-05-01
> **morellib said:**
> You are absolutely brilliant. 

Everything works perfectly, I can't thank you enough!

The only things I'd like to do with my awesome ubuntu machine now is figure out how to shut the beep off when shutting down/restarting and change my login password (So my wife-to-be can use my computer as well.)

Thank you so much for saving me from another huge headache!

I'll do the light lifting. ;)

Turn off the pc speaker by entering ```
gksudo gedit /etc/modprobe.d/blacklist
``` in a Terminal windows.

That will open the **blacklist** file. Scroll down to the bottom and add ```
#PC Speaker Off
blacklist pcspkr
``` to the bottom of the file and save it.

You'll hear it one last time when you log out, and you can make a few rude "good-bye" sounds at it. If you don't want to hear it one last time, enter ```
sudo rmmod pcspkr
``` in the terminal shell.

To change your password, go to **System/Administration/Users and Groups**, enter your password  to unlock it, highlight your account and click the **Properties** button. You can change the password there.

Of course, you have the option of adding an account for your fiance and each have your own, but that's personal preference.

---

### Post by morellib on 2009-05-01
Ya know, this is exactly why I'm so happy I belong to the Ubuntu community now, everyone is so very willing to help. (And this forum will be available for the next person that is sloppy with their installs and doesn't know what they're doing haha - like me)

Thanks so much for all your help again! No more loud beep to wake people up!

Thanks again everyone that helped I really appreciate it!

---

