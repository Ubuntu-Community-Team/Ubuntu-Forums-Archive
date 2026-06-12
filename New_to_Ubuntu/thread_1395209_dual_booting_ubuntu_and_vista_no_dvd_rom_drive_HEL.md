---
title: "dual booting ubuntu and vista no dvd rom drive HELP!!!"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by ydeardorff on 2010-01-31
Hello all,

Sry to those where I miss posted my problem.

I have been cooking the internet tying to source up a fix for this. Its compounded due to the fact I lost my DVD rom drive in the last couple of days. But thats another topic.

Right now I have ubuntu 9.04,  and windows Vista dual booted. Vista gave me some grief, but I managed to get both ubuntu and vista installed via usb drive.
When I try to use the usb drive to boot windows everything works minus the start up repair option.

When I try to boot windows I get a /boot/bcd  0xc0000001 error

here are my boot_info_script050 results:

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb487b4ea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   853,694,099   853,694,037   7 HPFS/NTFS
/dev/sda2         853,694,100   878,305,679    24,611,580  82 Linux swap / Solaris
/dev/sda3         878,305,680   976,768,064    98,462,385  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        12FABEEFFABECE6B                       ntfs                                     
/dev/sda2        2a1a69c4-adbf-4826-a77f-434b1684f73e   swap                                     
/dev/sda3        8c49ca77-2002-402c-b8b3-300b82a8dfd5   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/windows vista     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c49ca77-2002-402c-b8b3-300b82a8dfd5

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8c49ca77-2002-402c-b8b3-300b82a8dfd5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows Vista Home Premium 64 bit Edition:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows (loader)
rootnoverify	(hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=2a1a69c4-adbf-4826-a77f-434b1684f73e none swap sw 0 0
/dev/sda1 /media/windows\040vista ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Original setting
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0









[B][U]
And for those willing to help on the dvdrom issue:[/U][/B]





ls -l /dev/scd0


lrwxrwxrwx 1 root root 3 2010-01-30 09:30 /dev/scd0 -> sr0




cat /etc/fstab


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=8c49ca77-2002-402c-b8b3-300b82a8dfd5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=2a1a69c4-adbf-4826-a77f-434b1684f73e none swap sw 0 0
/dev/sda1 /media/windows\040vista ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Original setting
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0


 dmesg | grep -i CD-ROM


[    3.422141] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX02 PQ: 0 ANSI: 5
[    3.431185] Uniform CD-ROM driver Revision: 3.20
[    3.431253] sr 3:0:0:0: Attached scsi CD-ROM sr0


sudo lshw -c disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7530B
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NX02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: WDC WD5000BEVT-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WX20AB9D7162
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b487b4ea


sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb487b4ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       53140   426847018+   7  HPFS/NTFS
/dev/sda2           53141       54672    12305790   82  Linux swap / Solaris
/dev/sda3           54673       60801    49231192+  83  Linux
root@yaughn-laptop:~# 


fdisk -l -u

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb487b4ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   853694099   426847018+   7  HPFS/NTFS
/dev/sda2       853694100   878305679    12305790   82  Linux swap / Solaris
/dev/sda3       878305680   976768064    49231192+  83  Linux


It shows up in ubuntu and vista (when its working)
seeks on boot up, but will not read any disk.
When I try to access it, I get no media in the drive, or in windows I get please insert a disk followed by the tray ejecting.

Any help?

Im leaving on business day after tomorrow, and would really like to take my laptop (for my sanity) and for work, for the next two weeks.

Thanks in advance!

---

### Post by louieb on 2010-01-31
Try this - map commands are for faking windows out in to thinking its on the 1st hdd in the boot order. Not needed for a PC with a single hdd.
edit /boot/grub/menu.lst 
Press Alt+F2 to bring up the run dialog
```
gksudo gedit /boot/grub/menu.lst  
```near the bottom you wil find the Vista entry - remove the map commands - it should look like this when done. 
```

title        Windows (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


```

As far as the DVD drive goes it should just work out of the box in both Ubuntu and Vista - sounds like it died.

---

### Post by ydeardorff on 2010-01-31
Too Sweet!!!! 
Thank you so much!
So what was the problem windows was having? Just so mentally I can understand "why" it got fouled.

The dvd drive is damn bad timing! Although now I can use its crash to give me reason to buy a new blue ray player for my latop. LOL

So for the boot issue: [SOLVED]

I wonder what would have caused that entry?

Thank you so much again!

I really appreciate it.

---

### Post by louieb on 2010-01-31
> **ydeardorff said:**
> I wonder what would have caused that entry?


Guess you installed from a USB drive - grub setup got confused and thought you had 2 hard drives - with windows on the 2nd in the boot order.

---

### Post by Hralgmir on 2011-03-27
I had a problem with the optical drive failing to work after downloading some software updates on a desktop system, with Vista installed,  but it turned out to be a problem with the upper and lower registry filters that needed to be cleared. If it's affected the driver operation then maybe that would affect the DVD drive in Ubuntu as well. Uninstalling the driver and reinstalling it made no difference, I downloaded a tool from MS, Microsoft Fix It 50027 which sorted it. There was no problem with the hardware at all. Simple hardware checks might include cleaning the drive lens and unplugging and reconnecting the drive leads, and checking they are connected to the right sockets and that there are no issues with any master/slave jumpers or so on. If it has failed though, replacement may be the best option.

---

