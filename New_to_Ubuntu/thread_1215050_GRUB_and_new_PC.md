---
title: "GRUB and new PC"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by stalkier on 2009-07-16
Ok so here's the low down. I have two desktops. One has 4 hard drives in it (2 IDE and 2 SATA) GRUB is installed on SATA 1 over Windows MBR. Ubuntu is on IDE 2. I am wanting to take out the UBUNTU hdd and install it into desktop #2. I don't care if I have to reinstall the OS on there. I am needing to know if I will mess anything up on desktop #1. This system is critical. I have a Super Grub Disc if necessary to repair MBR on desktop #1.

OS on desktop #1 is Vista Ultimate 64bit.

---

### Post by Terry of Astoria on 2009-07-16
You can use the Boot Info Script to get information about where your grub is installed.
[https://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/boot_info_script032.sh/download](https://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/boot_info_script032.sh/download)
A lot of info is generated in a results.txt file - see the following excerpt from a forum here:
Download the Boot Info Script ([https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)) to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. Post here and maybe someone will have some good advice for you.

---

### Post by DGortze380 on 2009-07-16
> **stalkier said:**
> Ok so here's the low down. I have two desktops. One has 4 hard drives in it (2 IDE and 2 SATA) GRUB is installed on SATA 1 over Windows MBR. Ubuntu is on IDE 2. I am wanting to take out the UBUNTU hdd and install it into desktop #2. I don't care if I have to reinstall the OS on there. I am needing to know if I will mess anything up on desktop #1. This system is critical. I have a Super Grub Disc if necessary to repair MBR on desktop #1.

OS on desktop #1 is Vista Ultimate 64bit.

Yes, Windows will likely not boot after you remove the Ubuntu drive from Desktop #1.

It should be easily fixed with a Windows Install Disc and the fixmbr command, or Super Grub Disc and fixmbr.

Make backups first.

---

### Post by stalkier on 2009-07-16
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 66. But according to the info from fdisk, 
                       sdb5 starts at sector 351293421.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfbb4fbb4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   669,910,499   669,910,437   7 HPFS/NTFS
/dev/sda2         669,910,500 1,250,258,624   580,348,125   f W95 Ext d (LBA)
/dev/sda5         669,910,563 1,250,258,624   580,348,062   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb345413e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sdb2             411,648   351,291,391   350,879,744   7 HPFS/NTFS
/dev/sdb3         351,293,355   625,137,344   273,843,990   5 Extended
/dev/sdb5         351,293,421   625,137,344   273,843,924   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3f573ac5

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    25,880,714    25,880,652   7 HPFS/NTFS
/dev/sdc2          25,880,715   156,955,049   131,074,335   7 HPFS/NTFS
/dev/sdc3         156,955,050   160,039,529     3,084,480   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a8122

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    78,156,224    78,156,162  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="525082BE5082A7F5" LABEL="main" TYPE="ntfs" 
/dev/sda5: UUID="1504B932E3C0D6C1" LABEL="design" TYPE="ntfs" 
/dev/sdb1: UUID="54BC1138BC1115D8" LABEL="docs2" TYPE="ntfs" 
/dev/sdb2: UUID="D6806DCB806DB323" LABEL="design2" TYPE="ntfs" 
/dev/sdb5: UUID="28ACAE09ACADD19C" LABEL="teresa" TYPE="ntfs" 
/dev/sdc1: UUID="1458070E5806EE74" LABEL="tribal" TYPE="ntfs" 
/dev/sdc2: UUID="922C23922C237081" LABEL="APPS" TYPE="ntfs" 
/dev/sdc3: UUID="A4F44861F44837B6" LABEL="docs" TYPE="ntfs" 
/dev/sdd1: UUID="b2524403-a7e3-44a6-a431-835146e67ffd" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=john)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdd1/boot/grub/menu.lst: ===========================

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
default		5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=UUID=b2524403-a7e3-44a6-a431-835146e67ffd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash pci=nomsi vga=792

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
# howmany=1

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b2524403-a7e3-44a6-a431-835146e67ffd ro quiet splash pci=nomsi vga=792 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b2524403-a7e3-44a6-a431-835146e67ffd ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=b2524403-a7e3-44a6-a431-835146e67ffd /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  10.3GB: boot/grub/menu.lst
  10.3GB: boot/grub/stage2
  10.4GB: boot/initrd.img-2.6.24-23-generic
  10.4GB: boot/initrd.img-2.6.24-23-generic.bak
  10.3GB: boot/initrd.img-2.6.27-11-generic
  10.3GB: boot/initrd.img-2.6.28-11-generic
  10.3GB: boot/vmlinuz-2.6.24-23-generic
  10.3GB: boot/vmlinuz-2.6.27-11-generic
  10.3GB: boot/vmlinuz-2.6.28-11-generic
  10.3GB: initrd.img
  10.3GB: initrd.img.old
  10.3GB: vmlinuz
  10.3GB: vmlinuz.old
```

---

