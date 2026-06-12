---
title: "Grub Loader error 21 - after removing one HDD"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by izzyz on 2009-04-10
Hi I tried to find the answer in previous posts, but I have difficulties with it... I am fairly new to linux - have Ubuntu 8.10 - and it is installed on my main HDD (number 1 in BIOS setup) I also have windows installed on my second HDD (number 2 in BIOS setup. My 3rd HDD is placed on third position and is just a storage. 

Everything worked perfectly well with grub loader till I decided to remove HDD number 3 as I no longer need it. Trying to boot my PC grub error 21 shows up. I understand that grub loader settings must be configured, but I dont know how to do it. (When I tried to connect my 3rd HDD again to check if it works, yes it works again no problems)

So I got to the stage where my menu.lst shows up (with 3rd HDD attached) and it looks like this:

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
# kopt=root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=86502d4b-091c-4335-be95-fde42eb878bc

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
# defoptions=quiet splash vga=769

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
uuid		86502d4b-091c-4335-be95-fde42eb878bc
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		86502d4b-091c-4335-be95-fde42eb878bc
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		86502d4b-091c-4335-be95-fde42eb878bc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		86502d4b-091c-4335-be95-fde42eb878bc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		86502d4b-091c-4335-be95-fde42eb878bc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro quiet splash vga=769 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		86502d4b-091c-4335-be95-fde42eb878bc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=86502d4b-091c-4335-be95-fde42eb878bc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		86502d4b-091c-4335-be95-fde42eb878bc
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

---------------------------------------------------------------------

Now I have no idea what all that means, but I guess I have to remove something from here, so when it boots it doesnt take my 3rd HDD into account. ( I checked it is sda - that needs to be excluded).

Help much appreciated.

Thanks

---

### Post by Elfy on 2009-04-10
Can you boot with the livecd and run

```
sudo fdisk -l
ls -al /dev/disk/by-uuid/
```

---

### Post by bobmatino17 on 2009-04-10
this should be of help.

[http://ubuntuforums.org/showthread.php?t=1081550]("http://ubuntuforums.org/showthread.php?t=1081550")

---

### Post by izzyz on 2009-04-10
Thanks Forestpixie your tip solved my problem!

Thanks very much

---

### Post by Elfy on 2009-04-10
Great :)

---

### Post by egalvan on 2009-04-10
> **izzyz said:**
> Thanks Forestpixie your tip solved my problem!

Thanks very much

OK, I'm lost...

the "tip" was to list your partitions and UUID info....

How did this solve your problem?

Was this info somehow not right in your setup?

Thanks

---

### Post by izzyz on 2009-04-10
It solved the problem, as in my setup I had all 3 HDDs listed. After removing one of them, the setup had to be reconfigured. I hope this makes sense.

---

