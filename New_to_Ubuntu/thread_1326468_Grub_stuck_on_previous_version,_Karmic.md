---
title: "Grub stuck on previous version, Karmic"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by DrMilo on 2009-11-14
So I've installed KK, more than once, and grub still only gives me options for 8.10. Frankly I don't know what else to say. I have no idea what to do.

---

### Post by ranch hand on 2009-11-14
Well,  I have no idea what you are talking about here so I don't know what to say either.

8.10?

Are you trying to upgrade 8.10 to 9.10?  (this will not work)

Is this a clean install?

Are you trying to clean install over 8.10?

---

### Post by DrMilo on 2009-11-14
> **ranch hand said:**
> Well,  I have no idea what you are talking about here so I don't know what to say either.

8.10?

Are you trying to upgrade 8.10 to 9.10?  (this will not work)

Is this a clean install?

Are you trying to clean install over 8.10?

I have tried to install from 8.10 and that didn't work.

So I chose the option to erase and install 9.10 and that didn't work. 

Both times the install didn't say anything that led me to believe that there was a problem.

However, grub still has only 8.10 boot options.

I really have no idea how could get rid of the distro that I now without wiping out everything on that drive. Ideally that is what I'd do at this point.

---

### Post by ranch hand on 2009-11-14
What else is on this drive?

When you boot with a Live CD what can you see on the drive?

Did you check the md5sum on your ISO?

---

### Post by DrMilo on 2009-11-14
> **ranch hand said:**
> What else is on this drive?

When you boot with a Live CD what can you see on the drive?

Did you check the md5sum on your ISO?

There's any number of things on that drive; my concern is that 9.10 isn't doing what I would expect it to and erasing the previous OS.

Booting from the live CD lets me see, as far as I can tell, everything on that drive.

No I haven't done that. What would I do if I did that?

---

### Post by kansasnoob on 2009-11-14
The best way to start troubleshooting this is to run the Boot Info Script as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It runs equally well from either an installed version of Ubuntu or the Live CD.

Post the results here and I'll try my best to parse thru the info. Be aware though that I'm somewhat backed up!

It could take me a while to get to yours! I'm just now reviewing yesterdays stuff!

---

### Post by DrMilo on 2009-11-14
> **kansasnoob said:**
> The best way to start troubleshooting this is to run the Boot Info Script as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It runs equally well from either an installed version of Ubuntu or the Live CD.

Post the results here and I'll try my best to parse thru the info. Be aware though that I'm somewhat backed up!

It could take me a while to get to yours! I'm just now reviewing yesterdays stuff!

Thank you, it'll be a few hours as I'm away from my box.

---

### Post by DrMilo on 2009-11-15
> **kansasnoob said:**
> The best way to start troubleshooting this is to run the Boot Info Script as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It runs equally well from either an installed version of Ubuntu or the Live CD.

Post the results here and I'll try my best to parse thru the info. Be aware though that I'm somewhat backed up!

It could take me a while to get to yours! I'm just now reviewing yesterdays stuff!

Here you go:

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d653e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   476,327,249   476,327,187  83 Linux
/dev/sda2         476,327,250   488,392,064    12,064,815   5 Extended
/dev/sda5         476,327,313   488,392,064    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aca86

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   859,943,384   859,943,322  83 Linux
/dev/sdb2         859,943,385   976,768,064   116,824,680   5 Extended
/dev/sdb5         970,711,623   976,768,064     6,056,442  82 Linux swap / Solaris
/dev/sdb6         859,943,511   966,100,904   106,157,394  83 Linux
/dev/sdb7         966,100,968   970,711,559     4,610,592  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x515e515d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    26,619,704    26,619,642   c W95 FAT32 (LBA)
/dev/sdc2          66,974,985   117,868,904    50,893,920  83 Linux
/dev/sdc3         117,868,905   120,101,939     2,233,035   5 Extended
/dev/sdc5         117,868,968   120,101,939     2,232,972  82 Linux swap / Solaris
/dev/sdc4          26,619,705    66,974,984    40,355,280  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14669040

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1027 MB, 1027416576 bytes
32 heads, 62 sectors/track, 1011 cylinders, total 2006673 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f8e8

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62     2,005,823     2,005,762   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a2afc27a-3a36-4608-b35d-59f9fdc0ab5a" TYPE="ext4" 
/dev/sda5: UUID="5d1cb7b5-02ef-4f20-809f-474230e2c6ed" TYPE="swap" 
/dev/sdb1: UUID="e4fadf58-8d56-41a9-a82e-26f54e787997" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="18c253ed-1362-49cf-aa3b-1a2ded687a2a" TYPE="swap" 
/dev/sdb6: UUID="f34d1a04-d902-4a1b-af7e-88b5d315588e" TYPE="ext4" 
/dev/sdb7: UUID="d8a057ee-00df-4560-acbd-821b565385dd" TYPE="swap" 
/dev/sdc1: UUID="BC63-B44F" TYPE="vfat" 
/dev/sdc2: UUID="12666996-6447-4a75-a89d-82be07376426" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: UUID="a63a87b4-1a9b-4a3f-8273-b5b254b677af" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: TYPE="swap" 
/dev/sdd1: UUID="7C8061878061492A" TYPE="ntfs" 
/dev/sde1: UUID="BC83-DCE0" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sde1 on /media/BC83-DCE0 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set a2afc27a-3a36-4608-b35d-59f9fdc0ab5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a2afc27a-3a36-4608-b35d-59f9fdc0ab5a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a2afc27a-3a36-4608-b35d-59f9fdc0ab5a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a2afc27a-3a36-4608-b35d-59f9fdc0ab5a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a2afc27a-3a36-4608-b35d-59f9fdc0ab5a ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.25-2-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.25-2-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.25-2-386
}
menuentry "Ubuntu 8.10, kernel 2.6.25-2-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.25-2-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.25-2-386
}
menuentry "Ubuntu 8.10, kernel 2.6.24-25-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.24-25-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.24-25-386
}
menuentry "Ubuntu 8.10, kernel 2.6.24-25-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.24-25-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.24-25-386
}
menuentry "Ubuntu 8.10, kernel 2.6.15-52-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.15-52-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.15-52-386
}
menuentry "Ubuntu 8.10, kernel 2.6.15-52-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.15-52-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.15-52-386
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f34d1a04-d902-4a1b-af7e-88b5d315588e
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f34d1a04-d902-4a1b-af7e-88b5d315588e ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb6)" {
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f34d1a04-d902-4a1b-af7e-88b5d315588e
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f34d1a04-d902-4a1b-af7e-88b5d315588e ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
	insmod fat
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set bc63-b44f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a2afc27a-3a36-4608-b35d-59f9fdc0ab5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5d1cb7b5-02ef-4f20-809f-474230e2c6ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.25-2-386
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash 
initrd		/boot/initrd.img-2.6.25-2-386

title		Ubuntu 8.10, kernel 2.6.25-2-386 (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.25-2-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro  single
initrd		/boot/initrd.img-2.6.25-2-386

title		Ubuntu 8.10, kernel 2.6.24-25-386
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-25-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-25-386

title		Ubuntu 8.10, kernel 2.6.24-25-386 (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-25-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro  single
initrd		/boot/initrd.img-2.6.24-25-386

title		Ubuntu 8.10, kernel 2.6.15-52-386
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.10, kernel 2.6.15-52-386 (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro  single
initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-29-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		Ubuntu, memtest86+ (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1 -- converted during upgrade to edgy
UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 / ext3 defaults,errors=remount-ro,relatime 0 1
# /dev/sdb5 -- converted during upgrade to edgy
UUID=18c253ed-1362-49cf-aa3b-1a2ded687a2a none swap sw 0 0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0


# /dev/sda1 -- converted during upgrade to edgy
UUID=bb217c62-d256-4888-9372-f3cd6a50b5dc /media/drive21 ext3 defaults,relatime 0 2

# /dev/hda2 -- converted during upgrade to edgy
UUID=12666996-6447-4a75-a89d-82be07376426 /media/drive3 ext3 defaults,relatime 0 2

# /dev/hda4 -- converted during upgrade to edgy
UUID=a63a87b4-1a9b-4a3f-8273-b5b254b677af /media/drive ext3 defaults,relatime 0 2
#Added by diskmounter utility
# /dev/hdb1 -- converted during upgrade to edgy
UUID=7C8061878061492A /media/hdb1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
# /dev/hda1 -- converted during upgrade to edgy
UUID=BC63-B44F /media/hda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

#Security
tmpfs /dev/shm tmpfs defaults,ro 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.15-52-386
    .0GB: boot/initrd.img-2.6.24-25-386
    .0GB: boot/initrd.img-2.6.24-25-386.bak
    .0GB: boot/initrd.img-2.6.25-2-386
    .0GB: boot/initrd.img-2.6.27-15-generic
    .0GB: boot/vmlinuz-2.6.15-52-386
    .0GB: boot/vmlinuz-2.6.24-25-386
    .0GB: boot/vmlinuz-2.6.25-2-386
    .0GB: boot/vmlinuz-2.6.27-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set f34d1a04-d902-4a1b-af7e-88b5d315588e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f34d1a04-d902-4a1b-af7e-88b5d315588e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f34d1a04-d902-4a1b-af7e-88b5d315588e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set f34d1a04-d902-4a1b-af7e-88b5d315588e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f34d1a04-d902-4a1b-af7e-88b5d315588e ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.25-2-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.25-2-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.25-2-386
}
menuentry "Ubuntu 8.10, kernel 2.6.25-2-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.25-2-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.25-2-386
}
menuentry "Ubuntu 8.10, kernel 2.6.24-25-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.24-25-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.24-25-386
}
menuentry "Ubuntu 8.10, kernel 2.6.24-25-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.24-25-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.24-25-386
}
menuentry "Ubuntu 8.10, kernel 2.6.15-52-386 (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.15-52-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro quiet splash
	initrd /boot/initrd.img-2.6.15-52-386
}
menuentry "Ubuntu 8.10, kernel 2.6.15-52-386 (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/vmlinuz-2.6.15-52-386 root=UUID=e4fadf58-8d56-41a9-a82e-26f54e787997 ro single
	initrd /boot/initrd.img-2.6.15-52-386
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4fadf58-8d56-41a9-a82e-26f54e787997
	linux /boot/memtest86+.bin 
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
	insmod fat
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set bc63-b44f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=f34d1a04-d902-4a1b-af7e-88b5d315588e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=d8a057ee-00df-4560-acbd-821b565385dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 440.2GB: boot/grub/grub.cfg
 440.2GB: boot/initrd.img-2.6.31-14-generic
 440.2GB: boot/vmlinuz-2.6.31-14-generic
 440.2GB: initrd.img
 440.2GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


================================ sdc1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  40 90 66 14 00 00 00 01  |........@.f.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 e4 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  5a 4e 37 96 5a 4e 37 ff  8b 84 73 ff d1 cb c1 ff  |ZN7.ZN7...s.....|
00000010  8f 8a 7a ff 7d 79 68 ff  dd db d4 ff e6 e4 dd ff  |..z.}yh.........|
00000020  e6 e4 dd ff e6 e4 dd ff  e6 e4 dd ff e6 e4 dd ff  |................|
*
00000060  e6 e4 dd ff e6 e4 dd ff  e6 e4 dd ff 7e 7a 6b ff  |............~zk.|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  5a 4e 37 9f 5a 4e 37 ff  89 82 71 ff d2 cd c3 ff  |ZN7.ZN7...q.....|
00000090  90 8a 7a ff 83 7d 6e ff  e2 df d9 ff e8 e6 df ff  |..z..}n.........|
000000a0  e8 e6 df ff e8 e6 df ff  e8 e6 df ff e8 e6 df ff  |................|
*
000000e0  e8 e6 df ff e8 e6 df ff  e8 e6 df ff 87 82 74 ff  |..............t.|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  5a 4e 37 96 5a 4e 37 ff  7e 77 64 ff d3 cd c2 ff  |ZN7.ZN7.~wd.....|
00000110  96 8f 80 ff 85 7e 6f ff  e4 e1 db ff ea e8 e1 ff  |.....~o.........|
00000120  ea e8 e1 ff ea e8 e1 ff  ea e8 e1 ff ea e8 e1 ff  |................|
*
00000150  ea e8 e1 ff ea e7 e1 ff  ea e8 e1 ff ea e8 e1 ff  |................|
00000160  ea e8 e1 ff ea e8 e1 ff  ea e8 e1 ff 90 8c 7e ff  |..............~.|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  5a 4e 37 87 5a 4e 37 ff  71 68 54 ff cb c5 ba ff  |ZN7.ZN7.qhT.....|
00000190  a2 9b 8d ff 80 7a 6a ff  e3 e0 d9 ff ec e8 e3 ff  |.....zj.........|
000001a0  ec e8 e3 ff ec e8 e3 ff  ec e8 e3 ff ec e8 e3 ff  |................|
*
000001e0  ec e8 e3 ff ec e8 e3 ff  ec e8 e3 ff 98 94 88 ff  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

---

### Post by oldfred on 2009-11-15
Is your BIOS set to boot the 250GB drive first. If you are just getting old linux your 61.5GB drive must be booting first. You configuration looks correct to me if the 250GB drive is booting first. Perhaps someone else will see an issue.

Is this a mixed Sata & Pata configuration. I have had problems with my old setup where the pata almost always booted first and that motherboard would not let me change that order. My new motherboard allows all drives to be set in order regardless of whether they are Sata or Pata.

---

### Post by DrMilo on 2009-11-15
> **oldfred said:**
> Is your BIOS set to boot the 250GB drive first. If you are just getting old linux your 61.5GB drive must be booting first. You configuration looks correct to me if the 250GB drive is booting first. Perhaps someone else will see an issue.

Is this a mixed Sata & Pata configuration. I have had problems with my old setup where the pata almost always booted first and that motherboard would not let me change that order. My new motherboard allows all drives to be set in order regardless of whether they are Sata or Pata.

I believe that I can change the boot order. I will try that. I got the impression that the install went to the 250 but it's worth a try.

---

### Post by ranch hand on 2009-11-15
Actually you appear to have 2 perfectly good installations of 9.10.  One on sda1 and the other on sdb6.

Menus look right, fstabs look right.

The big question is were do you think you installed grub2?  MBR?

Grub1.97 is installed on the MBR of sda.

No bootloader is installed on the MBR of sdb.

---

### Post by DrMilo on 2009-11-15
> **ranch hand said:**
> Actually you appear to have 2 perfectly good installations of 9.10.  One on sda1 and the other on sdb6.

Menus look right, fstabs look right.

The big question is were do you think you installed grub2?  MBR?

Grub1.97 is installed on the MBR of sda.

No bootloader is installed on the MBR of sdb.

Heck I just followed the install. I could give a damn what drive it boots from.

So I should try and manually install grub2 somewhere?

Thanks BTW I really appreciate this.

---

### Post by ranch hand on 2009-11-15
There may be reason for you to give a damn if you want things to work.

An attitude like this and then ask others to bail you out is a little arrogant and certainly shows no respect what so ever for other peoples time.

Yes I realize that if you have a problem with Win JerryLewis Pro you just keep reinstalling until you get tired or it works.   With Linux, thinking is actually a plus.

---

### Post by DrMilo on 2009-11-15
> **ranch hand said:**
> There may be reason for you to give a damn if you want things to work.

An attitude like this and then ask others to bail you out is a little arrogant and certainly shows no respect what so ever for other peoples time.

Yes I realize that if you have a problem with Win JerryLewis Pro you just keep reinstalling until you get tired or it works.   With Linux, thinking is actually a plus.

Sorry, I had no intention of coming across like that. 

But if Ubuntu is going to have a GUI install then 'dummies' like myself are to be expected.

When the GUI install of a stable release of software tells me that it's installing something my expectation is that it isn't lying; that it will install all things needed to run the OS. Now after following the directions I'm hearing that I actually need to install something else manually and that the OS installed to 2 different drives!

If you wish you can also find my posts showing that the startup USB creator let me down, twice. Once when it said it would format my stick and actually made it inviable to Ubuntu itself instead (windows found it no problem), necessitating my formatting the stick with windows, the second when it failed to make that stick bootable! 

So now I've got a bootable CD after borrowing a friend's burner, because I didn't have one myself. And following the install instructions resulted in this.

I've been using Ubuntu since Dapper, sold computers for 6 years and am currently a student at a prestigious law school; I think that I can follow install instructions.

So what I meant to say was, "I would like to have Ubuntu boot up my machine from an HD, any HD is fine, and what is the simple way to accomplish that?"

---

### Post by oldfred on 2009-11-15
You are not the only one with this type of issue. It seems to be worse with grub2 but I had issues with old grub or maybe we are only seeing all the people with problems because a lot of users are upgrading.

There seems to be an issue with drive order. BIOS will always boot from the first drive. The issue seems to be that grub, ubuntu, BIOS do not always agree on first drive, if grub is not installed to the BIOS first drive you will have problems.

Did you check drive order in BIOS. Also print out /boot/grub/device.map to see what it says.

---

### Post by kansasnoob on 2009-11-15
That really is a royal mess!

You have one Karmic in sda1 and another in sdb6.

Had you just installed a new hard drive?

I can see from the older 8.10's menu.lst on sdb1 that when it was originally installed grub recognized it as being on sdd1 as indicated by the **root (hd3,0)**.

Where one XP is now recognized as being on sdc1 and another on sdd1, that old 8.10 menu.lst saw only one being on sda1 as indicated by the (hd0,0).

Unless you just installed a new hard drive I'd be very, very worried that you might be facing major data loss!

Just don't blame Ubuntu's installer. On multi-boot and/or multi-drive sytems it's fairly imperative to choose Manually select partitions (advanced) and have a previous plan laid out.

If you can get the Karmic on sda1 to boot you might be able to do some investigating and see if all your data is intact and then begin fixing things, but honestly I'm not comfortable advising on this.

I'd seek out a truly techie friend, not one that just thinks he knows what he's doing, but someone that really knows his stuff!

---

### Post by DrMilo on 2009-11-15
My thanks to the previous 2 posts!

I have a very competent friend but it's a matter of our schedules meshing.

Is there a fairly straightforward way to just get rid of both Ubuntus and reinstall from my Koala, or even a different distro, startup CD?

---

### Post by _john on 2009-11-15
Hi if I read right why can't you just update the kernel ? Could take the sting out though dont mind me its more of a what I'd do mate,  heres a how-to if they dont mind :D

[http://www.linux-noob.com/forums/index.php?/topic/376-apt-get-kernel-2-6/page__hl__update%20kernel__fromsearch__1](http://www.linux-noob.com/forums/index.php?/topic/376-apt-get-kernel-2-6/page__hl__update%20kernel__fromsearch__1)

and one more if you go this way ! 

[http://ubuntuforums.org/showthread.php?t=1194878](http://ubuntuforums.org/showthread.php?t=1194878)

Hope this helps

---

### Post by oldfred on 2009-11-16
Did you at least try changing the 250GB drive to first in the BIOS?

---

