---
title: "grub_ flashing on boot"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by tplant98 on 2009-02-08
I just installed 8.10 in its own partitions. After the successful install, on the first reboot, the bios screen flashes and then a grub_ comes up on the screen and I'm stuck. The plan is to dual boot with XP and Ubuntu.

I have tried to "rebuild grub" as some posts have recommended, but when I reboot the same message comes up.

I would love any suggestions or advice as I've spend a few hours on this and I'm stuck.

I've attached some supporting information.  


Disk /dev/sda: 119.9 GB, 119924582912 bytes
255 heads, 63 sectors/track, 14580 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7e3f7e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5879    47223036    7  HPFS/NTFS
/dev/sda2            5880       14580    69890782+   5  Extended
/dev/sda5            5880       14220    66999051   83  Linux
/dev/sda6           14221       14580     2891668+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


A copy of my menu.lst on the Linux drive is saved as an attachment.

Thank you so much for any assistance, as I'm dead in the water right now.

Thanks for your time,
Troy

---

### Post by caljohnsmith on 2009-02-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by tplant98 on 2009-02-08
Hi!

Thank you for the quick reply. I did what you suggested and the results are below.  Also, one thing I figured out, is if I boot up with the Ubuntu CD, and then select the "boot from the first hard drive" option, it appears to load the grub handler, and allows me to pick which OS I want to load, and loads correctly.  But, I still have the issue if I boot the computer directly, without the cd, I get the grub_ (flashing cursor)

Here is the results of the file.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 133194358 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 119.9 GB, 119924582912 bytes
255 heads, 63 sectors/track, 14580 cylinders, total 234227701 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7e3f7e3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    94,446,134    94,446,072   7 HPFS/NTFS
/dev/sda2          94,446,135   234,227,699   139,781,565   5 Extended
/dev/sda5          94,446,198   228,444,299   133,998,102  83 Linux
/dev/sda6         228,444,363   234,227,699     5,783,337  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DA6043A960438AE9" TYPE="ntfs" 
/dev/sda5: UUID="04a6dde3-a6f9-4efd-a2be-18fc3804007f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="aa6f22a7-3904-4c7b-8ef2-03997d4949a0" TYPE="swap" 
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

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


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
# kopt=root=UUID=04a6dde3-a6f9-4efd-a2be-18fc3804007f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=04a6dde3-a6f9-4efd-a2be-18fc3804007f

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
uuid		04a6dde3-a6f9-4efd-a2be-18fc3804007f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=04a6dde3-a6f9-4efd-a2be-18fc3804007f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		04a6dde3-a6f9-4efd-a2be-18fc3804007f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=04a6dde3-a6f9-4efd-a2be-18fc3804007f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		04a6dde3-a6f9-4efd-a2be-18fc3804007f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=04a6dde3-a6f9-4efd-a2be-18fc3804007f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		04a6dde3-a6f9-4efd-a2be-18fc3804007f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=04a6dde3-a6f9-4efd-a2be-18fc3804007f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		04a6dde3-a6f9-4efd-a2be-18fc3804007f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=04a6dde3-a6f9-4efd-a2be-18fc3804007f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aa6f22a7-3904-4c7b-8ef2-03997d4949a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.1GB: boot/grub/menu.lst
  68.1GB: boot/grub/stage2
  68.1GB: boot/initrd.img-2.6.27-11-generic
  68.1GB: boot/initrd.img-2.6.27-7-generic
  68.1GB: boot/vmlinuz-2.6.27-11-generic
  68.1GB: boot/vmlinuz-2.6.27-7-generic
  68.1GB: initrd.img
  68.1GB: initrd.img.old
  68.1GB: vmlinuz
  68.1GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-02-08
Grub problems like yours are really difficult to fix because you have Grub correctly installed to your HDD, and are even able to boot the HDD with the help of the Live CD, yet booting the HDD directly results in Grub choking. Is the HDD IDE or SATA? I would guess it's probably IDE. Sometimes Grub problems like you are experiencing are a result of how you have your HDD set up in BIOS, so how about going into your BIOS and let me know what HDD-related settings you have available. Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Let me know how that goes.

---

### Post by tplant98 on 2009-02-08
I looked in the bios and I didn't find much. Under boot, it listed a hard drive option, and when I expanded that, it showed the name of the drive, but no settings I could change.

It is an IDE drive..

When I do boot the hard drive from the Ubuntu cd, both the Ubuntu and Windows XP, seem to launch and run correctly.

Thanks,
Troy

---

### Post by caljohnsmith on 2009-02-08
Well, you could try downloading and using the [Super Grub Disk]("http://www.supergrubdisk.org") to reinstall Grub to your MBR, because using a slightly different version of Grub seems to make a difference sometimes. Let me know how that goes.

---

### Post by tplant98 on 2009-02-09
No luck with the super grub either. I actually went ahead and deleted my full hard drive and install only ubuntu, but still no luck! I get the same grub_ flashing.. For what ever reason this Toshiba laptop doesn't like grub!

I decided to reformat and install XP again, since I couldn't get it to work, and I'll just install Ubuntu within XP again.:(

Thanks for your help.
Troy

---

