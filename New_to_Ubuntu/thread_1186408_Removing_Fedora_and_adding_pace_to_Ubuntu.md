---
title: "Removing Fedora and adding pace to Ubuntu"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by DamienEros on 2009-06-13
I am Currently Triple  booting windows xp Fedora and Ubuntu, my grub menu is as follows:

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
timeout        120

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
# kopt=root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df207e6c-2acc-4e4f-8106-da9db8167a0f

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
uuid        df207e6c-2acc-4e4f-8106-da9db8167a0f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        df207e6c-2acc-4e4f-8106-da9db8167a0f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=df207e6c-2acc-4e4f-8106-da9db8167a0f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        df207e6c-2acc-4e4f-8106-da9db8167a0f
kernel        /boot/memtest86+.bin
quiet

title Fedora (2.6.27.5-117.fc10.i686)
    root (hd1,1)
    kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=5a23ec7b-b0c2-4720-93b7-a92fdb52465d rhgb quiet
    initrd /initrd-2.6.27.5-117.fc10.i686.img


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```How would I proceed to remove Fedora and adding the space gained from that into Ubuntu? My apologies if this answer might be posted somewhere.

I forgot to mention I have two Hardrives. The first is a TeraByte the other is a 250G.
Fedora Windows and Ubuntu are all in the Terabyte and the Boot partition is in the 250G

The harddrive partitions [http://i677.photobucket.com/albums/vv135/DamienEros/1.png](http://i677.photobucket.com/albums/vv135/DamienEros/1.png)
[http://i677.photobucket.com/albums/vv135/DamienEros/2.png](http://i677.photobucket.com/albums/vv135/DamienEros/2.png)

---

### Post by TeoBigusGeekus on 2009-06-13
System -> Administration -> Partition Editor.
Delete your Fedora partition, format it and then add it to Ubuntu or XP.
Then 
```
sudo gedit /boot/grub/menu.lst
```
and delete the Fedora option.

---

### Post by DamienEros on 2009-06-13
I deleted the Fedora partition but the option to resize the Ubuntu partition is greyed out, How do I add the unallocated space to Ubuntu
[http://i677.photobucket.com/albums/vv135/DamienEros/Screenshot.png](http://i677.photobucket.com/albums/vv135/DamienEros/Screenshot.png)

---

### Post by TeoBigusGeekus on 2009-06-13
Oh right, sorry, my fault: you can't perform any changes on your Ubuntu partition while using it (it makes sense, doesn't it?).
You must boot with a live cd in order to do so.

---

### Post by DamienEros on 2009-06-13
I also tried with live cd, I can only shrink the ubuntu partition, it doesn't allow me to grow it even though i Have 130G of free partitioned space

---

### Post by TeoBigusGeekus on 2009-06-13
Are you sure?
Perhaps you need to move the free space before of after Ubuntu to do this.
Play a bit and you'll find the solution.

---

### Post by DamienEros on 2009-06-13
While eating a chicken patty it suddenly came to me and i finally managed to get it to work.
What had me confused and stuck was I was trying to resize the ext3 which it wouldn't allow me to do.
What i realized as I enjoyed my chicken patty was that I needed memory inside of that blue frame( what the ext3 and swap were part of that was dubbed extended) So i resized extended then moved the freespace after the ext3. Only then was i able to resize the ext3 to what i wanted it to be.

---

