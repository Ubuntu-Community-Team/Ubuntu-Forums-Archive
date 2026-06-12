---
title: "Grub error - need help"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-07-20
Ive been running ubuntu quite happily for some time, i have a usb stick that i decided to put ubuntu on, instead of creating it as a live disk i decided to do a full install onto usb so i could do more with it. I ran a live cd and formatted the usb as fat32. Clicked on the install icon on the desktop and ran through the install as you would but changed the destination to /dev/sdb (the usb drive) All works okay on the usb, i can boot from it and do anything i would with a normal install, but now loading from my normal hard driive i get grub error 21. I dont know whats changed because i didnt think it would alter the HDD grub entry. Please help as i dont know how to deal with grub loaders and all google brings up is results about dual boots, which i dont have.

---

### Post by CaptainMark on 2009-07-20
I think the grub on my HDD is saying to boot from the USB because if i set my mobo to boot from my HDD it will boot the USB if it is plugged in. After a bit more googling i found its commonly to do with the menu.lst so here is the menu.lst from the filesystem when running usb ```
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
# kopt=root=UUID=072a3af4-cf51-4ffc-8441-bedb4794d521 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=072a3af4-cf51-4ffc-8441-bedb4794d521

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        072a3af4-cf51-4ffc-8441-bedb4794d521
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=072a3af4-cf51-4ffc-8441-bedb4794d521 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        072a3af4-cf51-4ffc-8441-bedb4794d521
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=072a3af4-cf51-4ffc-8441-bedb4794d521 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        072a3af4-cf51-4ffc-8441-bedb4794d521
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro single 
initrd        /boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot

```and here is the menu.lst from the HDD i retrieved by mounting it manually ```
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
timeout        3

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
# kopt=root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=757e303a-9af3-4ade-8fe4-5b50df0e3cea

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cea ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```And finally here is the output from sudo fdisk -l ```
mark@mark-usbboot:~$ sudo fdisk -l
[sudo] password for mark: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4d78be6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59578   478560253+  83  Linux
/dev/sda2           59579       60801     9823747+   5  Extended
/dev/sda5           59579       60801     9823716   82  Linux swap / Solaris

Disk /dev/sdb: 4059 MB, 4059561984 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000898b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         465     3735081   83  Linux
/dev/sdb2             466         493      224910    5  Extended
/dev/sdb5             466         493      224878+  82  Linux swap / Solaris
mark@mark-usbboot:~$ 

``` As you can see my HDD is still mounted as /dev/sda and my usb /dev/sdb
Please help, i just dont know what to do

---

### Post by CaptainMark on 2009-07-20
Okay nobody panic i googled "ubuntu repair grub" and got some helpful pages, i needn't  have posted really but i panicked, thought id ruined my rig.

---

