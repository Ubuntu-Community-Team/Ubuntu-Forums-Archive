---
title: "Error 17 attempting to dual boot from two different hard drives (1 PATA, 1 SATA)"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by petjakob on 2009-10-19
I just built a new system, AMD Phenom II 3.2GHz Asus M4A79T Deluxe motherboard, but I did not buy new hard drives yet. I decided at the moment I want to have ubuntu on my old primary OS hard drive, it is a 40gb PATA. The reason is for simplicity as I know I'm going to have to "clean install" Win7, it won't play nice to a drive that's partitioned for dual XP/Ubuntu. I was running fine as a dual boot with XP and ubuntu on that single drive. Now I've installed XP on a 150GB SATA drive that turned up. BIOS has to have the PATA drive as primary boot, otherwise XP just boots and grub never happens. So, my device.map edit was simply to swap the two entries (since it had the SATA as hd0) to get it matching the BIOS. When I first got the error 17 I thought it was due to my deletion of the previous XP partition on the PATA drive. So my first troubleshooting step was an attempt to do a clean reinstall of ubuntu using the whole drive. Error persisted after this.

I've tried all the steps detailed in the different threads for the grub error 17 and it all seems to work, except the final steps where I do the root and setup commands, they keep giving me Selected Disk Does Not Exist. I can't figure out why or if this is even the best way to resolve this. Ultimately long term I am going to obtain two more SATA hard drives, one for Ubuntu, one for data storage. But it could be months before this happens, and I want to reliably have grub booting me to either the PATA drive's ubuntu vs the SATA drive's Windows.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,480,314   312,480,252   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11061105

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    76,903,154    76,903,092  83 Linux
/dev/sdb2          76,903,155    80,292,869     3,389,715   5 Extended
/dev/sdb5          76,903,218    80,292,869     3,389,652  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3A74303A742FF6F3" TYPE="ntfs" 
/dev/sdb1: UUID="158a2a63-4bf8-45e9-97db-3636f13b159a" TYPE="ext3" 
/dev/sdb5: UUID="094cd140-d8d1-4200-95a6-343f620fc5e4" TYPE="swap" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /ubuntu type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer 

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
# kopt=root=UUID=158a2a63-4bf8-45e9-97db-3636f13b159a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=158a2a63-4bf8-45e9-97db-3636f13b159a

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
uuid        158a2a63-4bf8-45e9-97db-3636f13b159a
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        158a2a63-4bf8-45e9-97db-3636f13b159a
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        158a2a63-4bf8-45e9-97db-3636f13b159a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map         (hd1) (hd0)
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=158a2a63-4bf8-45e9-97db-3636f13b159a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=094cd140-d8d1-4200-95a6-343f620fc5e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  20.3GB: boot/grub/menu.lst
  20.3GB: boot/grub/stage2
  20.3GB: boot/initrd.img-2.6.28-11-generic
  20.2GB: boot/vmlinuz-2.6.28-11-generic
  20.3GB: initrd.img
  20.2GB: vmlinuz
```I solved the issue after noticing my output here states that grub is installed on both disks. I went into the bios, changed the SATA drive back to boot drive 1, and behold, my next reboot displayed a proper grub menu, though none of the options worked due to all my edits! So I Live booted once more and reset everything so the linux boots were from HD1,0 and the XP boot was from HD0,0 with no mapping. (And redid --device-map=device.map after editing it again to read sda (sata) as HD0 and sdb (PATA) as HD1). Now I am booting both again. Rebooted to ubuntu from xp in 70 seconds!

---

### Post by swoody on 2009-10-20
Great, glad to hear you figured it out. Just for future reference, to mark a thread as [SOLVED] just click on 'Thread Tools' in the top-right of this page and select 'Mark thread as solved :)

---

