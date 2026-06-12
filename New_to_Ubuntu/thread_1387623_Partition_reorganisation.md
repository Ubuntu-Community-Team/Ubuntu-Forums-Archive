---
title: "Partition reorganisation"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Ian Clark on 2010-01-22
I've deleted sda1 (because I can), while the others are not deletable. I wanted to try adding the space from sda1 to another partition for use. Like weichimaster, I'd like to clean up my drives. I've made several installations, and recently doing the Karmic installations, I didn't see how I could choose which sda to install to. I figured the installation would choose the largest free partition, but instead it makes a new partition. My latest partitions are sda15 and sda16, which are only ten gigs and seem to be giving me problems when trying to do video. Ideally I could take that 20 gigs from sda1 and add 10 or 15 gigs to these, and 5 or 10 gigs to another drive.

I keep getting the error "unable to delete sda*. please unmount any logical partitions with a number greater than 7". Do I need to cut gparted to a disk and run from disk? Is that how this works? 

Output of boot script:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #15 for /boot/grub.
sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda15: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda16: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x639e8ffd

Partition  Boot         Start           End          Size  Id System

/dev/sda2          38,379,285   390,716,864   352,337,580   f W95 Ext d (LBA)
/dev/sda5          76,276,683   152,553,239    76,276,557  83 Linux
/dev/sda6         152,553,303   189,101,114    36,547,812  83 Linux
/dev/sda7         228,845,988   266,775,389    37,929,402  83 Linux
/dev/sda8         308,319,543   366,892,469    58,572,927   b W95 FAT32
/dev/sda9    *    189,101,178   227,094,839    37,993,662  83 Linux
/dev/sda10        227,094,903   228,845,924     1,751,022  82 Linux swap / Solaris
/dev/sda11         38,379,411    74,605,859    36,226,449  83 Linux
/dev/sda12         74,605,923    76,276,619     1,670,697  82 Linux swap / Solaris
/dev/sda13        266,775,453   306,504,134    39,728,682  83 Linux
/dev/sda14        306,504,198   308,319,479     1,815,282  82 Linux swap / Solaris
/dev/sda15        366,892,533   389,608,379    22,715,847  83 Linux
/dev/sda16        389,608,443   390,716,864     1,108,422  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda10: UUID="aeae63cd-111f-4dfd-8ecf-5031cd9b59d1" TYPE="swap" 
/dev/sda11: UUID="d42405b2-e49e-4e85-97a0-f7ae0aa5a901" TYPE="ext4" 
/dev/sda12: UUID="b2846368-0f0d-495b-86c6-2036c1003cc4" TYPE="swap" 
/dev/sda13: UUID="8f7a4049-7176-4e05-b3c1-fad7d5417f22" TYPE="ext4" 
/dev/sda14: UUID="b38ea77c-8a59-458f-9fd2-9dd4aa406c21" TYPE="swap" 
/dev/sda15: UUID="9fb3fce7-e990-4b6e-9479-e0a9527eda9c" TYPE="ext4" 
/dev/sda16: UUID="2e10e7e2-68bd-4c56-9309-1bce574f2667" TYPE="swap" 
/dev/sda5: UUID="663ac83c-87d2-4a5b-b65f-dba37eb81535" TYPE="ext3" 
/dev/sda6: UUID="d66e80ed-0327-494a-a89c-c30a629eda87" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="b09f5984-079e-47d7-ad75-c8a92e936137" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="DISK1_VOL5" UUID="7912-AAB0" TYPE="vfat" 
/dev/sda9: UUID="7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda15 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /storage type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/heituzi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=heituzi)


=========================== sda9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.10, kernel 2.6.27-16-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,8)
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


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda10
UUID=aeae63cd-111f-4dfd-8ecf-5031cd9b59d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda5 /storage ext3 defaults,relatime 0 0

=================== sda9: Location of files loaded by Grub: ===================


  96.8GB: boot/grub/menu.lst
  96.8GB: boot/grub/stage2
  96.8GB: boot/initrd.img-2.6.22-14-generic
  96.8GB: boot/initrd.img-2.6.22-14-generic.bak
  96.8GB: boot/initrd.img-2.6.24-19-generic
  96.8GB: boot/initrd.img-2.6.24-19-generic.bak
  96.8GB: boot/initrd.img-2.6.27-11-generic
  96.8GB: boot/initrd.img-2.6.27-14-generic
  96.8GB: boot/initrd.img-2.6.27-15-generic
  96.8GB: boot/initrd.img-2.6.27-16-generic
  96.8GB: boot/vmlinuz-2.6.22-14-generic
  96.8GB: boot/vmlinuz-2.6.24-19-generic
  96.8GB: boot/vmlinuz-2.6.27-11-generic
  96.8GB: boot/vmlinuz-2.6.27-14-generic
  96.8GB: boot/vmlinuz-2.6.27-15-generic
  96.8GB: boot/vmlinuz-2.6.27-16-generic
  96.8GB: initrd.img
  96.8GB: initrd.img.old
  96.8GB: vmlinuz
  96.8GB: vmlinuz.old

========================== sda13/boot/grub/grub.cfg: ==========================

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
set root=(hd0,13)
search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro single 
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
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda11)" {
	insmod ext2
	set root=(hd0,11)
	search --no-floppy --fs-uuid --set c9112b51-aada-400d-9890-5b20eff08e8f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=c9112b51-aada-400d-9890-5b20eff08e8f ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda11)" {
	insmod ext2
	set root=(hd0,11)
	search --no-floppy --fs-uuid --set c9112b51-aada-400d-9890-5b20eff08e8f
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=c9112b51-aada-400d-9890-5b20eff08e8f ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda11)" {
	insmod ext2
	set root=(hd0,11)
	search --no-floppy --fs-uuid --set c9112b51-aada-400d-9890-5b20eff08e8f
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, kernel 2.6.27-16-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-16-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-16-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-16-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-16-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.24-19-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.22-14-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda13 during installation
UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda14 during installation
UUID=b38ea77c-8a59-458f-9fd2-9dd4aa406c21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda6  /media/videoj_01    ext3    defaults,user  0  0
/dev/sda5  /media/storage    ext3    defaults,user  0  0

=================== sda13: Location of files loaded by Grub: ===================


 136.5GB: boot/grub/core.img
 136.5GB: boot/grub/grub.cfg
 136.5GB: boot/initrd.img-2.6.31-14-generic
 136.5GB: boot/initrd.img-2.6.31-16-generic
 136.5GB: boot/initrd.img-2.6.31-17-generic
 136.5GB: boot/vmlinuz-2.6.31-14-generic
 136.5GB: boot/vmlinuz-2.6.31-16-generic
 136.5GB: boot/vmlinuz-2.6.31-17-generic
 136.5GB: initrd.img
 136.5GB: initrd.img.old
 136.5GB: vmlinuz
 136.5GB: vmlinuz.old

========================== sda15/boot/grub/grub.cfg: ==========================

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
set root=(hd0,15)
search --no-floppy --fs-uuid --set 9fb3fce7-e990-4b6e-9479-e0a9527eda9c
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,15)
	search --no-floppy --fs-uuid --set 9fb3fce7-e990-4b6e-9479-e0a9527eda9c
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9fb3fce7-e990-4b6e-9479-e0a9527eda9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,15)
	search --no-floppy --fs-uuid --set 9fb3fce7-e990-4b6e-9479-e0a9527eda9c
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9fb3fce7-e990-4b6e-9479-e0a9527eda9c ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,15)
	search --no-floppy --fs-uuid --set 9fb3fce7-e990-4b6e-9479-e0a9527eda9c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9fb3fce7-e990-4b6e-9479-e0a9527eda9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,15)
	search --no-floppy --fs-uuid --set 9fb3fce7-e990-4b6e-9479-e0a9527eda9c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9fb3fce7-e990-4b6e-9479-e0a9527eda9c ro single 
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
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda13)" {
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda13)" {
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda13)" {
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda13)" {
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda13)" {
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda13)" {
	insmod ext2
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 8f7a4049-7176-4e05-b3c1-fad7d5417f22
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8f7a4049-7176-4e05-b3c1-fad7d5417f22 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-16-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-16-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-16-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-16-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-16-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-15-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-15-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.24-19-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.24-19-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.22-14-generic (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro quiet splash
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19 ro single
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 7a0e62eb-7cdc-4999-b9c1-4646bf7d7e19
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda15/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda15 during installation
UUID=9fb3fce7-e990-4b6e-9479-e0a9527eda9c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda16 during installation
UUID=2e10e7e2-68bd-4c56-9309-1bce574f2667 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=663ac83c-87d2-4a5b-b65f-dba37eb81535       /storage ext3 defaults 0 0
UUID=d66e80ed-0327-494a-a89c-c30a629eda87      /videoj_01 ext3 defaults 0 0

=================== sda15: Location of files loaded by Grub: ===================


 187.8GB: boot/grub/core.img
 187.8GB: boot/grub/grub.cfg
 187.8GB: boot/initrd.img-2.6.31-14-generic
 187.8GB: boot/initrd.img-2.6.31-17-generic
 187.8GB: boot/vmlinuz-2.6.31-14-generic
 187.8GB: boot/vmlinuz-2.6.31-17-generic
 187.8GB: initrd.img
 187.8GB: initrd.img.old
 187.8GB: vmlinuz
 187.8GB: vmlinuz.old
```

---

### Post by garvinrick4 on 2010-01-22
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by Elfy on 2010-01-22
Please start your own threads - it could get confusing there talking about different partitions. 
> 
I keep getting the error "unable to delete sda*. please unmount any logical partitions with a number greater than 7".Boot with your livecd - right click on the swap partition and turn it off, then there should be no mounted drives and you can do as you want.

---

### Post by Ian Clark on 2010-01-23
:guitar:  Thanks! This did the trick. I wish that gparted would add this info in their error message.

---

### Post by egalvan on 2010-01-23
> **Ian Clark said:**
> :guitar:  Thanks! This did the trick.[COLOR="Red"] I wish that gparted would add this info in their error message[/COLOR].

See [COLOR="Red"]RED[/COLOR] part of message :)


> **Ian Clark said:**
> 
I keep getting the error "**[COLOR="Red"]unable to delete sda*. please unmount any logical partitions with a number greater than 7[/COLOR]**". 

```

sda10: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda12: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda14: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```

---

### Post by warfacegod on 2010-01-24
I'm absolutely astonished. I didn't know such a thing was possible. I see you've already solved your problem but if I may. Perhaps a more elegant solution would be to frag the entire mess and start from scratch.

---

### Post by Leppie on 2010-01-24
i don't know what "doing video" means to you, but IME video editing requires lots of disk space. just over 70gb i wouldn't reckon enough... actually, with a drive of 200gb i would be seriously thinking about expansion. hell, i don't do editing at the moment and still have 1,5tb attached to my system...

---

### Post by cascade9 on 2010-01-24
> **warfacegod said:**
> I'm absolutely astonished. I didn't know such a thing was possible. I see you've already solved your problem but if I may. Perhaps a more elegant solution would be to frag the entire mess and start from scratch.

Umm..yeah, +1. 

I've never seen a drive with 4 different swap partitions on it. Your /root partition is in about the slowest place you can put it.

---

### Post by warfacegod on 2010-01-24
> **cascade9 said:**
> Umm..yeah, +1. 

I've never seen a drive with 4 different swap partitions on it. Your /root partition is in about the slowest place you can put it.

Agreed, 4 swaps is 3 too many. Your installs should all be able to see the one swap and utilize it. I have the one swap created when I installed 9.10. Later on, when I partitioned my drive to add 9.10 UNR and later wiped it to install Mythbuntu, both saw the swap partition and used it. Neither one complained about "no swap" during install which what the install process *will* do.

---

### Post by Leppie on 2010-01-24
i've never really seen such messy partitioning, congrats to the OP

> **warfacegod said:**
> Agreed, 4 swaps is 3 too many. Your installs should all be able to see the one swap and utilize it. I have the one swap created when I installed 9.10. Later on, when I partitioned my drive to add 9.10 UNR and later wiped it to install Mythbuntu, both saw the swap partition and used it. Neither one complained about "no swap" during install which what the install process *will* do.
with enough ram, and depending on what you use the system for you could even run ubuntu perfectly fine without swap. foto/video editing would be a bit more difficult though...

---

### Post by warfacegod on 2010-01-24
> **Leppie said:**
> i've never really seen such messy partitioning, congrats to the OP


with enough ram, and depending on what you use the system for you could even run ubuntu perfectly fine without swap. foto/video editing would be a bit more difficult though...

I do it all the time. Most of the time, when I boot up, I turn swap off. With 2 GB of RAM, I've seen no side effects and I'm considering turning my swap over to another partition entirely.

---

### Post by Leppie on 2010-01-24
> **warfacegod said:**
> I do it all the time. Most of the time, when I boot up, I turn swap off. With 2 GB of RAM, I've seen no side effects and I'm considering turning my swap over to another partition entirely.
you're right. normal use would not require swap at all.
only operations like editing raw images, videos or music could require swap.

---

### Post by egalvan on 2010-01-25
> **Leppie said:**
> you're right. **normal** use would not require swap at all.


I've always thought that "Normal Use" is kinda self-centered :D

To granny, normal would be reading email, and admiring the latest snapshot of the grandchild.
 Normal means 256M of RAM and 256M swap.
Why would anyone need more than that?

to the tech at ILM or Pixar, normal means rendering a tera-byte of computer animation.
 Normal means a render-farm with 64TB of RAM and a PB (peta-byte) of storage.
How could *anyone* work with less than that? :KS

:popcorn:

Anyway, you are right.
IF YOU HAVE ENOUGH RAM FOR YOUR NEEDS then swap is not necessary.

Swap was born back in the good old days, when 4Meg and 8Meg was considered a large amount of RAM,
and today many distros will natter if they don't have at least 256M.

For instance, Puppy will be happy with 128M RAM if swap exists.

---

### Post by audiomick on 2010-01-25
> **Leppie said:**
> i've never really seen such messy partitioning, congrats to the OP


with enough ram, and depending on what you use the system for you could even run ubuntu perfectly fine without swap. foto/video editing would be a bit more difficult though...

and hibernate wont  work.

---

### Post by Leppie on 2010-01-25
> **audiomick said:**
> and hibernate wont  work.
what is so great about hibernating that so many ppl always want to hibernate?

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> what is so great about hibernating that so many ppl always want to hibernate?

Beats me.

---

### Post by Leppie on 2010-01-25
> **egalvan said:**
> I've always thought that "Normal Use" is kinda self-centered :D
of course, normal is always self centered. but that's human nature.

anyways, what i was saying is is that with the largest partition being under 80gb i wonder about the photo/video editing. raw video fills that space up with only a couple of minutes of material, and with the swap of less than 5gb he wouldn't do very much. he could play the videos but wouldn't have space to edit anything (unless he really has something like 64tb of memory, but then again, with that amount of memory why a drive of only 200gb).

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> Beats me.
maybe they're lazy and don't want to save their stuff so they can blame the system if they lose some work...

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> maybe they're lazy and don't want to save their stuff so they can blame the system if they lose some work...

Oh! the irony of losing work when Hibernating to save it.

I'm pretty sure it's an American invention. All these bears running around getting fat and sleeping for half the year. Americans are bears. And we like to pause our Nintendo games.

---

### Post by Leppie on 2010-01-25
> **warfacegod said:**
> Oh! the irony of losing work when Hibernating to save it.

I'm pretty sure it's an American invention. All these bears running around getting fat and sleeping for half the year. Americans are bears. And we like to pause our Nintendo games.
not sure if this would be something particularly American... laziness is a virtue all over the world...

---

### Post by audiomick on 2010-01-25
> **Leppie said:**
> what is so great about hibernating that so many ppl always want to hibernate?

actually, I don't use it myself either. It doesn't work and I am too lazy to find out why...

---

### Post by warfacegod on 2010-01-25
> **Leppie said:**
> not sure if this would be something particularly American... laziness is a virtue all over the world...

We hold the patent.

---

### Post by cascade9 on 2010-01-25
> **audiomick said:**
> actually, I don't use it myself either. It doesn't work and I am too lazy to find out why...

I wonder if mine works? I'm to lazy to try it to find out LOL

---

### Post by warfacegod on 2010-01-25
> **cascade9 said:**
> I wonder if mine works? I'm to lazy to try it to find out LOL

I'm so lazy, I haven't bothered to see if it's even installed in my system.

My friend Jeff is so lazy, he hasn't bothered to turn his laptop on for almost two years.

---

