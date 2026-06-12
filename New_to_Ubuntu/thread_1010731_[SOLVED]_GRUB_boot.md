---
title: "[SOLVED] GRUB boot"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by frostyfrog on 2008-12-14
Hi Folks,
Ive Just installed UBUNTU on my machine. Works great ........
I'm very new to this and am finding it a little scary so far.
I have installed UBUNTU on one of my three hard disks. Disks are as follows

250 GB - Ubuntu
500 GB - XP
250 GB - Storage

My problem is the GRUB loads OK but if I select the XP boot option I get an ERROR message 

[B]Starting Up ...
NTLDR is missing
[/B]

I suspect GRUB is looking only on the Ubuntu hard disk
can I fix easily

Any help appreciated

---

### Post by Michael.Godawski on 2008-12-14
hey, 
please post the output of this terminal command:

```
cat /boot/grub/menu.lst
```

I guess we can fix this. :p

---

### Post by frostyfrog on 2008-12-14
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
# kopt=root=UUID=2fc28b21-61f5-4077-8f0c-d8e7f152f507 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2fc28b21-61f5-4077-8f0c-d8e7f152f507 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2fc28b21-61f5-4077-8f0c-d8e7f152f507 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2fc28b21-61f5-4077-8f0c-d8e7f152f507 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2fc28b21-61f5-4077-8f0c-d8e7f152f507 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by MrPixel on 2008-12-14
hello,   I have a similar upgrade boot question, maybe someone has tread this path before and can recommend a procedure .. 
I'd like to remotely over the phone tell someone how to upgrade from Ubuntu 6 to Ubuntu 8.10  and the first problem I ran in to was that the vintage remote machine has an old CD  reader that couldn't read the upgrade disk. So the next option is to explain to the novice user how to hook up to the net, and download  8.10.. 
So my question is simple, can it be upgraded to 8.10 over the net using Ubuntu 6 with out burning a  new .iso disk? i.e. can it be installed over the net ? Or does it need to have a CD disk burned?

thanks in advance , Mr Pixel

---

### Post by Elfy on 2008-12-14
frostyfrog - can you run ```
sudo fdisk -l
``` post it's output please


mrpixiel - it depends what version it is - 6.06 LTS is still in support and you should be able to do so - if it's 6.10 then you'll need to use a cd - if you have any other questions please start a new thread

---

### Post by frostyfrog on 2008-12-14
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561   83  Linux
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c0daff5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x5fe8890e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      969016   488384032+   7  HPFS/NTFS

---

### Post by frostyfrog on 2008-12-14
Just wanted to add that XP boots fine if I enter BIOS setup and change hard disk boot order. ie; select the 500GB disk to boot from. I would obviously prefer not to do that but just use GRUB to choose OS.

---

### Post by Elfy on 2008-12-14
Well it all looks ok - try this. open the file to edit after backing it up, 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.1412
gksu gedit /boot/grub/menu.lst
```

Add this to the bottom of the file and then reboot and try the new option

> title Windows XP (hd2)
rootnoverify (hd2)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by frostyfrog on 2008-12-14
Followed the above instructions but with no effect. It did add the following line to GRUB options though 

windows XP (dh2)

Still get "NTLDR is Missing" message after choosing that option

I have learnt something though.

how to edit
how to copy
thanks for your patience forestpixie

---

### Post by Michael.Godawski on 2008-12-14
Seems to be some bigger "fun":


[LIST]
[*][http://ubuntuforums.org/showthread.php?t=2721](http://ubuntuforums.org/showthread.php?t=2721)
[*][http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
[/LIST]

---

### Post by frostyfrog on 2008-12-14
Thanks for links Michael G.
Tinyempire one looks very interesting
What would we do if we didnt spend endless hours sorting out computer problems.
I suppose it might be gardening,fishing, model making or just messing around in the shed. oops just listed most of my hobbies. Better than watching the silly goggle box though......

Ill keep working on it.
Thanks all.....

---

### Post by caljohnsmith on 2008-12-14
I think your issue might be that your Windows drive is 2nd in the BIOS boot order and not 3rd, and that would explain why you get a "NTLDR missing" when you try to boot the 3rd boot drive with your current Windows Grub entry. How about trying the following entry instead:
```
title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```
Let me know exactly what happens when you choose that from the Grub menu if it doesn't work, and we can go from there if you want.

---

### Post by Elfy on 2008-12-14
Didn't do that as 
> 
500 GB - XP - sdc
250 GB - Storage - sdb

It might also be confusion with PATA and SATA

---

### Post by frostyfrog on 2008-12-15
Problem solved. Thanks folks. It didnt start XP because as you said I needed 500GB as third on list of hard disks to boot from in BIOS. THANKYOU ..........PS all drives are SATA/1 if you are interested.

---

### Post by caljohnsmith on 2008-12-15
Glad to hear that worked; cheers and have fun with Windows and Ubuntu. :)

---

