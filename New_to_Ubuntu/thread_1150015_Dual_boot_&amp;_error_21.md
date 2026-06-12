---
title: "Dual boot &amp; error 21"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by lizandeen on 2009-05-05
I recently cloned my dual boot ubuntu/xp disk using Acronis and everything went fine until I tried to boot up again with the clone (the original got messed up with trying to install Ultimate Edition. The Grub boot menu is still there, Xp boots fine but when it comes to Ubuntu (8.04) all I get is "error 21:selected disk does not exist"! I've used this cloning process before and, with the use of the alternative cd, got everything working fine but have no idea what is going on this time, . Any suggestions? (The simpler and more idiot proof, the better!)

---

### Post by Didius Falco on 2009-05-05
Hi,

Boot up with your Live CD and download this little (57k) script to your desktop:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

The script will gather a lot of information that will help figure out the problem into a file named CONTENTS.txt

Open that file, select all and paste it in this thread, then put code tags (the # on the toolbar) around it.

It'll help people figure out the problem faster...

---

### Post by kay-man on 2009-05-05
If your grub menu is still there, but booting won't work it sounds like errors in your /boot/grub/menu.lst file. Check it to see if your root () entries are correct and pointing to the right partition on the right disk.

---

### Post by caljohnsmith on 2009-05-05
I agree with Didius Falco that it would help a lot if you could post the results of running the Boot Info Script that he linked to. But just as a small correction, that script will create a **RESULTS.txt** file in the same directory where the script is run (which is your desktop if you follow Didius Falco's directions), not a CONTENTS.txt file as Didius Falco mentioned. :)

John

---

### Post by Didius Falco on 2009-05-05
:oops:  Oops!

I plan on using that a lot to help people - so much so that I've linked the script in my signature and (too) quickly dashed off a little "form letter" to explain its use. As of right now, it's obviously a "malformed letter". <G>

I guess I'll go fix that now....

---

### Post by lizandeen on 2009-05-06
Here's the results. Maybe I should point out that I have 3 hard drives:a 320-the Xp dual boot that I can't access My old 8.04 boots from, a 160-the one I'm running this 8.04 from, and a 40 for old xp back-ups.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 280041568 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2da38c51

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   279,290,024   279,289,962   7 HPFS/NTFS
/dev/sda2         279,290,025   625,137,344   345,847,320   5 Extended
/dev/sda5         279,290,088   613,795,454   334,505,367  83 Linux
/dev/sda6         613,795,518   625,137,344    11,341,827  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00079bfa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   301,186,619   301,186,557  83 Linux
/dev/sdb2         301,186,620   312,576,704    11,390,085   5 Extended
/dev/sdb5         301,186,683   312,576,704    11,390,022  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe95fe95

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="7860DF9860DF5B86" TYPE="ntfs" 
/dev/sda5: UUID="199a8236-5f0d-4398-a221-9c5d09d4fd94" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" 
/dev/sdb1: UUID="0947e81e-4327-4dd2-943c-522fcb5489a4" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="db6bbe82-68d2-4dab-b86c-1453ce144966" 
/dev/sdc1: UUID="9E4427024426DCB1" LABEL="WINOS" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/lizandeen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lizandeen)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro

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
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro single 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=80c8aef6-fe7f-4521-ba6b-320f34b5f23c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 143.8GB: boot/grub/menu.lst
 143.3GB: boot/grub/stage2
 223.0GB: boot/initrd.img-2.6.27-11-generic
 223.0GB: boot/vmlinuz-2.6.27-11-generic
 223.0GB: initrd.img
 223.0GB: vmlinuz

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
# kopt=root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=db6bbe82-68d2-4dab-b86c-1453ce144966 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  71.4GB: boot/grub/menu.lst
  71.4GB: boot/grub/stage2
  71.4GB: boot/initrd.img-2.6.24-23-generic
  71.4GB: boot/initrd.img-2.6.24-23-generic.bak
  71.5GB: boot/initrd.img-2.6.24-24-generic
  71.4GB: boot/initrd.img-2.6.24-24-generic.bak
  71.4GB: boot/vmlinuz-2.6.24-23-generic
  71.4GB: boot/vmlinuz-2.6.24-24-generic
  71.5GB: initrd.img
  71.4GB: initrd.img.old
  71.4GB: vmlinuz
  71.4GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-05-06
OK, I'm confused from your description of the problem, because you originally said:
[QUOTE=lizandeen]The Grub boot menu is still there, Xp boots fine but when it comes to Ubuntu (8.04) all I get is "error 21:selected disk does not exist"![/QUOTE]
So does that mean you get the Grub menu on start up, but when you select Ubuntu 8.04 (your sdb1 partition) in the Grub menu, you get the Grub error 21? I don't understand that because the results you posted from the Boot Info Script were while you were booted into your 8.04 sdb1 partition. So can you please clarify and explain your problem in more detail?

---

### Post by lizandeen on 2009-05-06
Writing this via the LiveCD. The320g hd (the hard drive originally used for the xp/ubuntu dual boot) used to start up with the grub menu, but lost it after cloning, got it back and found out I couldn't boot my old 8.04 (I should point out that there is a version of 8.10 higher up the grub menu but this does not work due to a faulty install hence the reason I use the 8.04 lower down the grub list and never had a problem before) getting the Error 21 warning instead. Now for some reason I don't even get that-it just goes straight to xp. Hope that helps to clarify, here also is a new set of results I've just done.
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 139575375 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sdb5 and looks 
                       at sector 280041568 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
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

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe95fe95

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2da38c51

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   279,290,024   279,289,962   7 HPFS/NTFS
/dev/sdb2         279,290,025   625,137,344   345,847,320   5 Extended
/dev/sdb5         279,290,088   613,795,454   334,505,367  83 Linux
/dev/sdb6         613,795,518   625,137,344    11,341,827  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00079bfa

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   301,186,619   301,186,557  83 Linux
/dev/sdc2         301,186,620   312,576,704    11,390,085   5 Extended
/dev/sdc5         301,186,683   312,576,704    11,390,022  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="7860DF9860DF5B86" TYPE="ntfs" 
/dev/sdb5: UUID="199a8236-5f0d-4398-a221-9c5d09d4fd94" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" 
/dev/sdc1: UUID="0947e81e-4327-4dd2-943c-522fcb5489a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="db6bbe82-68d2-4dab-b86c-1453ce144966" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro

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
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro single 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24fdf6b0-e522-4d1a-a41d-6518fbc28296 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=80c8aef6-fe7f-4521-ba6b-320f34b5f23c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 143.8GB: boot/grub/menu.lst
 143.3GB: boot/grub/stage2
 223.0GB: boot/initrd.img-2.6.27-11-generic
 223.0GB: boot/vmlinuz-2.6.27-11-generic
 223.0GB: initrd.img
 223.0GB: vmlinuz

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
# kopt=root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=199a8236-5f0d-4398-a221-9c5d09d4fd94 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=0947e81e-4327-4dd2-943c-522fcb5489a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=db6bbe82-68d2-4dab-b86c-1453ce144966 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  71.4GB: boot/grub/menu.lst
  71.4GB: boot/grub/stage2
  71.4GB: boot/initrd.img-2.6.24-23-generic
  71.4GB: boot/initrd.img-2.6.24-23-generic.bak
  71.5GB: boot/initrd.img-2.6.24-24-generic
  71.4GB: boot/initrd.img-2.6.24-24-generic.bak
  71.4GB: boot/vmlinuz-2.6.24-23-generic
  71.4GB: boot/vmlinuz-2.6.24-24-generic
  71.5GB: initrd.img
  71.4GB: initrd.img.old
  71.4GB: vmlinuz
  71.4GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-05-07
> **lizandeen said:**
> 
```

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  [COLOR="Red"]Grub0.97 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 139575375 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

```
It looks like in the time between your post #6 and post #8, you went and accidentally installed Grub to the boot sector of your sda1 NTFS partition; unfortunately by doing that, sda1 is no longer mountable/readable. If you want to avoid doing that type of thing in the future, I would recommend never running "setup (hdX,Y)" in the Grub CLI unless you know for sure that (hdX,Y) is a linux partition and not an NTFS partition. If you have your Windows Install CD handy, you can fix the problem by booting the Install CD, going to the "recovery console" and first doing:
```
map
```
That will show all your drives/partitions and their corresponding drive letter; find the one that is your sda1 partition and then do:
```
fixboot X:
```
But replace "X" with the sda1 drive letter. That should make sda1 mountable and readable again.

But back to your booting problem: how about doing the following Grub commands from your Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And please post the output of the above commands prior to typing "quit". Also, did you modify your Grub's menu.lst in the Ubuntu on the 320 GB XP/Ubuntu drive? It looks like you did, because all your Ubuntu entries use Grub's "root" syntax instead of "uuid" which would be better. But anyway, try rebooting and see if you at least get the Grub menu on start up (which is 90% of the battle to get Grub working). If you do get the Grub menu, none of the OS entries will work I think because your menu.lst is modified, but see if you can at least get the Grub menu and we can work from there.

John

---

### Post by lizandeen on 2009-05-11
After the last post I overwrote the hard drive again and removed the other two hard drives to try and undo some of my previous mistakes but am still having major problems!! Windows booted up by itself but I still couldn't see my Ubuntu boot up menu at all. First of all I tried fixing the Windows side of things but my recovery console is not allowing me access as "my password is not valid", which is strange as I'm using the same password for my Xp system that I always have, so while I'm here does any body know a work-around for that? 
 Next the commands issued using the Live cd, Here are the results before I typed quit 
```
grub> find /boot/grub/stage1 
 (hd0,4) 

grub> root (hd0,4) 

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded. 
succeeded 
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2 
/boot/grub/menu.lst"... succeeded 
Done. 

```
 I rebooted the computer to find a very truncated grub menu consisting of just Windows and Linux (not _Ubuntu_or any of its subsidiaries-8.04,8.10 etc) and cannot boot either- it just says the disk doesn't exist. AAAAAArg! Any ideas?

---

### Post by BZF on 2009-05-11
My only idea is to take the computer in to recover the files, also dual booting is **VERY risky** and can cause problems to the original OS. but that I know of, you may have to send it in.

---

### Post by lizandeen on 2009-05-11
I just tried using the Super Grub Disk and managed to access my old 8.10/8.04 menu! Unfortunately when I tried to load any of them I received my old friend the "Error21: selected disk does not exist" message. Where can I go from here?
I was just checking other threads and they kept mentioning the"menu.lst" so, using the live cd I went looking in my boot files (I can still get to them using this cd) and found two-"menu.lst" and "menu.lst.old.7274" the second appearing to be the record of my old booting menu. Is there any way to swap one for the other or delete the first (it apparently won't let me do it using the cd) or would this do any good at all?

---

### Post by lizandeen on 2009-05-15
I just tried using the Super Grub Disk and managed to access my old 8.10/8.04 menu! Unfortunately when I tried to load any of them I received my old friend the "Error21: selected disk does not exist" message. Where can I go from here?
I was just checking other threads and they kept mentioning the"menu.lst" so, using the live cd I went looking in my boot files (I can still get to them using this cd) and found two-"menu.lst" and "menu.lst.old.7274" the second appearing to be the record of my old booting menu. Is there any way to swap one for the other or delete the first (it apparently won't let me do it using the cd) or would this do any good at all? (Sorry for pushing this issue but I'm desperate!)

---

