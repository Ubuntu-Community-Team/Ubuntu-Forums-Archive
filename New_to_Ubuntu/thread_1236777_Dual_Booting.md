---
title: "Dual Booting"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Gregz on 2009-08-10
ok I have a question then, I now have ubuntu on one hard drive and windows on another. I'm switching cables between the two now.

Is there and easy way to dual boot both?

Since they are on there own hard drives do I have to reinstall anything??

Thank you in advance.
Greg

---

### Post by LowSky on 2009-08-10
when you installed if you had Ubunt as the primary drive and windows as the slave or secondary, you could have installed GRUB (which would have installed by default) to handle the choices.
you can set it up afterwards very easily, make sure both drives are connected, with windows being the slave or secondary to the primary hard drive

use this command

```
 sudo gedit /boot/grub/menu.lst
```
 then posit it here, i or someone else can help add windows to the grub menu

---

### Post by kansasnoob on 2009-08-10
Honestly need to begin with hardware info: are both drives IDE or SATA or a combination of the two?

Second step: which drive is BIOS set to boot first?

IMHO this is the ultimate dual booting guide;

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Gregz on 2009-08-10
The bios will boot either. The way I do it now is to power down computer switch cables(IDE) then reboot. only one hard drive runs at once. I am getting sick of having to shut down to get in my case unhook rehook  ect ect . I use both so trying to make it easier  lol

---

### Post by Gregz on 2009-08-11
LowSky

Here it is:

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
#sudo gedit /boot/grub/menu.lst

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
# kopt=root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=32b0b915-6cda-4e9f-969e-165b73bf6678

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

title		Ubuntu 9.04, kernel 2.6.28-14-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.28-14-server

title		Ubuntu 9.04, kernel 2.6.28-13-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.28-13-server

title		Ubuntu 9.04, kernel 2.6.28-11-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.28-11-server

title		Ubuntu 9.04, kernel 2.6.27-14-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-server
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.27-14-server

title		Ubuntu 9.04, memtest86+
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Gregz on 2009-08-11
anyone ???

---

### Post by LewRockwell on 2009-08-11
> **Gregz said:**
> anyone ???

Please cut and paste into the code box in the future(especially long pastes)

To observe how this is done just attempt to quote this post

```
to see how we put stuff...pages and pages even...into a little box

Here it is:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#sudo gedit /boot/grub/menu.lst

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=32b0b915-6cda-4e9f-969e-165b73bf6678

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-14-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-server
quiet

title Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.28-14-server

title Ubuntu 9.04, kernel 2.6.28-13-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-server
quiet

title Ubuntu 9.04, kernel 2.6.28-13-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.28-13-server

title Ubuntu 9.04, kernel 2.6.28-11-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-server
quiet

title Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.28-11-server

title Ubuntu 9.04, kernel 2.6.27-14-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.27-14-server
quiet

title Ubuntu 9.04, kernel 2.6.27-14-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.27-14-server

title Ubuntu 9.04, memtest86+
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
__________________
AMD Athlon 1.8, ASUS Motherboard A7N8X-E, Nvidia NX7600GS Video Card. 2 Gig DDR Ram,Seagate 100 Gig HD 


```

there...

cool, huh!

.

---

### Post by LewRockwell on 2009-08-11
not really sure where you're at with your project...

you'll need to establish your hardware set-up with a master and slave designation for your drives

then adjust your menu.lst file appropriately

SuperGrubDisk can help and sometimes even correct problems automatically if you choose to make those selections while utilizing the SuperGrub

.

---

### Post by Gregz on 2009-08-11
> **LewRockwell said:**
> Please cut and paste into the code box in the future(especially long pastes)

To observe how this is done just attempt to quote this post

```
to see how we put stuff...pages and pages even...into a little box

Here it is:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#sudo gedit /boot/grub/menu.lst

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=32b0b915-6cda-4e9f-969e-165b73bf6678

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-14-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-server
quiet

title Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.28-14-server

title Ubuntu 9.04, kernel 2.6.28-13-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-server
quiet

title Ubuntu 9.04, kernel 2.6.28-13-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.28-13-server

title Ubuntu 9.04, kernel 2.6.28-11-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-server
quiet

title Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.28-11-server

title Ubuntu 9.04, kernel 2.6.27-14-server
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash
initrd /boot/initrd.img-2.6.27-14-server
quiet

title Ubuntu 9.04, kernel 2.6.27-14-server (recovery mode)
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro single
initrd /boot/initrd.img-2.6.27-14-server

title Ubuntu 9.04, memtest86+
uuid 32b0b915-6cda-4e9f-969e-165b73bf6678
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
__________________
AMD Athlon 1.8, ASUS Motherboard A7N8X-E, Nvidia NX7600GS Video Card. 2 Gig DDR Ram,Seagate 100 Gig HD 


```

there...

cool, huh!

.

ok sorry I wasn't thinking when posted, long day :P


Will this fix my problem   it's just a link.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6)

---

### Post by LewRockwell on 2009-08-11
> **Gregz said:**
> Will this fix my problem   it's just a link.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6)

I think if you read through that a time or two then that would give you a very good idea of the procedures commonly required to facilitate your desired outcome.

.

---

### Post by Gregz on 2009-08-11
ok sorry I wasn't thinking when posted, long day :P


Will this fix my problem. Can't find anything when both (os) are already installed on separate hard drives I also do not have a live cd.   it's just a link.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6)

---

### Post by kansasnoob on 2009-08-11
Well, if this is the right Motherboard,

[http://www.xbitlabs.com/articles/mainboards/display/asus-a7n8xe-deluxe.html](http://www.xbitlabs.com/articles/mainboards/display/asus-a7n8xe-deluxe.html)

you do appear to have two IDE/ATA headers to connect to. Of course I can't see what all else is connected; one or more IDE CD/DVD drives?

A quite typical factory set-up would have one IDE cable connected to the primary (aka: master) connector of the only hard drive and the secondary (aka: slave) connector attached to a CD/DVD ROM or RW drive.

In such a case I'd probably connect the second hard drive to the second IDE header. Of course two hard drives can also be connected to the same IDE cable, one as master and the other as slave.

I'm sure you can find a tutorial with some googling or the actual Users Manual for your model of MoBo.

Of course you must also know your hard drives. Most newer drives have three or more options that need to be set by a jumper or jumpers; basically Master, Slave, or Auto-Select. I personally never use auto-select!

As I say you must have some knowledge of hardware - remember static electricity can kill components as can any recklessness - so the hardware and BIOS are set correctly to begin with.

Then, and only then, you should be able to set the Ubuntu drive as Master and have it boot first, then with the Win drive installed as Slave (or connected to the secondary IDE header) Windows can be added to GRUB by chainloading:

[http://members.iinet.net.au/~herman546/p15.html#Windows_on_a_non-first_hard_disk](http://members.iinet.net.au/~herman546/p15.html#Windows_on_a_non-first_hard_disk)

---

### Post by Gregz on 2009-08-11
Thanks kansasnoob

I have Ubuntu as master and Vista as slave:lolflag:
I checked jumpers,also cable, good to go there. And yes thats the Motherboard.

---

### Post by Gregz on 2009-08-11
After copy and paste It will not boot vista. I changed where it had xp to vista. I did and fdisk results:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x250249da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf58df58d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488393795   244196866+   7  HPFS/NTFS
 

  

I take it as the the * spells trouble```
[CODE][CODE]
```[/CODE][/CODE]

---

### Post by kansasnoob on 2009-08-11
So you've done some editing to the menu list?

Please once again post it:

```
cat /boot/grub/menu.lst
```

BTW: the 'cat' command only allows viewing whereas the 'sudo gedit' or 'gksudo gedit' commands allow editing of the file.

---

### Post by kansasnoob on 2009-08-11
Oh, and:

> I take it as the the * spells trouble

No. That's no problem.

---

### Post by Gregz on 2009-08-11
```
james@Catfish:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=32b0b915-6cda-4e9f-969e-165b73bf6678

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

title		Ubuntu 9.04, kernel 2.6.28-14-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.28-14-server

title		Ubuntu 9.04, kernel 2.6.28-13-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-13-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.28-13-server

title		Ubuntu 9.04, kernel 2.6.28-11-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.28-11-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.28-11-server

title		Ubuntu 9.04, kernel 2.6.27-14-server
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-server
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-server (recovery mode)
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/vmlinuz-2.6.27-14-server root=UUID=32b0b915-6cda-4e9f-969e-165b73bf6678 ro  single
initrd		/boot/initrd.img-2.6.27-14-server

title		Ubuntu 9.04, memtest86+
uuid		32b0b915-6cda-4e9f-969e-165b73bf6678
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title              Windows vista
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

---

### Post by kansasnoob on 2009-08-11
Well that looks good to me except for a couple of things, shown in **bold** below:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[B]timeout		3
[/B]
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**hiddenmenu**


I would change the "timeout" to 10 (that's seconds) and "comment out" the hiddenmenu like this:

> #hiddenmenu

Adding a # is considered "commenting out" a line.

Or what I prefer is installing startupmanager:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

To accomplish the steps above you'd change the timeout to 10 and make sure the box is checked next to "Show Bootloader Menu".

Also you can cleanup that long list of kernels easily and safely by ticking on the Advanced tab and checking the box next to Limit number of kernels and selecting 2.

---

### Post by Gregz on 2009-08-11
Kansasnoob:

    Thank You,  

The start up manager worked great.  I would say resolved for this, except one small thing I noticed in grub boot menu it has 

ubuntu 9.04
ubuntu 9.04 recovery
ubuntu 9.04
ubuntu 9.04 recovery
windows vista

Why is ubuntu in there twice?? 

Again thank you 

                                 Greg

---

### Post by Bartender on 2009-08-11
The second Ubuntu entries are almost surely there because the kernel has updated since you first installed.  The previous kernels will remain on the machine, and available to you, unless you remove them.  Most people suggest keeping at least the previous kernel installed in case the newest one goes gunnysack.  You can then boot into the older kernel.

---

### Post by Gregz on 2009-08-11
Ahh  recovery for a recovery  :)

I like that.

---

### Post by kansasnoob on 2009-08-11
> **Gregz said:**
> Kansasnoob:
    Thank You the start up manager worked great.  I would say resolved for this except one small thing I noticed in grub boot menu it has 

ubuntu 9.04
ubuntu 9.04 recovery
ubuntu 9.04
ubuntu 9.04 recovery
windows vista

Why is ubuntu in there twice?? 

Again thank you 

                                 Greg

Because we chose to display 2 kernels under the advanced tab in Startupmanager. You could change it to 1, but every time you upgrade the kernel, which consists of:

linux-generic
linux-headers-generic
linux-image-generic
linux-libc-dev
linux-restricted-modules-common
linux-restricted-modules-generic

You take some risk (greater with some hardware than others) of breakage, especially with graphics drivers, wireless, etc. so it's recommended to always keep 2 kernels. That way if a kernel upgrade fails to boot you can always boot into the previous kernel until you both find a fix and have time to fool with it.

Personally, since I multi-boot four operating systems, I do keep only 1 kernel for each showing and then if I'm upgrading the kernel I change the value to 2 until I'm sure the new kernel boots OK.

---

### Post by Gregz on 2009-08-11
Let me see if I understand you correctly, 

I can have one then switch it back to two for updates? 

So the Kernels are still there it is just not reading them ?

---

### Post by kansasnoob on 2009-08-11
Correct.

I have a dumb question, why the "server" version of Ubuntu???

Inquiring minds and all that stuff:)

---

### Post by Gregz on 2009-08-11
To be honest for me to play with and working on hosting some websites.

Right now I'm playing around with joomla.  Don't know all of what it can do or what I want really.

---

### Post by Bartender on 2009-08-11
> **Gregz said:**
> I can have one then switch it back to two for updates?

Well, I'm not sure of your meaning, but the previous kernel just sits there unused.  You wouldn't bother to go back and update it.  New updates will install to the new kernel.  You keep the previous one just in case of emergency.

---

### Post by kansasnoob on 2009-08-11
> **Gregz said:**
> To be honest for me to play with and working on hosting some websites.

Right now I'm playing around with joomla.  Don't know all of what it can do or what I want really.

Cool, I was just curious.

---

### Post by Gregz on 2009-08-11
Thank you Bartender

---

