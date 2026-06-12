---
title: "edited /boot/grub/menu.lst  but enters memtest by default"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by mrprajesh on 2009-04-05
i have edited /boot/grub/menu.lst  ... thought i have not  changed the default num ...it loads into memtest rather  than ubuntu...
now i can not boot into ubuntu

the prime reason for editing that file was to make my grub menu appear simple !
so i commented  somthing similar to this ..

#title Ubuntu 8.04, kernel 2.6.22-14-generic
title Hardy
..
#title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
..
#title Ubuntu 8.04, memtest86+
..
#title Windows Vista/Longhorn (loader)
title vista


is it possible edit menu.lst through grub > ?
else help me with any other solution ??

---

### Post by kansasnoob on 2009-04-05
Well the simplest way is to use startupmanager which is in Synaptic or you can install by going to terminal and:

```
sudo apt-get install startupmanager
```

But I fear you already hosed your menu list so post the full output of:

```
cat /boot/grub/menu.lst
```

---

### Post by mrprajesh on 2009-04-05
i can not log on to ubuntu now !

grub > cat /boot/grub/menu.lst

i can see the output but how to copy from there to vista ( i am using vista  to talk to u )

---

### Post by mrprajesh on 2009-04-05
i think (may b wrong) problem could be i havent commented the lines other than title 

#title Ubuntu 8.04, memtest86+
..
#title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
..
..

is this causing the problems ?

so i thought of commenting these line wen grub is loading ( press 'e' twice)
i have commented but i don't know how to save it !! (as it boots to memtest again )

---

### Post by kansasnoob on 2009-04-05
OK! Do you still get the GRUB menu? If so try to choose "recovery mode", which after it runs will present you with a few options.

One of those will be "drop to root shell prompt", then you can type:

```
cat /boot/grub/menu.lst
```

BTW that's a lower case L.

---

### Post by pbpersson on 2009-04-05
> **mrprajesh said:**
> 

i can see the output but how to copy from there to vista ( i am using vista  to talk to u )

You could boot from a Live CD, mount the drive, get the output from the cat command, and then send it to us using Firefox on the Live CD

---

### Post by mrprajesh on 2009-04-05
as i told earler that i hav edited that file

i see only two things i.e
```

Hardy
other OS:
vista 
```

if i choose Hardy it enters to memtest

---

### Post by pbpersson on 2009-04-05
> **mrprajesh said:**
> as i told earler that i hav edited that file

i see only two things i.e
```

Hardy
other OS:
vista 
```

if i choose Hardy it enters to memtest

we would need to see the file.  The entries which control what is loaded would look something like:

```
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9946bed1-6674-4c2f-95e5-ff2a6d1a019a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
```

furthermore, you  cannot just comment out the titles!  Each section is a section.  You comment out the title AND the lines after it that are also in that section.

---

### Post by mrprajesh on 2009-04-05
very very sorry for being late.. (Firefox hanged while replying ! this happens often. even now i m replying u from vista ) 
i hav solved this prob !
i hav edited menu.lst after booting from live cd to make it look like default ! (using su not sudo)
```
#gedit /media/disk-1/boot/grub/menu.lst 
``` 
(some thing similar to one above)
now my system is OK !
thanx all for ur suggestions!

---

### Post by mrprajesh on 2009-04-05
any way i respect u all 
here is my menu.lst

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
# kopt=root=UUID=aca518d3-d015-42f5-8440-bb50291d14c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,10)

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

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
title		Hardy Heron  (Ubuntu v8.04)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aca518d3-d015-42f5-8440-bb50291d14c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=aca518d3-d015-42f5-8440-bb50291d14c9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, memtest86+
root		(hd0,10)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other OS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows Vista/Longhorn (loader)
title		Longhorn
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

