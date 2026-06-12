---
title: "please help with grub"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by flugo on 2009-09-05
i have a multiboot set up with vista, ubuntu 8.04 and ubuntu 9.04 . everything was just fine : even edited the grub menu successfully to boot vista first. THEN i decided i did not want 8.04 and formatted the partion it was on and installed dreamlinux there. Thats when my problems started. After the dream linux installation, all i had was its bootloader and could not choose any other OS so i reinstalled 8.04 and got back to the set up i had before but now my computer will only boot to the recovery mode of 9.04 . I have edited grub and it shows that the changes i made are there but it continues to boot in the 9.04 recovery mode. I also have redundant copies of 9.04 in the list so i have no idea what i screwed up but if some one could help me get back to where i was when everything was blissfull in my world i will be so gratefull and promise not to tinker til i educate myself in linux a bit more. Here is what i have in the grub menu:
                 ****************************************

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
default		8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
# kopt=root=UUID=345acf82-5353-4b1d-a530-8b716968c82c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=345acf82-5353-4b1d-a530-8b716968c82c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=345acf82-5353-4b1d-a530-8b716968c82c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=911f2d8b-22ae-4040-a484-c2dd0e8f4262 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=911f2d8b-22ae-4040-a484-c2dd0e8f4262 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=911f2d8b-22ae-4040-a484-c2dd0e8f4262 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=911f2d8b-22ae-4040-a484-c2dd0e8f4262 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=911f2d8b-22ae-4040-a484-c2dd0e8f4262 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=911f2d8b-22ae-4040-a484-c2dd0e8f4262 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu 9.04, memtest86+ (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Liolikas on 2009-09-05
This menu you entered here is empty just example for update-grub script.
Now you have who knows how much /boot folders and kernels....
---
To keep things clean create /boot partition like 0.5 Gb make it bootable merge all /boot contents from all Linux installations to it and install grub to it.
----
This is kinda standard configuration, but Linux "user friendly" distros tend to avoid those "difficulties" with 4+ partitions. But when matters come to 3+ distros booting from same hdd this manual setup is almost must-have.

---

### Post by SheaMan on 2009-09-05
I am getting the impression (from all this reading) that I should have mulitple partitions. My question is if that is the "way its supposed to be" why did the Jaunty CD I just installed only have the two options? 

I could keep windows (no). or I could "give Ubuntu the entire disk" and I got one 40g partition... do I need to change that as well?

---

### Post by lindsay7 on 2009-09-05
Flugo, download and read the instructions for "Super Grub". You may be able to fix your problem this way.

---

### Post by lindsay7 on 2009-09-05
SheaMan, There should have been a manual install option listed which would let you set up the partitions as you wanted.

---

### Post by flugo on 2009-09-05
Liolikas , thanks so much for replying but i am brand new to linux and i have no idea what you just said. I don't think that is just an example, i navigated to that page by using using this code " gksudo gedit /boot/grub/menu.lst" in terminal and then i edited it to have windows boot first - and it worked great til i installed dreamlinux on the partition that had 8.05 installed on it. now no matter what changes i make to the grub menu, it still does the same thing as i described earlier. I have no idea what all is being said in that grub menu page nor do i understand your suggestion to " keep things clean create /boot partition like 0.5 Gb make it bootable merge all /boot contents from all Linux installations to it and install grub to it. it almost seems like it would be easier to delete all partions but the one windows is on and start all over but i really don't want to do that. Help

---

### Post by flugo on 2009-09-05
Thanks Lindsay7 I will try that.

---

### Post by LewRockwell on 2009-09-05
145 operating systems on one machine...

[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

not your average anything...but good information nevertheless...

.

---

### Post by mike555 on 2009-09-05
it might be easier for you to install another boot manager like " GAG" .... [http://gag.sourceforge.net/](http://gag.sourceforge.net/)   ( you will need grub installed in the front of each partition to load linux , but it's great if you , like me are often installing different distro's)

---

