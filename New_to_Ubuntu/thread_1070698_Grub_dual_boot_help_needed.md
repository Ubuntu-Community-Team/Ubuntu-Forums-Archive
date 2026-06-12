---
title: "Grub dual boot help needed"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by saunders on 2009-02-15
Hi,

I've just installed Intrepid on a newly installed second hard disk of a computer. I followed the default options and Grub was loaded onto this HD.

Restarting took me directly into XP, and I guessed the boot loader had to be shifted onto the first HD to give me the option of selecting which OS I wanted to use. To do that, I followed [this thread]("http://ubuntuforums.org/showthread.php?t=609548").

On restarting, grub showed up and boots fine into Ubuntu.

However, selecting XP from the grub menu gives me GRUB ERROR 13.

I'm guessing the loader is looking in the wrong hard drive for XP. 

Can anyone help me fix this? How do I point Grub towards XP?

Here's my output from **fdisk -l**

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dff3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29480   236798068+  83  Linux
/dev/sda2           29481       30401     7397932+   5  Extended
/dev/sda5           29481       30401     7397901   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9019    72445086    7  HPFS/NTFS
/dev/sdb2            9021        9729     5695042+   c  W95 FAT32 (LBA)

and here's my **grub menu.lst**

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Many thanks!

---

### Post by minsf on 2009-02-15
what commands did you use to install the MBR? you say that you follow that thread, but what commands did you actually entered in the grub shell? 

does the linux boot ok, or do u also get an error when booting ubuntu?

i am not sure, but it seems to me that hd0 is your 80GB disk (/dev/sdb) because that's where the bios goes now. so maybe you should load windows from (hd0,0). (linux might still boot fine, because grub gives it a specific root id, or something like that...)
to be sure, please enter a grub shell (with "sudo grub") and then enter "geometry (hd0)" and "geometry (hd1)" and post here the output. this will identify hd0 and hd1 for us.

another possibility is to try to change the boot order in the bios. currently it seems that it transfers control to the MBR in the 80GB drive where you have the windows (/dev/sdb), but maybe you can change it in the bios. then you dont need to install grub to that disk, but to the 250GB disk (and i guess it will already be installed there).

---

### Post by minsf on 2009-02-15
> **saunders said:**
> 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

this seems a bit redundant to me. but i am not sure.
also do you have two versions of windows installed on the 80GB drive? if you just have one windows (in the 1st partition), and the other partition is used for storage or something like that, then the following seems to be redundant too:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


---

### Post by saunders on 2009-02-15
Thanks for the reply...

OK, commands used in the grub shell were:
**find /boot/grub/stage1** (which told me grub was on hd0)
**root hd(0)**
**setup (hd1)** (to install grub to the 80Gb disk containing XP)

Booting Ubuntu from Grub works fine, it's only XP being the problem.

I'm pretty sure sda1 is the linux partition hd0, and XP is sdb1, hd1

Geometry outputs are:

grub> geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> geometry (hd1)
drive 0x81: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is fat, partition type 0xc

---

### Post by saunders on 2009-02-15
Oops, just saw your second post...

There are two partitions on the XP disk, I believe the second one is some sort of disk backup. The computer belongs to a member of the family, not me.

---

### Post by saunders on 2009-02-15
Just out of interest, how do the **map** commands in the grub menu.lst work?

map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

Is this telling the computer to treat hd0 as hd1 and vice versa? 
If that's the case, will swapping the hd0 and hd1 point the bootloader back towards XP?

---

### Post by caljohnsmith on 2009-02-15
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by saunders on 2009-02-18
SOrry for the delay...

Right, the output...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Lilo is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dff3b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   473,596,199   473,596,137  83 Linux
/dev/sda2         473,596,200   488,392,064    14,795,865   5 Extended
/dev/sda5         473,596,263   488,392,064    14,795,802  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   144,890,234   144,890,172   7 HPFS/NTFS
/dev/sdb2         144,906,300   156,296,384    11,390,085   c W95 FAT32 (LBA)


Drive sdg: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdg: 990 MB, 990380032 bytes
33 heads, 34 sectors/track, 431 cylinders, total 483584 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             34       483,581       483,548   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="044bc646-0777-4ae4-8cb0-4faebdd1eef1" TYPE="ext3" 
/dev/sda5: UUID="7718f0c2-224a-49ad-9072-842a81606a87" TYPE="swap" 
/dev/sdb1: UUID="701C4CDE038E987E" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sdb2: LABEL="PRESARIO_RP" UUID="4B6E-6BC0" TYPE="vfat" 
/dev/sdg1: LABEL="ZEN Stone" UUID="0000-0000" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nigel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nigel)


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
# kopt=root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=044bc646-0777-4ae4-8cb0-4faebdd1eef1

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
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		044bc646-0777-4ae4-8cb0-4faebdd1eef1
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=044bc646-0777-4ae4-8cb0-4faebdd1eef1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7718f0c2-224a-49ad-9072-842a81606a87 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  53.1GB: boot/grub/menu.lst
  53.1GB: boot/grub/stage2
  53.2GB: boot/initrd.img-2.6.27-11-generic
  53.1GB: boot/initrd.img-2.6.27-7-generic
  53.2GB: boot/vmlinuz-2.6.27-11-generic
  53.2GB: boot/vmlinuz-2.6.27-7-generic
  53.2GB: initrd.img
  53.1GB: initrd.img.old
  53.2GB: vmlinuz
  53.2GB: vmlinuz.old

================================ sdb2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sdb2/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

Many thanks!

---

### Post by caljohnsmith on 2009-02-18
How about trying this entry for Windows:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Let me know exactly what happens when you try it from the Grub menu, and we can work from there if necessary.

---

### Post by saunders on 2009-02-19
Thanks for this, caljohnsmith. I'll have to try this on the weekend...it's a family member's computer so I don't have access to it until then.

---

### Post by saunders on 2009-02-22
That worked like a charm!

I can now successfully dual boot into Ubuntu and XP.

Many thanks Caljohnsmith!

---

### Post by caljohnsmith on 2009-02-22
Glad that entry worked OK to boot Windows; cheers and enjoy your dual-boot setup. :)

---

