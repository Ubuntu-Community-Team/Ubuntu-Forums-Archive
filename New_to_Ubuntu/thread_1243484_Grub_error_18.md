---
title: "Grub error 18"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Cmdr Ren Hoek on 2009-08-18
I have just finished new install of a dual boot: WinXP Home and Ubuntu 9.04.  When I went to restart after the Jaunty install was complete I got the Grub Error 18.

Hardware:  Dell Inspiron 8600 with new WD EIDE 160GB HDD

During the Windoz install I flashed the BIOS with the current version from Dell (A14).

I searched this forum and wasn't able to find an answer to this Error 18.  I did download the BootInfoScript and don't know what to look for.       

Any help would be appreciated.

---

### Post by anung524 on 2009-08-18
i found about error 18 here: [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)
maybe it could help you..

---

### Post by Cmdr Ren Hoek on 2009-08-18
Just so you have the information:


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65c565c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,576,704   230,661,270   5 Extended
/dev/sda5          81,915,498   276,478,649   194,563,152   7 HPFS/NTFS
/dev/sda6         276,478,713   286,246,169     9,767,457  83 Linux
/dev/sda7         286,246,233   305,781,209    19,534,977  83 Linux
/dev/sda8         305,781,273   312,576,704     6,795,432  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C2BC1CF4BC1CE527" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: UUID="534E9C2B779DBE59" LABEL="STORAGE" TYPE="ntfs" 
/dev/sda6: UUID="60f6336e-b457-42a5-9e87-4714d204a5e9" TYPE="ext2" 
/dev/sda7: UUID="60aeb297-dcee-4634-88e9-9bca28559e99" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="a121a8be-7741-4ed4-9736-c66a58e5f7ae" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=60f6336e-b457-42a5-9e87-4714d204a5e9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=60f6336e-b457-42a5-9e87-4714d204a5e9

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        60f6336e-b457-42a5-9e87-4714d204a5e9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60f6336e-b457-42a5-9e87-4714d204a5e9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        60f6336e-b457-42a5-9e87-4714d204a5e9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60f6336e-b457-42a5-9e87-4714d204a5e9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        60f6336e-b457-42a5-9e87-4714d204a5e9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=60f6336e-b457-42a5-9e87-4714d204a5e9 /               ext2    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=60aeb297-dcee-4634-88e9-9bca28559e99 /home           ext3    relatime        0       2
# swap was on /dev/sda8 during installation
UUID=a121a8be-7741-4ed4-9736-c66a58e5f7ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 142.3GB: boot/grub/menu.lst
 142.3GB: boot/grub/stage2
 144.3GB: boot/initrd.img-2.6.28-11-generic
 144.3GB: boot/vmlinuz-2.6.28-11-generic
 144.3GB: initrd.img
 144.3GB: vmlinuz


Thanks!

---

### Post by Penguin Guy on 2009-08-18
Basically your /boot folder needs to be closer to the start of your disk.
<- That way. The following explains it fully:

>   Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.
Error 18 on Dual Boot Systems Using a Single Hard Drive

This error often occurs when creating a dual boot system (with Windows) on a single hard disk drive, as in a notebook PC, because the Linux partitions end up being beyond the LBA range. On a large notebook drive you may need to **re-install Windows into a smaller primary partition (or resize the partition), then create an extended partition in the unallocated space and create partitions for Linux Root, Linux Swap, and Linux Home, then in the remaining unallocated space create another NTFS partition for Windows.** In other words, the Linux partitions must be immediately after the Primary Windows partition so they are still within the LBA range, then you can place additional NTFS or FAT32 partitions after the Linux partitions.

On a 160GB notebook drive, the following gave Error 18:

Primary: 80GB Windows NTFS

Extended: 4GB (FAT32), 50GB (NTFS), 4GB Linux Root (ext3), 2GB Linux Swap, 20GB Linux home (ext3).


The following worked:

Primary: 80GB Windows NTFS

Extended: 4GB Linux Root (ext3), 2GB Linux Swap, 20GB Linux home (ext3), 4GB (FAT32), 50GB (NTFS).

It can be somewhat of an annoyance to have the NTFS file system split into two partitions, but it's a workaround.


[Note: the reason for the 4GB FAT 32 partition is that it makes it possible for both Windows and Linux to access that partition, which can be useful when transferring files between the two operating systems.]
Removing GRUB After Error 18 on a Dual Boot System (Windows/Linux) Using a Single Hard Drive

If you install GRUB on a dual boot system with a single hard drive, and get Error 18, you will not be able to boot Windows. To fix this, you need to boot the system from a Windows Recovery CD, select "R" for Repair, and then run "fixmbr" (fix master boot record) at the DOS prompt in C:\windows. This will remove GRUB. If you don't have a recovery CD, you can download floppies from Microsoft for XP, see "http://support.microsoft.com/kb/310994".

Read more: [http://wiki.linuxquestions.org/wiki/GRUB#Error_18#ixzz0OYR7eLMH](http://wiki.linuxquestions.org/wiki/GRUB#Error_18#ixzz0OYR7eLMH)

---

### Post by oldfred on 2009-08-18
One other possibility:
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

from above explanation which is the same as Penguin Guy's, but has another solution that may work.

[COLOR=#999999]**" I had the same problem. Error 18 and After GRUB. The solution is in the bios.**[/COLOR]
                                              [COLOR=#999999]**Put the hard disk detection on auto and not on user. It did the trick for me."**[/COLOR]

---

