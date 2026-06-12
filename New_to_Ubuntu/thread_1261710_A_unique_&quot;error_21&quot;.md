---
title: "A unique &quot;error 21&quot;"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Cryo-man on 2009-09-09
Hi There, another noob here. I have seen the "errror 21" in many places all over the web, and that's also my problem. However I think my problem is a little more unique. I had windows vista installed on my comp, I then installed ubuntu. Everything was working fine, however now I have just installed ubuntu onto an external hard drive for a friend and I am now running into the same error as everyone else. Except I seem to have two copies of grub installed. One on the external hard drive and one on my internal. So I get the error when the external is not connected, however when it is connected I seem to have to pass through two different grub "stations". The first has 4 Ubuntu choices and 2 windows. When I click on one of the windows (I have only tried one, the other, I assume is by backup?) I get to the second grub "station" (the one I had originally). Which just has one of each.

Do I follow the same instructions that were posted to get rid of just the first grub? Any help would be more than appreciated.

---

### Post by louieb on 2009-09-09
What you need to do will depend on how you installed Ubuntu on the internal drive. (WUBI inside windows or traditional in its own partition).

Please follow the   [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt file in your next post. 

Once it is known how Ubuntu was install on the internal drive then the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") should be able to fix it so it will boot without the external drive attached.

---

### Post by Badmonkey005 on 2009-09-09
I just fixed the same error on my comp two topics down (before posting this)

[http://ubuntuforums.org/showthread.php?t=1261667](http://ubuntuforums.org/showthread.php?t=1261667)

---

### Post by Cryo-man on 2009-09-09
Hi louieb, here is the RESULTS.txt. Badmonkey, I did read your post before I even joined the Ubuntu forum, but I did not know if the end result would be the same becuase I seem to have 2 grubs installed. As I said, I am brand new to Ubuntu land:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdf6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,435,086,449 1,435,086,387   7 HPFS/NTFS
/dev/sda2       1,435,439,880 1,465,144,064    29,704,185   7 HPFS/NTFS
/dev/sda3       1,435,086,450 1,435,439,879       353,430   5 Extended
/dev/sda5       1,435,086,513 1,435,439,879       353,367  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb92eb92e

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63    19,535,039    19,534,977   b W95 FAT32
/dev/sdf2          19,535,040   156,296,384   136,761,345   5 Extended
/dev/sdf5          19,535,103   150,625,439   131,090,337  83 Linux
/dev/sdf6         150,625,503   156,296,384     5,670,882  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="11c22910-9652-478d-8f45-7aca88f38594" TYPE="ext3" 
/dev/sda1: UUID="1C987A63987A3AFA" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sda5: UUID="cbb9e195-310f-4912-adc8-7c9bfa31cece" TYPE="swap" 
/dev/sdf1: UUID="BD02-F124" TYPE="vfat" 
/dev/sdf5: UUID="64cc191a-68d8-4023-b6d1-1aa60ab8002a" TYPE="ext3" 
/dev/sdf6: UUID="597acc47-a93c-4685-829a-70a0060ab885" TYPE="swap" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cryo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cryo)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdf5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install(8 ), grub-floppy(8 ),
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
default        1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=1C987A63987A3AFA loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1C987A63987A3AFA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1C987A63987A3AFA loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1C987A63987A3AFA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1C987A63987A3AFA loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda1: Location of files loaded by Grub: ===================


  95.2GB: ubuntu/disks/boot/grub/menu.lst
  95.3GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  95.1GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
  95.1GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
  95.1GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic

=========================== sdf5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
# kopt=root=UUID=64cc191a-68d8-4023-b6d1-1aa60ab8002a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=64cc191a-68d8-4023-b6d1-1aa60ab8002a

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
uuid        64cc191a-68d8-4023-b6d1-1aa60ab8002a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=64cc191a-68d8-4023-b6d1-1aa60ab8002a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        64cc191a-68d8-4023-b6d1-1aa60ab8002a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=64cc191a-68d8-4023-b6d1-1aa60ab8002a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        64cc191a-68d8-4023-b6d1-1aa60ab8002a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdf5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdf5 during installation
UUID=64cc191a-68d8-4023-b6d1-1aa60ab8002a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdf6 during installation
UUID=597acc47-a93c-4685-829a-70a0060ab885 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdf5: Location of files loaded by Grub: ===================


  29.1GB: boot/grub/menu.lst
  29.1GB: boot/grub/stage2
  29.1GB: boot/initrd.img-2.6.28-11-generic
  29.1GB: boot/vmlinuz-2.6.28-11-generic
  29.1GB: initrd.img
  29.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by oldfred on 2009-09-09
The main question is what are you going to do with the external HD?

You are currently booting from your sda internal drive to sdf removable drive. The removable drive then chainboots back to your windows which has WUBI. If you change your GRUB on your internal drive you will have to modify the WUBI menu.lst to chainboot to the external drive.

One fix is to copy the ubuntu  stanzas from the menu.lst into your WUBI menu.lst but anytime ubuntu updates the kernel, you will have to manually edit it.
You can convert to chain booting by modifying the MBR of the external drive to point to the ubuntu on the external drive. This way the external drive will boot anytime/anywhere if it is selected as the first drive to boot. You in any case need to reinstall GRUB on your internal drive to point to your windows/WUBI install. I am not familiar with WUBI so some one else will have to help with specific commands if SuperGrub does not work (But I expect it will).

Long term, if you plan to stay with linux, you should think about converting your WUBI to a linux partition on your internal drive. You should have space to create the linux partitions on a drive of your size. That way if windows ever crashes on your internal drive you can still boot Linux from your internal drive.

---

### Post by louieb on 2009-09-09
Your internal drive has a WUBI (inside widows)  install of Ubuntu. 

from the results.txt
```
=> Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdf

sda1: __________________________________________________  

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk
```You kinda do have two Grub install but only the one on the external drive can be booted to by code in the MBR. And the code in the MBR is doing this now. The other is a modified version of GRUB made to be loaded by the windows boot loader. 

From your 1st post
>  I get to the second grub "station" (the one I had originally).That is actually the windows vista boot loader / manager. Giving you the choice of Vista and your WUBI install.  

Like I mentioned earlier the Super Grub Disk can change the MBR of the internal drive back the way it was before you installed Ubuntu on the external drive. (booting to the windows boot loader / manager).. And is probably the easiest way.  [IDBS on SuperGrub]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html") but there are other ways  [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

Once you get it booting to the internal drive again. Then you can get Ubuntu on the external drive booting too - but that would be another thread.

---

