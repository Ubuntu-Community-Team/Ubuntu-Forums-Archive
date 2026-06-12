---
title: "Need help with restoring"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by crash2win64 on 2009-10-10
Hey I recently installed Ubuntu 9.04 and did my updates here the other day and now after restarting the computer when it goes to load the desktop it freezes and won't do anything after that. It also displays a weird image and like 2 and a half little ubuntu logos and multicolored lines underneath that... I have no idea what to do from here. Can you revert to a safe point like windows or anything or make a boot disk that fixes whats wrong? I tried with the cd I got but to no avail and now I'm using that to be able to use the net here... 
Any help would be greatly appreciated
Thanks

---

### Post by LewRockwell on 2009-10-10
video driver problems likely

use your LiveCD to check for a previous kernel to revert to

should find them in /boot directory

keep us posted on your progress and solution(s)!

.

---

### Post by crash2win64 on 2009-10-10
How do you do that now? Do you load from the ubuntu install cd? Or get on trial version and pull from the disc then? This is pretty confusing for me... Or do I need to download this live cd and burn it?

---

### Post by cariboo on 2009-10-10
LewRockwell only gave you part of the solution, when booting up press escape at the grub menu, you will be presented with a menu, select one of the older kernels to boot from and see if the problem persists.

If you don't have any older kernels, you may have to do a liitle more work to get back to your desktop. Select recovery mode from the boot menu, it will boot to a menu, select drop to root prompt, this will drop you to a command shell. Once at the prompt type:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

The above command will move the X configuration file to a back up, this should allow you to get to your desktop. Once you have run the above command, type:

```
exit
```

then select Resume from the menu. this should get you back to a working desktop.

---

### Post by crash2win64 on 2009-10-12
cariboo907 I did exactly as you said and nothing changed. I went to boot after entering in that command and it did the exact same thing it's been doing with no change whatsoever...
I'm at a loss here...

---

### Post by crash2win64 on 2009-10-12
Ok I got an idea here after looking on the disc running ubuntu off of that.
So if I go into the file system on my HD and delete the boot files and replace them with the ones from the live disc will that work? Should I back up the files I'll be deleting and replacing with the same thing just from the disc? Or will that even matter?

The other thing I was considering doing was upgrade to 9.10... Would this fix the problem I'm having you think then??? Just putting it out there.

---

### Post by LewRockwell on 2009-10-12
> **crash2win64 said:**
> Ok I got an idea here after looking on the disc running ubuntu off of that.
So if I go into the file system on my HD and delete the boot files and replace them with the ones from the live disc will that work? Should I back up the files I'll be deleting and replacing with the same thing just from the disc? Or will that even matter?

The other thing I was considering doing was upgrade to 9.10... Would this fix the problem I'm having you think then??? Just putting it out there.

a fresh install of either 9.04 or 9.10 will correct your problem because you'll be running a different kernel version...of course, if you use 9.04 again then the updates will probably give you a repeat failure

for example, a fresh install of 9.04 would start you off again with the Ubuntu 9.04 kernel 2.6.28-11-generic...as opposed to whatever you are trying to boot right now


Here is what your /boot/grub/menu.lst file might look similar to:```
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
default		2

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
# kopt=root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=390f1d61-678e-42a7-9850-2d2643652c20

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If you check in the /boot directory of your installed ubuntu you will probably see several kernels listed

One such listing might be "vmlinuz-2.6.28-15-generic"

If you see a previous kernel there...say "vmlinuz-2.6.28-14-generic" then you could boot into that previous kernel which probably was the last one you were using

Also, a couple of posts back you were asking about the "LiveCD" we were referring to...that is just the Ubuntu CD booted into the "test-drive function" of the CD which we call "LiveCD" function

.

---

