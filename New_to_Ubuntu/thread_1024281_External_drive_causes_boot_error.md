---
title: "External drive causes boot error"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by mattcs on 2008-12-28
I have an external ntfs formatted drive connected via USB. When I boot (with it connected) I get:
GRUB Loading stage 1.5
GRUB loading please wait . . . 
Error 17
It's not a big issue as the drive is only for backups etc and I can simply connect it once the OS is up.
However, as I am new to Linux (Ubuntu), it would be nice to understand why :)
Thanks

---

### Post by caljohnsmith on 2008-12-28
It sounds like the reason is because you have Grub installed to the MBR of a different drive than the drive that has Grub's boot files (i.e the drive that has Ubuntu). In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the booting problem might be.

---

### Post by paydaydaddy on 2008-12-28
Check your bios with the external drive connected. Your computer may be trying to make the external drive the priority boot drive.I had a similar problem a while back, except that I did not get grub error. Your problem may not be related, but eliminate the simple things first.

---

### Post by mattcs on 2008-12-28
> **caljohnsmith said:**
> It sounds like the reason is because you have Grub installed to the MBR of a different drive than the drive that has Grub's boot files (i.e the drive that has Ubuntu). In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the booting problem might be.

Yes, I have two drives, one for Ubuntu and one for Win XP. I really have only been keeping the XP one for a particular multimedia app that I haven't as yet found a Linux equivalent for but I can live without it.

I would like to reformat that drive anyway and use it for something else. Can you suggest a safe strategy where I can install GRUB to the MBR of my 'Linux' drive. I will admit I was not exactly sure how I got the dual boot to work in the first place and now I don't need it any more.

Thanks

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 2048.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /grldr /Boot

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 1.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9aa39aa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195318269    97659103+  83  Linux
/dev/sda2       195318270   205085789     4883760   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:
omitting empty partition (5)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6dd82d47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   204812287   102405120    7  HPFS/NTFS
/dev/sdb2       204812685   625137344   210162330    f  W95 Ext'd (LBA)
/dev/sdb5       204812748   625137344   210162298+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: partition 1 does not end at a cylinder boundary

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f066c038-7279-44f6-8826-8a5cce30cbaf" TYPE="ext3" 
/dev/sda2: UUID="4eddeb8f-5c30-495a-8173-8decc4bb2ac9" TYPE="swap" 
/dev/sdb1: UUID="4EF2822DF282197B" TYPE="ntfs" 
/dev/sdb5: UUID="B6647CA8647C6CCD" LABEL="Local Disk" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mcsmith/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mcsmith)

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f066c038-7279-44f6-8826-8a5cce30cbaf ro

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
# defoptions=quiet splash xforcevesa

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f066c038-7279-44f6-8826-8a5cce30cbaf ro quiet splash xforcevesa noapic
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f066c038-7279-44f6-8826-8a5cce30cbaf ro single noapic
initrd        /boot/initrd.img-2.6.24-19-generic

# 20081128 mcsmith: commented out the following 4 lines
#title        Ubuntu 8.04.1, memtest86+
#root        (hd1,0)
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
#map        (hd0) (hd1)
#map        (hd1) (hd0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f066c038-7279-44f6-8826-8a5cce30cbaf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=4eddeb8f-5c30-495a-8173-8decc4bb2ac9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 54324
drwxr-xr-x  3 root root    4096 2008-12-10 20:01 .
drwxr-xr-x 21 root root    4096 2008-11-29 07:50 ..
-rw-r--r--  1 root root  422667 2008-08-21 14:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 13:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-25 08:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80049 2008-08-21 14:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 13:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-25 08:47 config-2.6.24-22-generic
drwxr-xr-x  2 root root    4096 2008-11-29 08:16 grub
-rw-r--r--  1 root root 7491538 2008-11-19 04:00 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7885217 2008-11-18 15:48 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7494292 2008-11-19 04:30 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7494552 2008-11-19 04:28 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7494458 2008-12-10 20:01 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7493918 2008-11-29 08:00 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 20:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 14:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 13:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-25 08:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921464 2008-08-21 14:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 13:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-25 08:47 vmlinuz-2.6.24-22-generic

=============================== sda1/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2008-11-29 08:16 .
drwxr-xr-x 3 root root   4096 2008-12-10 20:01 ..
-rw-r--r-- 1 root root    197 2008-11-18 15:48 default
-rw-r--r-- 1 root root     30 2008-11-18 15:48 device.map
-rw-r--r-- 1 root root   8056 2008-11-18 15:48 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-18 15:48 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-18 15:48 installed-version
-rw-r--r-- 1 root root   8608 2008-11-18 15:48 jfs_stage1_5
-rw-r--r-- 1 root root   4713 2008-11-29 08:16 menu.lst
-rw-r--r-- 1 root root   4653 2008-11-29 08:00 menu.lst~
-rw-r--r-- 1 root root   7324 2008-11-18 15:48 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-18 15:48 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-18 15:48 stage1
-rw-r--r-- 1 root root 108356 2008-11-18 15:48 stage2
-rw-r--r-- 1 root root   9276 2008-11-18 15:48 xfs_stage1_5

================================== sdb1/Boot: ==================================

total 768
drwxrwxrwx 1 root root   4096 2008-10-01 15:38 .
drwxrwxrwx 1 root root   8192 2008-12-13 06:18 ..
-rwxrwxrwx 1 root root  32768 2008-12-13 06:11 BCD
-rwxrwxrwx 1 root root 262144 2008-12-13 06:11 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-10-01 15:38 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-10-01 15:38 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-10-01 15:38 bootstat.dat
drwxrwxrwx 1 root root      0 2008-10-01 15:38 cs-CZ
drwxrwxrwx 1 root root      0 2008-10-01 15:38 da-DK
drwxrwxrwx 1 root root      0 2008-10-01 15:38 de-DE
drwxrwxrwx 1 root root      0 2008-10-01 15:38 el-GR
drwxrwxrwx 1 root root      0 2008-10-01 15:38 en-US
drwxrwxrwx 1 root root      0 2008-10-01 15:38 es-ES
drwxrwxrwx 1 root root      0 2008-10-01 15:38 fi-FI
drwxrwxrwx 1 root root   4096 2008-10-01 15:38 Fonts
drwxrwxrwx 1 root root      0 2008-10-01 15:38 fr-FR
drwxrwxrwx 1 root root      0 2008-10-01 15:38 hu-HU
drwxrwxrwx 1 root root      0 2008-10-01 15:38 it-IT
drwxrwxrwx 1 root root      0 2008-10-01 15:38 ja-JP
drwxrwxrwx 1 root root      0 2008-10-01 15:38 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-21 12:21 memtest.exe
drwxrwxrwx 1 root root      0 2008-10-01 15:38 nb-NO
drwxrwxrwx 1 root root      0 2008-10-01 15:38 nl-NL
drwxrwxrwx 1 root root      0 2008-10-01 15:38 pl-PL
drwxrwxrwx 1 root root      0 2008-10-01 15:38 pt-BR
drwxrwxrwx 1 root root      0 2008-10-01 15:38 pt-PT
drwxrwxrwx 1 root root      0 2008-10-01 15:38 ru-RU
drwxrwxrwx 1 root root      0 2008-10-01 15:38 sv-SE
drwxrwxrwx 1 root root      0 2008-10-01 15:38 tr-TR
drwxrwxrwx 1 root root      0 2008-10-01 15:38 zh-CN[/QUOTE]
drwxrwxrwx 1 root root      0 2008-10-01 15:38 zh-HK
drwxrwxrwx 1 root root      0 2008-10-01 15:38 zh-TW

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2008-12-29
OK, the good news is you all ready have Grub correctly installed to the MBR of your Ubuntu drive, but you also have Grub installed to the MBR of your Vista drive. That means if you get that Grub error 17 on start up, the Vista drive is being booted, and also that your USB drive is now the 2nd in the BIOS boot order; that's also confirmed by the fact that your Ubuntu entries in the Grub menu use (hd1,0) instead of (hd0,0) which would be the same drive. So to correct the problem, I would change all your Ubuntu entries in the Grub menu.lst to use (hd0,0), change your Vista entry to use (hd1,0) and mapping, and then if you make sure the Ubuntu drive gets booted first on start up (make it first in your BIOS boot order), I don't think you will see any more booting problems when you connect the USB drive. To open your menu.lst you could do:
```
gksudo gedit /boot/grub/menu.lst
```
And then change all the Ubuntu entries similar to:
```
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        [COLOR="Blue"](hd0,0)[/COLOR]
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=f066c038-7279-44f6-8826-8a5cce30cbaf ro quiet splash xforcevesa noapic
initrd        /boot/initrd.img-2.6.24-19-generic
quiet
```
Also, change your Vista entry at the bottom to use the following two entries:
```
title        Windows Vista (hd1)
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

title        Windows Vista (hd2)
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
```
Then if you boot your Ubuntu drive on start up, you should be able to boot Vista and Ubuntu no problem regardless of whether the USB drive is attached or not. It is necessary to use two possible entries for Vista since I don't know whether Vista will end up being the 2nd boot drive (hd1) or the 3rd boot drive (hd2) when you attach your USB drive. How about giving that a shot and let me know how it goes. :)

---

### Post by mattcs on 2008-12-29
Thank you, works fine (just had to change the boot order in my BIOS as well) but makes a bit more sense now.

---

### Post by caljohnsmith on 2008-12-29
Glad that did the trick; cheers and have fun with Vista and Ubuntu. :)

---

