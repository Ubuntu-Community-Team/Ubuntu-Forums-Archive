---
title: "Apologies another Grub Puzzler"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by dazzler on 2009-05-24
Sorry about this i have been trying to get this sorted myself but im in a muddle.

Basically i was testing Windows 7 beta, long story short it messed up and didnt like my cpu or something it was constantly at 100% after an update anyway that had to go.

I stuck another hd in to backup all important files to, and have done so, managed to install xp and transfer said backups, i then wiped the windows 7 drive which had grub installed.

I have reinstalled grub but cant get the xp boot to work properly can someone look at my menu.lst for me im lost now, thanks.

Fdisk output
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0d1e77c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38765   293057320+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ebc2385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc620c620

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    5  Extended

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b657bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       18701   150215751   83  Linux
/dev/sdd2           18702       19457     6072570    f  W95 Ext'd (LBA)
/dev/sdd5           18702       19457     6072538+  82  Linux swap / Solaris

```

and finally menu.lst

```
hiddenmenu
default 5
timeout 5

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
# kopt=root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72

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

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu jaunty (development branch), memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Pro
root (hd2,0)
chainloader +1

```

sda1 is my Media Drive (photos, music etc)
sdb1 is the xp drive
sdc1 is now wiped
sdd is jaunty

Many thanks

---

### Post by Elfy on 2009-05-24
root (hd2,0) refers to sdc1

Grub counts from 0 - sda1 is hd0,0 and sdb1 is hd1,0 etc.

---

### Post by dazzler on 2009-05-24
Thanks thats what i thought, i did have the right disk/partition in grub.

However it just says 'Starting Up................' when i select that entry.

Do i need to use xp disc and fixmbr and fixboot or something?

---

### Post by Elfy on 2009-05-24
Are you saying that XP is installed on sdc1? Fdisk -l says either sda or sdb - which are hd0 or hd1 not hd2 as is shown in your menu list.

If it is on sdb (hd1) try adding this between root and chainloader

rootnoverify (hd1,0)
map (hd1)(hd0)
map (hd0)(hd1)

---

### Post by dazzler on 2009-05-24
Sorry you were right sdb1 is the xp disk i want to boot, told you i was confused ;)

Changed grub as per your instructions i now get error 11 Unrecognised Device string starting XP entry

title Other operating systems:
root

title Windows XP Pro
root (hd1,0)
rootnoverify (hd1,0)
map (hd1)(hd0)
map (hd0)(hd1)
chainloader +1

---

### Post by Elfy on 2009-05-24
sorry my bad, try a space between the maps

map (hd1) (hd0)
map (hd0) (hd1)

---

### Post by dazzler on 2009-05-24
Lol sorry to drag you into my mess

Now get 
Starting Up.......
Loading Stage 2.......
_ (Blinking)

:oops:

---

### Post by Elfy on 2009-05-24
are you sure it is on sdb - sda appears to have the bootflag

---

### Post by dazzler on 2009-05-24
Yes i know, i dont know why sda1 now shows as boot it changed after i formatted the old windows 7 disc which was boot.

Sda1 is definitely just my media disk, xp for sure is the new 500gb sata drive i have just installed. (sdb1)

I had to change the disk boot order in bios to get to grub stage perhaps if i changed it again to have the 500gb disc boot first, then reinstall grub, would that put me in better standing?

---

### Post by Elfy on 2009-05-24
mmm - ok well it's a long time now since I played with win

Follow [this post]("http://ubuntuforums.org/showpost.php?p=7245321&postcount=5") to get the information for your system then post it here please - also make sure to use code tags around it - it will be long :)

[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end

---

### Post by dazzler on 2009-05-24
Again apologies for this headache heres the results.txt

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdd1 and 
                       looks at sector 248119359 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdd. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d1e77c1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,114,703   586,114,641   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ebc2385

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc620c620

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   5 Extended
Empty Partition


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd5b657bb

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   300,431,564   300,431,502  83 Linux
/dev/sdd2         300,431,565   312,576,704    12,145,140   f W95 Ext d (LBA)
/dev/sdd5         300,431,628   312,576,704    12,145,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="E2144B0D144AE3DF" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: UUID="8874E24374E2341A" TYPE="ntfs" 
/dev/sdd1: UUID="4f7a31ef-f2a1-4868-9ecc-fc646a4ced72" TYPE="ext3" 
/dev/sdd5: TYPE="swap" UUID="e75d2ee5-f6f9-45b8-b730-de9775d21092" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dazzler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dazzler)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=dazzler)


=========================== sdd1/boot/grub/menu.lst: ===========================

hiddenmenu
default 5
timeout 5

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
# kopt=root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72

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

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu jaunty (development branch), memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows XP Pro
root (hd1,0)
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=4f7a31ef-f2a1-4868-9ecc-fc646a4ced72 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=e75d2ee5-f6f9-45b8-b730-de9775d21092 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sdd1: Location of files loaded by Grub: ===================


 126.9GB: boot/grub/menu.lst
 127.0GB: boot/grub/stage2
 127.0GB: boot/initrd.img-2.6.27-11-generic
 127.0GB: boot/initrd.img-2.6.28-11-generic
 127.0GB: boot/vmlinuz-2.6.27-11-generic
 127.0GB: boot/vmlinuz-2.6.28-11-generic
 127.0GB: initrd.img
 127.0GB: initrd.img.old
 127.0GB: vmlinuz
 127.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sde 
```

---

### Post by Elfy on 2009-05-24
Just realised I gave you root and rootnoverify - remove the root line so 

> title Other operating systems:
root

title Windows XP Pro
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

I've also used makeactive in the past I think - add these and try them

title Microsoft Windows
root (hd1,0)
makeactive
chainloader +1

title Microsoft Windows
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

not sure if you still get issues though

---

### Post by dazzler on 2009-05-24
Error 12 on both entries

Will now try a fixmbr and fixboot ive read that may work

---

### Post by Elfy on 2009-05-24
yea - ok :)

afterwards you'll need to reinstall grub for ubuntu

---

