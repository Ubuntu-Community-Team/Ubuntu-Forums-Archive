---
title: "GRUB Booting stage 1.5 Error 15,nothing works"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by aliov_85 on 2009-05-08
Hi guys, trying to load up my PC which (was) dual booting Ubuntu Jaunty and WinXP.

The problem:
[quote]Can't load past the boot loader. I get the messages;
GRUB Loading Stage1.5.


GRUB loading, please wait...
Error 15
[quote/]

I can't neither boot from live cd,neither go to the setup of the pc at the start up stage

best regards

---

### Post by Gone fishing on 2009-05-08
Have a look at [http://ubuntuforums.org/showthread.php?t=297261&page=2](http://ubuntuforums.org/showthread.php?t=297261&page=2)

To boot from the CD should be no problem if you have BIOS set to boot from the CD. The setup page you mean BIOS? Unplug from the power and reboot should be fine.

---

### Post by cjv8888 on 2009-05-08
> **aliov_85 said:**
> Hi guys, trying to load up my PC which (was) dual booting Ubuntu Jaunty and WinXP.

The problem:
[quote]Can't load past the boot loader. I get the messages;
GRUB Loading Stage1.5.


GRUB loading, please wait...
Error 15
[quote/]

I can't neither boot from live cd,neither go to the setup of the pc at the start up stage

best regards

Do you mean you were dual booting successfully before it suddenly went wrong?

---

### Post by aliov_85 on 2009-05-08
exactly cjv8888

---

### Post by cjv8888 on 2009-05-08
Did it happen just after a kernel update or some change in the hardware?

---

### Post by aliov_85 on 2009-05-08
I don't think there was an kernel update. I was on windows and I tried to resizing partitions through partition magick.But I didn't  made any change. I've two ubuntus installed(mistakely)

---

### Post by cjv8888 on 2009-05-08
First of all you will need to boot a live CD.

You will need to change the boot order in the BIOS to boot from CDROM first.
To get to the BIOS page, press the F8 or Delete or another function button while the computer first starts.

---

### Post by aliov_85 on 2009-05-08
What should I do after booting from live CD?

Thanks

---

### Post by cjv8888 on 2009-05-08
To get a better picture of your booting problem, please then download the **Boot Info Script** to your liveCD desktop from the following link

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and do:

> sudo bash ~/Desktop/boot_info_script*.sh

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by aliov_85 on 2009-05-08
Here you have

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #12 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb74ce6e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   976,768,064   812,921,130   f W95 Ext d (LBA)
/dev/sda5         163,846,998   327,693,869   163,846,872   7 HPFS/NTFS
/dev/sda6         327,693,933   465,017,489   137,323,557   7 HPFS/NTFS
/dev/sda7         465,017,553   490,319,864    25,302,312  83 Linux
/dev/sda8         490,319,928   491,540,804     1,220,877  82 Linux swap / Solaris
/dev/sda9         491,540,868   544,491,044    52,950,177   7 HPFS/NTFS
/dev/sda10        544,491,108   954,277,064   409,785,957  83 Linux
/dev/sda11        959,514,318   971,530,874    12,016,557  82 Linux swap / Solaris
/dev/sda12        971,530,938   976,414,634     4,883,697  83 Linux
/dev/sda13        976,414,698   976,768,064       353,367  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="68E4078EE4075E26" LABEL="System" TYPE="ntfs" 
/dev/sda5: UUID="683C058A3C05550A" LABEL="Data" TYPE="ntfs" 
/dev/sda6: UUID="18642BE9642BC878" LABEL="Mehdi" TYPE="ntfs" 
/dev/sda7: UUID="a84e3009-36b1-4a27-88a3-4627d1a0fb38" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="1bf48589-c511-4855-af80-24548d2d5c34" TYPE="swap" 
/dev/sda9: UUID="F66C3A836C3A3F25" LABEL="Mahtab" TYPE="ntfs" 
/dev/sda10: UUID="71fa0116-b58e-4726-9592-00e6b6c32103" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="90bb6406-180f-4226-a84d-8578a75d9638" TYPE="swap" 
/dev/sda12: UUID="8151f77a-d224-4b2d-823c-54f02dcd95ed" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: UUID="caa7a13c-9339-4085-858d-800cdba95da9" TYPE="swap" 
/dev/sdd1: LABEL="WDPASSPORT" UUID="F8C9-F860" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/WDPASSPORT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=9K5ZD2

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a84e3009-36b1-4a27-88a3-4627d1a0fb38 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a84e3009-36b1-4a27-88a3-4627d1a0fb38

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a84e3009-36b1-4a27-88a3-4627d1a0fb38
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a84e3009-36b1-4a27-88a3-4627d1a0fb38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a84e3009-36b1-4a27-88a3-4627d1a0fb38
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a84e3009-36b1-4a27-88a3-4627d1a0fb38 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a84e3009-36b1-4a27-88a3-4627d1a0fb38
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=71fa0116-b58e-4726-9592-00e6b6c32103 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=71fa0116-b58e-4726-9592-00e6b6c32103 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 9.04, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda12 during installation
UUID=a84e3009-36b1-4a27-88a3-4627d1a0fb38 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda13 during installation
UUID=1bf48589-c511-4855-af80-24548d2d5c34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 238.6GB: boot/grub/menu.lst
 238.6GB: boot/grub/stage2
 238.6GB: boot/initrd.img-2.6.28-11-generic
 238.7GB: boot/vmlinuz-2.6.28-11-generic
 238.6GB: initrd.img
 238.7GB: vmlinuz

========================== sda10/boot/grub/menu.lst: ==========================

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
# kopt=root=UUID=71fa0116-b58e-4726-9592-00e6b6c32103 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=71fa0116-b58e-4726-9592-00e6b6c32103

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		71fa0116-b58e-4726-9592-00e6b6c32103
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=71fa0116-b58e-4726-9592-00e6b6c32103 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		71fa0116-b58e-4726-9592-00e6b6c32103
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=71fa0116-b58e-4726-9592-00e6b6c32103 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		71fa0116-b58e-4726-9592-00e6b6c32103
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=71fa0116-b58e-4726-9592-00e6b6c32103 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=90bb6406-180f-4226-a84d-8578a75d9638 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 439.1GB: boot/grub/menu.lst
 439.2GB: boot/grub/stage2
 439.2GB: boot/initrd.img-2.6.28-11-generic
 439.2GB: boot/vmlinuz-2.6.28-11-generic
 439.2GB: initrd.img
 439.2GB: vmlinuz

=============================== sda12/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=8151f77a-d224-4b2d-823c-54f02dcd95ed /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=caa7a13c-9339-4085-858d-800cdba95da9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc 


```

---

### Post by cjv8888 on 2009-05-08
You seem to have 2 bootable partitions of Ubuntu at sda7 and sda10 but the grub is pointing to sda12.

Try the following from the terminal of your live CD line by line.

```
sudo grub
grub> root (hd0,6)
grub> setup (hd0)
grub> quit
```

---

### Post by aliov_85 on 2009-05-08
Thank you very much.

Now grub is loaded after a while by initializing first paritions and then it loads grub as before. I tried to resize partitions from windows but couldn't resize ext3 partitions. How can I remove the ubuntu on sd10 and it's swap memory and extend hd0,6?

---

### Post by cjv8888 on 2009-05-08
> **aliov_85 said:**
> Thank you very much.

Now grub is loaded after a while by initializing first paritions and then it loads grub as before. I tried to resize partitions from windows but couldn't resize ext3 partitions. How can I remove the ubuntu on sd10 and it's swap memory and extend hd0,6?

You are booted into sda7 and sda10 is unmounted.  So you can run Gparted from Administration-Partition Editor then proceed to delete sda10 and expand sda7 etc.  Partition Magic will not work properly on ext3 partitions.  If you have Boot Magic in Windows, make sure it is disabled.

If there is no partition editor there , just install by

> sudo apt-get install gparted

Cheers!

---

