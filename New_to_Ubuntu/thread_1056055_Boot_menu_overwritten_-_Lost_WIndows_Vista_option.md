---
title: "Boot menu overwritten - Lost WIndows Vista option"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by wc4r on 2009-01-31
I use Ubuntu 8.10 and Windows Vista on the same PC. OS are on separate drives.
My default boot menu was Vista then Ubuntu, etc.
During a Linux update today, the menu was overwritten and now I lost my Vista option. :confused:
I tried to use the Start-up manager but Vista was not an OS option there.:eek:
**How can I get the Vista option back?**
Joe

---

### Post by Jynxx on 2009-01-31
One thing you can do is install KGRUBEditor from add/remove. This will allow you to see everything and select Windows as default boot if you so desire.

---

### Post by handydan918 on 2009-01-31
> **wc4r said:**
> I use Ubuntu 8.10 and Windows Vista on the same PC. OS are on separate drives.
My default boot menu was Vista then Ubuntu, etc.
During a Linux update today, the menu was overwritten and now I lost my Vista option. :confused:
I tried to use the Start-up manager but Vista was not an OS option there.:eek:
**How can I get the Vista option back?**
Joe
If you can post the output of ```
cat /boot/grub/menu.lst
``` I bet you can find someone who can straighten it out for ya. It's usually just a matter of adding about 4 line of text to add windows....

---

### Post by wc4r on 2009-01-31
Here is the code I have now --- 
joe@joe-linux:~$ cat /boot/grub/menu.lst
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
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color yellow/blue green/blue

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
# kopt=root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0bd9ad05-dcb6-449d-b18d-46e0edcf903e

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0bd9ad05-dcb6-449d-b18d-46e0edcf903e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0bd9ad05-dcb6-449d-b18d-46e0edcf903e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
joe@joe-linux:~$

---

### Post by caljohnsmith on 2009-01-31
Wc4r, so can you still boot into Ubuntu OK, but just not Vista? How about also posting:
```
sudo fdisk -lu
```
And please identify your Vista partition.

---

### Post by wc4r on 2009-01-31
I think this answers the question.
The master SATA drive (250 GB) is for Vista. The slave drive (320 GB) is for Linux.
Ignore the 3rd (250 GB) drive. It's an external one used for file backups only. 
Joe
====================== 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3648b38b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488394751   244196352    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd3c24894

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   606919634   303459786   83  Linux
/dev/sdb2       606919635   625137344     9108855    5  Extended
/dev/sdb5       606919698   625137344     9108823+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x069e755c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488392064   244196001    7  HPFS/NTFS
joe@joe-linux:~$

---

### Post by caljohnsmith on 2009-01-31
OK, since we don't know yet which drive you are booting on start up, there are three possible Grub entries that could work to boot Vista, so probably the easiest would be to just try all three. How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add these entries at the end of the file:
```
title       Windows Vista (hd0)
root       (hd0,0)
chainloader +1

title       Windows Vista (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows Vista (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Please make sure to add the entries after:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
Because if you put the entries before that in the Debian automagic kernel section, your Vista entries will be deleted the next time you get a kernel upgrade (that's probably why you lost your Vista entry to begin with). Anyway, how about trying each of the above Vista entries from the Grub menu on start up, and let me know how that goes.

---

### Post by wc4r on 2009-01-31
Excellent!

This is what I needed:
title       Windows Vista (hd0)
root       (hd0,0)
chainloader +1

A follow up to this is how can I make it the first option so Vista will load by default as the first one on the list. It would keep my wife happy.

---

### Post by caljohnsmith on 2009-01-31
Glad to hear that first Vista entry worked OK. If you want to make that Vista entry first in the Grub menu, just move the Vista entry right above the Debian automagic kernels section like:
```
title Windows Vista
root (hd0,0)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
That should work because your menu.lst has "default 0" which means the first entry will get booted by default if you don't do anything on start up. Anyway, cheers and have fun with Vista and Ubuntu. :)

---

### Post by wc4r on 2009-01-31
Thanks. Your idea is even better.
I went to the start-up manager and just made Vista the default operating system. It may be at the bottom but it does the trick. 
Your info give it a better "look".
Thanks!!!

---

