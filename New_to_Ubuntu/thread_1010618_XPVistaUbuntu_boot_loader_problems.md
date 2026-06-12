---
title: "XP/Vista/Ubuntu boot loader problems"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by FlyingYellow on 2008-12-13
Hey guys. This is my first post here (as you can probably tell).

I'm having some problems with my OS setup and bootloader. First, I got my computer with XP installed. I tried wubi for a while, then I split my disk and put ubuntu on its own partition. A little while later, I split the disk again so that there could be a separate home partition. That worked fine for a while, then I thought that since I had a Vista disk lying around, I might as well see what everyone was complaining about. Sooo, I chopped my disk again and installed Vista. Now, the problem is that, while before I installed Vista, the GRUB bootloader handled booting into Ubuntu or XP, after I installed Vista, it decided that it would take over bootloader duties. As a result, I now have some Windows bootloader that lets me choose between "Windows Vista" and "Previous Windows" and I have no idea how to get back into my Ubuntu. Furthermore, when I try to boot into the previous windows version option, I get an error message and my machine reboots (I don't remember the message at the moment but I'll add it as soon as I can). I'm currently stuck in Vista. 

Help would be greatly appreciated. :(

On a side note, I think these forums are wonderful. I've been able to solve nearly all my nooby linux problems through here. Thanks guys XD

---

### Post by Michael.Godawski on 2008-12-14
hi FlyingYellow, 
Vista's MBR will overwrite GRUB during installation so we have to fix this.
Have a look at this guide:

[LIST]
[*][http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[/LIST]
Especially have a look at page 5.

---

### Post by tomtom1982 on 2008-12-14
You can also use the SuperGrubDisk to reinstall grub. There you have a step-by-step support and you haven't got to fix it manually.

You'll get the ISO for burn it to CD here:
[http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9770.iso](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9770.iso)

More Infos for using SuperGrubDisk you'll get on [http://www.supergrubdisk.org](http://www.supergrubdisk.org).

---

### Post by bumanie on 2008-12-14
I don't think either of the two suggestions above will help, due to having two windows bootloaders to deal with - they are fine with one windows installation to deal with, but won't help unless the bootloader issue has been dealt with first. The issue is that xp and vista's bootloaders recognize each other but will not boot each other without the bootloaders being added together. In your situation with xp and grub previously working, you should add vista's bootloader to xp bootloader files and then reinstall grub to it's presnet configuration. The easiest way to add vista's boot files to xp's is with easybcd bootloader available from [here]("http://neosmart.net/dl.php?id=1"). Then reinstall grub via live ubuntu cd by following [this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Tom--d on 2008-12-14
The best way to solve this is Install Windows frist then Ubuntu last. Then you can set up the boot menu.

---

### Post by bumanie on 2008-12-14
> **Tom--d said:**
> The best way to solve this is Install Windows frist then Ubuntu last. Then you can set up the boot menu.
That is helpful, but there is still the issue of getting two architectually  different windows bootloaders to get to work together.

---

### Post by caljohnsmith on 2008-12-14
How about booting your Live CD and download the attached "boot_info6.sh.txt" file to your desktop; then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
And that will create a "BootInfo.txt" file on your desktop. Please attach that file to your next post, or post the contents of that file. The results will give me a clear picture of your setup and what it might take to get XP and Vista booting separately from Grub, which is certainly possible to set up. Or if you want, you could keep your current Vista boot loader and I can try to help you figure out why XP isn't booting. Let me know if you would like my help.

---

### Post by FlyingYellow on 2008-12-14
Oops sorry guys. I didn't really explain what I wanted did I. >.<

I would like to get my bootloader to how it was before (Ubuntu and XP) and have the option of booting Vista from Grub. Sorry if I caused any confusion.

and caljohnsmith: Here's the output from the script you gave me. It doesn't look very good o.o

```
ubuntu@ubuntu:~$ sudo sh ~/Desktop/boot_info6.sh.txt

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/hdb: unrecognized partition table type
No partitions found

```

Uh oh :confused:

---

### Post by FlyingYellow on 2008-12-14
Here's the boot info file:

```
/dev/hda:None
/dev/hdb:None
hda1 :vfat:BS: None:OS : /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
hda2 :ntfs:BS: Vista:OS : /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot 
hda3 ::BS: None:OS : 
hda5 :ext3:BS: None:OS Linux: /boot/grub/menu.lst /boot /boot/grub 
hda6 :ext3:BS: None:OS : 
hda7 :ntfs:BS: Vista:OS Vista: 
hda8 :swap:BS: None:OS : 

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    14346044     7172991    b  W95 FAT32
/dev/hda2   *    14346045    57448439    21551197+   7  HPFS/NTFS
/dev/hda3        57448440   234436544    88494052+   5  Extended
/dev/hda5        57448566    77931314    10241374+  83  Linux
/dev/hda6        77931378   180329624    51199123+  83  Linux
/dev/hda7       180330496   229165055    24417280    7  HPFS/NTFS
/dev/hda8       229167288   234436544     2634628+  82  Linux swap / Solaris
# partition table of /dev/hda
unit: sectors

/dev/hda1 : start=       63, size= 14345982, Id= b
/dev/hda2 : start= 14346045, size= 43102395, Id= 7, bootable
/dev/hda3 : start= 57448440, size=176988105, Id= 5
/dev/hda4 : start=        0, size=        0, Id= 0
/dev/hda5 : start= 57448566, size= 20482749, Id=83
/dev/hda6 : start= 77931378, size=102398247, Id=83
/dev/hda7 : start=180330496, size= 48834560, Id= 7
/dev/hda8 : start=229167288, size=  5269257, Id=82

hda2/boot.ini

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER


hda2/Boot

total 504
drwxrwxrwx 1 root root   4096 2008-12-14 01:04 .
drwxrwxrwx 1 root root   8192 2008-12-14 02:37 ..
-rwxrwxrwx 1 root root  24576 2008-12-14 16:40 BCD
-rwxrwxrwx 1 root root  21504 2008-12-14 16:23 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-12-14 01:04 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-12-14 01:04 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-12-14 01:04 bootstat.dat
drwxrwxrwx 1 root root      0 2008-12-14 01:04 cs-CZ
drwxrwxrwx 1 root root      0 2008-12-14 01:04 da-DK
drwxrwxrwx 1 root root      0 2008-12-14 01:04 de-DE
drwxrwxrwx 1 root root      0 2008-12-14 01:04 el-GR
drwxrwxrwx 1 root root      0 2008-12-14 01:04 en-US
drwxrwxrwx 1 root root      0 2008-12-14 01:04 es-ES
drwxrwxrwx 1 root root      0 2008-12-14 01:04 fi-FI
drwxrwxrwx 1 root root      0 2008-12-14 01:04 Fonts
drwxrwxrwx 1 root root      0 2008-12-14 01:04 fr-FR
drwxrwxrwx 1 root root      0 2008-12-14 01:04 hu-HU
drwxrwxrwx 1 root root      0 2008-12-14 01:04 it-IT
drwxrwxrwx 1 root root      0 2008-12-14 01:04 ja-JP
drwxrwxrwx 1 root root      0 2008-12-14 01:04 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 09:51 memtest.exe
drwxrwxrwx 1 root root      0 2008-12-14 01:04 nb-NO
drwxrwxrwx 1 root root      0 2008-12-14 01:04 nl-NL
drwxrwxrwx 1 root root      0 2008-12-14 01:04 pl-PL
drwxrwxrwx 1 root root      0 2008-12-14 01:04 pt-BR
drwxrwxrwx 1 root root      0 2008-12-14 01:04 pt-PT
drwxrwxrwx 1 root root      0 2008-12-14 01:04 ru-RU
drwxrwxrwx 1 root root      0 2008-12-14 01:04 sv-SE
drwxrwxrwx 1 root root      0 2008-12-14 01:04 tr-TR
drwxrwxrwx 1 root root      0 2008-12-14 01:04 zh-CN
drwxrwxrwx 1 root root      0 2008-12-14 01:04 zh-HK
drwxrwxrwx 1 root root      0 2008-12-14 01:04 zh-TW

hda5/boot/grub/menu.lst

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f6dc1b33-e97c-4239-8c7e-524652f81528 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		-------------------------------------------------
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Piece of Smelly Crap
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


hda5/boot

total 56684
drwxr-xr-x  3 root root    4096 2008-12-09 04:53 .
drwxr-xr-x 24 root root    4096 2008-12-14 05:19 ..
-rw-r--r--  1 root root  420224 2008-08-20 22:15 abi-2.6.24-19-generic
-rw-r--r--  1 root root  420395 2008-10-22 01:49 abi-2.6.24-21-generic
-rw-r--r--  1 root root  420395 2008-11-24 22:19 abi-2.6.24-22-generic
-rw-r--r--  1 root root   74164 2008-08-20 22:15 config-2.6.24-19-generic
-rw-r--r--  1 root root   74177 2008-10-22 01:49 config-2.6.24-21-generic
-rw-r--r--  1 root root   74177 2008-11-24 22:19 config-2.6.24-22-generic
drwxr-xr-x  4 root root    4096 2008-11-29 06:04 grub
-rw-r--r--  1 root root 7737086 2008-10-12 21:43 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 8408945 2008-10-12 07:06 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7738844 2008-11-07 23:27 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7738468 2008-10-27 22:21 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7737900 2008-12-09 04:53 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7737427 2008-11-29 06:04 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 11:03 memtest86+.bin
-rw-r--r--  1 root root 1152364 2008-08-20 22:15 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1153201 2008-10-22 01:49 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1153201 2008-11-24 22:19 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1903096 2008-08-20 22:15 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1905688 2008-10-22 01:49 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1905656 2008-11-24 22:19 vmlinuz-2.6.24-22-generic

hda5/boot/grub

total 236
drwxr-xr-x 4 root root    4096 2008-11-29 06:04 .
drwxr-xr-x 3 root root    4096 2008-12-09 04:53 ..
-rw-r--r-- 1 root root     197 2008-10-12 07:07 default
-rw-r--r-- 1 root root      30 2008-10-12 07:07 device.map
-rw-r--r-- 1 root root    8056 2008-10-12 07:07 e2fs_stage1_5
-rw-r--r-- 1 root root    7904 2008-10-12 07:07 fat_stage1_5
drwxr-xr-x 2 root root    4096 2008-11-01 19:17 images
-rw-r--r-- 1 root root      16 2008-10-12 07:07 installed-version
-rw-r--r-- 1 root root    8608 2008-10-12 07:07 jfs_stage1_5
-rw-r--r-- 1 1000 admin   5625 2008-11-29 06:04 menu.lst
-rw-r--r-- 1 1000 admin   5257 2008-11-29 06:03 menu.lst~
-rw-r--r-- 1 root root    5246 2008-11-01 19:37 menu.lst.backup
-rw-r--r-- 1 root root    5183 2008-11-01 19:14 menu.lst.bak
-rw-r--r-- 1 root root    7324 2008-10-12 07:07 minix_stage1_5
-rw-r--r-- 1 root root    9632 2008-10-12 07:07 reiserfs_stage1_5
drwxr-xr-x 2 root root    4096 2008-11-01 19:37 splashimages
-rw-r--r-- 1 root root     512 2008-10-12 07:07 stage1
-rw-r--r-- 1 root root  108356 2008-10-12 07:07 stage2
-rw-r--r-- 1 root root    9276 2008-10-12 07:07 xfs_stage1_5
```

---

### Post by caljohnsmith on 2008-12-14
OK, that helps clear things up quite a bit about your setup. First off, do you have hda and hdb in a RAID configuration? It looks like you might have them RAIDed, and that could complicate things. And is hda2 your XP install and hda7 is Vista? How about posting the output of the attached "script1.sh.txt" by downloading it to your desktop and doing:
```
sudo sh ~/Desktop/script1.sh.txt
```
Also, if you want to separate Vista from XP so you can boot them separately from Grub, it looks like you will need a Vista Install CD in order to repair the boot sector of the XP partition, because both your Windows partitions are set to boot Vista's "bootmgr" rather than XP's "ntldr". If you don't have a Vista Install CD, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes. :)

---

