---
title: "Windows gone from boot loader"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-08-25
I just updated today to latest software via update mgr and the boot manager (GRUB) does not list Windows Vista in the boot list.

It now says at the end of available kernels and OS: Other Operating Systems - and when I choose that option another screen comes up with:
 
Error 11: unrecognized device string
Press any key to continue...

After which I go back to the list of versions of Ubuntu (I'm using 2.6.28-15 generic kernel)

How do I edit the list to make windows an option again? 

Here is my set up: Two HD, primary with Windows Vista and secondary (/dev/sdb1) with Ubuntu Jaunty 9.04 

Sorry for the bother, Thanks for the help! :KS

---

### Post by eagle416 on 2009-08-25
you could reinstall grub, or look at a backup (if you have one) of menu.lst. Give it a shot.

-EDIT-

see if you can find the location of your windows partition. from your description, it might be at hd0,1. If you think you know its location, copy and paste this into your menu.lst, editing the "root" value to whatever the location is:

title		Windows Vista
root		(hd0,1)
makeactive
chainloader	+1

Reboot. select windows vista and try booting it. If it works, great. If not, choose windows vista on the grub menu, and hit "e" until you can edit the "hd0,1 bit". Try all combinations (hd0,1    hd0,2,  hd0,3    hd1,1   hd1,2 .....etc) and try booting with each one until it works. If it boots, remember the combination and put that into menu.lst under the root  (hd*,*). It sounds crazy, but this is how I saved my computer once.

---

### Post by kansasnoob on 2009-08-25
It would be very helpful to see the full output of the following two commands:

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

Errm, make that three:

```
cat /boot/grub/menu.lst.backup
```

Please paste the outputs using the Quote tags.

---

### Post by mayagrafix on 2009-08-25
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1311       30394   233612288    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971c6f2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4844    38909398+  83  Linux
/dev/sdb2           18706       19457     6040440    5  Extended
/dev/sdb3            4845       18705   111338482+   7  HPFS/NTFS
/dev/sdb5           18706       19457     6040408+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdg: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005bbe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         789     6337611    7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(788, 254, 63)
doggo@Inspiron-530:~$
```

---

### Post by mayagrafix on 2009-08-25
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
# kopt=root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad9b8dab-718a-42b2-9fac-a93abb19838c

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
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
# this one dont work
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


```

---

### Post by mayagrafix on 2009-08-25
cat: /boot/grub/menu.lst.backup: No such file or directory

---

### Post by kansasnoob on 2009-08-25
> **mayagrafix said:**
> cat: /boot/grub/menu.lst.backup: No such file or directory

Cool. Give me a while to digest this. I'd never, ever seen an sdg - I mean sda=drive #1, sdb=drive #2, abcdefg ................ I need time to digest!

I do see the boot mark on sdg!

Must. Think.

---

### Post by kansasnoob on 2009-08-25
OK, working on too many things at once.

Reading your original post, this resulted only due to an update/upgrade!

Do you have any external drives or media cards installed - anything like that - even a camera?

Or did you have during the updates? And then did you accept the "package maintainers version of grub"??????????

---

### Post by kansasnoob on 2009-08-25
> **mayagrafix said:**
> cat: /boot/grub/menu.lst.backup: No such file or directory

Also if you ran the command "cat**:** /boot/grub/menu.lst.backup" that one : hosed it, so lets do this the gui way:

Go to Places > Computer > Filesystem (double click) > boot folder (double click) > grub folder (double click) and look for anything beginning with menu.lst:

[ATTACH]126262[/ATTACH]

---

### Post by kansasnoob on 2009-08-25
Regardless lets clean up that long string of kernel updates by installing 'startupmanager':

```
sudo apt-get install startupmanager
```

You'll then see it in System > Administration. You can look at my previous screenshots here in post #8:

[http://ubuntuforums.org/showthread.php?t=1249178](http://ubuntuforums.org/showthread.php?t=1249178)

You'll see my recommended menu.lst changes in **bold** below:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
# this one dont work
**#**title		Windows Vista/Longhorn (loader)
**#**root		(hd0,1)
**#**savedefault
**#**makeactive
**#**chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
**#**title		Windows (loader)
**#**root		(hd0,2)
**#**savedefault
**#**makeactive
**#**chainloader	+1

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn
root        (hd0,2)
savedefault
makeactive
map        (hd1) (hd0)
map        (hd0) (hd1)
chainloader    +1[/B]



You'll notice that I chose to comment out (with #) existing lines rather than destroying them.

I'm sure you know that you must edit using:

```
gksudo gedit /boot/grub/menu.lst
```

Remember to click on save!

I'd rather have restored the menu.lst that existed prior to the updates!

---

### Post by mayagrafix on 2009-08-25
Thanks for showing me the way :KS

I edited the menu.lst file as per your advice and now I can has windows on start up. 

yes there is a external USB HD I use for file transfers hooked up. Not a good idea to have when upgrading Ubuntu?

Again, thanks for your help.

---

### Post by kansasnoob on 2009-08-25
> **mayagrafix said:**
> Thanks for showing me the way :KS

I edited the menu.lst file as per your advice and now I can has windows on start up. 

yes there is a external USB HD I use for file transfers hooked up. Not a good idea to have when upgrading Ubuntu?

Again, thanks for your help.

From now on click on "unmount" so that drive doesn't mess with you during an upgrade, that's assuming you get a desktop icon indicating that drive.

If not you may want to try installing 'pmount' from synaptic. It's pretty nifty at dealing with drives that aren't automatically added in fstab.

---

