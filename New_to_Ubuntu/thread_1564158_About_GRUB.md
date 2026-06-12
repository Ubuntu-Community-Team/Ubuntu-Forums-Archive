---
title: "About GRUB"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by suomalainen on 2010-08-30
Ubunteros,

Way back when..... I installed Ubuntu 10.04LTS on my USB Seagate 500GB Expansion Portable Drive.

Prior to the install process, I removed the hard disk drive that resided in my Dell Inspiron 2200.

I can launch Ubuntu 10.04LTS but not in the conventional way by using Grub and choosing between 2 different operating systems.

Instead, my process relies on the following during boot-up:

F2-->BIOS-->boot sequence (remove HHD as boot order) enter & save now reboot...

After this step Ubuntu will boot up w/o problem.

I guess I need to find out where grub actually is residing and then move it to the right location?

Anyway, does anyone know how to go about tackling this issue?

Thanks!

---

### Post by Rubi1200 on 2010-08-31
Boot a LiveCD and click on the link at the bottom of my post.

Post the results back here and we can then advise you.

Thanks.

---

### Post by suomalainen on 2010-08-31
OK folks here it is... And thanks for offering to help me.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    71,151,884    71,055,495   7 HPFS/NTFS
/dev/sda3          71,151,885    78,124,094     6,972,210  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,356,721,379 1,356,721,317   7 HPFS/NTFS
/dev/sdb2       1,356,721,380 1,460,597,669   103,876,290  83 Linux
/dev/sdb3       1,460,597,670 1,465,144,064     4,546,395  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D5-0B16                              vfat       DellUtility                   
/dev/sda2        0EA8C6E9A8C6CF01                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        64F0E18EF0E166B0                       ntfs       John Paavo Tengstrom          
/dev/sdb2        51a8859b-9c27-4e9d-b7cf-f17178aefc95   ext3       Ununtu 10.04 LTS              
/dev/sdb3        1fb0bff6-e5fa-405c-ba42-f5a8003c90d5   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/Mobiililaajakais  iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/John Paavo Tengstrom fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/Ununtu 10.04 LTS  ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=51a8859b-9c27-4e9d-b7cf-f17178aefc95

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		51a8859b-9c27-4e9d-b7cf-f17178aefc95
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 51a8859b-9c27-4e9d-b7cf-f17178aefc95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 51a8859b-9c27-4e9d-b7cf-f17178aefc95
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 51a8859b-9c27-4e9d-b7cf-f17178aefc95
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 51a8859b-9c27-4e9d-b7cf-f17178aefc95
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 51a8859b-9c27-4e9d-b7cf-f17178aefc95
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 51a8859b-9c27-4e9d-b7cf-f17178aefc95
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=51a8859b-9c27-4e9d-b7cf-f17178aefc95 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=47e44357-e347-4c8b-8ab3-f1c789353e05 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 701.2GB: boot/grub/core.img
 701.1GB: boot/grub/grub.cfg
 701.2GB: boot/grub/menu.lst
 701.1GB: boot/initrd.img-2.6.32-21-generic
 701.1GB: boot/initrd.img-2.6.32-22-generic
 701.1GB: boot/initrd.img-2.6.32-23-generic
 701.1GB: boot/initrd.img-2.6.32-24-generic
 701.1GB: boot/vmlinuz-2.6.32-21-generic
 701.1GB: boot/vmlinuz-2.6.32-22-generic
 701.1GB: boot/vmlinuz-2.6.32-23-generic
 701.1GB: boot/vmlinuz-2.6.32-24-generic
 701.1GB: initrd.img
 701.1GB: initrd.img.old
 701.1GB: vmlinuz
 701.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by suomalainen on 2010-09-03
........any advice based on the additional info provided?

---

### Post by Rubi1200 on 2010-09-03
I am not able to give you a solution for this, but I know there is a way to fix this. Do a search on the forum for postings by oldfred and with keywords like > external > drive > booting (something like that).

Oldfred is a very experienced forum member and I have seen posts where he mentioned this, I just can't remember where now.

I hope this helps.

---

### Post by suomalainen on 2010-09-03
Are you sure "Oldfred" exists???? I did a search and this user doesn't exist.

---

### Post by Rubi1200 on 2010-09-03
> **suomalainen said:**
> Are you sure "Oldfred" exists???? I did a search and this user doesn't exist.
Yes he exists! Type lowercase oldfred. Take a look at my profile under Friends and you will find him there. Then under his statistics, click find all posts by...but it is a loooong list.

Did you try searching with the other terms I suggested?

---

### Post by oldfred on 2010-09-03
There really is an oldfred, not sure about Oldfred except when at the start of  a sentence. In windows that would not matter but linux recognizes a difference between capitals and small letters. :)

You have grub2 installed in sdb the 750GB drive. Is that your external?

You have no bootloader installed in sda, so without your external you cannot boot at all.

If in BIOS you set the external as first to boot you should not have to go thru the process you are. BIOS will default to external then if not found try to boot the internal. Or you may have floppy and or CD in the list also, but put external first.

Also since you have windows on the internal you can install the windows (or windows like) boot loader to sda, If you install grub to sda then you still have to have the external connected.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by suomalainen on 2010-09-04
Hello oldfred and thank you for finding me!!!!

The 750GB is a Seagate USB external hard disk drive that is partioned into two parts. One partion is about 700GB and the other partion the remaining 50GB or so. The latter is the one Ubuntu 10.04LTS is installed on.

You stated:

"You have no bootloader installed in sda, so without your external you cannot boot at all."

I assume that you mean Ubuntu? With the external usb HDD disconnected Windows XP still boots up properly.

You also said:

"If in BIOS you set the external as first to boot you should not have to go thru the process you are."

I agree with you 100%. But unfortunately this is not the case. Even with the external HDD listed as the only bootable device Ubuntu fails to boot automatically. The process I described is the only way I can get up and running. However, with that said, I can launch Ubuntu and then, for example, choose to "restart" and that will go w/o a hitch.... Otherwise, for firstime boot it's the process I described.

I'm a bit confused about the following:

Also since you have windows on the internal you can install the windows (or windows like) boot loader to sda, If you install grub to sda then you still have to have the external connected.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

1. what does "If you install grub to sda then you still have to have the external connected." mean exactly? Wouldn't I want to have the external USB drive connected so I can launch Ubuntu???

2. When you say "May show error messages about the rest of lilo missing, ignore, we just want MBR" does this mean that when I enter these commands in Terminal that I will be asked certain specific questions? AND to only answer to those pertaining to MBR????

I asked alot of questions but want to get this right. If my laptop get's messed up I'm in the creek if you know what I mean......

Thanks for your support!

---

### Post by Ducatiboy Stu on 2010-09-04
If you plug in your USB drive and set it to first boot in BIOS does it boot up

What you should be able to do is set the BIOS to boot 

1. USB
2. Int HDD
3. CD/Floppy

Then, if you plug in to USB it will boot to Ubuntu, If it is not plugged in, then it will boot up windows off the Int HDD

You wont need to have Grub on the USB drive or the Int HDD

---

### Post by oldfred on 2010-09-04
I agree with Ducatiboy Stu.

=> No boot loader is installed in the MBR of /dev/sda

I do not even see how your windows boots. The script shows no boot loader in the MBR of sda. Without the external you have no bootloader. Standard MBR/msdos computers have booted the same since IBM came out with the PC in the early '80s. BIOS starts and jumps to the MBR of the primary master hard drive which continues the boot process. MBR is also small so it usually just jumps to another address on hard drive. Floppies, CDs and USB devices are similar, depending on in BIOS what device you select as first. Now with newer BIOS you can set boot drive or other device directly in BIOS, even though I can boot any SATA drive mine still calls the boot drive the primary master.

You should see a windows boot loader in the MBR of sda. Since you only have windows on sda you do not want grub installed to sda but the windows boot loader. The lilo boot loader works just like windows in the MBR as it looks for the active partition (boot flag) and jumps to that partition to continue booting. We do not install lilo's code to the PBR partition boot sector but leave windows code there. I believe lilo will say that you will not be able to boot without the rest of it being installed but you already have windows and just want the part of lilo that will start the boot process, which is the part in the MBR. 

You can also install the windows boot loader to the MBR with a windows CD. From a windows repair console use the command fixMBR, if from Vista/7 the equivalent command is BootRec.exe /fixmbr. But we use lilo since you have Ubuntu and we know you can easily install that. Many do not even have windows CDs.

---

### Post by suomalainen on 2010-09-04
Ubuntu is booting exactly the way I have stated. I really don't know what more I can add?

---

### Post by oldfred on 2010-09-04
Is f2 a one time boot key or are you in BIOS? If in BIOS just set external first and internal second as previously mentioned. I still think you need a windows boot loader in sda.

---

### Post by Rubi1200 on 2010-09-04
> **oldfred said:**
> Is f2 a one time boot key or are you in BIOS? If in BIOS just set external first and internal second as previously mentioned. I still think you need a windows boot loader in sda.
Just to add to what oldfred has said:
on my laptop I can either enter BIOS via F2 to make permanent changes or F12 for quick booting options (which then revert to whatever is set in BIOS after the particular session).
As far as the advice goes; I would follow what has been previously posted.

---

### Post by suomalainen on 2010-09-04
Hi all.

Is there something that I am not correctly articulating that in my humble opinion has already been addressed in the posts I've made???

I just ask this because I have already provided the answers to the questions you are asking me....

---

### Post by oldfred on 2010-09-04
No we are just two ships passing in the night.:)

I just have never seen a system boot without a boot loader in the MBR. You say it works so obviously it must work. Maybe you have a special BIOS that works differently somehow. 

A few like to use the BIOS to boot. Most of use use grub and choose what to boot from the grub menu. But with external drives you need two boot loaders, grub in the external and whatever system is in the internal needs to be in the internals MBR.

If you leave the external first in BIOS and can still boot with the external unplugged, then there is no problem.

More info here:
Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

