---
title: "XP Primary/Logical Multiboot Issues After Ubuntu Install"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by span237 on 2009-03-29
Firstly I apologize for the length of this post - just trying to give as much info as possible.
 

The computer I'm working on originally had this setup:

C: XP Pro (Primary partition)
Extended Partition:
D: XP Home (logical)
E: XP Pro (logical)

I defragged and shrank the C: partition, leaving me with about 20GB of unallocated space. 

I installed Ubuntu using this unallocated space making:
/root ~9GB
/swap ~1GB
/home ~10GB

The result is shown in the attached screenshot from gparted.

The GRUB boot screen shows the usual Ubuntu entries, then 'Other Operating Systems' and then 'Windows NT/2000/XP (loader)' which takes me to the same operating system list I used to have with the 3 XP installations:

Windows XP Professional (C: )
Windows XP Home (D: )
Windows XP Professional (E: )

Here's where it gets confusing - 
**The XP Pro on the C: drive boots fine. The XP Home on the D: gives a 'hal.dll missing or corrupt' error, and the XP Pro on the E: actually boots the XP Home rather than the Pro edition it should.**

So, the XP install on the primary partition works fine, but the two on logical partitions are having some issues. :confused:

I've searched and read a fair bit about hal.dll and boot errors and understand that it's probably all still there, but the boot.ini file is a bit screwy. Unfortunately I'm still not sure how to attempt to fix this.

I ran the command posted by caljohnsmith in [his post here]("http://ubuntuforums.org/showpost.php?p=6497755&postcount=3").

Here's the result:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadcbadcb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,783,584     9,783,522   7 HPFS/NTFS
/dev/sda2          29,318,625   156,280,319   126,961,695   f W95 Ext d (LBA)
/dev/sda5          51,199,218    92,164,904    40,965,687   7 HPFS/NTFS
/dev/sda6          92,164,968   156,280,319    64,115,352   7 HPFS/NTFS
/dev/sda7          29,318,751    31,278,554     1,959,804  82 Linux swap / Solaris
/dev/sda8          31,278,618    51,199,154    19,920,537  83 Linux
/dev/sda3           9,783,585    29,318,624    19,535,040  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="00AC5097AC5088D4" TYPE="ntfs" 
/dev/sda3: UUID="ebe4d917-57b4-4beb-b4b0-c26749fc4f86" TYPE="ext3" 
/dev/sda5: UUID="C018A1AA18A1A040" TYPE="ntfs" 
/dev/sda6: UUID="2298752F98750299" LABEL="New Volume" TYPE="ntfs" 
/dev/sda7: TYPE="swap" UUID="b04116df-efc3-4c59-8106-cf872e8d2359" 
/dev/sda8: UUID="11937cb5-e195-41ca-b96e-ea55f3d31425" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


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
# kopt=root=UUID=ebe4d917-57b4-4beb-b4b0-c26749fc4f86 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ebe4d917-57b4-4beb-b4b0-c26749fc4f86

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ebe4d917-57b4-4beb-b4b0-c26749fc4f86
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ebe4d917-57b4-4beb-b4b0-c26749fc4f86 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ebe4d917-57b4-4beb-b4b0-c26749fc4f86
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ebe4d917-57b4-4beb-b4b0-c26749fc4f86 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ebe4d917-57b4-4beb-b4b0-c26749fc4f86
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ebe4d917-57b4-4beb-b4b0-c26749fc4f86 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ebe4d917-57b4-4beb-b4b0-c26749fc4f86
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ebe4d917-57b4-4beb-b4b0-c26749fc4f86 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ebe4d917-57b4-4beb-b4b0-c26749fc4f86
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ebe4d917-57b4-4beb-b4b0-c26749fc4f86 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=11937cb5-e195-41ca-b96e-ea55f3d31425 /home           ext3    relatime        0       2
# /dev/sda7
UUID=b04116df-efc3-4c59-8106-cf872e8d2359 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


   9.0GB: boot/grub/menu.lst
   9.0GB: boot/grub/stage2
   9.1GB: boot/initrd.img-2.6.27-11-generic
   9.1GB: boot/initrd.img-2.6.27-7-generic
   9.1GB: boot/vmlinuz-2.6.27-11-generic
   9.1GB: boot/vmlinuz-2.6.27-7-generic
   9.1GB: initrd.img
   9.1GB: initrd.img.old
   9.1GB: vmlinuz
   9.1GB: vmlinuz.old

```

Also my Boot.ini file:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

```

Any help/suggestions would be greatly appreciated.

---

### Post by cariboo on 2009-03-29
When you select Windows from the grub menu and it takes you to the Windows boot menu, your problem is probably with boot.ini, you will probably have to edit the file to point to the right partitions. I has nothing to do with grub.

Jim

---

### Post by span237 on 2009-03-29
Thanks cariboo907, I thought it might be something like that.

Any ideas on how to fix this issue? I'm not sure how to work out what about my boot.ini file is wrong (considering the changes to my partitions).

Would it also be an option to add the Windows entries to the GRUB menu.lst file, or will the boot.ini file still cause issues?

---

