---
title: "Vista wont start"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Somiac on 2009-03-12
So a while back I fixed my GRUB Error with that reinstall GRUB onto the external HDD and reinstall the bootloader on to vista and all is good right?

Now I can boot windows without the harddrive plugged in which was the issue.

But now I have a new issue!

When I have the harddrive plugged in, it can't boot windows! It just comes with an error like cannot locate...eh yea basically grub doesn't see my internal hard drive? or something...

From what I saw when the external harddrive is plugged in, it's turned into

sda (0.0) hard drive and the internal is known as sdb (0.1) 

but GRUB tries loading the internal as sda (0.1) or something when the internal should be sda(0.0) and the external should be sdb...

or so I think,

---

### Post by philinux on 2009-03-12
Ok post the output of these.

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

Dont forget to wrap code tags around to make things easy to read.

---

### Post by fly-by-night on 2009-03-12
I might not understand you correctly, but could this not be a boot order in the CMOS issue.  
You might have the external HDD before the internal on the bootlist.  And the external have a outdated grub.

---

### Post by Somiac on 2009-03-12
Okay here are the results of it.

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
# kopt=root=UUID=d40eb5ac-5c07-4f39-afae-cc3146ac2a5e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d40eb5ac-5c07-4f39-afae-cc3146ac2a5e

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
uuid		d40eb5ac-5c07-4f39-afae-cc3146ac2a5e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d40eb5ac-5c07-4f39-afae-cc3146ac2a5e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d40eb5ac-5c07-4f39-afae-cc3146ac2a5e
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d40eb5ac-5c07-4f39-afae-cc3146ac2a5e ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d40eb5ac-5c07-4f39-afae-cc3146ac2a5e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d40eb5ac-5c07-4f39-afae-cc3146ac2a5e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d40eb5ac-5c07-4f39-afae-cc3146ac2a5e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d40eb5ac-5c07-4f39-afae-cc3146ac2a5e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d40eb5ac-5c07-4f39-afae-cc3146ac2a5e
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
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

and

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac8f771c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1015     8147968   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1015       17544   132773188    7  HPFS/NTFS
/dev/sda3           17545       19457    15366172+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1941f507

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris
```

---

### Post by philinux on 2009-03-12
Reboot, press esc at the grub menu and select the last windows boot option at the bottom of the list.

---

### Post by Somiac on 2009-03-12
Okay, I will try that but care to explain how you know or how to find out which one to use etc? :)

---

### Post by philinux on 2009-03-12
You've got 2 entries for Windows/Vista. Look a the last one. (hd0,1), and look at fstab.
Linux counts from zero so hd0 is the first disk also known as sda, partition sda2 has the * boot flag, in fstab, and therefore partition two is counted as 1. Hence hd0,1. hd0,0 is not where windows lives.


```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by Somiac on 2009-03-12
Alright that helps a lot, thanks :)

---

### Post by LowSky on 2009-03-12
Also depending on the BIOS boot order, your PC will pick which to see first, which can change the order of the hard drives, like fly-by-night said, so be careful this error might pop up agian if you mess withthe BIOS or Reinstall

---

### Post by theherk on 2009-03-12
I'm no expert, trust any of this at your own risk.

The drives are numbered in some order starting at zero. When you see hd(0,1), that means the second partition of the first disk(0 is actually 1 and 1 is 2).

I believe you need to load GRUB on both disks. Selecting which disk boots first will determine which GRUB is called. The GRUB on the windows side should not make reference to the other drive, as that will generate an error about the drive not being found.

The only option should be to load Windows on the hd(0,1) GRUB. It would seem that in this configuration you should have the linux disk set to boot first(when it is removed the next will boot with the other GRUB), but when it is in, the GRUB on hd(1,0) will give you both options.

I'm not sure if any of that is true.

---

### Post by philinux on 2009-03-12
> **theherk said:**
> I'm no expert, trust any of this at your own risk.

The drives are numbered in some order starting at zero. When you see hd(0,1), that means the second partition of the first disk(0 is actually 1 and 1 is 2).

I believe you need to load GRUB on both disks. Selecting which disk boots first will determine which GRUB is called. The GRUB on the windows side should not make reference to the other drive, as that will generate an error about the drive not being found.

The only option should be to load Windows on the hd(0,1) GRUB. It would seem that in this configuration you should have the linux disk set to boot first(when it is removed the next will boot with the other GRUB), but when it is in, the GRUB on hd(1,0) will give you both options.

I'm not sure if any of that is true.

Why post then.

---

