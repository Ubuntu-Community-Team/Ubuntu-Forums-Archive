---
title: "UbuntuStudio installation problems"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2009-01-18
My idea was to add UbuntuStudio onto my computer, which is also running Ubuntu Intrepid and Windows XP. I figured out how to boot the UbuntuStudio CD in its own environment and it install properly. I put the partition on my external hard drive, and I made it so that UbuntuStudio is on the Master OS Choice list when i boot up my computer. The only problem is, UbuntuStudio isn't on the Master list and I cannot boot it. The installation CD isn't like th LiveCD where it can boot off of that, per say, and when I enter the installation CD, all it does is bring me to an installation menu.

Help??

---

### Post by logos34 on 2009-01-18
so you're saying you added ubuntustudio entry to your 'master' (intrepid?) menu.lst, but it doesn't show up on the grub boot screen?

---

### Post by DucksAndDolphins on 2009-01-18
Yes. That and it doesnt boot.

---

### Post by logos34 on 2009-01-18
post the output of the following:

sudo fdisk -l

cat /boot/grub/menu.lst

sudo blkid

---

### Post by DucksAndDolphins on 2009-01-18
sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10509    84413511    7  HPFS/NTFS
/dev/sda2           10511       12030    12209400    c  W95 FAT32 (LBA)
/dev/sda3           12031       12161     1052257+  d7  Unknown

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48457   389230821   83  Linux
/dev/sdb2           48458       48641     1477980    5  Extended
/dev/sdb5           48458       48641     1477948+  82  Linux swap / Solaris


cat /boot/grub/menu.lst

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
# kopt=root=UUID=0F2B43EB33CDF71E loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0F2B43EB33CDF71E loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0F2B43EB33CDF71E loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0F2B43EB33CDF71E loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0F2B43EB33CDF71E loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Embedded
root		(hd0,2)
savedefault
chainloader	+1


sudo blkid[

/dev/sda1: UUID="0F2B43EB33CDF71E" TYPE="ntfs" 
/dev/sda2: LABEL="PRESARIO_RP" UUID="3EC6-2E70" TYPE="vfat" 
/dev/sda3: UUID="96E418EFE418D2FB" TYPE="ntfs" 
/dev/loop0: UUID="015e05ee-e841-49d7-8596-bc1806390175" TYPE="ext3" 
/dev/sdb1: UUID="e8a6cf52-6e6f-401c-8616-1a09e355a8d2" TYPE="ext3" 
/dev/sdb5: UUID="62f10470-f45d-41d5-8a85-be8153923688" TYPE="swap" 

Thats all!

PS: The smileys are all 8's in parentheses, sorry.

---

### Post by mjheagle8 on 2009-01-18
why are you installing studio if you already have intrepid? i'd just install the studio programs inside intrepid.

---

### Post by DucksAndDolphins on 2009-01-18
i have my reasons.

---

### Post by mjheagle8 on 2009-01-18
may i ask what reasons?

---

### Post by DucksAndDolphins on 2009-01-18
I think its more of a subliminal thing where I can have all of my music programs in one spot that I can go to, and all my work stuff in another spot. I agree, I could just put those programs into Intrepid, but I wanted to try Studio first.

---

### Post by mjheagle8 on 2009-01-18
oh ok. just curious. have you considered a separate user account designed for multimedia/entertainment?

---

### Post by DucksAndDolphins on 2009-01-18
no, i havent. how does that work?

---

### Post by mjheagle8 on 2009-01-18
you can install the studio programs you like in intrepid, then edit your menu to not show them where you're doing work.  create a new user account, then customize it and show the multimedia programs that you're interested in using under the other account.

---

### Post by DucksAndDolphins on 2009-01-18
oh okay. thanks. ill consider doing that instead.

---

### Post by logos34 on 2009-01-18
oh, so this is a wubi installation.

Mjheagle8 has a point...although you'd also want to install the linux-rt (real-time) kernel to test it out--a moot point in this case since (last time I checked) there was no -rt kernel for intrepid 'studio due to bugs.  But a separate install is fine too, lot of people do it that way.

anyway, try 

gksudo gedit /boot/grub/menu.lst

add either of these entries to bottom of menu.lst:
> 
title UbuntuStudio 8.10 (on /dev/sdb1)
root (hd1,0) 
kernel /vmlinuz [COLOR="RoyalBlue"]root=[/COLOR]UUID=e8a6cf52-6e6f-401c-8616-1a09e355a8d2 ro splash quiet
initrd /initrd.img

(this will use the kernel symlinks)

or

> title UbuntuStudio 8.10 (/dev/sdb1)
configfile (hd1,0)/boot/grub/menu.lst

[edited]

---

### Post by DucksAndDolphins on 2009-01-18
okay i entered the top one into the bottom and i still have the same problem.

---

### Post by logos34 on 2009-01-18
> **DucksAndDolphins said:**
> okay i entered the top one into the bottom and i still have the same problem.

sorry, typo on the 'configfile' entry--try the fixed version above.  Hopefully that will work

---

### Post by DucksAndDolphins on 2009-01-18
i just enter that, and then click save, right??

---

### Post by logos34 on 2009-01-18
yes

---

### Post by DucksAndDolphins on 2009-01-18
alright well i did it, i dont think it worked. 

im going to try it again, ill let you know.

---

### Post by logos34 on 2009-01-18
If it doesn't want to work for some reason (wubi-related?), you might want install grub to the MBR of the external disk and boot directly off that.  

Boot the Ubuntu 8.10 live cd, and restore grub following the link in my signature, except use '(hd1,0)' and '(hd1)':

sudo grub

> root (hd1,0)
> setup (hd1)
> quit

Then enter the Bios at reboot and change the hard disk boot priority to boot the USB first, ahead of the internal hdd

Btw, I forgot to ask if your Bios supports booting from USB devices

---

### Post by DucksAndDolphins on 2009-01-18
alright ill try and see if that works.

yeah, my BIOS supports it, so it should be alright.

---

### Post by DucksAndDolphins on 2009-01-18
i did it.

now, if i press ESC while ubuntu is loading, at the bottom of the list is UbuntuStudio, but when i load it, i get another list containing:

Ubuntu 8.10
Recovery Mode
memtest

and when i select the first one, i get a black screen showing the loading processes. it then asks me for username/password, which are the ones i specified for Studio. After that, it just gives me a terminal.

---

### Post by logos34 on 2009-01-18
> **DucksAndDolphins said:**
> at the bottom of the list is UbuntuStudio, but when i load it, i get another list containing:

Ubuntu 8.10
Recovery Mode
memtest


if you're going through two grub menus it sounds like you're booting off the internal disk ('configfile' entry at bottom pulls up menu.lst on the sdb1).  If you were booting directly to the USB, you should get only one grub screen, showing the above.


> and when i select the first one, i get a black screen showing the loading processes. it then asks me for username/password, which are the ones i specified for Studio. After that, it just gives me a terminal.

so the problem is that it's not loading the desktop, and drops you at the console.  Any error messages, i.e. about video card config?

At the prompt you might want run this and post output: 

dmesg | tail

---

### Post by DucksAndDolphins on 2009-01-18
i got it!!

thanks a bunch.

---

### Post by logos34 on 2009-01-18
ok, enjoy

---

