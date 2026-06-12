---
title: "Can't entry MS-DOS, Menu.lst"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by linsq109 on 2009-12-27
I have a hard disk, and
 dev/sda1 is windows 7 system
dev/sda3 Extended
dev/sda5 ntfs
dev/sda6 ntfs
dev/sda7 linux-swap
dev/sda8 Ext3
dev/sda9 ntfs
dev/sds10 FAT32 MS-DOS7.1

I just install MS-DOS7.1
so Add

# This entry is for MS-DOS7.1 by sqlin
title         MS-DOS7.1
root         (hd0,9)
savedefault
makeactive
chainloader +1

but not activate still can't entry,prompt: Invalid device request when I select MS-DOS7.1


menu.lst as following:

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
default        6

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
# kopt=root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows 7 Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

# This entry is for MS-DOS7.1 by sqlin
title         MS-DOS7.1
root         (hd0,9)
savedefault
makeactive
chainloader +1

---

### Post by christophski on 2009-12-27
Are you using Ubuntu 9.10? Because if so, 9.10 uses Grub2 which does not use the menu.lst file. There are some threads in this forum about editing grub2 which you should be able to find easily with the search function.

---

### Post by linsq109 on 2009-12-27
ubuntu 9.04

---

### Post by gradinaruvasile on 2009-12-27
Is the partition marked as boot?

---

### Post by presence1960 on 2009-12-27
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by linsq109 on 2009-12-27
how to justify it ?
I try in command 
grub>root (hd0,9)
grub>chainloader    +1
grub>boot

screen promote: Starting Up
but seems no action long time

---

### Post by linsq109 on 2009-12-27
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

bash: /home/linshunqiang/Desktop/boot_info_script*.sh: No such file or directory
?

---

### Post by presence1960 on 2009-12-27
> **linsq109 said:**
> bash: /home/linshunqiang/Desktop/boot_info_script*.sh: No such file or directory
?

Did you download the file from the link in my signature. If so you have not placed the file on Desktop. Place it on desktop and then run the command.

---

### Post by linsq109 on 2009-12-27
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda8 and looks 
                       at sector 222994985 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc73fc73

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    61,446,143    61,239,296   7 HPFS/NTFS
/dev/sda3          61,447,742   312,575,759   251,128,018   f W95 Ext d (LBA)
/dev/sda5          61,447,743   144,637,919    83,190,177   7 HPFS/NTFS
/dev/sda6         144,637,983   195,078,239    50,440,257   7 HPFS/NTFS
/dev/sda7         195,093,423   198,981,089     3,887,667  82 Linux swap / Solaris
/dev/sda8         198,981,153   226,564,694    27,583,542  83 Linux
/dev/sda9         226,573,263   310,927,679    84,354,417   7 HPFS/NTFS
/dev/sda10        310,927,743   312,575,759     1,648,017   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D682C3F482C3D6E1" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="1E50D5FD50D5DC19" TYPE="ntfs" 
/dev/sda5: UUID="66608A65608A3C35" LABEL="Software" TYPE="ntfs" 
/dev/sda6: UUID="34C0E578C0E540AA" LABEL="Personal" TYPE="ntfs" 
/dev/sda7: TYPE="swap" UUID="6af86dd7-3ad5-4cdc-b066-bc990ccfdddc" 
/dev/sda8: UUID="5d1a3e12-5f37-4f4c-b1b6-dd80404968ef" TYPE="ext3" 
/dev/sda9: UUID="00C00B53C00B4E7A" LABEL="Entertainment" TYPE="ntfs" 
/dev/sda10: LABEL="MS-DOS7" UUID="4499-D61F" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/linshunqiang/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=linshunqiang)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows 7" /noexecute=optin /fastdetect 
c:\g2ldr.mbr="Ubuntu 9.10" 

=========================== sda8/boot/grub/menu.lst: ===========================

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
default        6

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
# kopt=root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5d1a3e12-5f37-4f4c-b1b6-dd80404968ef
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows 7 Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

# This entry is for MS-DOS7.1 by sqlin
title        MS-DOS7.1
rootnoverify    (hd0,9)
chainloader    +1
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
# / was on /dev/sda9 during installation
UUID=5d1a3e12-5f37-4f4c-b1b6-dd80404968ef /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=6af86dd7-3ad5-4cdc-b066-bc990ccfdddc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 114.1GB: boot/grub/menu.lst
 114.1GB: boot/grub/stage2
 114.2GB: boot/initrd.img-2.6.28-11-generic
 114.1GB: boot/initrd.img-2.6.28-15-generic
 114.1GB: boot/vmlinuz-2.6.28-11-generic
 114.1GB: boot/vmlinuz-2.6.28-15-generic
 114.1GB: initrd.img
 114.2GB: initrd.img.old
 114.1GB: vmlinuz
 114.1GB: vmlinuz.old

```

---

### Post by oldfred on 2009-12-27
I do not know if the new DOS recognizes extended partitions or not, but DOS goes back to the days when we only had 4 primary partitions. Since you still have sda4 available I would create sda4 and install your DOS there.

Windows typically without major workarounds will not work from extended partitions, so I am very suspicious that DOS does not either.

---

