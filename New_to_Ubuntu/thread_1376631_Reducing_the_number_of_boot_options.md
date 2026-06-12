---
title: "Reducing the number of boot options"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by timmyhiggy on 2010-01-09
Hi

I have been running Ubuntu netbook remix long enough to have had a fair few kernel updates. Every time this happens, is just adds the latest kernel to the top of the boot list on start up, so the list is now absolutely enormous! 
I found some threads about editing a config file, but it had a bit too much assumed knowledge. If I were to follow it, I wouldn't really know what I was changing!

Could anyone help me with a simple guide on changing the boot list?

My GRUB config file looks liek this:

> 
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
# kopt=root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4654ec37-42ea-4da6-8545-ce08e1a638d7

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=4654ec37-42ea-4da6-8545-ce08e1a638d7 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		4654ec37-42ea-4da6-8545-ce08e1a638d7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
chainloader	+1



And I'd like it to be just the most recent 2 kernels followed by the windows loaders...

---

### Post by mikewhatever on 2010-01-09
Just go to Synaptic package manager and uninstal the kernels you don't need, grub will get updated in the process. Search for linux-image to find the kernels.

---

### Post by Elfy on 2010-01-09
You can do this a few ways, edit the file - which just removes the menu item or remove the kernels which clears both the menu item and removes the packages as well, also you can use the startupmanager tool - the advanced tab gives the option to set it to how many kernels to keep , though I would suggest keeping 2 until you are sure any newer one works ok for you.

---

### Post by kansasnoob on 2010-01-09
I see you have a menu.lst so I suppose you have legacy grub.

To be sure run this command:

```
grub-install -v
```

0.97 is legacy grub and 1.97 is grub2

If you have legacy grub the simplest way to handle that is by installing Startup Manager:

```
sudo apt-get install startupmanager
```

You'll then find it in System > Administration:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

Under the Advanced tab you'll see an option to limit the number of kernels displayed. I generally like setting it to 2 so just in case a kernel update fails I can still boot the previous kernel.

It also allows you to remove the seldom used Memtest option.

---

### Post by garyed on 2010-01-09
If you only want to clean up the boot menu then you could just add a "#" sign in front of all the menu lines you don't want to appear at startup.
This way all your kernels will still be available if needed.
Make a copy of your menu.lst before you edit it just in case something goes wrong.

---

### Post by timmyhiggy on 2010-01-09
Cheers for the help guys, I installed startup manager and reduced the number of kernels in the list to 2.

---

### Post by threepenpals on 2010-01-22
Under Xubuntu 9.10, at least, the "advanced" pane of StartUp-Manager does not allow the user to set the number of kernels in the boot menu, or the number of kernels that will be retained.

Does anyone know of another way to set the package manager to only retain a limited number of kernels?

---

