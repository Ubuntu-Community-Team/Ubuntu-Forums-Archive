---
title: "Windows 7 is not loading.."
date: 2010-02-14
forum: New to Ubuntu
---

### Post by shoosha on 2010-02-14
Hello,

I installed Windows 7 on my system and then proceeded to install ubuntu. However as soon as I did that and rebooted my computer I am able to load ubuntu, but windows selection was throwing 

**Error12: Invalid Device Requested** 

So I searched this forum and arrived at this thread: [http://ubuntuforums.org/showthread.php?t=1123109](http://ubuntuforums.org/showthread.php?t=1123109)

I followed the first reply from there and went ahead and downloaded bootinfoscript from [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Here is what I got in the resulting Result.txt

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x232f232e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   142,234,764   142,234,702   7 HPFS/NTFS
/dev/sda2         142,239,510   461,210,084   318,970,575   f W95 Ext d (LBA)
/dev/sda5         282,952,908   407,837,004   124,884,097   7 HPFS/NTFS
/dev/sda6         407,838,720   461,209,599    53,370,880  82 Linux swap / Solaris
/dev/sda7         142,239,636   282,952,844   140,713,209  83 Linux
/dev/sda3    *    461,210,085   488,375,999    27,165,915  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E0A84EEAA84EBEB2                       ntfs                                     
/dev/sda3        fd71de80-006c-4172-a5eb-048311d16350   swap                                     
/dev/sda5        6C30C7B230C78216                       ntfs       WinXp                         
/dev/sda7        3def4a7f-5466-4744-8c98-ac6cd2bdc608   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3def4a7f-5466-4744-8c98-ac6cd2bdc608

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3def4a7f-5466-4744-8c98-ac6cd2bdc608
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3def4a7f-5466-4744-8c98-ac6cd2bdc608
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3def4a7f-5466-4744-8c98-ac6cd2bdc608
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows NT/2000/XP
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=fd71de80-006c-4172-a5eb-048311d16350 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 115.3GB: boot/grub/menu.lst
 115.2GB: boot/grub/stage2
 115.3GB: boot/initrd.img-2.6.28-11-generic
 115.2GB: boot/vmlinuz-2.6.28-11-generic
 115.3GB: initrd.img
 115.2GB: vmlinuz
=============================== StdErr Messages: ===============================

blkid: invalid option -- 'p'
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghlLv] [-o format] [-s <tag>] [-t <token>]
    [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)
blkid: invalid option -- 'p'
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghlLv] [-o format] [-s <tag>] [-t <token>]
    [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)
``` 





And from then onwards I went ahead and followed reply number 5 in that same thread, I edited the menu.lst with following changes

"root (hd0,4)" in the Windows entry to "root (hd0,0)".

And then put in the windows 7 dvd, did the repair got to the command prompt and executed the **bootrec /fixboot** command succesfully.

Now when I select the windows option it gives a "**BOOTMGR is missing**" error. I would really appreciate it, if someone can help me solve this issue, thanks!

---

### Post by louieb on 2010-02-14
looks like you have done every thing I would try.

One thing - the boot flag - use Gparted and set the boot flag on sda1 - currently on sda3 for some unknown reason.  I've read that Win7 does not care if the boot flag is set or not - but earlier versions of windows did require the flag be set on their install partition. 

Then try the bootrec /fixboot command again. Believe the boot flag is how the program know which partition to fix the boot sector on. 

Also double check the change made to the root statement  should be root (hd0,0)

---

### Post by kio_http on 2010-02-14
Boot your Windows 7 DVD and run the Startup Repair option. This will restore windows's boot. Then in Windows add an entry for Ubuntu using Easy BCD 2 beta. Note Easy BCD 2 is the only one compatible for Ubuntu 9.10. Version 1 will not work.

---

### Post by meierfra. on 2010-02-14
> use Gparted and set the boot flag on sda

Also double check the change made to the root statement should be root (hd0,0)

I agree.
>   Operating System:  Windows 7
Boot files/dirs:   /Windows/System32/winload.exe

The boot files (/bootmgr and /boot/bcd) for Window 7 are missing.

To fix it boot from your Window 7 CD/DVD.  At the screen where you can choose the "command prompt" choose "Startup Repair"

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

This should be enough to get Window 7 booting. You will have to do some more work to boot Windows XP, but we'll worry about that later.

---

### Post by sandyd on 2010-02-14
> **shoosha said:**
> Hello,

I installed Windows 7 on my system and then proceeded to install ubuntu. However as soon as I did that and rebooted my computer I am able to load ubuntu, but windows selection was throwing 

**Error12: Invalid Device Requested** 

So I searched this forum and arrived at this thread: [http://ubuntuforums.org/showthread.php?t=1123109](http://ubuntuforums.org/showthread.php?t=1123109)

I followed the first reply from there and went ahead and downloaded bootinfoscript from [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Here is what I got in the resulting Result.txt

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x232f232e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   142,234,764   142,234,702   7 HPFS/NTFS
/dev/sda2         142,239,510   461,210,084   318,970,575   f W95 Ext d (LBA)
/dev/sda5         282,952,908   407,837,004   124,884,097   7 HPFS/NTFS
/dev/sda6         407,838,720   461,209,599    53,370,880  82 Linux swap / Solaris
/dev/sda7         142,239,636   282,952,844   140,713,209  83 Linux
/dev/sda3    *    461,210,085   488,375,999    27,165,915  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E0A84EEAA84EBEB2                       ntfs                                     
/dev/sda3        fd71de80-006c-4172-a5eb-048311d16350   swap                                     
/dev/sda5        6C30C7B230C78216                       ntfs       WinXp                         
/dev/sda7        3def4a7f-5466-4744-8c98-ac6cd2bdc608   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3def4a7f-5466-4744-8c98-ac6cd2bdc608

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3def4a7f-5466-4744-8c98-ac6cd2bdc608
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3def4a7f-5466-4744-8c98-ac6cd2bdc608
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3def4a7f-5466-4744-8c98-ac6cd2bdc608
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows NT/2000/XP
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=3def4a7f-5466-4744-8c98-ac6cd2bdc608 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=fd71de80-006c-4172-a5eb-048311d16350 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 115.3GB: boot/grub/menu.lst
 115.2GB: boot/grub/stage2
 115.3GB: boot/initrd.img-2.6.28-11-generic
 115.2GB: boot/vmlinuz-2.6.28-11-generic
 115.3GB: initrd.img
 115.2GB: vmlinuz
=============================== StdErr Messages: ===============================

blkid: invalid option -- 'p'
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghlLv] [-o format] [-s <tag>] [-t <token>]
    [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)
blkid: invalid option -- 'p'
blkid 1.0.0 (12-Feb-2003)
usage:	blkid [-c <file>] [-ghlLv] [-o format] [-s <tag>] [-t <token>]
    [-w <file>] [dev ...]
	-c	cache file (default: /etc/blkid.tab, /dev/null = none)
	-h	print this usage message and exit
	-g	garbage collect the blkid cache
	-s	show specified tag(s) (default show all tags)
	-t	find device with a specific token (NAME=value pair)
	-l	lookup the the first device with arguments specified by -t
	-v	print version and exit
	-w	write cache to different file (/dev/null = no write)
	dev	specify device(s) to probe (default: all devices)
``` 





And from then onwards I went ahead and followed reply number 5 in that same thread, I edited the menu.lst with following changes

"root (hd0,4)" in the Windows entry to "root (hd0,0)".

And then put in the windows 7 dvd, did the repair got to the command prompt and executed the **bootrec /fixboot** command succesfully.

Now when I select the windows option it gives a "**BOOTMGR is missing**" error. I would really appreciate it, if someone can help me solve this issue, thanks!

why does everyone end up falling into the trap of not defragging and resizing using the windows 7 partition manager?

p.s. 
see if these work. (not sure if these files are computer specific...)

---

### Post by meierfra. on 2010-02-14
> why does everyone end up falling into the trap of not defragging and resizing using the windows 7 partition manager?
????  this does not cause missing boot files. 


> see if these work. (not sure if these files are computer specific...) 

bootmgr is not specfic, but bcd is (at least most versions). 
Anyway, "startup repair" in general does a  good job restoring the boot files. 

PS:  I don't think it's appropriate to ask the OP to download a file whose contents one does not understand.

---

### Post by shoosha on 2010-02-14
thanks a lot for the replies and sugguestions guys. Actually I solved the issue last night itself (10 mins after posting this thread). 

All I did to fix the issue, was copied the bootmgr file from my friends working win 7 laptop and pasted that on my root, and voilaa!! 

thanks again, fellas!

---

### Post by meierfra. on 2010-02-14
> Actually I solved the issue last night itself (10 mins after posting this thread). 
Thanks for letting as know so soon.;)

> was copied the bootmgr file from my friends working win 7 laptop and pasted that on my root, and voilaa!! 

You must have done more than  that( at least after you run the boot info script)  since you were missing other  boot files. But no need to argue.

---

