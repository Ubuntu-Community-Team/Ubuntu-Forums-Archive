---
title: "Yet Another &quot;NTLDR is missing&quot; thread"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Lorthirk on 2009-05-11
Hello all. I had Windows Vista on my desktop PC, and I decided to try out Ubuntu 9.04. While Ubuntu is booting and working fine, I have troubles to boot back in Vista. I have a SATA HDD which is hosting both Vista and Ubuntu, plus another data partition, and an IDE drive with only data on it. As topic says, when I choose "Windows Vista" in GRUB, i get the NTLDR is missing message. here's the content of bootscript.sh:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /GRLDR

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /GRLDR

sdb3: _________________________________________________________________________

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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 164.6 GB, 164696555520 byte
255 testine, 63 settori/tracce, 20023 cilindri, totale 321672960 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x26fab749

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   321,669,494   321,669,432   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.0 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x04650464

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    84,791,069    84,791,007   7 HPFS/NTFS
/dev/sdb2          84,791,073   586,078,182   501,287,110   7 HPFS/NTFS
/dev/sdb3         586,083,330   625,137,344    39,054,015   5 Extended
/dev/sdb5         586,083,393   590,083,514     4,000,122  82 Linux swap / Solaris
/dev/sdb6         590,083,578   625,137,344    35,053,767  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A993F98A6D23B6DB" LABEL="SCRIVANIA_D" TYPE="ntfs" 
/dev/sdb1: UUID="BC42441F4243DCB0" LABEL="SCRIVANIA_C" TYPE="ntfs" 
/dev/sdb2: UUID="0000000046E2AF67" LABEL="SCRIVANIA_E" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="d0c34487-7ee6-4ffd-b822-de851a9d7bfb" 
/dev/sdb6: UUID="1058b9a9-af48-47cb-80dd-df3af0fdb12e" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext4 (rw,relatime,errors=remount-ro)
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
/dev/sdb1 on /windows/C type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /windows/D type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=512)
/dev/sdb2 on /windows/E type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cm0901/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cm0901)
/dev/sr0 on /media/cdrom0 type iso9660 (rw,nosuid,nodev,utf8,user=cm0901)


=========================== sdb6/boot/grub/menu.lst: ===========================

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
default        3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

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
# kopt=root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1058b9a9-af48-47cb-80dd-df3af0fdb12e

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

title        Ubuntu 9.04, kernel 2.6.28-12-generic
uuid        1058b9a9-af48-47cb-80dd-df3af0fdb12e
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid        1058b9a9-af48-47cb-80dd-df3af0fdb12e
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro  single
initrd        /boot/initrd.img-2.6.28-12-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        1058b9a9-af48-47cb-80dd-df3af0fdb12e
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        1058b9a9-af48-47cb-80dd-df3af0fdb12e
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Chainload into GRUB 2
#root        1058b9a9-af48-47cb-80dd-df3af0fdb12e
#kernel        /boot/grub/core.img

title        Ubuntu 9.04, memtest86+
uuid        1058b9a9-af48-47cb-80dd-df3af0fdb12e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
#title        Windows Vista (loader)
#rootnoverify    (hd1,1)
#savedefault
#map        (hd0) (hd1)
#map        (hd1) (hd0)
#chainloader    +1


=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd1,6)
search --fs-uuid --set 1058b9a9-af48-47cb-80dd-df3af0fdb12e
if font /usr/share/grub/ascii.pff ; then
set gfxmode=1280x1024
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
set root=(hd1,6)
search --fs-uuid --set 1058b9a9-af48-47cb-80dd-df3af0fdb12e
menuentry "Ubuntu, linux 2.6.28-11-generic" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro splash #GRUB_DISABLE_LINUX_UUID=true vga=795 quiet splash
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e ro single splash #GRUB_DISABLE_LINUX_UUID=true vga=795
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
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    set root=(hd1,1)
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    set root=(hd1,2)
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=1058b9a9-af48-47cb-80dd-df3af0fdb12e /               ext4    relatime,errors=remount-ro 0       1
# /windows/C was on /dev/sdb1 during installation
UUID=BC42441F4243DCB0 /windows/C      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /windows/D was on /dev/sda1 during installation
UUID=A993F98A6D23B6DB /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /windows/E was on /dev/sdb2 during installation
UUID=0000000046E2AF67 /windows/E      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=d0c34487-7ee6-4ffd-b822-de851a9d7bfb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 304.6GB: boot/grub/grub.cfg
 303.7GB: boot/grub/menu.lst
 304.4GB: boot/grub/stage2
 305.4GB: boot/initrd.img-2.6.28-11-generic
 302.9GB: boot/initrd.img-2.6.28-12-generic
 304.5GB: boot/vmlinuz-2.6.28-11-generic
 306.8GB: boot/vmlinuz-2.6.28-12-generic
 302.9GB: initrd.img
 305.4GB: initrd.img.old
 306.8GB: vmlinuz
 304.5GB: vmlinuz.old

```Any help is really appreciated. Thanks.

---

### Post by lisati on 2009-05-11
Do you have a Vista disk or some such recovery disk? If so, you might be able to use it to get the NTLDR error fixed using a recovery console.

---

### Post by Lorthirk on 2009-05-11
Yes, I have a Vista setup disk... But after that, won't GRUB go away overwritten by the "new" NTLDR?

---

### Post by lisati on 2009-05-11
A tentative "possibly", but if you have an Ubuntu Live CD available, it is fairly straightforward to reinstall grub.

---

### Post by Lorthirk on 2009-05-11
Ok, So after I reinstall GRUB too, everything should be fine? Or I'll find myself again back to square one?

---

### Post by lisati on 2009-05-11
> **Lorthirk said:**
> Ok, So after I reinstall GRUB too, everything should be fine? Or I'll find myself again back to square one?

I've only had the missing message once, some months back, which was easily fixed with the help of a Vista recovery disk. Once I'd done the repair and made sure Ubuntu was bootable, I don't recall any other problems.

---

