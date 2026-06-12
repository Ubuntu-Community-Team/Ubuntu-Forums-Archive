---
title: "I have screwed up GRUB!"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-17
I have screwed up grub. How can I install it again? I mean I want to rest the configuration, I want to make it like when I have installed ubuntu. Need help!

---

### Post by caljohnsmith on 2008-12-17
When you say you screwed up Grub, can you be more specific? Are you getting a Grub error on start up? What exactly happened that caused Grub to get messed up? 

In order to get a clearer picture of your setup, how about booting your Live CD, download the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by looi76 on 2008-12-17
I think I have just done a stupid thing, I have restarted my laptop#-o. It stops booting by showing me this:

```
GNU GRUB version 0.97 (637K lower / 3143424k upper memory)

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>*_*
```

---

### Post by shane8002 on 2008-12-17
The best resolve is to just reinstall it. Pop in your ubuntu boot disk and there is an option to reinstall grub.

---

### Post by looi76 on 2008-12-17
Can you please explain to me step-by-step :P ?

---

### Post by shane8002 on 2008-12-17
It´s simple just put your live cd in and click on rescue option from the main menu and you should see the option to reinstall grub.

---

### Post by looi76 on 2008-12-17
> **caljohnsmith said:**
> When you say you screwed up Grub, can you be more specific? Are you getting a Grub error on start up? What exactly happened that caused Grub to get messed up? 

In order to get a clearer picture of your setup, how about booting your Live CD, download the attached "boot_info9.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info9.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

This is the output:

```
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for its boot files.

sda1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63
    Operating System: Vista
    Boot files/directories present:  /boot.ini /bootmgr /ntldr /NTDETECT.COM /boot

sda2:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda2 starts at sector 391343400
    Operating System: XP
    Boot files/directories present:  /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda3:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda3 starts at sector 601152300
    Operating System: 
    Boot files/directories present:  /bootmgr /boot

sda4:
    File system:  
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda5:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda6:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8b59c4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   370362509   185181223+   7  HPFS/NTFS
/dev/sda2       370362510   475299089    52468290    7  HPFS/NTFS
/dev/sda3       601152300   625137344    11992522+   7  HPFS/NTFS
/dev/sda4       475299090   601152299    62926605    5  Extended
/dev/sda5       475299153   584380439    54540643+  83  Linux
/dev/sda6       584380503   601152299     8385898+  82  Linux swap / Solaris

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=370362447, Id= 7, bootable
/dev/sda2 : start=370362510, size=104936580, Id= 7
/dev/sda3 : start=601152300, size= 23985045, Id= 7
/dev/sda4 : start=475299090, size=125853210, Id= 5
/dev/sda5 : start=475299153, size=109081287, Id=83
/dev/sda6 : start=584380503, size= 16771797, Id=82

sda1/boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

sda1/boot

total 1040
drwxrwxrwx 1 root root   4096 2008-07-27 15:13 .
drwxrwxrwx 1 root root  20480 2008-12-17 01:57 ..
-rwxrwxrwx 1 root root  28672 2008-12-17 13:59 bcd
-rwxrwxrwx 1 root root 262144 2008-12-17 13:49 BCD.LOG
-rwxrwxrwx 2 root root 262144 2007-12-28 17:13 BCD.LOG1
-rwxrwxrwx 2 root root      0 2006-11-09 12:48 BCD.LOG2
-rwxrwxrwx 1 root root   1024 2006-09-18 12:27 bootfix.bin
-rwxrwxrwx 1 root root  65536 2006-11-09 12:48 bootstat.dat
drwxrwxrwx 1 root root      0 2008-07-27 15:13 cs-CZ
drwxrwxrwx 1 root root      0 2008-07-27 15:13 da-DK
drwxrwxrwx 1 root root      0 2008-07-27 15:13 de-DE
drwxrwxrwx 1 root root      0 2008-07-27 15:13 el-GR
drwxrwxrwx 1 root root      0 2008-07-27 15:13 en-US
drwxrwxrwx 1 root root      0 2008-07-27 15:13 es-ES
-rwxrwxrwx 1 root root   2048 2006-09-18 12:27 etfsboot.com
drwxrwxrwx 1 root root      0 2008-07-27 15:13 fi-FI
drwxrwxrwx 1 root root   4096 2008-07-27 15:13 fonts
drwxrwxrwx 1 root root      0 2008-07-27 15:13 fr-FR
drwxrwxrwx 1 root root      0 2008-07-27 15:13 hu-HU
drwxrwxrwx 1 root root      0 2008-07-27 15:13 it-IT
drwxrwxrwx 1 root root      0 2008-07-27 15:13 ja-JP
drwxrwxrwx 1 root root      0 2008-07-27 15:13 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-07-27 15:13 nb-NO
drwxrwxrwx 1 root root      0 2008-07-27 15:13 nl-NL
drwxrwxrwx 1 root root      0 2008-07-27 15:13 pl-PL
drwxrwxrwx 1 root root      0 2008-07-27 15:13 pt-BR
drwxrwxrwx 1 root root      0 2008-07-27 15:13 pt-PT
drwxrwxrwx 1 root root      0 2008-07-27 15:13 ru-RU
drwxrwxrwx 1 root root      0 2008-07-27 15:13 sv-SE
drwxrwxrwx 1 root root      0 2008-07-27 15:13 tr-TR
drwxrwxrwx 1 root root      0 2008-07-27 15:13 zh-CN
drwxrwxrwx 1 root root      0 2008-07-27 15:13 zh-HK
drwxrwxrwx 1 root root      0 2008-07-27 15:13 zh-TW

sda2/boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

sda3/boot

total 8708
drwxrwxrwx 1 root root   12288 2008-05-15 08:09 .
drwxrwxrwx 1 root root   12288 2008-12-16 16:24 ..
-rwxrwxrwx 1 root root   28672 2008-06-02 06:41 BCD
-rwxrwxrwx 1 root root  262144 2008-06-02 06:41 BCD.LOG
-rwxrwxrwx 2 root root  262144 2006-08-29 09:47 bcd.LOG1
-rwxrwxrwx 2 root root       0 2006-08-29 09:47 bcd.LOG2
-rwxrwxrwx 1 root root    1024 2006-07-06 08:16 BOOTFIX.BIN
-rwxrwxrwx 1 root root 3170304 2006-05-19 08:00 boot.sdi
-rwxrwxrwx 1 root root   87552 2006-11-02 00:30 BOOTSECT.EXE
-rwxrwxrwx 1 root root     891 2008-09-06 11:19 Desktop.ini
-rwxrwxrwx 1 root root    2048 2006-09-18 13:27 ETFSBOOT.COM
-rwxrwxrwx 1 root root    8134 2002-09-10 16:14 Folder.htt
drwxrwxrwx 1 root root       0 2008-05-15 06:31 FONTS
-rwxrwxrwx 1 root root  385024 2006-08-13 17:40 memtest.exe
-rwxrwxrwx 2 root root  181898 2002-09-16 14:37 protect.chinese hong kong
-rwxrwxrwx 2 root root  181916 2002-09-16 14:37 protect.chinese simplified
-rwxrwxrwx 2 root root  181898 2002-09-16 14:37 protect.chinese traditional
-rwxrwxrwx 2 root root  181865 2006-04-27 16:19 protect.czech
-rwxrwxrwx 2 root root  181726 2005-11-03 15:21 protect.danish
-rwxrwxrwx 2 root root  181605 2002-09-10 13:56 protect.dutch
-rwxrwxrwx 1 root root  181651 2002-09-10 13:50 Protect.ed
-rwxrwxrwx 2 root root  181648 2004-11-22 15:28 protect.english
-rwxrwxrwx 2 root root  181673 2005-11-03 15:20 protect.finnish
-rwxrwxrwx 2 root root  181736 2005-11-03 15:19 protect.french
-rwxrwxrwx 2 root root  181669 2005-11-03 15:18 protect.german
-rwxrwxrwx 2 root root  182689 2005-11-23 15:56 protect.greek
-rwxrwxrwx 2 root root  182605 2006-01-23 09:18 protect.hebrew
-rwxrwxrwx 2 root root  181696 2007-08-28 14:58 protect.hungarian
-rwxrwxrwx 2 root root  181554 2005-11-03 15:17 protect.italian
-rwxrwxrwx 2 root root  182566 2006-04-10 09:46 protect.japanese
-rwxrwxrwx 2 root root  218295 2005-11-24 11:24 protect.korean
-rwxrwxrwx 2 root root  181578 2005-11-03 15:15 protect.norwegian
-rwxrwxrwx 2 root root  181789 2006-04-25 14:44 protect.polish
-rwxrwxrwx 2 root root  181624 2005-11-03 15:13 protect.portuguese
-rwxrwxrwx 2 root root  181882 2005-10-27 19:24 protect.portuguese brazilian
-rwxrwxrwx 2 root root  211936 2004-06-28 08:52 protect.russian
-rwxrwxrwx 2 root root  181586 2005-11-03 15:11 protect.spanish
-rwxrwxrwx 2 root root  181602 2002-09-10 14:15 protect.swedish
-rwxrwxrwx 2 root root  181783 2003-08-12 10:37 protect.turkish

sda5/boot/grub/menu.lst

gfxmenu /boot/grub/message.blusplash

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
# kopt=root=UUID=505fb5f6-7488-4eba-bf40-db493ffe920b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=505fb5f6-7488-4eba-bf40-db493ffe920b

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		505fb5f6-7488-4eba-bf40-db493ffe920b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=505fb5f6-7488-4eba-bf40-db493ffe920b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		505fb5f6-7488-4eba-bf40-db493ffe920b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=505fb5f6-7488-4eba-bf40-db493ffe920b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		505fb5f6-7488-4eba-bf40-db493ffe920b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=505fb5f6-7488-4eba-bf40-db493ffe920b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		505fb5f6-7488-4eba-bf40-db493ffe920b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=505fb5f6-7488-4eba-bf40-db493ffe920b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		505fb5f6-7488-4eba-bf40-db493ffe920b
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
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


sda5/boot

total 23804
drwxr-xr-x  3 root root    4096 2008-12-17 16:42 .
drwxr-xr-x 20 root root    4096 2008-12-17 16:41 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-17 23:48 grub
-rw-r--r--  1 root root 8202242 2008-12-17 16:41 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8202660 2008-12-17 16:42 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

sda5/boot/grub

total 1628
drwxr-xr-x 2 root root   4096 2008-12-17 23:48 .
drwxr-xr-x 3 root root   4096 2008-12-17 16:42 ..
-rw-r--r-- 1 root root    197 2008-12-17 23:48 default
-rw-r--r-- 1 root root     15 2008-12-17 15:38 device.map
-rw-r--r-- 1 root root   7444 2008-12-17 23:48 e2fs_stage1_5
-rw-r--r-- 1 root root   7268 2008-12-17 23:48 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-17 15:38 installed-version
-rw-r--r-- 1 root root   6580 2008-12-17 23:48 iso9660_stage1_5
-rw-r--r-- 1 root root   8064 2008-12-17 23:48 jfs_stage1_5
-rw-r--r-- 1 root root   5509 2008-12-17 23:44 menu.lst
-rw-r--r-- 1 root root   5471 2008-12-17 16:41 menu.lst~
-rw-r--r-- 1 1000 1000 127488 2006-07-18 22:12 message.blusplash
-rw-r--r-- 1 1000 1000 146432 2006-07-25 19:35 message.kubu
-rw-r--r-- 1 1000 1000 142336 2006-07-09 11:33 message.kubuntu
-rw-r--r-- 1 1000 1000 140288 2006-07-09 20:24 message.new
-rw-r--r-- 1 1000 1000 129536 2006-07-24 03:56 message.snow
-rw-r--r-- 1 1000 1000 128000 2008-01-18 07:47 message.suse
-rw-r--r-- 1 1000 1000 135168 2006-07-14 11:27 message.ubu
-rw-r--r-- 1 1000 1000 160768 2006-07-13 20:42 message.ububrown
-rw-r--r-- 1 1000 1000 142848 2006-07-13 16:58 message.ubugrey
-rw-r--r-- 1 1000 1000 140288 2006-07-24 23:52 message.xubu
-rw-r--r-- 1 root root   6740 2008-12-17 23:48 minix_stage1_5
-rw-r--r-- 1 root root   9012 2008-12-17 23:48 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-17 23:48 stage1
-rw-r--r-- 1 root root 100948 2008-12-17 23:48 stage2
-rw-r--r-- 1 root root   8700 2008-12-17 23:48 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
mount: you must specify the filesystem type
/dev/sda4: unknown volume type
umount: sda4: not mounted
/dev/sda6 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sda6: not mounted

```

---

### Post by caljohnsmith on 2008-12-17
OK, according to the script, you have Grub correctly installed to the MBR (Master Boot Record) of your sda drive, so you should be able to boot it just fine. So what is the problem with Grub? Are you getting some Grub error? What exactly happens on start up?

---

### Post by looi76 on 2008-12-17
Thnx caljohnsmith, I have reinstalled Ubuntu :P

---

