---
title: "Grub - Errors 18 &amp; 16 on XP Dual Boot System"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by lkraemer on 2010-01-22
My built up computer with one IDE Western Digital 500 Gig IDE drive,
with 4 Primary Partitions has been giving GRUB errors 18 and now 16.

EVGA Motherboard 650i

Motherboard 122-CK-NF66-T1 with 2 IDE (Master & Slave) Ports
and 4 SATA Ports.  Only one Harddrive (Western Digital 500 Gig IDE
MASTER and one IDE DVDRW IDE SLAVE are connected to the Primary IDE Port)

Partitions are laid out as per the png file.
 
Windows XP installed on /dev/sda1 and not activated = timed out
Windows does not have SATA drivers installed

UBUNTU 8.04.3 LTS installed on /dev/sda2 for /
/dev/sda3 is /home
/dev/sda4 is Linux-Swap

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000a386

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       18485    25599577+  83  Linux
/dev/sda3           18486       60482   337340902+  83  Linux
/dev/sda4           60483       60801     2562367+  82  Linux swap / Solaris

Disk /dev/sdc: 63 MB, 63488000 bytes
255 heads, 63 sectors/track, 7 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00267901

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1           8       61968+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(6, 254, 63) logical=(7, 183, 16)
ubuntu@ubuntu:~$ 

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000a386

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/sda2         245,762,370   296,961,524    51,199,155  83 Linux
/dev/sda3         296,961,525   971,643,329   674,681,805  83 Linux
/dev/sda4         971,643,330   976,768,064     5,124,735  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A4C0E847C0E82172" TYPE="ntfs" 
/dev/sda2: UUID="3432e47f-8c14-4a8b-beb6-347e11360b75" TYPE="ext2" 
/dev/sda3: UUID="628ffe72-beca-4157-855d-acc8c5a56c4c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="276518eb-910b-474f-84de-9861233f8198" 
/dev/sda4: UUID="276518eb-910b-474f-84de-9861233f8198" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=628ffe72-beca-4157-855d-acc8c5a56c4c /home           ext3    relatime        0       2
# /dev/sda3
UUID=276518eb-910b-474f-84de-9861233f8198 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0


=================== sda2: Location of files loaded by Grub: ===================


 127.4GB: boot/grub/menu.lst
 127.4GB: boot/grub/stage2
 127.3GB: boot/initrd.img-2.6.24-16-generic
 127.4GB: boot/initrd.img-2.6.24-16-generic.bak
 127.3GB: boot/initrd.img-2.6.24-19-generic
 127.4GB: boot/initrd.img-2.6.24-19-generic.bak
 127.3GB: boot/initrd.img-2.6.24-21-generic
 127.4GB: boot/initrd.img-2.6.24-21-generic.bak
 127.3GB: boot/initrd.img-2.6.24-22-generic
 127.4GB: boot/initrd.img-2.6.24-22-generic.bak
 127.4GB: boot/initrd.img-2.6.24-23-generic
 127.3GB: boot/initrd.img-2.6.24-23-generic.bak
 127.3GB: boot/initrd.img-2.6.24-25-generic
 127.3GB: boot/initrd.img-2.6.24-25-generic.bak
 127.4GB: boot/initrd.img-2.6.24-26-generic
 127.4GB: boot/initrd.img-2.6.24-26-generic.bak
 127.4GB: boot/vmlinuz-2.6.24-16-generic
 127.4GB: boot/vmlinuz-2.6.24-19-generic
 127.4GB: boot/vmlinuz-2.6.24-21-generic
 127.4GB: boot/vmlinuz-2.6.24-22-generic
 127.3GB: boot/vmlinuz-2.6.24-23-generic
 127.3GB: boot/vmlinuz-2.6.24-25-generic
 127.3GB: boot/vmlinuz-2.6.24-26-generic
 127.4GB: initrd.img
 127.3GB: initrd.img.old
 127.3GB: vmlinuz
 127.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory

```

I built a Grub Boot CDR, and can boot from that when I need to.

Yesterday's Update of the Kernel has caused Error 16 and I must use
a previous Grub Menu selection for previous kernel (2.6.24-25-generic)
to get it to boot and run.  Prior to this I had numerous Grub 18 Errors
with lots of problems booting to Ubuntu.

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=3432e47f-8c14-4a8b-beb6-347e11360b75 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

Any help would be appreciated, until Ubuntu 10.04 LTS arrives and I can
rebuild my system.  (I just don't want to lose anything in my home partition,
and I want to be able to always boot into Ubuntu.  Forget Windows for now!)

UPDATED:  17:45
Since my original post I booted Gparted LiveCD and formatted the Windows Partition /dev/sda1 as ext3.
Then I booted my Grub CDR and installed grub back to HD0.  It is at least is currently booting.....
but I still would like some help.

Thanks.

lk

---

### Post by presence1960 on 2010-01-22
your results.txt file from the boot info script looks OK to me. I think the best thing to do is backtrack and work our way back since you have been having multiple boot errors. The GRUB error 18 baffles me since I looked up your mobo and the BIOS on that should not have a limitation on reading your hard disk at boot. But let's work on the lastest error first. Now that you are able to boot go System > Administration > Synaptic Package Manager. Uninstall the 2.6.24-26 kernel by marking for complete removal:

linux-image-2.6.24-26
linux-image-2.6.24-26-generic-2.6.24-26xxx
linux-headers-2.6.24-26
linux-headers-2.6.24-26-generic-2.6.24-26xxx

Click Apply on top toolbar. When completed reboot & report back how your machine boots.

---

### Post by lkraemer on 2010-01-22
Well, it has been booting at times with the latest kernel, and then again
I have to go to the previous kernel.  The last time I tried, I couldn't
even get it to boot with my Grub Boot CDR.  So, I stuck in my Grub Boot
Floppy.  AHhh, Then I noticed a small squeal from the floppy drive, and
it seemed like the floppy wasn't even turning.  But to my joy it booted
into the latest kernel.  So, I unplugged the power to the floppy and
also the data cable at the next power down.  Then I booted twice into the
latest kernel in the Grub Menu.  WHEW!  Worked twice in a row!

So, just maybe I found the culprit.  I'll go to Fry Electronics tomorrow
and pick up a new Floppy for less than $5.00 and see if that is the problem.
I don't really use the floppy much anymore, but I like to have it for some
of the older stuff I have on my old Win2K Laptop.

If you still want I can remove the latest kernel, but I would prefer to wait
and see if it continues to boot, before doing too much.

This problem has been bugging me for the last 20 days or so.  It comes and
goes at different times.  I typically boot it and let it run the remainder
of the day, if I get it booted.  I did buy a SATA Drive, and
have sda3 all backed up so I won't lose anything.

I had a thought about trying to copy the sda2 (/) partition (8.04.3) to the
sda1 partition, then after I had it booting I would delete the
original sda2 partition and expand sda1.  Then I could copy my data
from sda3 to sda1.  That would get me a clean install until 10.04 LTS
arrives.  But, I don't know how to remove the mount point (/) on sda2
and then make one on sda1, other than doing it with Gparted during the
install.

THANKS for the reply.

lk

---

### Post by lkraemer on 2010-01-23
Well, after three successful boots in a row yesterday, this morning I got
ERROR 18 on the initial boot.  Then when I Reset the Computer I got ERROR 16
on the second try by using the latest Kernel.  Then I tried the second
Kernel in the Grub menu and it booted to Ubuntu 8.04.3 LTS.

So, I may have spoke too soon, as the Floppy is still unplugged.

HELP!  I need some options to keep it booting until 10.04 LTS arrives.

I'm sick of these ERROR Messages.

lk

---

### Post by presence1960 on 2010-01-23
> **lkraemer said:**
> Well, after three successful boots in a row yesterday, this morning I got
ERROR 18 on the initial boot.  Then when I Reset the Computer I got ERROR 16
on the second try by using the latest Kernel.  Then I tried the second
Kernel in the Grub menu and it booted to Ubuntu 8.04.3 LTS.

So, I may have spoke too soon.

HELP!  I need some options to keep it booting until 10.04 LTS arrives.

I'm sick of these ERROR Messages.

lk

Remove the newest kernel as I suggested in an earlier post. Then try using the next recent kernel for a while. If the errors do not persist it would point to the newest kernel being the culprit. At the very least this will help rule out whether the newest kernel is the problem or not.

---

### Post by lkraemer on 2010-01-23
OK, I used Synaptic to remove the image and headers of Kernel xxxxxx-26

Then I rebooted from the Ubuntu menu, and it booted correctly.  Next I
powered off the computer for 1 minute, (Power switch on case OFF) and
when I booted I got ERROR 18.  I pressed the RESET button on the case
and it booted normally.

Next I booted from the 8.04.3 LiveCD and was going to re-install GRUB.
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub
Probing devices to guess BIOS drives. This may take a long time.
root@ubuntu:/home/ubuntu#

and I got this error message.  But Grub finds it as follows:

grub> find /boot/grub/stage1
 (hd0,1)

grub> 

So, now I have Kernel xxxx-25-generic in my menu and I have the same
ERROR 18, but haven't seen the Error 16 for a bit (2-3 boots).

Thanks.

lk

---

### Post by lkraemer on 2010-01-23
UPDATE:
I attempted to locate a new floppy drive today, and did not find one.

If I connect the power and data cable to the floppy, I get continuous
ERROR 18's when I boot.  If I remove the cables it boots into Kernel
xxxxxx-25 without the ERROR 16 I was getting with Kernel xxxx-26.

I was trying to run Spinrite 6.0 on the first Partition but can't get
Spinrite to run.  It hangs on the screen saying working........

lk

---

