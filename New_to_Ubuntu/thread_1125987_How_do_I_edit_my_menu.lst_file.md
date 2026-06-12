---
title: "How do I edit my menu.lst file?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by nitroguy on 2009-04-14
So, I'm supposed to add iommu=noaperature to my /boot/grub/menu.list file (per [http://rubbad.wordpress.com/2008/11/28/ubuntu-810-iommu/](http://rubbad.wordpress.com/2008/11/28/ubuntu-810-iommu/)), but i don't know what that means. I get to my menu.list file, and this is what I see.

Where do I type this in?```
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
# kopt=root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5487bd55-be16-46a4-a978-03c7e08b5003

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
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

---

### Post by llamabr on 2009-04-14
sudo nano /boot/grub/menu.list

---

### Post by jbrown96 on 2009-04-14
> **nitroguy said:**
> So, I'm supposed to add iommu=noaperature to my /boot/grub/menu.list file (per [http://rubbad.wordpress.com/2008/11/28/ubuntu-810-iommu/](http://rubbad.wordpress.com/2008/11/28/ubuntu-810-iommu/)), but i don't know what that means. I get to my menu.list file, and this is what I see.

Where do I type this in?```
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
# kopt=root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5487bd55-be16-46a4-a978-03c7e08b5003

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
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

You will probably want to use gedit, so open the file by pressing Alt+F2 then type ```
gksu gedit /boot/grub/menu.lst
``` Then go down near the bottom. You will see a bunch of entries like > title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5487bd55-be16-46a4-a978-03c7e08b5003
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet You need to add the option to the end of the "kernel" line after "splash". Add this for the newest kernel and probably the rescue kernel as well (entry directly below it). Then save and exit.

---

### Post by _Purple_ on 2009-04-14
You have to add it on the same line as ```
# kopt=root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro

```

---

### Post by juancarlospaco on 2009-04-15
***Keep a Backuuuuuuuuuuuuuuuuuuuuuuuuup...***

---

### Post by jbrown96 on 2009-04-15
> **juancarlospaco said:**
> ***Keep a Backuuuuuuuuuuuuuuuuuuuuuuuuup...***
Very good advice. You can make a backup by running ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` Then if something bad happens, you can restore the original by running the previous command but switch the order of the two files.

---

### Post by freak42 on 2009-04-15
As purple pointed out you should add it like this:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5487bd55-be16-46a4-a978-03c7e08b5003 ro **iommu=noaperature**

then you issue the 'sudo update-grub' command.
that way 'iommu=noaperature' will be added to every new kernel automatically, because if you follow jbrown's advice (about editing not about making backups), after a kernel update your additions to the line will be gone.

hth

---

