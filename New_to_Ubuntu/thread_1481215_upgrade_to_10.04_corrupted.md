---
title: "upgrade to 10.04 corrupted"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-12
Hi, I was using ubuntu 9.04 which I upgraded to 9.10 and then immediately it showed in the package manager that 10.04 was available to upgrade. I permitted it to do this. Now when my computer boots it still shows Ubuntu 9.04 in the bootloader instead of 10.04 and it dumps a lot of garbage on the screen. It doesnot even go to the login screen. what shall I do?? Can I revert back to 9.10 or do I need to install 10.04 from a CD.

---

### Post by kansasnoob on 2010-05-12
Please post the output of the Boot Info Script using a Live CD as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oaridus on 2010-05-12
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6b64fc8d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,667,519    28,667,457   7 HPFS/NTFS
/dev/sda2          28,676,025   156,296,384   127,620,360   5 Extended
/dev/sda5          28,676,088    44,291,204    15,615,117  83 Linux
/dev/sda6          44,291,268    46,251,134     1,959,867  82 Linux swap / Solaris
/dev/sda7          46,251,198    75,553,694    29,302,497  83 Linux
/dev/sda8          75,553,758    91,184,939    15,631,182  83 Linux
/dev/sda9          91,185,003   100,952,459     9,767,457   b W95 FAT32
/dev/sda10        100,952,523   156,296,384    55,343,862   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       C36F-1E7C                              vfat                                     
/dev/sda1        9AA08F5CA08F3E2F                       ntfs                                     
/dev/sda5        d3c243cb-a3a3-459f-ad85-021a2f3470af   ext3                                     
/dev/sda6                                               swap                                     
/dev/sda7        edb69a9a-bd5f-431a-b0cf-31029c4d406f   ext3                                     
/dev/sda8        3c91ae2d-ee48-4859-9fb6-3cbf570f4a90   ext3                                     
/dev/sda9        8DC0-7BB9                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sda7        /data                    ext3       (rw)
/dev/sda9        /win_small               vfat       (rw)
/dev/sda10       /win_big                 vfat       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub, info grub, update-grub
#            grub-install, grub-floppy,
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet

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
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-686
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/sda5 ro quiet
initrd        /boot/initrd.img-2.6.26-2-686

title        Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/sda5 ro single
initrd        /boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title        Ubuntu 9.04, memtest86+ (on /dev/sda
root        (hd0,7)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
/dev/sda7       /data           ext3    defaults        0       2
/dev/sda9       /win_small      vfat    defaults        0       0
/dev/sda10      /win_big        vfat    defaults        0       0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda5: Location of files loaded by Grub: ===================


  17.7GB: boot/grub/menu.lst
  17.7GB: boot/grub/stage2
  17.8GB: boot/initrd.img-2.6.26-2-686
  17.8GB: boot/initrd.img-2.6.26-2-686.bak
  17.7GB: boot/vmlinuz-2.6.26-2-686
  17.8GB: initrd.img
  17.7GB: vmlinuz

=========================== sda8/boot/grub/menu.lst: ===========================

# menu.lst - See: grub, info grub, update-grub
#            grub-install, grub-floppy,
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
# kopt=root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Debian GNU/Linux, kernel 2.6.18-6-686 (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.18-6-686 root=/dev/sda5 ro 
initrd        /boot/initrd.img-2.6.18-6-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Debian GNU/Linux, kernel 2.6.18-6-686 (single-user mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.18-6-686 root=/dev/sda5 ro single 
initrd        /boot/initrd.img-2.6.18-6-686
savedefault
boot


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 /               ext3    relatime,errors=remount-ro 0       1
# /media/data was on /dev/sda7 during installation
UUID=edb69a9a-bd5f-431a-b0cf-31029c4d406f /media/data       ext3    relatime        0       2
# /media/win_big was on /dev/sda10 during installation
UUID=C36F-1E7C  /media/win_big    vfat    defaults,umask=007,gid=46 0       1
# /media/win_small was on /dev/sda9 during installation
UUID=8DC0-7BB9  /media/win_small  vfat    defaults,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=dcdce6cf-85cc-435d-b260-60dcf0198f32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  40.8GB: boot/grub/menu.lst
  40.8GB: boot/grub/stage2
  40.9GB: boot/initrd.img-2.6.28-15-generic
  40.9GB: boot/initrd.img-2.6.32-21-generic
  40.9GB: boot/vmlinuz-2.6.28-15-generic
  40.9GB: boot/vmlinuz-2.6.32-21-generic
  40.9GB: initrd.img
  40.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda

---

### Post by kansasnoob on 2010-05-12
You're going to palm slap yourself in the forehead :P

You also have Debian on sda5:

> sda5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Debian GNU/Linux 5.0
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

And it has control of booting:

> => Grub 0.97 is installed in the MBR of /dev/sda and [B][COLOR="Red"]looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst[/COLOR][/B].

Legacy grub menu.lst's only "auto-magically" update their own kernel updates :)

Lucid's menu.lst did update properly:

```
title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid 3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid 3c91ae2d-ee48-4859-9fb6-3cbf570f4a90
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=3c91ae2d-ee48-4859-9fb6-3cbf570f4a90 ro single
initrd /boot/initrd.img-2.6.32-21-generic
```

So you can either manually add Lucid to Debian's menu.lst or (I checked Lucid's menu.lst and it looks pretty good) so you could just hand boot off to Lucid by booting into Debian and running:

```
sudo grub
```

```
root (hd0,7)
```

```
setup (hd0)
```

Note: wait for it to say done!

```
quit
```

Note: there is one tiny glitch in the Debian entries in Lucid's menu.lst, the "quiet" is missing where indicated below in red:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title Debian GNU/Linux, kernel 2.6.18-6-686 (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.18-6-686 root=/dev/sda5 ro **[COLOR="Red"]quiet[/COLOR]**
initrd /boot/initrd.img-2.6.18-6-686
savedefault
boot
```

That would only effect the quiet splash.

That's what's nice about grub2! If Lucid had grub2 you should be able to just hand boot off to it and run "sudo update-grub" :)

If you do decide to upgrade to grub2 let me know. (Don't do it the official way, it leaves remnants of legacy grub and flubs up in time.)

---

### Post by oaridus on 2010-05-16
I reinstalled unbuntu 10.04 from scratch to solve this problem. It worked

---

