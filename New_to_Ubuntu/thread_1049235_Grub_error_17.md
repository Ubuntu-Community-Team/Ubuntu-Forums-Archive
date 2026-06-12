---
title: "Grub error 17"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by mustava on 2009-01-24
Hi Guys,

Tried installing ubuntu 9.04, 8.04 and xubuntu 8.10 on a fujitsu/siemens laptop but each time the installation finishes ok (without any apparent problems), following ejection of the disk and a re-boot, I get the same "grub error 17".

The disks above have loaded ok on other machines, and I have also tried the "check disk" prior to installing, and that passed ok as well.

I have tried the "sudo fsck  xxxxxxx" command in terminal where the xxx's are the HDD ie. /dev/sda1 without any success, even tho' the fsck said it had fixed it.

Any help would be appreciated.

Mustava....
PS I did a search prior to opening this thread, but couldn't find anything appropriate.

---

### Post by caljohnsmith on 2009-01-24
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by mustava on 2009-01-24
Cheers matey, here it is


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

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 4327 MB, 4327464960 bytes
255 heads, 63 sectors/track, 526 cylinders, total 8452080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cc00

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63    7,968,239    7,968,177  83 Linux
/dev/sda2          7,968,240    8,450,189      481,950   5 Extended
/dev/sda5          7,968,303    8,450,189      481,887  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a7e170ab-2627-4e48-b753-694efdf84a6f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="c08103d9-b8b4-458d-a1a4-9c2ab9d4f32f" TYPE="swap" 
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
# kopt=root=UUID=a7e170ab-2627-4e48-b753-694efdf84a6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7e170ab-2627-4e48-b753-694efdf84a6f

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
uuid		a7e170ab-2627-4e48-b753-694efdf84a6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a7e170ab-2627-4e48-b753-694efdf84a6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a7e170ab-2627-4e48-b753-694efdf84a6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a7e170ab-2627-4e48-b753-694efdf84a6f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a7e170ab-2627-4e48-b753-694efdf84a6f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a7e170ab-2627-4e48-b753-694efdf84a6f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c08103d9-b8b4-458d-a1a4-9c2ab9d4f32f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


   1.2GB: boot/grub/menu.lst
   1.3GB: boot/grub/stage2
   1.3GB: boot/initrd.img-2.6.27-7-generic
   1.3GB: boot/vmlinuz-2.6.27-7-generic
   1.3GB: initrd.img
   1.3GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-24
According to the script, it looks like Grub is installed correctly, so getting an error 17 in those circumstances can sometimes be a result of how the drive is set up in BIOS. Is it a USB flash drive? What BIOS settings do you have related to that drive? How about checking your BIOS and let me know what drive-related settings you have like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Also, is there maybe a BIOS upgrade available for your computer? Sometimes that's all it takes. Another option is to download and use the [Super Grub Disk]("http://www.supergrubdisk.org") to reinstall Grub to your drive, because sometimes using a slightly different version of Grub makes a difference. If you try that, let me know how it goes.

---

### Post by mustava on 2009-01-24
Ta VM for the reply.

I did check that the BIOS was set to Auto on the HDD.

I only have one HDD, its a small one but its just to make sure all works ok prior to the full change-over....

However I'll do as you suggest shortly and post back.

Thanks for your help it is appreciated..

Must.

---

### Post by mustava on 2009-01-25
caljohnsmith,
Sorry for not getting back before now, but as requested I did check the bios settins and all hdd were on "auto", and the rest looked reasonable.

So I downloaded Hirens V9.7 boot disk, and not sure what sorted it, but I went in to something to do with the boot sequence, selected "not quite sure", but it's working fine now.

If I work out what I actually did, I will post back.

Thanks for all your help

Mustava....

---

### Post by caljohnsmith on 2009-01-25
That sounds intriguing, I would be interested to know exactly what you did from Hiren's boot CD to get it working. Glad to hear that whatever it was, it worked.

---

