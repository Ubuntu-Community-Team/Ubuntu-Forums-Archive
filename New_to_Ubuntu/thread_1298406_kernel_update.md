---
title: "kernel update"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by wobin77 on 2009-10-22
After kernel update today, ubuntu won't start with new kernel (grub) however it does boot with previous one. 

? 

:-)

---

### Post by wojox on 2009-10-22
What kernel update ? I did not get one. Huh...

Try:

```
sudo update-grub
```

---

### Post by drs305 on 2009-10-22
> **wobin77 said:**
> After kernel update today, ubuntu won't start with new kernel (grub) however it does boot with previous one. 

? 

:-)

Do you know what your menu.lst or grub.cfg file settings are? It's possible your system is set to boot the last one used or a specific kernel.  I recommend StartUp-Manager - a GUI app for tweaking grub's menu.lst. It can let you pick which kernel you want to use, if that is the problem.

Click on the SUM link in my signature line for installation and setup. It's easy!

Or do you mean you can click on it and it fails? If so, what error messages do you get or what specifically happens.

---

### Post by wobin77 on 2009-10-22
thanks for quick replies. How can i show what comes up to grub on startup? 

I can choose from three different kernels, (after update, normally it's two) the second one works fine, but the third one (the new one) fails to boot.

---

### Post by ranch hand on 2009-10-22
Boot to the one that will work and post your /boot/grub/menu.lst (assuming you are using grub-legacy).

---

### Post by wobin77 on 2009-10-23
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        de51ab1c-08b2-4ed6-bdf3-5337ba1d59a1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

---

### Post by ranch hand on 2009-10-23
That looks like you should be booting to the new kernal.

Post out put of 
```

uname -a

```
Just cut and paste to terminal.

---

### Post by wobin77 on 2009-10-23
yes indeed, just booted into the new kernel. Last night it would just hang upon booting 2.6.28-16.
```
Linux wobin-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

```. 

Strange... but now i don't have any sound in firefox with flash. (youtube, ...)

---

### Post by wobin77 on 2009-10-23
When booting 2.6.28-15 this issue is solved... 
```
Linux wobin-desktop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

```

---

### Post by ranch hand on 2009-10-23
Hmm, I am on a 9.10 install right now.  I will have to try that when I get back to 9.04.

You should, if needed, start a new thread for that and got to the top of the page here
and under "thread tools" mark this as solved.

This will save folks time if they want to help and will let folks with a similar problem know it is solvable

---

### Post by wobin77 on 2009-10-23
Ok, will do so. Thanks!

---

### Post by SaRJe on 2009-10-29
I found a thread pointing to a GUI interfaced application that TOTALLY solved my GRUB problem AND MORE.  Look at [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

It's called Start-Up Manager.

Just search for startupmanager in the Synaptec Package Manager.

The aforementioned thread goes into detail about how to use this wonderful resource.

---

