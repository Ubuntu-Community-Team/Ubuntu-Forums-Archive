---
title: "trying to install"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by alisonf on 2009-08-17
I've been trying to install ubuntu on a dell inspiron 4700 but have been running into some difficulty.  I originally tried to install hardy heron as a dual boot with windows but ran into some issues.  The live cd would work but the install would take me to busy box everytime.  I tried some of the fixes but that didn't seem to work.  So I thought I would try to install the new version of ubuntu but now when my computer boots it only seems to boot into the older ubuntu and doesn't even attempt the newer install.  Have I installed it incorrectly or is there a setting I can change?  Any help greatly appreciated. Thanks

---

### Post by mapes12 on 2009-08-17
In Terminal ```
sudo fdisk -l
``` and post the output back here.

---

### Post by ptn107 on 2009-08-17
Try using a Dell Factory Recovery DVD for Ubuntu 9.04[1] or Ubuntu 8.04.1.[2]

[1] [http://linux.dell.com/files/ubuntu/jaunty/iso-images/ubuntu-9.04-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/jaunty/iso-images/ubuntu-9.04-dell-reinstall.iso)

[2] [http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso)

[http://linux.dell.com/wiki/index.php/Products/Client](http://linux.dell.com/wiki/index.php/Products/Client)

---

### Post by alisonf on 2009-08-17
so sudo fdisk -l gives me:
 
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32
/dev/sda2   *         620       17031   124074720    7  HPFS/NTFS
/dev/sda3           17032       25841    66603600    5  Extended
/dev/sda5           17032       25476    63844168+  83  Linux
/dev/sda6           25477       25841     2759368+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde71de71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14885   119563731    7  HPFS/NTFS
/dev/sdb2           14886       19457    36724590    5  Extended
/dev/sdb5           14886       19263    35166253+  83  Linux
/dev/sdb6           19264       19457     1558273+  82  Linux swap / Solaris
 
I am afraid I don't have any clue what all that means.  This was done from the live disk as well.  Where do i go from here?

---

### Post by northern lights on 2009-08-17
Most likely you installed two instances of Ubuntu instead of overwriting Hardy with Jaunty. When booting, press the *ESC* key and see whether Jaunty appears in the GRUB menu.

---

### Post by alisonf on 2009-08-17
When I looked at the grub menu it seemed there was only one kernel but is that because when I dual boot I have to choose the 8.04 version of ubuntu before pressing esc to get into the grub menu? or should it show it anyways?

---

### Post by northern lights on 2009-08-17
If there's only Hardy listed in the menu there's only Hardy completely installed.

You've posted the *fdisk -l* output. Do you recognize all your partitions? How many ext3 partitions do you use / have you created?

Count your hdd space - does add up to the entire disks size?

How did you attempt to install Jaunty?

---

### Post by presence1960 on 2009-08-17
Let's see exactly what you have there as well as your boot process. use the link from my signature line from Ubuntu or Live CD to download the boot info script 0.32 to the desktop. Once on the desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here, highlight all pasted text & click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2009-08-17
> **northern lights said:**
> If there's only Hardy listed in the menu there's only Hardy completely installed.



Not necessarily true. GRUB from each version may have been installed to MBR of it's respective disk. If the hardy disk is booting first it's GRUB will not have the jaunty kernels on it because Hardy was installed first. 

it looks like OP installed jaunty to a different disk than hardy instead of installing jaunty to the same partition hardy is on. To avoid all guessing or what may be I suggest running the boot info script which will reveal a plethora of info about the setup and boot process. Then we can go from there.

---

### Post by alisonf on 2009-08-18
So here's the results from running the boot script.  From what I can tell 9.04 is on there.  That's about all I could tell unfortunately.  Thanks for all the help, but more is greatly needed for a newb like me. :)

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf806f806

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,359,279     9,359,217   b W95 FAT32
/dev/sda2    *      9,359,280   257,508,719   248,149,440   7 HPFS/NTFS
/dev/sda3         257,508,720   390,715,919   133,207,200   5 Extended
/dev/sda5         257,508,783   385,197,119   127,688,337  83 Linux
/dev/sda6         385,197,183   390,715,919     5,518,737  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde71de71

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   239,127,524   239,127,462   7 HPFS/NTFS
/dev/sdb2         239,127,525   312,576,704    73,449,180   5 Extended
/dev/sdb5         239,127,588   309,460,094    70,332,507  83 Linux
/dev/sdb6         309,460,158   312,576,704     3,116,547  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="2E35-2EF9" TYPE="vfat" 
/dev/sda2: UUID="C644A78244A77439" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda5: UUID="89d2e356-5779-4303-8547-9cc10c633fdf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="ddb82ae1-659c-4c47-90f9-e0ab0674c24a" TYPE="swap" 
/dev/sdb1: UUID="9250CB1350CAFCCB" TYPE="ntfs" 
/dev/sdb5: UUID="90c9fce7-46fb-4fe9-bd53-4486f3e38913" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="4de9c059-f7a7-4179-9dfb-a0147ad0275a" TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=89d2e356-5779-4303-8547-9cc10c633fdf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=89d2e356-5779-4303-8547-9cc10c633fdf

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

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        89d2e356-5779-4303-8547-9cc10c633fdf
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=89d2e356-5779-4303-8547-9cc10c633fdf ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        89d2e356-5779-4303-8547-9cc10c633fdf
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=89d2e356-5779-4303-8547-9cc10c633fdf ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        89d2e356-5779-4303-8547-9cc10c633fdf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=89d2e356-5779-4303-8547-9cc10c633fdf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ddb82ae1-659c-4c47-90f9-e0ab0674c24a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 168.1GB: boot/grub/menu.lst
 168.2GB: boot/grub/stage2
 168.2GB: boot/initrd.img-2.6.27-7-generic
 168.1GB: boot/vmlinuz-2.6.27-7-generic
 168.2GB: initrd.img
 168.1GB: vmlinuz

======================== sdb1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
c:\wubildr.mbr="Ubuntu" 

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=90c9fce7-46fb-4fe9-bd53-4486f3e38913 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=90c9fce7-46fb-4fe9-bd53-4486f3e38913

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        90c9fce7-46fb-4fe9-bd53-4486f3e38913
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=90c9fce7-46fb-4fe9-bd53-4486f3e38913 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        90c9fce7-46fb-4fe9-bd53-4486f3e38913
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=90c9fce7-46fb-4fe9-bd53-4486f3e38913 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        90c9fce7-46fb-4fe9-bd53-4486f3e38913
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=89d2e356-5779-4303-8547-9cc10c633fdf ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=89d2e356-5779-4303-8547-9cc10c633fdf ro single 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=90c9fce7-46fb-4fe9-bd53-4486f3e38913 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4de9c059-f7a7-4179-9dfb-a0147ad0275a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 151.1GB: boot/grub/menu.lst
 151.2GB: boot/grub/stage2
 151.2GB: boot/initrd.img-2.6.28-11-generic
 151.1GB: boot/vmlinuz-2.6.28-11-generic
 151.2GB: initrd.img
 151.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by presence1960 on 2009-08-18
This is all messed up. The reason you're getting hardy when you boot is your UUID's in the kernel lines of GRUB are hardys. You also have 2 partitions with windows XP on them, one on each disk and one has Ubuntu installed through wubi.

We can try to work with this setup or you can remove duplicate windows partition (sdb1), decide if you want hardy or jaunty & remove the one you don't want. You can keep both. let us know how you want to proceed. BTW why is XP installed twice on the same machine?

---

### Post by alisonf on 2009-08-23
Because the machine is older it has been through a couple of hard disk crashes and some parts have been scavenged off an even older machine.  I believe that's why xp is on there twice.  If one could be removed that 's fantastic but I don't have a boot disk available to me at the moment.  What I would like to do is have the machine dual boot between xp and jaunty because hardy heron just wouldn't seem to work for me.  Any advice on how to boot jaunty and get rid of hardy would be greatly appreciated.

---

### Post by presence1960 on 2009-08-23
> **alisonf said:**
> Because the machine is older it has been through a couple of hard disk crashes and some parts have been scavenged off an even older machine.  I believe that's why xp is on there twice.  If one could be removed that 's fantastic but I don't have a boot disk available to me at the moment.  What I would like to do is have the machine dual boot between xp and jaunty because hardy heron just wouldn't seem to work for me.  Any advice on how to boot jaunty and get rid of hardy would be greatly appreciated.
Ok alisonf, in order to get 9.04 to boot you are going to put GRUB on MBR of sdb (160 GB disk) and then in BIOS set the sdb (160 GB) disk to boot first in the hard disk boot order. This will brring up GRUB from sdb when you boot, which points to 9.04 partition and the menu.lst is correct in that sdb5 partition. So do this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

In #6 use setup (hd1) to put GRUB to MBR of sdb (160 GB disk).

Next reboot and go into BIOS. Set the sdb hard disk (160 GB) to boot first in the hard disk boot order. Save that and exit BIOS. When your machine boots you should get GRUB with correct version of Ubuntu on it. Make sure it boots into Ubuntu.

Then we can sort out which Windows to keep. I see sda1 is recovery partition. I would keep windows on that disk. Even if you have to use the recovery partition to recover windows, your Ubuntu is safe because it is on another hard disk plus you can always unplug the 160 GB disk when you recover windows. 

Then we can get rid of the Ubuntu on sda. But first do these suggestions, once 9.04 is booting we can take care of the other stuff!

---

