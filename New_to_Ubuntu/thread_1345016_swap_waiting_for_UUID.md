---
title: "swap: waiting for UUID"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Falc7 on 2009-12-03
My laptop when i try to start ubuntu just reads the message:
swap: waiting for UUID............ 
And then does nothing :/

---

### Post by Falc7 on 2009-12-16
Still have this problem, do i have to reinstall? I've noticed pressied escape sometimes helps it to boot

---

### Post by slakkie on 2009-12-16
No need to reinstall. Did you format move/resized your swap?
Or did you install another Debian/Ubuntu release on another drive?

Eitherway, if you boot with a live CD you can easily fix it:

```

sudo fdisk -l

```

This will show output similar to this:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6c5f6c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  83  Linux
/dev/sda2               9        1028     8193150   83  Linux
/dev/sda3            1029        2048     8193150   83  Linux
/dev/sda4            2049        9729    61697632+   5  Extended
/dev/sda5   *        2049        3068     8193118+  83  Linux
/dev/sda6            3069        3323     2048256   82  Linux swap / Solaris
/dev/sda7            3324        3361      305203+  83  Linux
/dev/sda8            3362        3552     1534176   83  Linux
/dev/sda9            3553        9729    49616721   83  Linux

```

Look for the swap partition, now mount your root, assuming /dev/sda1.

```

sudo mount /dev/sda1 /mnt
cd /mnt/etc/
sudo vi fstab # I use vi, use whatever editor you prefer.

```

Change the swap entry from 

UUID="some-uuid-string" none swap etc to 

```

/dev/sda6       none            swap    sw              0       0

```

Reboot and done.

---

### Post by bodhi.zazen on 2009-12-16
Better to list your partitions with blkid (shows uuid)

```
sudo blkid
```

You then update /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Last, no need to reboot, that is sooo Windows :twisted:

Simply :

```
sudo swpaon -a
```

You can see if swap is working via free:

```
free -m
```

---

### Post by slakkie on 2009-12-16
> **bodhi.zazen said:**
> Better to list your partitions with blkid (shows uuid)

```
sudo blkid
```

You then update /etc/fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Last, no need to reboot, that is sooo Windows :twisted:

Simply :

```
sudo swpaon -a
```

You can see if swap is working via free:

```
free -m
```

You need to reboot if you're on a livecd ;)

And btw, the blkid for swap on Debian based systems is tricky. Install Debian or Ubuntu next to Debian or Ubuntu and the UUID has changed and you can change it again. Really anoying! That's why I advise the /dev/sdaX notation.

---

### Post by bodhi.zazen on 2009-12-16
> **slakkie said:**
> You need to reboot if you're on a livecd ;)

And btw, the blkid for swap on Debian based systems is tricky. Install Debian or Ubuntu next to Debian or Ubuntu and the UUID has changed and you can change it again. Really anoying! That's why I advise the /dev/sdaX notation.

It is annoying, most distros format the swap partition when you install, which chages the UUID (not limited to Debian / Ubuntu) :(

---

### Post by kansasnoob on 2009-12-16
This sounds very much like a grub2 and/or encrypted home problem I encountered during Karmic development. I'd really like to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Also do you recall if you chose to "encrypt" /home during installation?

---

### Post by Falc7 on 2009-12-17
I've tried Slakki's suggestion first, i've restarted twice so far and it seems to be working. However i've noticed that i get an error message during start up, the only words i can catch are 'swap' and 'may experience problems'. Is there someway to get a good look at what this error is?

Here are the results of the boot script, unfortunately i don't remember if i encrypted the hard drive.
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfec7e353

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    55,825,874    55,825,812   7 HPFS/NTFS
/dev/sda2          55,825,875   234,436,544   178,610,670   5 Extended
/dev/sda5          55,825,938    62,460,719     6,634,782  82 Linux swap / Solaris
/dev/sda6          62,460,783   234,436,544   171,975,762  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A22AA8492AA81BF3" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="5ade465f-0e45-4383-8a1b-a0c46e726376" TYPE="swap" 
/dev/sda6: UUID="5911b21c-9354-4a2c-91b9-06562ac7d765" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jane)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================

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
default		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5911b21c-9354-4a2c-91b9-06562ac7d765

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		5911b21c-9354-4a2c-91b9-06562ac7d765
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		5911b21c-9354-4a2c-91b9-06562ac7d765
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		5911b21c-9354-4a2c-91b9-06562ac7d765
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		5911b21c-9354-4a2c-91b9-06562ac7d765
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, memtest86+
uuid		5911b21c-9354-4a2c-91b9-06562ac7d765
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda6       none            swap    sw              0       0  sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  31.9GB: boot/grub/menu.lst
  31.9GB: boot/grub/stage2
  31.9GB: boot/initrd.img-2.6.31-15-generic
  31.9GB: boot/initrd.img-2.6.31-16-generic
  31.9GB: boot/vmlinuz-2.6.31-15-generic
  31.9GB: boot/vmlinuz-2.6.31-16-generic
  31.9GB: initrd.img
  31.9GB: initrd.img.old
  31.9GB: vmlinuz
  31.9GB: vmlinuz.old
```

---

### Post by bodhi.zazen on 2009-12-17
This line is wrong (in fstab):

> # swap was on /dev/sda5 during installation[FONT=monospace]
[/FONT]/dev/sda6       none            swap    sw              0       0  sw              0       0

First, your swap partition is /dev/dsa5

Second the line should read

```
/dev/sda5  none  swap  sw 0 0
```

---

### Post by Falc7 on 2009-12-17
> **bodhi.zazen said:**
> This line is wrong (in fstab):



First, your swap partition is /dev/dsa5

Second the line should read

```
/dev/sda5  none  swap  sw 0 0
```

I have changed fstab using this: sudo gedit fstab #

to be this:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=5911b21c-9354-4a2c-91b9-06562ac7d765 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/dsa5 during installation
/dev/sda5       none            swap    sw              0       0  sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Is that right?

---

### Post by bodhi.zazen on 2009-12-17
Almost, you still have a bit of extra info

Change > /dev/sda5       none            swap    sw              0       0  sw              0       0to```
/dev/sda5  none  swap  sw  0  0
```(drop the repeated "sw 0 0")

---

### Post by Falc7 on 2009-12-17
Cool edited that now, it seems to boot consistently now, thanks!
I still get a delayed boot up that displays an error message that flashes away very quickly, i can make out the words 'unknown', 'controller', 'version' and 'you may experience problems', is there something i can do about this?

---

