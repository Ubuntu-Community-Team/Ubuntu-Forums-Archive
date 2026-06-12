---
title: "Windows MBR gone"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by tampablendie on 2009-05-17
hey guys I just installed 9.04 on my computer and somehow deleted my Windows MBR.  I am able to mount the drive which contains my Vista 64 OS.  Everything is there and looks good.

I have tried using the recovery/installation cd but the partition for my OS is not recognized.  I have Vista on my second HDD so I'm wondering if because it's on my second hard drive if it's not set up as a bootable partion?

My first hard drive had a 32bit version of vista that I was keeping around in case of application conflicts in 64bit OS.  I have had no issues with application conflicts on 64bit in the past 6 months, so I decided to scrap the 32 bit OS.  During the 9.04 install I selected use entire disk (for my first HDD).  I'm guessing that's where the MBR resided.

Any thoughts on my next steps?
Here is my bootinfo script results.
Thanks in advance.
> 
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   488,278,015   467,193,856  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb1f6480

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   807,825,399   807,823,352   7 HPFS/NTFS
/dev/sdb2         807,828,525   976,768,064   168,939,540   5 Extended
/dev/sdb5         807,828,588   969,795,854   161,967,267  83 Linux
/dev/sdb6         969,795,918   976,768,064     6,972,147  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0A13" TYPE="vfat" 
/dev/sda2: UUID="8A96FA3096FA1C7F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0" TYPE="ext3" 
/dev/sdb1: UUID="8A706F3B706F2CDF" LABEL="OS-64bit" TYPE="ntfs" 
/dev/sdb5: UUID="b672eb1f-bcae-4bf3-864d-088d6276cf00" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="56629312-ab1f-412e-953e-51955d999f04" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tampablendie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tampablendie)
/dev/sdb1 on /media/OS-64bit type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0

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
uuid		d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro quiet splash all_generic_ide floppy=off irqpoll 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro quiet splash all_generic_ide floppy=off irqpoll 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=56629312-ab1f-412e-953e-51955d999f04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 133.6GB: boot/grub/menu.lst
 133.6GB: boot/grub/stage2
 133.7GB: boot/initrd.img-2.6.28-11-generic
 133.6GB: boot/vmlinuz-2.6.28-11-generic
 133.7GB: initrd.img
 133.6GB: vmlinuz

=========================== sdb5/boot/grub/menu.lst: ===========================

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
default		4

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
# kopt=root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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
# defoptions=quiet splash all_generic_ide floppy=off irqpoll

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro quiet splash all_generic_ide floppy=off irqpoll
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro quiet splash all_generic_ide floppy=off irqpoll
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=56629312-ab1f-412e-953e-51955d999f04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 462.2GB: boot/grub/menu.lst
 462.1GB: boot/grub/stage2
 462.2GB: boot/initrd.img-2.6.24-23-generic
 462.2GB: boot/initrd.img-2.6.24-23-generic.bak
 462.2GB: boot/initrd.img-2.6.24-24-generic
 462.2GB: boot/initrd.img-2.6.24-24-generic.bak
 462.2GB: boot/vmlinuz-2.6.24-23-generic
 462.2GB: boot/vmlinuz-2.6.24-24-generic
 462.2GB: initrd.img
 462.2GB: initrd.img.old
 462.2GB: vmlinuz
 462.2GB: vmlinuz.old

---

### Post by tampablendie on 2009-05-17
bump

---

### Post by kansasnoob on 2009-05-17
Are you currently able to boot into both Ubuntu 9.04 and the Ubuntu 8.04.2 on sdb5?

---

### Post by kansasnoob on 2009-05-17
I suppose it doesn't matter much at this point if you can boot into 8.04.2 or not, I was just curious, but my thought is to edit 9.04's /boot/grub/menu.lst (using the command **sudo gedit /boot/grub/menu.lst** and of course choosing to Save changes) as below:

> ## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0 ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid d9559f11-d9c6-4ad0-bc3d-6babfe9d86a0
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

[B]# This entry manually added for a non-linux OS
# on /dev/sdb1
title        Windows Vista
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1[/B]


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sdb5)
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=b672eb1f-bcae-4bf3-864d-088d6276cf00 ro quiet splash all_generic_ide floppy=off irqpoll
initrd /boot/initrd.img-2.6.24-24-generic
savedefault
boot


The section I'm suggesting you add to 9.04's menu list is in **bold**.

If that doesn't work you can color me stumped!

---

### Post by egalvan on 2009-05-17
> **kansasnoob said:**
> ... my thought is to edit 9.04's /boot/grub/menu.lst 
(using the command **sudo gedit /boot/grub/menu.lst** and of course choosing to Save changes) as below:




Shouldn't that be:

**[COLOR="Red"]gksudo[/COLOR] gedit /boot/grub/menu.lst**

??

---

### Post by egalvan on 2009-05-17
> **tampablendie said:**
> hey guys I just installed 9.04 on my computer and somehow deleted my Windows MBR.

**first hard drive** had a 32bit version of vista ... decided to scrap the 32 bit OS.
 During the 9.04 install** I [COLOR="Red"]selected use entire disk[/COLOR] **(for my first HDD).  I'm guessing that's where the MBR resided.

Here is bootinfo script results.


**[COLOR="Red"]sda1[/COLOR]**: ___________________________________________________
File system:** vfat**
Boot sector type: **Dell Utility: Fat16**
Boot sector info: No errors found...
Operating System:
Boot files/dirs:

**[COLOR="Red"]sda2[/COLOR]**: __________________________________________________
File system:** ntfs**
Boot sector type: **Windows Vista**
Boot sector info: No errors found...
Operating System:** Windows Vista**
Boot files/dirs:

**[COLOR="Red"]sda3[/COLOR]**: __________________________________________________
File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab


You selected to use the entire first hard drive for Ubuntu install...

So did you choose to keep the first two partitions as Windows-type?

---

### Post by tampablendie on 2009-05-17
ok I edited the grub as you suggested, and tried to boot to vista and got the error BOOTMGR missing.  I'm googling now to see if I can find a generic bootmgr file and put it in the correct location for the OS because I have that drive mounted in Ubuntu.

Any other ideas welcomed!

---

### Post by kansasnoob on 2009-05-17
> **egalvan said:**
> Shouldn't that be:

**[COLOR="Red"]gksudo[/COLOR] gedit /boot/grub/menu.lst**

??

Actually either will work in that specific situation, but you do have a valid point. Aysiu explains it very well here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by kansasnoob on 2009-05-17
You may be able to find the answer here:

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

Nearly at the end there's a section:

> WINDOWS VISTA SECTION
and WINDOWS 7

And a subsection:

> BOOTMGR is missing (Vista/XP dual boot when adding Ubuntu)


---

### Post by egalvan on 2009-05-17
> **kansasnoob said:**
> Actually either will work in that specific situation, but you do have a valid point. Aysiu explains it very well here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Yep, that's exactly where I found the info.

aysiu has some amazing info there....

should be mandatory reading for all Ubuntu users... ;)

along with Herman's web site...

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

):P

---

### Post by tampablendie on 2009-05-17
O.K.  I got Vista up and running.  

Looks like Vista looks for the BOOTMGR file from the first boot drive (even if the OS is on the second!!)

So I went into the BIOS and changed the boot order on my drives.

I was then able to use the Windows installation DVD to repair the startup options.  I think the BOOTMGR has now been placed on my second drive.

I'm now going to reboot, switch the boot order back and see if I can launch Vista from the grub menu.  I'll post a report in a couple of minutes.

---

### Post by tampablendie on 2009-05-17
Success!

Thanks for the insight guys everything is now in order.

---

