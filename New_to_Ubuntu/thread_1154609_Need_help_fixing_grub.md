---
title: "Need help fixing grub"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by ebeckhusen on 2009-05-09
I just installed Gos along side my Ubuntu 9.04.  When I did that, the installer overwrote my grub but did not include an entry for Ubuntu.  I formatted Ubuntu as Ext4, so Gos will not mount it.  Will I be able to restore grub by using the Ubuntu live CD, or will that remove the entry for Gos?

---

### Post by Didius Falco on 2009-05-09
You can restore Grub to your Ubuntu install and then add the info for Gos to your menu.lst and fstab files.

If you need directions on how to do that, just ask...


Regards,

Didius

---

### Post by ebeckhusen on 2009-05-10
> **Didius Falco said:**
> You can restore Grub to your Ubuntu install and then add the info for Gos to your menu.lst and fstab files.

If you need directions on how to do that, just ask...


Regards,

Didius

Okay, so how do I do that?  I'm assuming I have to use the Live CD?

---

### Post by superprash2003 on 2009-05-10
this is similar [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ebeckhusen on 2009-05-10
> **superprash2003 said:**
> this is similar [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks for that, but it was a bit over my head :(.  A great resource, though, and have bookmarked it for the future.

---

### Post by ebeckhusen on 2009-05-10
Okay, so what I did was try to edit menu.lst, but now it gives me a device not found error.  The output of my fdisk is:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           18603       19457     6867787+   7  HPFS/NTFS
/dev/sda3               1       18602   149420533+   5  Extended
/dev/sda5               1        9002    72308502   83  Linux
/dev/sda6   *        9003       18287    74581731   83  Linux
/dev/sda7           18288       18602     2530206   82  Linux swap / Solaris


```
With Ubuntu being on /dev/sda6 and Gos on sda5

My grub looks like this:

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
# kopt=root=UUID=00e5777c-6f00-4eaa-b395-32569464819d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash loglevel=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=00e5777c-6f00-4eaa-b395-32569464819d ro quiet splash loglevel=0
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=00e5777c-6f00-4eaa-b395-32569464819d ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=00e5777c-6f00-4eaa-b395-32569464819d ro quiet splash loglevel=0
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=00e5777c-6f00-4eaa-b395-32569464819d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title Ubuntu 9.04
root (hd0,5)
savedefault
makeactive 
chainloader +1

```

I know I should have a kernel line in there, but didn't know what to put as I can't access the partition at all (Gos can't access Ext4 filesystems).  Am I on the right track, and can someone walk me through the rest of this?

---

### Post by caljohnsmith on 2009-05-10
How about doing the following from your 9.04 Live CD:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0,5)
grub> quit
```
Then use the following entry for 9.04 in your Gos menu.lst:
```
title Ubuntu 9.04
root (hd0,5)
chainloader +1
```
Note it is imperative not to use "makeactive" in the above entry, unlike your current 9.04 Grub entry, because Grub can't make a logical partition active, i.e. set the boot flag on that partition; you will get a Grub error if you try. Anyway, how about giving the above a shot and let me know how it goes or if you run into problems.

John

---

### Post by ebeckhusen on 2009-05-10
Thank you, thank you, thank you.  That worked perfectly!  Will need to remember that in case of future emergency.

---

### Post by caljohnsmith on 2009-05-10
You're welcome, I'm glad that worked OK. Cheers and have fun with Ubuntu. :)

John

---

