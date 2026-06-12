---
title: "Reinstalling Grub Issue"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by bneva on 2011-06-23
edit: I am using 11.04 32b and am running off my USB while I do this.

So the usual problem, when you reinstall windows it gets rid of Grub.  Now I am following the guide here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I used fdisk -l and got this output
```
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6284573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27428   220315378+   7  HPFS/NTFS
/dev/sda2           27429       30401    23880622+   5  Extended
/dev/sda3           30273       30401     1036161   82  Linux swap / Solaris
/dev/sda5           27429       30272    22844367   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd224d224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7774    62444623+   7  HPFS/NTFS
/dev/sdb2            7775        9729    15702625+   5  Extended
/dev/sdb5            9642        9729      706828+  82  Linux swap / Solaris
/dev/sdb6            7775        9641    14995456   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders
Units = cylinders of 1892 * 512 = 968704 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           5        4138     3909696    c  W95 FAT32 (LBA)
```

Now the Ubuntu I want is sdb6 so I mounted it
```
mount /dev/sdb6 /mnt/hd
```

Here is my problem.  The guide says check your mount using mount | tail -l and you should get an output like 
```
/dev/sda2 on /media/0d104aff-ec8c-44c8-b811-92b993823444 type ext4 (rw,nosuid,nodev,uhelper=devkit)
```

this is my output
```
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb6 on /mnt/hd type ext4 (rw)
```

what line am I supposed to use?  It says I will need volumes UUID later but my output looks nothing like the guides.

---

### Post by TeoBigusGeekus on 2011-06-23
You've mounted your partition on /mnt, that's why you don't see it under /media.

A better guide to reinstall grub2 is [this]("https://help.ubuntu.com/community/Grub2#ChRoot").

---

### Post by bneva on 2011-06-23
> **TeoBigusGeekus said:**
> You've mounted your partition on /mnt, that's why you don't see it under /media.

A better guide to reinstall grub2 is [this]("https://help.ubuntu.com/community/Grub2#ChRoot").

I tried the ChRoot one that you linked me to but it didn't work.  I restarted and there was no grub, it just went straight to windows.

I'm going to try it again, I never did update-grub. maybe that will change something.

edit: I tried it again and it didn't work.  It just keeps going straight back to windows.

---

### Post by bneva on 2011-06-23
I tried using the Boot-Repair on my live CD and I reinstalled it (11.04 on sdb) which is where my partition that I want to use and still nothing!  I might just reinstall ubuntu because that seems like it is the only way it's going to work.

---

### Post by TeoBigusGeekus on 2011-06-23
Sorry, I can't help you; I hate grub2 - I still use grub legacy: plain, simple and does exactly what it's supposed to do without giving me any troubles.
Sorry again...

---

### Post by jtarin on 2011-06-23
> **bneva said:**
> I tried the ChRoot one that you linked me to but it didn't work. If you are able to mount the USB as a Live CD then everything is OK....to that point. You are not entering some commands correctly or missing some commands. I have used the CHROOT environment many times and it works. Link to,and download the BootInfo Script in my signature so we can see your disk setup.

---

### Post by bneva on 2011-06-23
> **jtarin said:**
> If you are able to mount the USB as a Live CD then everything is OK....to that point. You are not entering some commands correctly or missing some commands. I have used the CHROOT environment many times and it works. Link to,and download the BootInfo Script in my signature so we can see your disk setup.

here...
sdb6 is where my 11.04 is.  The only part of the Chroot thing I didn't do was when it said if you have a separate boot partition mount it in /mnt/boot because I wasn't sure what that meant.  Also when I did that, the next command which was a for command didn't work.  So I reverted back to just mounting sdb6 in /mnt

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30462 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   440,630,819   440,630,757   7 NTFS / exFAT / HPFS
/dev/sda2         440,630,820   488,392,064    47,761,245   5 Extended
Extended partition linking to another extended partition.
/dev/sda5         440,630,946   486,319,679    45,688,734  83 Linux
/dev/sda3         486,319,743   488,392,064     2,072,322  82 Linux swap / Solaris

/dev/sda2 overlaps with /dev/sda3

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   124,889,309   124,889,247   7 NTFS / exFAT / HPFS
/dev/sdb2         124,891,134   156,296,384    31,405,251   5 Extended
/dev/sdb5         154,882,728   156,296,384     1,413,657  82 Linux swap / Solaris
/dev/sdb6         124,891,136   154,882,047    29,990,912  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4022 MB, 4022337536 bytes
12 heads, 4 sectors/track, 163669 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               1,096     7,856,127     7,855,032   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6A5C26265C25ED8F                       ntfs       
/dev/sda3        9a3b3779-7a63-4e2c-8ab3-66349eba517c   swap       
/dev/sda5        279a4161-3118-4204-8992-37912d668ffa   ext3       
/dev/sdb1        BEF0A867F0A8281B                       ntfs       New Volume
/dev/sdb5        45ed3126-b054-4858-b826-f84b12d72916   swap       
/dev/sdb6        c35ab644-b9be-4b5d-b694-c84b494564f8   ext4       
/dev/sdc1        12F5-2336                              vfat       PENDRIVE
/dev/sdd1        3433-3231                              vfat       BROOKES

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb6        /mnt                     ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd1        /mnt/usb                 vfat       (rw)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
#timeout		0

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
# kopt=root=UUID=279a4161-3118-4204-8992-37912d668ffa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=279a4161-3118-4204-8992-37912d668ffa

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		279a4161-3118-4204-8992-37912d668ffa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		279a4161-3118-4204-8992-37912d668ffa
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

--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=279a4161-3118-4204-8992-37912d668ffa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=9a3b3779-7a63-4e2c-8ab3-66349eba517c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 215.291691780 = 231.167693824  boot/grub/menu.lst                             1
 215.312451363 = 231.189984256  boot/grub/stage2                               2
 214.525723457 = 230.345241600  boot/initrd.img-2.6.27-11-generic             25
 214.392506599 = 230.202201088  boot/initrd.img-2.6.28-11-generic             43
 214.674725533 = 230.505231360  boot/initrd.img-2.6.28-13-generic             45
 214.681550026 = 230.512559104  boot/initrd.img-2.6.28-15-generic             42
 214.364205360 = 230.171812864  boot/vmlinuz-2.6.27-11-generic                13
 214.292214394 = 230.094513152  boot/vmlinuz-2.6.28-11-generic                 7
 214.322609901 = 230.127150080  boot/vmlinuz-2.6.28-13-generic                21
 214.277314186 = 230.078514176  boot/vmlinuz-2.6.28-15-generic                15
 214.681550026 = 230.512559104  initrd.img                                    42
 214.674725533 = 230.505231360  initrd.img.old                                45
 214.277314186 = 230.078514176  vmlinuz                                       15
 214.322609901 = 230.127150080  vmlinuz.old                                   21

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root c35ab644-b9be-4b5d-b694-c84b494564f8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root c35ab644-b9be-4b5d-b694-c84b494564f8
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root c35ab644-b9be-4b5d-b694-c84b494564f8
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c35ab644-b9be-4b5d-b694-c84b494564f8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root c35ab644-b9be-4b5d-b694-c84b494564f8
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c35ab644-b9be-4b5d-b694-c84b494564f8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root c35ab644-b9be-4b5d-b694-c84b494564f8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos6)'
	search --no-floppy --fs-uuid --set=root c35ab644-b9be-4b5d-b694-c84b494564f8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 6A5C26265C25ED8F
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.28-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/vmlinuz-2.6.27-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa ro single
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 279a4161-3118-4204-8992-37912d668ffa
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=45ed3126-b054-4858-b826-f84b12d72916 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.769203186 = 68.471660544   boot/grub/core.img                             1
  63.757823944 = 68.459442176   boot/grub/grub.cfg                             1
  60.713111877 = 65.190207488   boot/initrd.img-2.6.38-8-generic               1
  64.378883362 = 69.126299648   boot/vmlinuz-2.6.38-8-generic                  1
  60.713111877 = 65.190207488   initrd.img                                     1
  64.378883362 = 69.126299648   vmlinuz                                        1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by jtarin on 2011-06-23
You can run CHROOT again and install Grub2 to "/dev/sda" to give you a Grub menu to boot Windows and Ubuntu or you can use the link in my signature to leave Grub where it is ( MBR of /dev/sdb )and use EasyBCD to manage your boots.

---

