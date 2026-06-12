---
title: "Bootloader Replace"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by novasta on 2009-03-01
Hi everybody!
I am a newbie to Linux systems.I have a question.

I installed the latest version of ubuntu to my External hard drive.In my internal hard disk i have WinXp Pro.
I realized after installation that Ubuntu changed the BOOT LOADER for my computer and now Linux Boot loader opens bot Ubuntu and Windows.There is no problem about that.Windows works,Linux works perfect.But When i unplug the External drive(which there is UBUNTU) boot-loader gives error and i cant reach windows.
My question is
Is there any way to replace or copy boot-loader to my C drive  to load windows independently from my External Hard Drive.

Thanks

---

### Post by novasta on 2009-03-02
anybody?

---

### Post by caljohnsmith on 2009-03-02
I think you will find the solution to your problem in either of these threads:

[http://ubuntuforums.org/showthread.php?p=6665548](http://ubuntuforums.org/showthread.php?p=6665548)
[http://ubuntuforums.org/showthread.php?p=6452340](http://ubuntuforums.org/showthread.php?p=6452340)

Let me know how that goes or if you run into problems.

---

### Post by novasta on 2009-03-02
Hi caljohnsmith
I did what you suggest,windows loads OK.But i lost contact with ubuntu.Althouh in bios i set boot drive Usb hdd,it doesn't load.Any advice

By the way thanks very much for your time.

---

### Post by caljohnsmith on 2009-03-02
OK, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Make sure your Ubuntu external drive is connected, then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by novasta on 2009-03-02
```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b943b94

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00d200d2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99f5714a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   299,805,029   299,804,967  83 Linux
/dev/sdc2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdc5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030463 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19cf12d8

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     4,030,462     4,030,400   b W95 FAT32

/dev/sdd1 ends after the last cylinder of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="60A492C5A4929D5A" TYPE="ntfs" 
/dev/sdb1: UUID="20D07919D078F67E" LABEL="Storage" TYPE="ntfs" 
/dev/sdc1: UUID="d66b1b11-f5b0-4bca-b944-e2c9ce294eca" TYPE="ext3" 
/dev/sdc5: UUID="b665e25a-65b8-4a8d-b819-5464afb22bb7" TYPE="swap" 
/dev/sdd1: LABEL="FLASHNOVA" UUID="707C-FCB1" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/FLASHNOVA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
# kopt=root=UUID=d66b1b11-f5b0-4bca-b944-e2c9ce294eca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d66b1b11-f5b0-4bca-b944-e2c9ce294eca

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
uuid		d66b1b11-f5b0-4bca-b944-e2c9ce294eca
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d66b1b11-f5b0-4bca-b944-e2c9ce294eca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d66b1b11-f5b0-4bca-b944-e2c9ce294eca
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d66b1b11-f5b0-4bca-b944-e2c9ce294eca ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d66b1b11-f5b0-4bca-b944-e2c9ce294eca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d66b1b11-f5b0-4bca-b944-e2c9ce294eca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d66b1b11-f5b0-4bca-b944-e2c9ce294eca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d66b1b11-f5b0-4bca-b944-e2c9ce294eca ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d66b1b11-f5b0-4bca-b944-e2c9ce294eca
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


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=d66b1b11-f5b0-4bca-b944-e2c9ce294eca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=b665e25a-65b8-4a8d-b819-5464afb22bb7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/menu.lst
   6.7GB: boot/grub/stage2
   6.8GB: boot/initrd.img-2.6.27-11-generic
   6.8GB: boot/initrd.img-2.6.27-7-generic
   6.7GB: boot/vmlinuz-2.6.27-11-generic
   6.7GB: boot/vmlinuz-2.6.27-7-generic
   6.8GB: initrd.img
   6.8GB: initrd.img.old
   6.7GB: vmlinuz
   6.7GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-03-02
OK, how about doing:
```
sudo grub
grub> root (hd2,0)
grub> makeactive
grub> setup (hd2)
grub> quit

```
Reboot, set your BIOS to boot the Ubuntu sdc drive, and if all goes well you should be able to boot into Ubuntu. Let me know how that goes.

---

### Post by novasta on 2009-03-02
now,still gives some eror that i cant understand.
i tried for both HDD(anyway i have 2 hdd + 1 external)

here is the results: (first i tried this)

```
grub> root (hd2,0)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

here is the results: (secondly, i tried to adress hd3 -if i am correct hd3,0 my external drive's-)

```
grub> root (hd3,0)

grub> setup (hd3,0) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd3,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd3,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd3,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

```

And i reboot computer and nothing occurs,windows have loaded:)

---

### Post by caljohnsmith on 2009-03-02
It may be your HDD device names are changing. If using "root (hd3,0)" works, then you should do "setup (hd3)", not "setup (hd3,0)".

---

### Post by novasta on 2009-03-02
i tried again,here is the result

```

grub> setup (hd3)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
```

---

### Post by caljohnsmith on 2009-03-02
OK, let's try again:
```
sudo grub
grub> root (hd3,0)
grub> setup (hd3)
grub> quit
```
And please post the output of the commands before doing "quit".

---

### Post by novasta on 2009-03-03
```
grub> setup (hd3)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
```

same eror again.I dont understand i opened live cd.and then check stage1 if it's there(in boot folder of external hdd).And it's there.And i thought that this bootloader thing written in C:(primary hdd).I am stuck.
What do you suggest re-install Ubuntu?

---

### Post by novasta on 2009-03-03
i recover Grub again.And all things all-right now.Just cant accomplished what i need,but no prblem, ubuntu works.

thanks very much for your time.

---

