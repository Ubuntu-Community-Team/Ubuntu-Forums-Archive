---
title: "Boot Problem for Jaunty"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by grewolf on 2009-06-24
To See output from Boot Info Script Item on bottom portion of this post.  



I had 4 HDD.  2 were 500 GB sata drives one with Ubuntu Intrepid Ibex on it and the other with windows xp on it.  The other 2 were 160 gb IDE drives one with windows 7 beta on it and the other with Ubuntu Gutsy Gibbon on it.  I was able to boot Into Ibex and then select any of the others from the menu list.  I tried to install Jaunty on the IDE drive that had windows 7 beta on it.  Didn't work wasn't able to boot anything.  Followed the instructions in this post  [http://ubuntuforums.org/showthread.php?p=7191858]("http://ubuntuforums.org/showthread.php?p=7191858") and still didn't work.

I now bought 2 new 1 TB hard drives and loaded Jaunty on one.  I can now boot Jaunty and windows xp but can not access Intrepid 

Hear is the grub list from Jaunty
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
# kopt=root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e315702d-f8a4-4023-ad22-71c2d48e4a87

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#This is to try and dual boot Windows
title	   Windows XP (hd2)
rootnoverify       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```

here is the grub list from Intrepid

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
# kopt=root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd363224-32e5-4cec-824e-4a9dc02367d4

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is to try and dual boot Windows
title	   Windows XP (hd3)
rootnoverify       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```

and here is the output from the Boot Info Script from source forge 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002f63f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,932,346,394 1,932,346,332  83 Linux
/dev/sda2       1,932,346,395 1,953,520,064    21,173,670   5 Extended
/dev/sda5       1,932,346,458 1,953,520,064    21,173,607  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc46dc46

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   971,530,874   971,530,812   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49ace41c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   955,498,004   955,497,942  83 Linux
/dev/sdc2         955,498,005   976,768,064    21,270,060   5 Extended
/dev/sdc5         955,498,068   976,768,064    21,269,997  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00090585

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="e315702d-f8a4-4023-ad22-71c2d48e4a87" TYPE="ext3" 
/dev/sda5: UUID="283a1431-60c0-4344-82db-4ae3d4cbeb97" TYPE="swap" 
/dev/sdb1: UUID="86208ABB208AB22B" TYPE="ntfs" 
/dev/sdc1: UUID="dd363224-32e5-4cec-824e-4a9dc02367d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="d586d939-ad45-4d41-b4a9-56c9a08182d9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jwilson/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jwilson)


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
# kopt=root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e315702d-f8a4-4023-ad22-71c2d48e4a87

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e315702d-f8a4-4023-ad22-71c2d48e4a87
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#This is to try and dual boot Windows
title	   Windows XP (hd2)
rootnoverify       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e315702d-f8a4-4023-ad22-71c2d48e4a87 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=283a1431-60c0-4344-82db-4ae3d4cbeb97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 832.6GB: boot/grub/menu.lst
 832.6GB: boot/grub/stage2
 832.6GB: boot/initrd.img-2.6.28-11-generic
 832.6GB: boot/initrd.img-2.6.28-13-generic
 832.6GB: boot/vmlinuz-2.6.28-11-generic
 832.6GB: boot/vmlinuz-2.6.28-13-generic
 832.6GB: initrd.img
 832.6GB: initrd.img.old
 832.6GB: vmlinuz
 832.6GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER


=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd363224-32e5-4cec-824e-4a9dc02367d4

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05f6e796-b299-4d9a-b932-91fe117bba68 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

#This is to try and dual boot Windows
title	   Windows XP (hd3)
rootnoverify       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1


=============================== sdc1/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 /               ext3    relatime,errors=remount-ro 0       1
UUID=d586d939-ad45-4d41-b4a9-56c9a08182d9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 466.0GB: boot/grub/menu.lst
 402.7GB: boot/grub/stage2
 146.2GB: boot/initrd.img-2.6.27-11-generic
 147.8GB: boot/initrd.img-2.6.27-14-generic
 402.8GB: boot/initrd.img-2.6.27-7-generic
 402.8GB: boot/initrd.img-2.6.27-9-generic
 118.9GB: boot/vmlinuz-2.6.27-11-generic
  77.8GB: boot/vmlinuz-2.6.27-14-generic
 402.8GB: boot/vmlinuz-2.6.27-7-generic
 402.8GB: boot/vmlinuz-2.6.27-9-generic
 147.8GB: initrd.img
 146.2GB: initrd.img.old
  77.8GB: vmlinuz
 118.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sde 
```

---

### Post by jimv on 2009-06-24
What exactly is happening...are you getting an error message when you try to boot Intrepid, or are you missing the grub entry for Intrepid altogether?

I assume you want everything to show up on the same boot screen, so try running this to backup and then regenerate your boot list:

sudo cp /boot/grub/menu.lst /boot/grub/menu.backup
sudo update-grub

---

### Post by grewolf on 2009-06-24
> **jimv said:**
>   I assume you want everything to show up on the same boot screen, so try running this to backup and then regenerate your boot list:

sudo cp /boot/grub/menu.lst /boot/grub/menu.backup
sudo update-grub

You are correct.  I have tried this with no luck.  Can I copy and paste part of the intrepid grub into the grub lst for Jaunty, or will that mess up booting altogether?

---

### Post by jimv on 2009-06-24
Yeah, you can put these lines in your Jaunty menu.list

```
title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

```

---

### Post by grewolf on 2009-06-24
This worked perfectly.  Thank you



> **jimv said:**
> Yeah, you can put these lines in your Jaunty menu.list

```
title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		dd363224-32e5-4cec-824e-4a9dc02367d4
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=dd363224-32e5-4cec-824e-4a9dc02367d4 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

```

---

