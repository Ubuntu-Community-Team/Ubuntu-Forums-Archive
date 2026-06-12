---
title: "grub4dos problem"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by SANDKON on 2008-12-14
I had ubuntu 8.10 installed as dual boot with XP on external hdd, all ok but then exprienced some issues. Reinstalled ubuntu using livecd. Now cannot boot into either ubuntu nor XP. Get GRUB4DOS error screen and cannot boot. Didnot know i had grub 4 dos. thought had grub loader. grub/boot/menu,lst looks ok and bios can access external hdd or at least used to before reinstall. Please help as getting big headache!!!!!!

---

### Post by logos34 on 2008-12-14
Sounds like you were toggling the boot drive in the Bios to get to either OS.  [Edit: or maybe you were using grub4dos to boot ubuntu from the windows boot.ini menu]...But when you reinstalled it overwrote the windows bootloader on the internal drive rather than the mbr of the usb disk.  Correct me if I'm wrong

You can restore the windows bootloader (either with fixmbr from the xp install cd or super grub disk), then reinstall ubuntu following [this guide]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") (basically all you need to do is hit 'advanced' button at Step 7 and change grub location to the external drive).

---

### Post by caljohnsmith on 2008-12-14
In order to get a better picture of your current setup, how about booting your Live CD, download the attached "boot_info6.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will greatly clarify what your setup is like.

---

### Post by SANDKON on 2008-12-14
text here.
/dev/sda:Syslinux
/dev/sdb:Grub:00ff
/dev/sdc:None
/dev/sdd:None
/dev/sde:None
/dev/sdf:None
sda1 :vfat:BS: None:OS : /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
sda2 :ntfs:BS: XP:OS : /boot.ini /ntldr /NTDETECT.COM 
sdb1 :ext3:BS: None:OS Linux: /boot/grub/menu.lst /boot /boot/grub 
sdb2 ::BS: None:OS : 
sdb5 :swap:BS: None:OS : 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ace39a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7711199     3855568+  1b  Hidden W95 FAT32
/dev/sda2         7711263   156344579    74316658+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a336e8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1950515909   975257923+  83  Linux
/dev/sdb2      1950515910  1953520064     1502077+   5  Extended
/dev/sdb5      1950515973  1953520064     1502046   82  Linux swap / Solaris
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=  7711137, Id=1b, bootable
/dev/sda2 : start=  7711263, size=148633317, Id= 7
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=1950515847, Id=83, bootable
/dev/sdb2 : start=1950515910, size=  3004155, Id= 5
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=1950515973, size=  3004092, Id=82

sda1/boot.ini

[boot loader]

timeout=15

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

c:\wubildr.mbr="Ubuntu"


sda2/boot.ini

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

timeout=15

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


sdb1/boot/grub/menu.lst

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
# kopt=root=UUID=26ae1cf2-bb40-4900-8d75-8b1f8e849f5f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=26ae1cf2-bb40-4900-8d75-8b1f8e849f5f

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		26ae1cf2-bb40-4900-8d75-8b1f8e849f5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26ae1cf2-bb40-4900-8d75-8b1f8e849f5f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		26ae1cf2-bb40-4900-8d75-8b1f8e849f5f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26ae1cf2-bb40-4900-8d75-8b1f8e849f5f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		26ae1cf2-bb40-4900-8d75-8b1f8e849f5f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1


sdb1/boot

total 11952
drwxr-xr-x  3 root root    4096 2008-12-14 20:13 .
drwxr-xr-x 20 root root    4096 2008-12-14 20:13 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-14 20:13 grub
-rw-r--r--  1 root root 8183619 2008-12-14 20:13 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

sdb1/boot/grub

total 216
drwxr-xr-x 2 root root   4096 2008-12-14 20:13 .
drwxr-xr-x 3 root root   4096 2008-12-14 20:13 ..
-rw-r--r-- 1 root root    197 2008-12-14 20:13 default
-rw-r--r-- 1 root root     30 2008-12-14 20:13 device.map
-rw-r--r-- 1 root root   8108 2008-12-14 20:13 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-14 20:13 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-14 20:13 installed-version
-rw-r--r-- 1 root root   8712 2008-12-14 20:13 jfs_stage1_5
-rw-r--r-- 1 root root   4770 2008-12-14 20:13 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-14 20:13 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-14 20:13 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-14 20:13 stage1
-rw-r--r-- 1 root root 121460 2008-12-14 20:13 stage2
-rw-r--r-- 1 root root   9556 2008-12-14 20:13 xfs_stage1_5

---

### Post by caljohnsmith on 2008-12-14
OK, part of the problem is that your sda1 recovery partition has the boot flag set, when your Windows sda2 partition should have the boot flag set instead. You can fix that by doing the following command:
```
sudo sfdisk -A2 /dev/sda
```
And then you should be able to boot into Windows. Also, it looks like you have Grub correctly installed to the MBR (Master Boot Record) of your Ubuntu sdb drive, so to boot Ubuntu, simply go into your BIOS and change the boot order so that the sdb drive boots before the sda drive. Let me know how that goes.

---

### Post by SANDKON on 2008-12-14
Bios boot order  doesn4t show external hdd but does have a usb fdd and usb zip line

list includes hard disk cd rom. floppy. usb fdd . usb zip.

is this the cause?

---

### Post by caljohnsmith on 2008-12-14
If you can't find a way to boot your Ubuntu drive, you could install Grub to the MBR of your sda drive and boot it that way. How about doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. Then reboot and let me know what happens.

---

### Post by logos34 on 2008-12-14
looks like you had a wubi install before--that explains the grub4dos.  You might want to clean up sda1 boot.ini, remove the wubildr entry

---

### Post by SANDKON on 2008-12-14
> **caljohnsmith said:**
> OK, part of the problem is that your sda1 recovery partition has the boot flag set, when your Windows sda2 partition should have the boot flag set instead. You can fix that by doing the following command:
```
sudo sfdisk -A2 /dev/sda
```
And then you should be able to boot into Windows. Also, it looks like you have Grub correctly installed to the MBR (Master Boot Record) of your Ubuntu sdb drive, so to boot Ubuntu, simply go into your BIOS and change the boot order so that the sdb drive boots before the sda drive. Let me know how that goes.

Now boots directly into XP, which is something I'm grateful about: at least I can get one OS! When boots there is no boot menu allowing a choice of OS. It goes straight into the windows xp loading screen.

Will reply to last post you made tomorrow. Thanks a million so far. Please bear with me and hopefully tomorrow everything will be done.

---

### Post by SANDKON on 2008-12-15
Is it a problem that I can't find a boot.ini file only a back up. Did search on XP partition including hidden files and no boot.ini? Before I set grub to MBR I would like to know if this is important.
Thanks

---

### Post by SANDKON on 2008-12-17
> **caljohnsmith said:**
> If you can't find a way to boot your Ubuntu drive, you could install Grub to the MBR of your sda drive and boot it that way. How about doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. Then reboot and let me know what happens.
 
Command output>

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

---

### Post by SANDKON on 2008-12-17
> **SANDKON said:**
> Command output>

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

on reboot grub error 5 noz cant boot into xp again

---

