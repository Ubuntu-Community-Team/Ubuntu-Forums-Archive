---
title: "I need a bit of help with grub..."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by LostMagix on 2009-01-24
I have installed XP on a unused partition and im not sure how to get it in the grub menu. I have been searching the forums but havnt found anything that reallys helps me.

I downloaded "boot_info_script021.sh" here is what came out...

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00082154

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   39,070,079   39,070,017   b W95 FAT32


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43434343

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63  330,071,489  330,071,427  83 Linux
/dev/sdb2        482,351,625  488,392,064    6,040,440   5 Extended
/dev/sdb5        482,351,688  488,392,064    6,040,377  82 Linux swap / Solaris
/dev/sdb3        330,071,490  482,351,624  152,280,135   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80808080

Partition  Boot        Start          End         Size  Id System

/dev/sdc1    *            63   78,156,224   78,156,162  83 Linux


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot        Start          End         Size  Id System

/dev/sdd1    *            63    7,855,784    7,855,722   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="495F-D238" TYPE="vfat" 
/dev/sdb1: UUID="e530acd2-76fc-438d-be2c-4176c53de7a4" TYPE="ext3" 
/dev/sdb3: UUID="15E5D1602071EC2B" TYPE="ntfs" 
/dev/sdb5: UUID="9eb05ab3-1293-45d6-9752-a6d1580e8bf0" TYPE="swap" 
/dev/sdc1: UUID="f76a8c9a-ea21-4e44-9020-642ca2a553e2" TYPE="ext2" 
/dev/sdd1: UUID="495E-EB9B" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lost/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lost)
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb3 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Unidentified operating system on drive C."


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e530acd2-76fc-438d-be2c-4176c53de7a4

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
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9eb05ab3-1293-45d6-9752-a6d1580e8bf0 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location  of files loaded by Grub: ===================


  69.2GB: boot/grub/menu.lst
  69.1GB: boot/grub/stage2
  69.2GB: boot/initrd.img-2.6.27-11-generic
  69.1GB: boot/initrd.img-2.6.27-7-generic
  69.1GB: boot/initrd.img-2.6.27-9-generic
  69.1GB: boot/vmlinuz-2.6.27-11-generic
  69.1GB: boot/vmlinuz-2.6.27-7-generic
  69.1GB: boot/vmlinuz-2.6.27-9-generic
  69.2GB: initrd.img
  69.1GB: initrd.img.old
  69.1GB: vmlinuz
  69.1GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.
```


I know this is very simple, but I have never played with grub and I dont want to break it :/

---

### Post by LostMagix on 2009-01-24
Windows XP is on /dev/sdb3

---

### Post by chronographer on 2009-01-24
Hi

You can add something like the code below (which is from my grub) to your /boot/grub/menu.lst (edit it with gksu gedit /boot/grub/menu.lst).

Don't worry, if you don't delete anything from grub then you can't break anything! If you do break something we can fix it!

in your case you should change the location of windows to /dev/sda which is hd0,0 (see below) so you can probably just use the same code as mine bewlo.




```
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
```

---

### Post by toopi on 2009-01-24
> **LostMagix said:**
> Windows XP is on /dev/sdb3

Because it's on sdb3, it'll be:
```
(hd1,2)
```

hd1 -- because it's at sdb
2 -- because it's at the 3rd partition, and count starts at 0.

Does it work?  =)

---

### Post by LostMagix on 2009-01-25
With ether lable i get "errror 13 invald or unsupported extention format" after i choose windows XP in the grub menu

---

### Post by toopi on 2009-01-25
Can you post your menu.lst after you edited it?  The follwing will do:
```
 cat /boot/grub/menu.lst 
```

---

### Post by LostMagix on 2009-01-25
```
:~$  cat /boot/grub/menu.lst
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
# kopt=root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e530acd2-76fc-438d-be2c-4176c53de7a4

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
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root


title		Microsoft Windows XP Professional
root		(hd1,2)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```


I hope this helps...

---

### Post by toopi on 2009-01-25
Try putting the Windows XP stanza after
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST 
```

---

### Post by LostMagix on 2009-01-25
The grub loader came back with "error 22: no such partition"

---

### Post by LostMagix on 2009-01-25
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST


title		Other operating systems:
root


title		Microsoft Windows XP Professional
root		(hd1,2)
savedefault
makeactive
chainloader	+1
```

---

### Post by toopi on 2009-01-25
> **LostMagix said:**
> The grub loader came back with "error 22: no such partition"

I did a little research and landed at this [page]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows").  It seems like you'll have to map the drive since XP is not on the first drive.  I'll be back with something after thinking more into it.  Of course, you'll come up with something too, after reading it.  :)

---

### Post by toopi on 2009-01-25
Try this:

```

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,2)
makeactive
chainloader +1

```

---

### Post by LostMagix on 2009-01-25
I read over that a few times, but im having trouble grasping exactly what I need to do...


While I have used Ubuntu for a while, im just now learning how to really USE it, I still kinda need things explained to me.

---

### Post by LostMagix on 2009-01-25
> **toopi said:**
> Try this:

```

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,2)
makeactive
chainloader +1

```

Returned with Error 22

---

### Post by toopi on 2009-01-25
> **LostMagix said:**
> I read over that a few times, but im having trouble grasping exactly what I need to do...


While I have used Ubuntu for a while, im just now learning how to really USE it, I still kinda need things explained to me.

Yes, it's complicated.  All you need is patience here.  :)

This is also my first time trying to boot windows that does not reside in the first drive.  So, bear with me here.

---

### Post by LostMagix on 2009-01-25
> **toopi said:**
> Yes, it's complicated.  All you need is patience here.  :)

This is also my first time trying to boot windows that does not reside in the first drive.  So, bear with me here.

Take as much time as you need, I'm in no hurry and I appreciate the help.

---

### Post by toopi on 2009-01-25
Could you also give me the output of
```
 sudo fdisk -l 
```

Edit:
How about like this:
```

title Microsoft Windows XP Professional
rootnoverify (hd1,2)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

```

---

### Post by LostMagix on 2009-01-25
```
:~$  sudo fdisk -l
[sudo] password for lost: 

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00082154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43434343

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20546   165035713+  83  Linux
/dev/sdb2           30026       30401     3020220    5  Extended
/dev/sdb3           20547       30025    76140067+   7  HPFS/NTFS
/dev/sdb5           30026       30401     3020188+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80808080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4865    39078081   83  Linux
/dev/sdc4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdd: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         489     3927861    b  W95 FAT32

```


Rebooting now

---

### Post by LostMagix on 2009-01-25
```
title	Microsoft Windows XP Professional
rootnoverify	(hd1,2)
map 	(hd0) (hd1)
map 	(hd1) (hd0)
makeactive
chainloader +1
```

error 22

---

### Post by toopi on 2009-01-25
> **LostMagix said:**
> ```
title	Microsoft Windows XP Professional
rootnoverify	(hd1,2)
map 	(hd0) (hd1)
map 	(hd1) (hd0)
makeactive
chainloader +1
```

error 22

Thought so... :D

I'm trying grasp these threads.  They have sort of similar problems, and I'm trying to apply those to yours.  This is just for the record when people later come and search for solutions.

[http://www.linuxquestions.org/questions/linux-software-2/grub-error-dual-booting-linux-and-winxp-371087/](http://www.linuxquestions.org/questions/linux-software-2/grub-error-dual-booting-linux-and-winxp-371087/)

[http://www.linuxforums.org/forum/installation/56461-grub-menu-lst-chainloader-help-needed.html](http://www.linuxforums.org/forum/installation/56461-grub-menu-lst-chainloader-help-needed.html)

[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)

---

### Post by LostMagix on 2009-01-25
Would it help if i just swiched the sata cables for /dev/sdb and /dev/sda

---

### Post by toopi on 2009-01-25
> **LostMagix said:**
> Would it help if i just swiched the sata cables for /dev/sdb and /dev/sda

I was just thinking about it.  It might solve a lot of the problems we're facing now, i.e. placing the drive that contains XP as the first drive.

Right now, your Ubuntu partition is on sdb1.  After you switch it, it should become sda1.  In case you can't boot back into Ubuntu,

- Boot into Live CD
- type "sudo grub" into Terminal (you'll get into the GRUB command-line mode)
- Assuming Ubuntu is on /dev/sda, enter the following:
```

device (hd0) /dev/sda
root (hd0,0)
setup (hd0)
quit

```

There shouldn't be any errors from the output.  Goodluck!  :)

---

### Post by LostMagix on 2009-01-25
This is what i have now.....

```
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
# kopt=root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e530acd2-76fc-438d-be2c-4176c53de7a4

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
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST


title		Other operating systems:
root


title		 Microsoft Windows XP Professional
rootnoverify		 (hd1,2)
map 		(hd0) (hd1)
map 		(hd1) (hd0)
makeactive
chainloader +1
```


```
:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43434343

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20546   165035713+  83  Linux
/dev/sda2           30026       30401     3020220    5  Extended
/dev/sda3           20547       30025    76140067+   7  HPFS/NTFS
/dev/sda5           30026       30401     3020188+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80808080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         489     3927861    b  W95 FAT32

```

---

### Post by LostMagix on 2009-01-25
I just unpluged the 20GB HDD, i didnt really need it for anything.

---

### Post by toopi on 2009-01-25
Replace the stanza with the following:
```

title Microsoft Windows XP Professional
root (hd0,2)
makeactive
chainloader +1

```

Cross your fingers =)

It'd be really helpful if there's another computer nearby, because you can actually edit the GRUB menu on the fly and test it without needing to reboot after every changes.  And I think it'd be more productive if we're on an IRC or chat.

---

### Post by LostMagix on 2009-01-25
Now i got "bootmgr missing"

Im assuming this means that something went wrong when I installed windows. I used a XP sp3 install ISO from a questionable source, so that may be it also.

Unless you think this may still be a grub problem, I have been wanting to try windows 7 so I could just put that on that extra partition.

---

### Post by toopi on 2009-01-25
Now, at least we know that we got the right partition.

Let's fix the Windows partition first.

I can't quite recall the exact procedure, but after you pop in your XP cd, you'll have to press "R" and get into the console.  Then you type in:
```
 fixboot 
```
```
 fixmbr 
```
You should now be able to boot into XP, but the GRUB is gone for now.

To get back the GRUB menu,
- Boot into Live CD
- In Terminal ```
 sudo grub-install /dev/sda 
```
Then ```
 sudo update-grub 
```
That should install GRUB, and it should also find the Windows XP partition.  If not, then I'm a bit clueless.

Edit:  BRB tomorrow.  A bit late here.

---

### Post by caljohnsmith on 2009-01-25
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by LostMagix on 2009-01-25
XP in now working, no grub and this is from live boot....


```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43434343

Partition  Boot        Start          End         Size  Id System

/dev/sda1                 63  330,071,489  330,071,427  83 Linux
/dev/sda2    *   330,071,490  482,351,624  152,280,135   7 HPFS/NTFS
/dev/sda3        482,351,625  488,392,064    6,040,440   5 Extended
/dev/sda5        482,351,688  488,392,064    6,040,377  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80808080

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63   78,156,224   78,156,162  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot        Start          End         Size  Id System

/dev/sdc1    *            63    7,855,784    7,855,722   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="e530acd2-76fc-438d-be2c-4176c53de7a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="15E5D1602071EC2B" TYPE="ntfs" 
/dev/sda5: UUID="9eb05ab3-1293-45d6-9752-a6d1580e8bf0" TYPE="swap" 
/dev/sdb1: UUID="f76a8c9a-ea21-4e44-9020-642ca2a553e2" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: UUID="495E-EB9B" TYPE="vfat" 

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
/dev/scd2 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

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
# kopt=root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e530acd2-76fc-438d-be2c-4176c53de7a4

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
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e530acd2-76fc-438d-be2c-4176c53de7a4
kernel		/boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST


title		Other operating systems:
root


title Microsoft Windows XP Professional
root (hd0,2)
makeactive
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e530acd2-76fc-438d-be2c-4176c53de7a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9eb05ab3-1293-45d6-9752-a6d1580e8bf0 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  69.2GB: boot/grub/menu.lst
  69.1GB: boot/grub/stage2
  69.2GB: boot/initrd.img-2.6.27-11-generic
  69.1GB: boot/initrd.img-2.6.27-7-generic
  69.1GB: boot/initrd.img-2.6.27-9-generic
  69.1GB: boot/vmlinuz-2.6.27-11-generic
  69.1GB: boot/vmlinuz-2.6.27-7-generic
  69.1GB: boot/vmlinuz-2.6.27-9-generic
  69.2GB: initrd.img
  69.1GB: initrd.img.old
  69.1GB: vmlinuz
  69.1GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-25
OK, how about from your Live CD do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change your Windows entry at the bottom to be:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd0,1)[/COLOR]
makeactive
chainloader +1
```
Reboot, try both Ubuntu and Windows from your Grub menu, and let me know how far you get. We can work from there if necessary.

---

### Post by LostMagix on 2009-01-25
This post is just for record...


Your grub folder is missing quiet a few files.
Please copy all the files from

/usr/lib/grub/i386-pc
to
/boot/grub

Then you can reinstall grub

sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1

One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
Code:

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit





I am trying a how-to found at [https://answers.launchpad.net/ubuntu/+source/grub/+question/51306]("https://answers.launchpad.net/ubuntu/+source/grub/+question/51306")

---

### Post by toopi on 2009-01-25
It's weird that Windows partition changes from sda3 to sda2...

I'm awaiting results also...  =)

---

### Post by LostMagix on 2009-01-25
Im sorry, i got tied up with googlizing, forgot to hit refresh....

---

### Post by toopi on 2009-01-25
> **LostMagix said:**
> Im sorry, i got tied up with googlizing, forgot to hit refresh....

No worries.  Happened to me a lot too.  I had to subscribe it via instant email.  Gmail does a nice job in that their mail servers push the new email to you, so no more refreshes.  :)

---

### Post by LostMagix on 2009-01-25
That did it, i can boot both the XP and Ubuntu partitions.




Thanks for your time, you have been a tremendous help and i have learn quite a bit from this.

---

### Post by caljohnsmith on 2009-01-25
Glad that's all it took to get Windows and Ubuntu booting OK; cheers and enjoy Windows and Ubuntu. :)

---

### Post by LostMagix on 2009-01-25
Where is the "thanks" button, I dont see it any more....

---

### Post by LostMagix on 2009-01-25
and the "mark as solved" isn't under thread tools any more....


Where did they change the forums up?

---

### Post by overdrank on 2009-01-25
> **LostMagix said:**
> and the "mark as solved" isn't under thread tools any more....


Where did they change the forums up?

It has been temporarily disabled :)

---

### Post by toopi on 2009-01-25
I guess they changed the forum layout a bit.  I guess people were not using the "SOLVED" enough.  Could it be the forum is going under certain maintainance?

EDIT:  Nevermind.  overdrank clarified it.  Thanks overdrank.

---

### Post by LostMagix on 2009-01-25
Owell, this will have to do under the circumstances...


This thread = SOLVED! :p

---

