---
title: "After Grub reinstall the message &quot;Minimal BASH-like line edeiting...&quot;with grub prompt"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-28
I installed recently Windows XP and can't succeed in using old instruction I was so comfortable with before last time. It's here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Back in those times I used 8.04 live CD, but I spoilt that one and got new 10.04. Can't get grub working. One thing important - before I managed to install Windows from USB stick I happpened to reinstall grub once successfully. Same actions wouldn't work today((
When I boot on top of screen it says "GNU Grub version ....."(approximately)
then it says "Minimal BASH-like line editing is supported.(also says about Tab)"
then grub prompt


P.S. I recently realized this is probably connected with different Grub versions. The system I am trying to boot in is Jaunty that uses Grub Legacy, while the live CD 10.04 uses Grub2. Do you know any other way I can restore Legacy other that live CD? I don't have a spare CD right now and can't download 600Mb. What can I do?

---

### Post by rosehipzero on 2010-05-29
I have the same problem right now, i cant seem to figure out what to do. Installing the grub worked on previous versions of Ubuntu, but on 10.04 (maybe its a coincidence) I get a BASH-line command prompt where the user is the grub

---

### Post by clockworkpc on 2010-11-10
Same here.  Refurbishing a customer's Dell Inspiron 9200, but haven't been able to get grub going.  Stuck in this infernal grub command line.

---

### Post by sikander3786 on 2010-11-10
> **clockworkpc said:**
> Same here.  Refurbishing a customer's Dell Inspiron 9200, but haven't been able to get grub going.  Stuck in this infernal grub command line.
Please boot into a LiveCD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your current situation and thus help you accordingly. Please wrap your output with proper code tags # from the post menu.

---

### Post by clockworkpc on 2010-11-10
> **sikander3786 said:**
> Please boot into a LiveCD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your current situation and thus help you accordingly. Please wrap your output with proper code tags # from the post menu.

Thanks for the instructions.  Here are the results:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,904   251,142,143   169,226,240   7 HPFS/NTFS
/dev/sda3         302,343,300   312,576,704    10,233,405  83 Linux
/dev/sda4         251,144,190   302,342,143    51,197,954   5 Extended
/dev/sda5         251,144,192   300,130,303    48,986,112  83 Linux
/dev/sda6         300,132,352   302,342,143     2,209,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
255 heads, 63 sectors/track, 1948 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     8,594,774     8,594,712   b W95 FAT32
/dev/sdb2           8,594,775    31,294,619    22,699,845  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7A23738A07B6CC8A                       ntfs       Windows                       
/dev/sda2        70E61D8D3E1E3156                       ntfs       DATA                          
/dev/sda3        8690c82b-1347-4741-99aa-d6baa3dc1f02   ext4                                     
/dev/sda5        a409ae48-3ff1-4ce3-90f4-7730b4a575aa   ext4                                     
/dev/sda6        38c8e0bf-3712-4493-8f59-69609763507f   swap                                     
/dev/sdb1        1498-EC24                              vfat       installer                     
/dev/sdb2        57cb8ab1-2817-4f63-bac2-a73df248a4c3   ext4       DATA                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=2c050fe0)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a409ae48-3ff1-4ce3-90f4-7730b4a575aa
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a409ae48-3ff1-4ce3-90f4-7730b4a575aa
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a409ae48-3ff1-4ce3-90f4-7730b4a575aa
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a409ae48-3ff1-4ce3-90f4-7730b4a575aa ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a409ae48-3ff1-4ce3-90f4-7730b4a575aa
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a409ae48-3ff1-4ce3-90f4-7730b4a575aa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a409ae48-3ff1-4ce3-90f4-7730b4a575aa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a409ae48-3ff1-4ce3-90f4-7730b4a575aa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a409ae48-3ff1-4ce3-90f4-7730b4a575aa /               ext4    errors=remount-ro 0       1
# /media/DATA was on /dev/sda2 during installation
UUID=70E61D8D3E1E3156 /media/DATA     ntfs    defaults,umask=007,gid=46 0       0
# /media/windows was on /dev/sda1 during installation
UUID=7A23738A07B6CC8A /media/windows  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=38c8e0bf-3712-4493-8f59-69609763507f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 135.1GB: boot/grub/core.img
 148.2GB: boot/grub/grub.cfg
 135.1GB: boot/initrd.img-2.6.32-24-generic
 135.1GB: boot/vmlinuz-2.6.32-24-generic
 135.1GB: initrd.img
 135.1GB: vmlinuz

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: initrd.gz
    ??GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi

```

---

### Post by sikander3786 on 2010-11-11
Your Results.txt seems extremely fine to me. I didn't find anything offensive there.

However you can try re-installing Grub. Boot into a Live CD and from the terminal, perform following commands.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Note for the 2nd command it is just sda, not sda5.

---

### Post by hantech on 2010-12-10
i suppose to have grub.cfg if it is GRUB2 isn't it?
but i only have grub menu.lst.

anyone?


                                        ```
   	 	 	 	 	 	                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 54947767 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdc has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   159,862,814   159,862,752  83 Linux
/dev/sda2    *    159,863,760   305,076,239   145,212,480   7 HPFS/NTFS
/dev/sda3         305,090,415   312,576,704     7,486,290   5 Extended
/dev/sda5         305,090,478   312,576,704     7,486,227  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2061 MB, 2061500416 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4026368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,026,367     4,026,305   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0a9425a1-8573-42cd-b814-7b15a93eb4f9   ext3                                     
/dev/sda2        30B44576B4453F98                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8aeed067-7840-471d-9be2-a320540442b7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        30C5-F623                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc         6026-D258                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc         /media/6026-D258         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
# kopt=root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a9425a1-8573-42cd-b814-7b15a93eb4f9

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro  single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		0a9425a1-8573-42cd-b814-7b15a93eb4f9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=0a9425a1-8573-42cd-b814-7b15a93eb4f9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8aeed067-7840-471d-9be2-a320540442b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  28.1GB: boot/grub/core.img
  28.1GB: boot/grub/menu.lst
  28.1GB: boot/grub/stage2
  28.1GB: boot/initrd.img-2.6.28-11-generic
  28.1GB: boot/initrd.img-2.6.31-22-generic
  28.1GB: boot/initrd.img-2.6.32-26-generic
  28.0GB: boot/vmlinuz-2.6.28-11-generic
  28.1GB: boot/vmlinuz-2.6.31-22-generic
  28.1GB: boot/vmlinuz-2.6.32-26-generic
  28.1GB: initrd.img
  28.1GB: initrd.img.old
  28.1GB: vmlinuz
  28.1GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by drs305 on 2010-12-10
hantech,

As you can see, your RESULTS.txt didn't come out in a readable format. Please use the 'Edit' feature and see if you can repaste it into something we can read. You can use the 'preview' function before submitting it.

If you open RESULTS.txt with Gedit and then copy the contents it should paste properly.

---

### Post by hantech on 2010-12-10
> **drs305 said:**
> hantech,

As you can see, your RESULTS.txt didn't come out in a readable format. Please use the 'Edit' feature and see if you can repaste it into something we can read. You can use the 'preview' function before submitting it.

If you open RESULTS.txt with Gedit and then copy the contents it should paste properly.

i'm sorry.
already edit it.
thankyou.

---

### Post by drs305 on 2010-12-10
You are correct that you don't have a grub.cfg file. You have Grub2 installed in the MBR but Grub legacy files in your Ubuntu partition.

The easiest way to fix this is to boot the LiveCD, chroot into your real installation (sda1) and then purge grub/grub-pc/grub-common and then reinstall grub-common and grub-pc.

It's a simple process if you know how to cut/paste into a terminal. Here is the guide on how to accomplish this chroot procedure:
[_HOWTO: Purge and Reinstall Grub 2 from the Live CD_]("http://http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by hantech on 2010-12-10
> **drs305 said:**
> You are correct that you don't have a grub.cfg file. You have Grub2 installed in the MBR but Grub legacy files in your Ubuntu partition.

The easiest way to fix this is to boot the LiveCD, chroot into your real installation (sda1) and then purge grub/grub-pc/grub-common and then reinstall grub-common and grub-pc.

It's a simple process if you know how to cut/paste into a terminal. Here is the guide on how to accomplish this chroot procedure:
[_HOWTO: Purge and Reinstall Grub 2 from the Live CD_]("http://http://ubuntuforums.org/showthread.php?t=1581099")


```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
bash: groups: command not found
root@ubuntu:/# apt-get update #
bash: apt-get: command not found
 
```i stuck on

2. Confirm an Internet Connection

---

### Post by drs305 on 2010-12-10
> **hantech said:**
> i stuck on

2. Confirm an Internet Connection

Did you have an Internet connection before you ran the chroot command?
Did you run the resolv.conf command?
How exactly are you 'stuck'?  Command doesn't run, server not found, etc...
Error messages?

---

### Post by Rubi1200 on 2010-12-10
Just to add to what drs305 has already said; are you using the 32 or 64bit version of Ubuntu on the computer in question?

The LiveCD you use needs to match the system you are trying to chroot into; 32bit for 32bit, 64 for 64.

Hope this helps.

---

### Post by hantech on 2010-12-10
> **drs305 said:**
> Did you have an Internet connection before you ran the chroot command?
Did you run the resolv.conf command?
How exactly are you 'stuck'?  Command doesn't run, server not found, etc...
Error messages?

yes. i have an internet connection before run chroot command.
i try to 'ping google.com' in chroot and it's okay.

```
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
```did i run the resolv.conf using command above?

when i type apt-get update
terminal display : bash: apt-get: command not found

---

### Post by hantech on 2010-12-10
> **Rubi1200 said:**
> Just to add to what drs305 has already said; are you using the 32 or 64bit version of Ubuntu on the computer in question?

The LiveCD you use needs to match the system you are trying to chroot into; 32bit for 32bit, 64 for 64.

Hope this helps.

it is 32 bit.

---

### Post by nm_geo on 2010-12-10
root@ubuntu:/# apt-get update #

Is the # symbol necessary or confusing the issue?  I am really asking the gurus here 
I don't know..

---

### Post by drs305 on 2010-12-10
> **hantech said:**
> 
when i type apt-get update
terminal display : bash: apt-get: command not found

Yes, you copied resolv.conf if you ran that command.

The command "apt-get update" should run. If it's not finding the command it probably means something didn't get mounted correctly. 

I would suggest rebooting and starting again. (Restarting will ensure everything is unmounted when you retry the commands.) 

Did you run the "for i in ..." command. Some users thought that was a comment and not one of the commands to run.

@ nm_geo - the # at the start is just part of the prompt, The # at the end, while not normal, will not affect the running of the command.

---

### Post by nm_geo on 2010-12-10
Thank you drs305 I knew you had the answer to that question.

---

### Post by hantech on 2010-12-14
It still didn't work even I have restarting my pc a few times.
i just reinstall ubuntu.

thanks to all for your help.
really appreciate it.

---

