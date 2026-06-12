---
title: "Grub2 won't dual-boot XP"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by YesWeCan on 2010-06-01
Why can't they ever get GRUB right? Grub2 has a nicer look and feel but it still has its share of critical defects and does not seem to have been tested very well with Windows.

I have 2 hard disks. One, hd0, has Ubuntu 9.04 only. The other, hd1, has Windows XP64 only. Grub is installed on hd0. All was ok using Grub-legacy and then I upgraded to Grub2 yesterday and now I cannot boot XP. I just get a blank screen and blinking cursor.

I am using Grub 1.96 (as reported by 'grub-install -v')

After some arduous research (especially as the Gnu folks don't seem to think documentation is valuable) I think I have discovered these facts:
1) XP won't boot because it expects to be hd0. In Grub-legacy this was resolved using the map command: map (hd0) (hd1) and map (hd1) (hd0).
2) The Grub2 system identifies the XP OS and adds it to the menu but fails to add commands to make it think its hd0. So XP hangs when booted.
3) I came across a Grub2 command named drivemap. I read that it does the same thing as map did. When I add this to the Grub2 boot commands it breaks Grub2!
Eg:
[COLOR=Blue]### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
menuentry "Windows XP 64" {
set root=(hd1,1)
drivemap -s (hd0) (hd1)
chainloader +1
}
### END /etc/grub.d/40_custom ###[/COLOR]

When this menu item is selected from the boot menu, Grub fails to boot and reports that the chainloader command is invalid! It is as if the drivemap command changes the place where grub looks for its commands. So this is a catch 22: without the drivemap command XP won't boot and with it Grub can't execute a chainload.

I also notice that, after Grub reports the chainloader invalid error, if I then go back to the boot menu and select the Ubuntu boot it also fails and tells me I need to load a kernel. This confirms that the drivemap command changes something that then affects a normally functional Ubuntu boot script.

I would be most appreciative if anyone can provide a work-around or the source of a fixed Grub2.

Thanks,
Brian

---

### Post by drs305 on 2010-06-01
> **YesWeCan said:**
> 
I would be most appreciative if anyone can provide a work-around or the source of a fixed Grub2.

Thanks,
Brian

Brian, 

Have you tried it without the "drivemap" line?

If you post the contents of the boot info script (between code tags) we can take a look:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by YesWeCan on 2010-06-01
Yes, without the drivemap command I end up with a blank screen and flashing cursor and nothing happens. I am assuming this is because the XP booter hangs if it isn't hd0.
(PS: I lied in my post to keep things simpler. I have a 3rd, 34GB HD also with XP on it but I never use it)


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 1.96 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'lvm2pv'

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

vg1-safe: _________________________________________________________________________

    File system:       crypt_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg1-multimedia: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg1-home: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5e10c381

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,917,554    40,917,492  83 Linux
/dev/sda2         378,796,635   390,716,864    11,920,230   5 Extended
/dev/sda5         378,796,698   390,716,864    11,920,167  82 Linux swap / Solaris
/dev/sda3          40,917,555   378,796,634   337,879,080  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb3486c8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   390,700,799   390,700,737   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 34.2 GB, 34219745280 bytes
255 heads, 63 sectors/track, 4160 cylinders, total 66835440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    66,814,334    66,814,272   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptoswap 8e5e9f46-e6ed-4d7c-bd2e-7be09f6f0787   swap                                     
/dev/mapper/_dev_mapper_vg1_safe a9c444e7-5849-4490-90ee-eb98fb37d464   ext4                                     
/dev/mapper/vg1-home eb587913-3bd2-4fc7-b146-51c7b8aaed25   ext3                                     
/dev/mapper/vg1-multimedia d630422c-d1fc-440f-b954-d8a0954434ef   ext3                                     
/dev/mapper/vg1-safe a78bb0d8-4922-4cb3-ae87-3b1208ba3eed   crypt_LUKS                               
/dev/sda1        98324d6a-7232-47f4-b784-68d72c319396   ext3                                     
/dev/sda3        nOrFSp-tFq5-Y50s-gA5Z-9Pxm-4XUq-35AGdT lvm2pv                                   
/dev/sdb1        9A041B2D041B0C3F                       ntfs                                     
/dev/sdc1        5004AD3204AD1BCA                       ntfs                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptoswap
_dev_mapper_vg1_safe
vg1-home
vg1-multimedia
vg1-safe

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/mapper/vg1-home /home                    ext3       (rw)
/dev/mapper/vg1-multimedia /multimedia              ext3       (rw)
/dev/sdb1        /media/WindowsC          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/WindowsD          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/mapper/vg1-safe /home/bam/Safe           crypt      (defaults)


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
default         0

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
# kopt=root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98324d6a-7232-47f4-b784-68d72c319396

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
##      altoptions=(single-user) single
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

title        Chainload into GRUB 2
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Debian GNU/Linux, kernel 2.6.28-18-generic
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro quiet splash
initrd        /boot/initrd.img-2.6.28-18-generic

title        Debian GNU/Linux, kernel 2.6.28-18-generic (recovery mode)
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Debian GNU/Linux, kernel 2.6.28-17-generic
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro quiet splash
initrd        /boot/initrd.img-2.6.28-17-generic

title        Debian GNU/Linux, kernel 2.6.28-17-generic (recovery mode)
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Debian GNU/Linux, kernel 2.6.28-16-generic
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro quiet splash
initrd        /boot/initrd.img-2.6.28-16-generic

title        Debian GNU/Linux, kernel 2.6.28-16-generic (recovery mode)
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Debian GNU/Linux, kernel 2.6.28-11-generic
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic

title        Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Debian GNU/Linux, kernel memtest86+
root        98324d6a-7232-47f4-b784-68d72c319396
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional x64 Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=30
set root=(hd0,1)
search --fs-uuid --set 98324d6a-7232-47f4-b784-68d72c319396
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,1)
search --fs-uuid --set 98324d6a-7232-47f4-b784-68d72c319396
menuentry "Ubuntu, linux 2.6.28-18-generic" {
    linux    /boot/vmlinuz-2.6.28-18-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-18-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-18-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single 
    initrd    /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic" {
    linux    /boot/vmlinuz-2.6.28-17-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-17-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-17-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single 
    initrd    /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic" {
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-16-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single 
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=98324d6a-7232-47f4-b784-68d72c319396 ro single 
    initrd    /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sdb1)" {
    set root=(hd1,1)
    chainloader +1
}
menuentry "Windows XP Professional x64 Edition (on /dev/sdc1)" {
    set root=(hd2,1)
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
menuentry "Windows XP 64" {
drivemap -s (hd0) (hd1)
set root=(hd1,1)
chainloader (hd0,1)+1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=98324d6a-7232-47f4-b784-68d72c319396 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
# UUID=18eb8e02-f6f0-4439-adbb-e546ad0b9bff none swap sw 0 0
/dev/mapper/cryptoswap swap swap sw 0 0

# Home directory
/dev/vg1/home /home ext3 defaults 0 1

# Multi-media directory
/dev/vg1/multimedia /multimedia ext3 defaults 0 1

# DVD RW
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

# floppy disk
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

# 160GB NTFS drive - Windows C:
UUID=9A041B2D041B0C3F /media/WindowsC ntfs-3g defaults,locale=en_GB.UTF-8 0 0

# 34GB NTFS drive - Windows D:
UUID=5004AD3204AD1BCA /media/WindowsD ntfs-3g defaults,locale=en_GB.UTF-8 0 0

# NFS mounts
10.8.0.1:/mnt/Archive /mnt/picassoArchive nfs rsize=8192,wsize=8192,timeo=14,intr
10.8.0.1:/srv /mnt/picassoSrv nfs rsize=8192,wsize=8192,timeo=14,intr

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   2.3GB: boot/grub/grub.cfg
   2.3GB: boot/grub/menu.lst
   4.1GB: boot/initrd.img-2.6.28-11-generic
   2.3GB: boot/initrd.img-2.6.28-16-generic
   2.3GB: boot/initrd.img-2.6.28-17-generic
   2.6GB: boot/initrd.img-2.6.28-18-generic
   4.1GB: boot/vmlinuz-2.6.28-11-generic
   2.3GB: boot/vmlinuz-2.6.28-16-generic
   2.8GB: boot/vmlinuz-2.6.28-17-generic
   2.5GB: boot/vmlinuz-2.6.28-18-generic
   2.6GB: initrd.img
   2.3GB: initrd.img.old
   2.5GB: vmlinuz
   2.8GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /NoExecute=OptOut /usepmtimer 

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  e4 65 d6 00 8c 33 2d c0  8f f7 52 b3 97 9a 5c b4  |.e...3-...R...\.|
00000010  7b ce 63 84 e5 5b 35 35  e2 bb c1 9d 97 16 d4 8b  |{.c..[55........|
00000020  83 dc 40 2b 1c 1c f1 20  74 74 4e c1 3a 1f 8d 6a  |..@+... ttN.:..j|
00000030  b2 bd 23 2b 94 81 b7 4c  5c 88 e4 da 72 c6 d8 9f  |..#+...L\...r...|
00000040  9c 88 1c d2 f8 dd f5 5f  06 f9 96 c0 6a 6c a0 86  |......._....jl..|
00000050  d3 e7 eb fa e8 f9 af 21  fc 14 07 d8 17 ff 77 59  |.......!......wY|
00000060  f0 ed 80 04 9f 84 c8 67  08 ca e2 d1 ce 89 3d ab  |.......g......=.|
00000070  40 af e9 98 12 5e 31 df  8e ba bb 49 1a 7c ba f7  |@....^1....I.|..|
00000080  77 a7 17 11 d2 e5 cb b7  9b aa cd 67 e4 e0 e9 d9  |w..........g....|
00000090  11 59 c8 71 23 71 75 b6  73 01 8c 81 c6 a6 6b 4e  |.Y.q#qu.s.....kN|
000000a0  20 49 16 d8 2c a3 38 c4  63 05 fd f9 2c 4f 58 05  | I..,.8.c...,OX.|
000000b0  5c 8a 91 6e b4 84 52 cc  b8 0b 1b 9e 42 2a c1 7a  |\..n..R.....B*.z|
000000c0  d6 ef cc 0b b1 0f ec c7  9b ae 92 3b 15 08 5d ad  |...........;..].|
000000d0  f4 2c 29 b7 f7 54 f1 1e  8c ad df a9 ca f6 a8 75  |.,)..T.........u|
000000e0  55 3b 62 2c c2 49 f8 19  85 0a 5c 0b 92 0c 4e 49  |U;b,.I....\...NI|
000000f0  e8 a8 3c 34 b5 c3 35 83  a8 05 5d 0b 73 bd 20 de  |..<4..5...].s. .|
00000100  91 ef 1d 69 73 b7 91 5d  20 e1 1d 5b c3 ab fd d9  |...is..] ..[....|
00000110  dc 41 2f 7e 82 5d 9f 17  2e 9e b8 7f b9 cd fa c5  |.A/~.]..........|
00000120  50 e6 62 c1 fd 01 c0 7b  05 ee 27 eb 3f f9 d2 c6  |P.b....{..'.?...|
00000130  09 c7 63 b4 c8 78 8a 16  93 c4 ef 18 d2 e6 9f 42  |..c..x.........B|
00000140  e6 3b 57 18 32 79 80 c7  04 87 ab 8d 5b cb 93 f7  |.;W.2y......[...|
00000150  64 d0 64 75 81 29 21 a4  6f 7a b1 77 de 67 b6 c8  |d.du.)!.oz.w.g..|
00000160  f1 46 3b d1 2f c6 44 e2  fd 39 a4 3f 74 61 09 0b  |.F;./.D..9.?ta..|
00000170  a8 c9 5a c8 dd 0d 4d cd  a2 7a 45 0d a7 a2 38 47  |..Z...M..zE...8G|
00000180  58 1e 7c 6f 0d 4d eb 5b  50 e7 14 ad 64 c4 f0 eb  |X.|o.M.[P...d...|
00000190  dd cb 4e c3 73 b2 68 f9  7c c7 70 6c 3f 3b 4e c5  |..N.s.h.|.pl?;N.|
000001a0  0e c7 5c ce b8 05 f6 cb  ac f5 09 7b 5a 1c 4f 06  |..\........{Z.O.|
000001b0  83 05 49 0b fd a9 2b 2b  73 89 68 b4 b4 67 da 42  |..I...++s.h..g.B|
000001c0  72 7b e4 84 5f 7a a4 f1  d8 c5 2a aa 11 32 ae 88  |r{.._z....*..2..|
000001d0  b2 d0 bd 2a 20 eb 5f 44  c3 db b3 17 ea 04 4d c9  |...* ._D......M.|
000001e0  1b 9b fc e8 ed 2b 7f 06  4a 6a 08 ad 91 b0 70 e2  |.....+..Jj....p.|
000001f0  62 14 41 8f 21 45 35 97  b8 de 39 37 71 68 4b 66  |b.A.!E5...97qhKf|
00000200

Unknown BootLoader  on vg1-safe

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  15 2a c6 c9 9f 78 61 fb  39 1a e3 f5 23 84 e6 fb  |.*...xa.9...#...|
00000080  09 9b 9b 18 05 04 bd 4a  65 d7 54 bd 72 36 4d 00  |.......Je.T.r6M.|
00000090  fb f1 cc 8a df 24 1e 65  a7 6f a9 a1 35 5d 6b 21  |.....$.e.o..5]k!|
000000a0  b9 89 ba ac 00 00 00 0a  61 37 38 62 62 30 64 38  |........a78bb0d8|
000000b0  2d 34 39 32 32 2d 34 63  62 33 2d 61 65 38 37 2d  |-4922-4cb3-ae87-|
000000c0  33 62 31 32 30 38 62 61  33 65 65 64 00 00 00 00  |3b1208ba3eed....|
000000d0  00 ac 71 f3 00 04 b4 00  63 1c dd ae 73 98 18 99  |..q.....c...s...|
000000e0  0f 58 9d 95 85 4a 67 1f  37 bd 90 c6 a6 2c 4f e6  |.X...Jg.7....,O.|
000000f0  f0 88 7e 4c a3 cc 72 5e  00 00 00 08 00 00 0f a0  |..~L..r^........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```

---

### Post by zika on 2010-06-01
> **YesWeCan said:**
> (PS: I lied in my post to keep things simpler. I have a 3rd, 34GB HD also with XP on it but I never use it)[img]http://i.mnsls.com/478/47831.gif[/img]

---

### Post by YesWeCan on 2010-06-01
Please share the joke...I could do with some light relief. :)

---

### Post by zika on 2010-06-01
> **YesWeCan said:**
> Please share the joke...I could do with some light relief. :)But, I did... I was laughing on Your statement that You "lied" about XP... It is not a crime...

---

### Post by YesWeCan on 2010-06-01
Ah I see. :P
I sometimes feel ashamed to mention Windows here, let alone admit I have two installations! When I moved to linux I never looked back...but having XP is a necessary vice at the moment.

---

### Post by zika on 2010-06-01
> **YesWeCan said:**
> Ah I see. :P
I sometimes feel ashamed to mention Windows here, let alone admit I have two installations! When I moved to linux I never looked back...but having XP is a necessary vice at the moment.Nothing to be ashamed of... It's, even, allowed to look back... Not for long, obviously...

---

### Post by oldfred on 2010-06-01
I do not know back with grub 1.96. I have seen the drivemap used regularly with 1.97 Karmic and 1.98 Lucid.

You seem to have two or three choices. Revert to old grub. Install grub 1.98 from Lucid since it is the newest version. Or possibly edit boot.ini so it knows it is on disk 1 not disk 0.

[boot loader] 
timeout=30 
default=multi(0)[COLOR=Red]disk(0)[/COLOR]rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(1)\WINDOWS="Windows XP Professional x64 Edition" /fastdetect /NoExecute=OptOut /usepmtimer 

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)
Need to find the latest release not the experimental one.
[https://launchpad.net/ubuntu/lucid/+source/grub2/1.98-1ubuntu6](https://launchpad.net/ubuntu/lucid/+source/grub2/1.98-1ubuntu6)

---

### Post by YesWeCan on 2010-06-02
Thank you oldfred, spot on info.
I didn't know the boot.ini file could be customized. That's very useful. I think I'll try this first as it seems the most direct approach. Otherwise I'll give that experimental 1.98 a go.

With regard to grub 1.98, will this operate ok in 9.04? I am curious as to why 9.04 package manager defaults to 1.96 whereas 10.04 defaults to 1.98. Can you direct me to the version history for grub2 so I can read the changes made between 1.96 and 1.98?

Thanks again,
Brian

---

### Post by oldfred on 2010-06-02
If you click on the last link launchpad and the first clickable link on that page it takes you to a history of grub. 
                              
[LIST]
[*]       [All versions of grub2 source in Ubuntu]("https://launchpad.net/ubuntu/+source/grub2")
[/LIST]


Do not know if there would be any issue with the newest grub. The only other time I saw someone use a newer grub was the link I showed where someone with 9.10 (1.97) installed the early version of 1.98.

---

### Post by YesWeCan on 2010-06-03
I have tried various combinations of changes to boot.ini but none have worked. I either get a blank screen with flashing cursor or I get a parity error.

I haven't had time to try the 1.98 Grub2 yet.

I may not be looking hard enough but I can't seem to find a change history for Grub2. What I mean by this is a list of code change descriptions, written in English, between the main releases. I suppose I ought to log a bug report.

---

### Post by YesWeCan on 2010-06-06
I have decided to make my life easy and re-install grub-legacy. XP boot works fine again. :)

I was also trying to solve a Grub2 "feature" on an Ubuntu server that has a RAID1 LVM2 whereby the HD drive letter allocations get mixed up at boot time, seemingly at random, and this breaks the RAID1 during boot causing the boot to hang waiting for the user to respond to say it is ok not to mount the RAID. This is a nuiscance and is a disaster if you are remotely administering the server like I am. I read up a lot of articles and postings about Grub2 and came across some weird issues concerning LVM and such; life is too short so I going back to grub-legacy here too until the Gnu folks finish Grub2.

For anyone wanting to revert to grub-legacy here are good instructions: [http://ubuntuforums.org/showthread.php?t=1330347](http://ubuntuforums.org/showthread.php?t=1330347)

---

### Post by YesWeCan on 2010-06-07
I upgraded from 9.04 -> 9.10 -> 10.04 yesterday. Grub2 now boots XP successfully. So I assume something critical changed between Grub2 1.96 and 1.98.

Out of interest my upgrade to 9.10 was hampered for several hours due to a dmraid issue. Although I have fake raid disabled on my Gygabyte MB (I once used it years ago) the upgrade to 9.10 caused Ubuntu to think my two HDs were part of an nVidia RAID array and it failed to find the root partition. Boot failure - scary! This had me foxed for quite some time and it wasn't until I physically disconnected the XP disk (one of the alleged raid pair) that Ubuntu would boot. However, it had a go at resyncing my XP disk first and I had to spend an hour repairing my XP installation. Final solution was to uninstall dmraid completely, reinstall Grub2 from the alternative install CD. So lots of blood everywhere but it is booting ok now. Except for my luks encrypted swap partition that wouldn't mount - I have now refomatted it without encryption.

FYI I estimate I spent 8 hours upgrading Ubuntu and troubleshooting and repairing things. However, prior to this I upgraded a Ubuntu server installation and that took under 2 hours.

---

