---
title: "Need help editing a menu.lst file"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-26
A friend of mine has a laptop and he wants Windows to be the default option at the top of the grub menu.  Here's the relevant part of his menu.lst file:

```
title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```

Would the following modification do the trick?

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1



```

---

### Post by Warren Watts on 2009-01-26
yes.  :)

---

### Post by diablo75 on 2009-01-26
> **Warren Watts said:**
> yes.  :)

Awesome.

---

### Post by igknighted on 2009-01-26
That might confuse dpkg when you get a kernel upgrade.  I would find the line that says "default 0" and change the 0 to correspond with the line for Windows.  In the case of your original, it would be "default 13"

---

### Post by mcduck on 2009-01-26
Actually the next kernel update would wipe the Window entry completely from the list..

If you want to move Windows (or any other additional entry) to the top of the list, make sure that you keep is outside of the area marked as "Automagick kernels list". That section is always re-created during kernel updates.

So, whatever you put in menu.lst keep it outside of this area:
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
.
. default options & Ubuntu kernels here
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST

```

Moving the Windows entry immediately above the "begin automagick kernels list"-line works fine.

---

### Post by Rolcol on 2009-01-26
If you want a program with a GUI to edit that file, I suggest Startup-Manager.  I haven't dualbooted since last year so I don't know whether it will remove the windows option with an update.
```
sudo apt-get install startupmanager
```

---

### Post by RyanVanDiemen on 2009-01-26
whatever happened to qgrubeditor, I didn`t find them in the repositories after 8.10 installation. it broke my heart and now I rather edit menu.lst myself...

---

### Post by louieb on 2009-01-26
easy does it. find the lines that read :
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

```and move the windows entry there, when your done it should look sonething like this.
```

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1
### BEGIN AUTOMAGIC KERNELS LIST

```opps see **mcduck** beat me:p

---

### Post by diablo75 on 2009-01-26
Okay, here's his entire menu.lst file:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```

I would want to do this?? (below):

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

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
# kopt=root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=d38744f2-b94c-484d-8318-a0553cb7a7c0 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Emergency Destructive Recovery Tool (Wipes HD/Reloads Original Software)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by stchman on 2009-01-26
I recommend installing StartUpManager to do those type of duties.

```

sudo apt-get install startupmanager

```

This will allow you which is the default OS.

When you get a kernel upgrade your top text will be wiped out and you will need to reinstall GRUB.  Editing menu.lst by hand is not recommended.

---

### Post by mcduck on 2009-01-26
> **diablo75 said:**
> Okay, here's his entire menu.lst file:
..

I would want to do this?? (below):
...

Yes, looks correct, and your Windows entry will stay even through kernel updates.

After that change Grub will boot to Windows MCE by default, if you don't want this then change the default boot option near the beginning of the menu.lst to "1" (which would be the first Ubuntu entry).

---

### Post by oldos2er on 2009-01-26
Qgrubeditor is now Kgrubeditor: [http://www.kde-apps.org/content/show.php/KGRUBEditor?content=75442](http://www.kde-apps.org/content/show.php/KGRUBEditor?content=75442)

---

### Post by LarZman on 2009-01-26
My Mythbuntu install will not properly load the boot menu from Grub. Mythbuntu will run fine from Grub 1.5, but when I choose Windows XP (last entry in boot menu), it comes back with "NTLDR.exe not found". When I boot from a Super Grud Disc (only thing on a CD), Linux will not load, but Windows XP loads fine.

Anyone got any idedas? Booting Mythbuntu through Grub, the menu.1st file has nothing in it (blank!), which I think is part of the problem. 

A little histoty from a Linux noob: I installed and had operating both O/S's working from Grub. I then moved a drive (and reformatted & reinstalled) to accommodate a larger one. I then reinstalled Mythbuntu to a completely clean drive.... then the problems started. I'm thinking it's the Grub loader and locations of the new files, but I don't want to further hose my htpc, as XP will still run very well and output to a plasma display (TV).

Any suggestions would be appreciated, but plese, keep them simple as I'm  not fluent in Linux... yet :-)

---

### Post by Vantrax on 2009-01-26
> **LarZman said:**
> My Mythbuntu install will not properly load the boot menu from Grub. Mythbuntu will run fine from Grub 1.5, but when I choose Windows XP (last entry in boot menu), it comes back with "NTLDR.exe not found". When I boot from a Super Grud Disc (only thing on a CD), Linux will not load, but Windows XP loads fine.

Anyone got any idedas? Booting Mythbuntu through Grub, the menu.1st file has nothing in it (blank!), which I think is part of the problem. 

A little histoty from a Linux noob: I installed and had operating both O/S's working from Grub. I then moved a drive (and reformatted & reinstalled) to accommodate a larger one. I then reinstalled Mythbuntu to a completely clean drive.... then the problems started. I'm thinking it's the Grub loader and locations of the new files, but I don't want to further hose my htpc, as XP will still run very well and output to a plasma display (TV).

Any suggestions would be appreciated, but plese, keep them simple as I'm  not fluent in Linux... yet :-)

I would suggest you make a new thread, new problem = new thread.

Adding it into this one will likely just make things more confusing.

---

### Post by RyanVanDiemen on 2009-01-27
> **oldos2er said:**
> Qgrubeditor is now Kgrubeditor: [http://www.kde-apps.org/content/show.php/KGRUBEditor?content=75442](http://www.kde-apps.org/content/show.php/KGRUBEditor?content=75442)

Kgrubeditor used to be the editor for KDE, however, I installed Kgrubeditor last week, but it just didn`t do anything when I tried to run it (I`m using gnome). 
Anyway, startupmanager is pretty good too as far as I can remember since you can do much more with it, not only editing GRUB preferences...

---

### Post by oldos2er on 2009-01-27
I have Kgrubeditor installed on Gnome and it works fine. I find it much more useful than Startupmanager.

---

