---
title: "Grub error 15"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by stans on 2009-02-15
I am encountering Grub error 15 at boot time - every entry in the forum suggests booting from the live cd, bringing up grub, and doing a find on /boot/grub/stage1. 

Well - that just gives me 'error 15: file not found'.

Sure hope this doesn't mean my hard drive is defective.

I'd appreciate advice -

---

### Post by extraspecialbitter on 2009-02-15
> **stans said:**
> I am encountering Grub error 15 at boot time - every entry in the forum suggests booting from the live cd, bringing up grub, and doing a find on /boot/grub/stage1. 

Well - that just gives me 'error 15: file not found'.

Sure hope this doesn't mean my hard drive is defective.

I'd appreciate advice -

The good news is that you probably don't have a defective hard drive.

Error 15 means that grub can't find your menu.lst file, which often happens when a second Linux distribution has been installed on a different partition.  It might help to know 1) what hardware you are using, 2) your disk configuration, and 3) whether or not you have more than one operating system on your PC.

Is the "find" command giving you a second error 15, or is your attempt to boot from CD causing the issue?  If the latter (boot from CD), then you might need to interrupt the boot process (usually a function key) to tell your BIOS to boot from CD instead of your hard drive.  If it's the find command giving you the error, then you will probably need to reinstall grub using the /usr/sbin/grub-install command.

---

### Post by stans on 2009-02-15
Thanks for the quick reply. The error 15 is showing up at boot time from the hard drive, then it is also showing up as a result of issuing the FIND command after booting up from the install CD. 

I only have Ubuntu on the system, no partitions with other operating systems.

OK - tried the /usr/sbin/grub-install and I guess there is some more learning I need to do. How do I know where to install it ?

---

### Post by kansasnoob on 2009-02-15
Boot the live CD and run in terminal:

```
sudo fdisk -l
```

Or, even better, post a screenshot of gparted!

---

### Post by kansasnoob on 2009-02-15
Oh, and what led up to this?

---

### Post by stans on 2009-02-15
Format of install device not recognized. 

I did the fdisk - and /dev/sdb1 was returned in the display. 

I issued 

/usr/sbin/grub-install /dev/sdb1

Nothing of any significance whatsoever led up to this. Had a great several hour session in the morning, shut it down to do some household repairs... then few hours later this grub error.

---

### Post by caljohnsmith on 2009-02-15
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Live CD Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by stans on 2009-02-15
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00005028

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   573,922,124   573,922,062  83 Linux
/dev/sda2         573,922,125   586,067,264    12,145,140   5 Extended
/dev/sda5         573,922,188   586,067,264    12,145,077  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00005028

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,854,319   149,854,257  83 Linux
/dev/sdb2         149,854,320   156,248,189     6,393,870   5 Extended
/dev/sdb5         149,854,383   156,248,189     6,393,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="910440c5-7bd2-48e5-a885-85cf80f50c8b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="8a462438-77e4-4138-86f1-3810c73931f2" TYPE="swap" 
/dev/sdb1: UUID="92ffad00-edf4-41ae-8784-dcc07dfedac4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8a462438-77e4-4138-86f1-3810c73931f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 198.8GB: boot/grub/menu.lst
 198.8GB: boot/grub/stage2
 198.8GB: boot/initrd.img-2.6.24-19-generic
 198.8GB: boot/initrd.img-2.6.24-19-generic.bak
 198.8GB: boot/initrd.img-2.6.24-21-generic
 198.8GB: boot/initrd.img-2.6.24-21-generic.bak
 198.7GB: boot/initrd.img-2.6.24-22-generic
 198.8GB: boot/initrd.img-2.6.24-22-generic.bak
 198.9GB: boot/initrd.img-2.6.24-23-generic
 198.8GB: boot/initrd.img-2.6.24-23-generic.bak
 198.8GB: boot/vmlinuz-2.6.24-19-generic
 198.8GB: boot/vmlinuz-2.6.24-21-generic
 198.9GB: boot/vmlinuz-2.6.24-22-generic
 198.7GB: boot/vmlinuz-2.6.24-23-generic
 198.9GB: initrd.img
 198.7GB: initrd.img.old
 198.7GB: vmlinuz
 198.9GB: vmlinuz.old


```

---

### Post by caljohnsmith on 2009-02-16
You have Grub installed to the MBR of both your sda and sdb drives, but it looks like only your 300 GB sda drive is correctly configured to boot. Booting the sdb drive would give you exactly what you got, i.e. a Grub error 15. Did you try to install Ubuntu to your sdb drive too? I'm wondering because your sdb drive has all the necessary partitions set up, but there is no OS on that drive. The Ubuntu on your sda drive looks like it is all ready to boot though, so if you can go into your BIOS and change the boot order so your sda drive boots before the sdb drive, I think that will solve your problem. Let me know how that goes.

---

### Post by stans on 2009-02-16
I do appreciate your assistance. I see your replies to other folks... 

The clone is about two years old and came with the 80g drive. I originally installed Ubuntu on it, then added the 300g drive quite some time back.

Not sure how the boot order could have changed... I did look at it (Asus motherboard) and will look at it again based on your advice cause I couldn't really determine 'boot order' per se - unless it is indicated by the order displayed - and sba is first in the display.

---

### Post by caljohnsmith on 2009-02-16
> **stans said:**
> 
Not sure how the boot order could have changed... I did look at it (Asus motherboard) and will look at it again based on your advice cause I couldn't really determine 'boot order' per se - unless it is indicated by the order displayed - and sba is first in the display.
The boot order is set up in your BIOS, you shouldn't have to change anything physically on your motherboard (at least not at this point). To get into your BIOS, you have to press some special key on start up, usually a function key like F10, F12, etc. Sometimes the BIOS splash screen that comes up when you first turn on some computers will tell you which key to press.

---

### Post by stans on 2009-02-16
Yes, I know.. the DEL key right at bootup. I was looking at it yesterday... 

Will have to wait till this evening when I get home. Not sure how it could have changed. 

Thanks again for your support.

---

### Post by stans on 2009-02-16
Well I will be darned ! The boot sequence of the two drives were reversed - and once I corrected that, I was able to get by my grub error 15 !

How the heck does that happen ? A bug in the bios ?

I must thank you again very much - it's people like you that make this forum what it is...

---

### Post by caljohnsmith on 2009-02-16
That's great news, glad to hear you can boot OK now. I don't know how your drives got reversed in the boot order, but at least it's not too hard to correct. Cheers and enjoy your Ubuntu install. :)

---

