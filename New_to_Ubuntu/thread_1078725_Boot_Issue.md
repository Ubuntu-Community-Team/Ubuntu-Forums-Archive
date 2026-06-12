---
title: "Boot Issue"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Benjammn on 2009-02-23
I recently installed Ubuntu 8.10 and cannot access my other OS (Windows 7) on boot (as in there is no boot menu to allow me to choose Windows 7).  I've been trying to look into GRUB, but I'm failing badly.  Any help?  Thanks.:D

---

### Post by caljohnsmith on 2009-02-23
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Benjammn on 2009-02-23
Here are the results of running the Boot Info Script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c828c82

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,302,559    29,302,497  83 Linux
/dev/sda2          29,302,560   195,366,464   166,063,905   f W95 Ext d (LBA)
/dev/sda5         134,371,503   195,365,519    60,994,017   7 HPFS/NTFS
/dev/sda6          29,302,686    29,479,274       176,589  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0d3fd8ce-cec8-4472-af4c-4cfedde98b14" TYPE="ext3" 
/dev/sda5: UUID="122E23532E232F63" TYPE="ntfs" 
/dev/sda6: UUID="3c44a824-9146-4df0-9c3d-ee2669bc4f5d" TYPE="swap" 

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
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ketelb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ketelb)


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=0d3fd8ce-cec8-4472-af4c-4cfedde98b14 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d3fd8ce-cec8-4472-af4c-4cfedde98b14

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0d3fd8ce-cec8-4472-af4c-4cfedde98b14
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0d3fd8ce-cec8-4472-af4c-4cfedde98b14 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0d3fd8ce-cec8-4472-af4c-4cfedde98b14
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0d3fd8ce-cec8-4472-af4c-4cfedde98b14 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0d3fd8ce-cec8-4472-af4c-4cfedde98b14
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d3fd8ce-cec8-4472-af4c-4cfedde98b14 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=3c44a824-9146-4df0-9c3d-ee2669bc4f5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  11.5GB: boot/grub/menu.lst
  11.6GB: boot/grub/stage2
  11.5GB: boot/initrd.img-2.6.27-7-generic
  11.6GB: boot/vmlinuz-2.6.27-7-generic
  11.5GB: initrd.img
  11.6GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-02-23
You probably deleted a primary NTFS/FAT partition when you installed Ubuntu, because Windows 7 is missing its boot files; Windows 7 is installed to a logical partition, sda5, so it would have put its boot files in some primary NTFS/FAT partition. I would recommend following [meierfra's tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") for how to boot Win 7 from a logical partition; that tutorial will also show you how to restore Win 7's boot files, and also fix the Win 7 partition boot sector. Let me know how that goes or if you run into problems.

---

