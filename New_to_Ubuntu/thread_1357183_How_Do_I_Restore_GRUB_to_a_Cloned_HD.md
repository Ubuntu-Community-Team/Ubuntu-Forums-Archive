---
title: "How Do I Restore GRUB to a Cloned HD?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by mulluysavage on 2009-12-16
I decided the way to back up my system was to clone my partition. I did this on a 60GB HD. To test it, I tried setting this as the boot HD. It didn't boot - it just filled the screen up with the word "GRUB". I figure it didn't clone my grub right and I need to re-install it. 

Hod do I figure out the (hdx,x) to install it to? If I go find /boot/grub/stage1, which HD will it be looking at (I have both my system and the backup clone installed at the moment)

---

### Post by presence1960 on 2009-12-16
> **mulluysavage said:**
> I decided the way to back up my system was to clone my partition. I did this on a 60GB HD. To test it, I tried setting this as the boot HD. It didn't boot - it just filled the screen up with the word "GRUB". I figure it didn't clone my grub right and I need to re-install it. 

Hod do I figure out the (hdx,x) to install it to? If I go find /boot/grub/stage1, which HD will it be looking at (I have both my system and the backup clone installed at the moment)

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mulluysavage on 2009-12-16
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Which disk will this give me results for? I should have two bootable HDs installed in my tower

---

### Post by presence1960 on 2009-12-17
> **mulluysavage said:**
> Which disk will this give me results for? I should have two bootable HDs installed in my tower

whatever disks you have in your machine will be taken care of by the script.

---

### Post by mulluysavage on 2009-12-17
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub  is installed in the MBR of /dev/sdb and looks on boot drive #-127 in 
    partition #1 for /.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 115346700.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002a7af

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   115,346,699   115,346,637  83 Linux
/dev/sda2         230,693,400   625,137,344   394,443,945   5 Extended
/dev/sda5         606,180,708   625,137,344    18,956,637  82 Linux swap / Solaris
/dev/sda6         230,693,526   606,180,644   375,487,119  83 Linux
/dev/sda3         115,346,700   230,693,399   115,346,700   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002a7af

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   115,346,699   115,346,637  83 Linux
/dev/sdb2         115,346,700   117,178,109     1,831,410  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   913,809,329   913,809,267   c W95 FAT32 (LBA)
/dev/sdc2         974,085,210   976,768,064     2,682,855   5 Extended
/dev/sdc5         974,085,273   976,768,064     2,682,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6a2ae9e4-30a8-42a9-a578-0d7ca170e94d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="16AD-BBD8" TYPE="vfat" 
/dev/sda5: UUID="48965a9d-2363-4aee-896c-72e4c6ebb054" TYPE="swap" 
/dev/sda6: UUID="492a7b69-8e8d-46df-85f1-210a304b58ed" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="6a2ae9e4-30a8-42a9-a578-0d7ca170e94d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="57f85c32-4922-483b-9b68-1f686088356d" TYPE="swap" 
/dev/sdc1: LABEL="HELIANTHUS" UUID="0380-924F" TYPE="vfat" 
/dev/sdc5: UUID="46001006-e856-4885-b35f-126737aeba46" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


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
# kopt=root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=48965a9d-2363-4aee-896c-72e4c6ebb054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/media/40GScratch	vfat	rw	0	0

=================== sda1: Location of files loaded by Grub: ===================


  30.9GB: boot/grub/menu.lst
  11.7GB: boot/grub/stage2
  11.7GB: boot/initrd.img-2.6.24-19-generic
  11.7GB: boot/initrd.img-2.6.24-19-generic.bak
  11.7GB: boot/initrd.img-2.6.24-23-generic
  11.7GB: boot/initrd.img-2.6.24-23-generic.bak
  28.2GB: boot/initrd.img-2.6.24-24-generic
  28.3GB: boot/initrd.img-2.6.24-24-generic.bak
  28.2GB: boot/initrd.img-2.6.24-25-generic
  28.2GB: boot/initrd.img-2.6.24-25-generic.bak
  31.0GB: boot/initrd.img-2.6.24-26-generic
  30.9GB: boot/initrd.img-2.6.24-26-generic.bak
  11.7GB: boot/vmlinuz-2.6.24-19-generic
  11.8GB: boot/vmlinuz-2.6.24-23-generic
  28.2GB: boot/vmlinuz-2.6.24-24-generic
  28.2GB: boot/vmlinuz-2.6.24-25-generic
  30.9GB: boot/vmlinuz-2.6.24-26-generic
  31.0GB: initrd.img
  28.2GB: initrd.img.old
  30.9GB: vmlinuz
  28.2GB: vmlinuz.old

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
# kopt=root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=48965a9d-2363-4aee-896c-72e4c6ebb054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/media/60GBclone	vfat	rw	0	0
/dev/sda6	/media/sriracha		ext3	defaults	0	0
UUID=0380-924F 	/media/My\040Book	vfat rw,uid=phil 0 	0

=================== sdb1: Location of files loaded by Grub: ===================


  30.9GB: boot/grub/menu.lst
  11.7GB: boot/grub/stage2
  11.7GB: boot/initrd.img-2.6.24-19-generic
  11.7GB: boot/initrd.img-2.6.24-19-generic.bak
  11.7GB: boot/initrd.img-2.6.24-23-generic
  11.7GB: boot/initrd.img-2.6.24-23-generic.bak
  28.2GB: boot/initrd.img-2.6.24-24-generic
  28.3GB: boot/initrd.img-2.6.24-24-generic.bak
  28.2GB: boot/initrd.img-2.6.24-25-generic
  28.2GB: boot/initrd.img-2.6.24-25-generic.bak
  31.0GB: boot/initrd.img-2.6.24-26-generic
  30.9GB: boot/initrd.img-2.6.24-26-generic.bak
  11.7GB: boot/vmlinuz-2.6.24-19-generic
  11.8GB: boot/vmlinuz-2.6.24-23-generic
  28.2GB: boot/vmlinuz-2.6.24-24-generic
  28.2GB: boot/vmlinuz-2.6.24-25-generic
  30.9GB: boot/vmlinuz-2.6.24-26-generic
  31.0GB: initrd.img
  28.2GB: initrd.img.old
  30.9GB: vmlinuz
  28.2GB: vmlinuz.old

```

---

### Post by presence1960 on 2009-12-17
If you set your sda disk to be the first hard disk to boot in BIOS it will boot 8.04.

Now for the case of the clone on what is now your sdb disk. If you look at the script output for menu.lst & fstab on the clone:

```
## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# [COLOR="Red"]/dev/sda1[/COLOR]
UUID=6a2ae9e4-30a8-42a9-a578-0d7ca170e94d /               ext3    relatime,errors=remount-ro 0       1
# [COLOR="Red"]/dev/sda5[/COLOR]
UUID=48965a9d-2363-4aee-896c-72e4c6ebb054 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1	/media/60GBclone	vfat	rw	0	0
/dev/sda6	/media/sriracha		ext3	defaults	0	0
UUID=0380-924F 	/media/My\040Book	vfat rw,uid=phil 0 	0
```

Note the entries in red. They are all referring to the original disk & partitions. To get sdb to boot it must be first in hard disk boot order in BIOS so it can be (hd0). Also note the bootloader info for the clone:
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
[COLOR="Red"] => Grub  is installed in the MBR of /dev/sdb and looks on boot drive #-127 in 
    partition #1 for /.[/COLOR]
 => Windows is installed in the MBR of /dev/sdc

```

That disk was meant to be restored to the Ubuntu disk not actually booted itself. While it may be possible to boot that sdb disk you will have to put sdb as the first disk to boot in BIOS and restore GRUB to it like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)(hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You may run into problems with fstab, I am not certain.

---

### Post by mulluysavage on 2009-12-19
will this find the grub stage 1 of my clone or my primary hd?

---

### Post by presence1960 on 2009-12-19
> **mulluysavage said:**
> will this find the grub stage 1 of my clone or my primary hd?

your primary (sda) should boot fine if it is set to first in the hard disk boot order in BIOS. The instructions I gave were for booting sdb (60 GB clone).

---

