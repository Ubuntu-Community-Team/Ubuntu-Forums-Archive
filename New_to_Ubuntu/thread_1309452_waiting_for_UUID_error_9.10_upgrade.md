---
title: "waiting for UUID error 9.10 upgrade"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by maroonforest on 2009-11-01
Hello I a have another 9.10 upgrade problem.
I upgraded from 9.04 and on boot up I see the message

swap: waiting for UUID=0c399ifb-5320-4afc-8eb2-6cb25504
Press ESC to enter a recovery shell
 
3 progress bars and a white logo 


I've looked through the other messages and couldn't see on here with this, sorry if it's a duplicate.

thanks

---

### Post by kansasnoob on 2009-11-01
Does it then just sit there forever and never boots?

If so follow the steps in the following guide and post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by ratsbane on 2009-11-02
I had the same problem in upgrading an Acer Aspire with an N270 Atom CPU and 8gb SSD from Ubuntu 9.04 to 9.10 Karmic.  I'm not sure if the upgrade spontaneously froze or tripping over the cord and knocking the netbook to the floor had anything to do with it.  There wasn't any lasting damage but I might have knocked the removable SSD loose while it was busy.  It might have been frozen for a while before I tripped on the cord.

Here's the error message I saw when entering the recovery shell:

One or more of the mounts listed in /etc/fstab cannot yet be mounted

After trying several things here's what finally worked for me:

Press Esc to enter the recovery shell
Remount the / filesystem as read-write: mount -o remount,rw /
Continue the upgrade: dpkg --configure -a

After that it continued with the dist-upgrade, restarted, and everything is normal now.

---

### Post by maroonforest on 2009-11-03
Hello
these are the results 

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadd63633

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,388,619   153,388,557  83 Linux
/dev/sda2         153,388,620   156,296,384     2,907,765   5 Extended
/dev/sda5         153,388,683   156,296,384     2,907,702  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="277f20d8-0421-4dc5-b5f7-edf43a08b6d9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="0c3991fb-5320-4afc-8eb2-6cb2551a8504" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="Cruzer" UUID="E805-8D0A" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=277f20d8-0421-4dc5-b5f7-edf43a08b6d9

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
uuid		277f20d8-0421-4dc5-b5f7-edf43a08b6d9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=277f20d8-0421-4dc5-b5f7-edf43a08b6d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0c3991fb-5320-4afc-8eb2-6cb2551a8504 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  38.6GB: boot/grub/menu.lst
  38.6GB: boot/grub/stage2
  37.3GB: boot/initrd.img-2.6.27-7-generic
  37.3GB: boot/initrd.img-2.6.28-11-generic
  37.3GB: boot/initrd.img-2.6.28-13-generic
  37.4GB: boot/initrd.img-2.6.28-14-generic
  61.8GB: boot/initrd.img-2.6.28-15-generic
  38.8GB: boot/initrd.img-2.6.28-16-generic
  37.4GB: boot/vmlinuz-2.6.27-7-generic
  37.4GB: boot/vmlinuz-2.6.28-11-generic
  37.4GB: boot/vmlinuz-2.6.28-13-generic
  37.4GB: boot/vmlinuz-2.6.28-14-generic
  61.7GB: boot/vmlinuz-2.6.28-15-generic
  38.1GB: boot/vmlinuz-2.6.28-16-generic
  61.7GB: boot/vmlinuz-2.6.31-14-generic
  38.8GB: initrd.img
  61.8GB: initrd.img.old
  38.1GB: vmlinuz
  61.7GB: vmlinuz.old


are these of any help?
thank you very much

thanks ratsbane but could you let me know what part of your solution I  type  into a terminal?  still finding my way these things cheers

---

### Post by 1oki on 2009-11-03
I have the exact same issue... I have tried upgrading about 3 times now and I keep getting the Swap: Waiting for UUID=1fc54d57-f823-43c3-9c33-848624f2142f

It will just hang out there forever. When I try to reboot into recovery mode, nothing happens. I am forced to reinstall 9.04 again, where as nothing works.

I have a Dell Dimension 4800 with a P4 3.0ghz, and 2 gigs of ram. any clue here, or should I just sit on it and wait for the bug to work it's self out?

---

### Post by 1oki on 2009-11-03
> **ratsbane said:**
> I had the same problem in upgrading an Acer Aspire with an N270 Atom CPU and 8gb SSD from Ubuntu 9.04 to 9.10 Karmic.  I'm not sure if the upgrade spontaneously froze or tripping over the cord and knocking the netbook to the floor had anything to do with it.  There wasn't any lasting damage but I might have knocked the removable SSD loose while it was busy.  It might have been frozen for a while before I tripped on the cord.

Here's the error message I saw when entering the recovery shell:

One or more of the mounts listed in /etc/fstab cannot yet be mounted

After trying several things here's what finally worked for me:

Press Esc to enter the recovery shell
Remount the / filesystem as read-write: mount -o remount,rw /
Continue the upgrade: dpkg --configure -a

After that it continued with the dist-upgrade, restarted, and everything is normal now.

I'm giving this a try, as we speak... hopefully it will work for me :)

---

### Post by 1oki on 2009-11-03
well that worked... I reconfigured with dpkg and then continued with the upgrade... though when that was done I still had to reboot into recovery console and fix broken packages. I still get an error when booting into the system. I wasn't quick enough to write it down though... maybe when i next reboot i will. 

thanks.

---

### Post by sdaau on 2009-11-04
> **ratsbane said:**
> 
Remount the / filesystem as read-write: mount -o remount,rw /


Thanks for that, it helped a lot - for me, actually this was a two step problem after upgrade, which I posted (under a wrong topic, unfortunately) here:

[Bug #472964 in xulrunner-1.9.1 (Ubuntu): “package xulrunner-1.9.1 1.9.1.4+nobinonly-0ubuntu0.9.10.1 failed to install/upgrade: Unterprozess installiertes post-installation-Skript gab den Fehlerwert 127 zurück”](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.1/+bug/472964)

At first drop to shell, I had to manually ln -s the root partition to the respective UUID, and at second drop to shell, had to do the mount -o remount,rw / ..

This unfortunately needs to be done at each boot - only thing I could figure out was to edit /boot/grub/menu.lst - and comment the UUID entries or replace them with say root=/dev/sdaX (instead of root=UUID=...) in the respective default grub entry...

Cannot tell if this has anything to do with the fact that my root partition is formatted as ext2 (and for 9.10 I hear the recommended is ext4)... Does anyone know if keeping the root partition as ext2 could somehow be harmful/problematic under 9.10/Karmic ?

Thanks,
Cheers..

---

### Post by sdaau on 2009-11-25
Ok, I think I understand what the problem is now - up to 9.04 Jaunty, vol_id is used to obtain disk signatures, and it is more tolerant of "double signatures"; in 9.10 blk_id is used, which refuses to mount if disk signatures conflict. 

So how do you find if you have "double signatures"? One way is using blkid:
```

sudo BLKID_DEBUG=0xffff blkid -p /dev/sdaX

```as given in [Bug #426027 in util-linux (Ubuntu): &#8220;/dev/disk/by-uuid doesn't exist in karmic kernels&#8221;]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/426027") - or, a slightly more straightforward output can be obtained by running the fix_superblock.py script, found in [Bug #428435 in cryptsetup (Ubuntu): &#8220;luks encrypted partition not detected&#8221;]("https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/428435") (or [Bug #428435 in util-linux (Ubuntu): &#8220;luks encrypted partition not detected&#8221;](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/428435))

Unfortunately, the double signature I have is "vfat" and "ext2", and fix_superblock.py cannot clean vfat signatures...

Cheers!

---

### Post by jeschvi on 2009-11-30
About the error:[INDENT]One or more of the mounts listed in /etc/fstab cannot yet be mounted
swap: waiting for UUID
[/INDENT]This worked for me:
1. Run blkid. This lists the UUID's for your partitions. Find the one with TYPE="swap".
2. Edit /etc/fstab: change the UUID for swap to the one listed in the output from blkid.

The upgrade to version 9.10 seems to insert the wrong UUID in /etc/fstab.

After some (one?) boots this failed. Insted changed the UUID=.... thing to the original value (which happened to be /dev/sda6). This seem to solve it for good.

---

### Post by ububaba on 2009-12-01
> **jeschvi said:**
> About the error:[INDENT]One or more of the mounts listed in /etc/fstab cannot yet be mounted
swap: waiting for UUID
[/INDENT]This worked for me:
1. Run blkid. This lists the UUID's for your partitions. Find the one with TYPE="swap".
2. Edit /etc/fstab: change the UUID for swap to the one listed in the output from blkid.

The upgrade to version 9.10 seems to insert the wrong UUID in /etc/fstab.

I had the same problem. Following the above process was a lucky break.  The strangest
thing was that the id provided for "swap" in /etc/fstab did not even exist in blkid!

---

### Post by nagpai on 2009-12-04
> **ratsbane said:**
> I had the same problem in upgrading an Acer Aspire with an N270 Atom CPU and 8gb SSD from Ubuntu 9.04 to 9.10 Karmic.  I'm not sure if the upgrade spontaneously froze or tripping over the cord and knocking the netbook to the floor had anything to do with it.  There wasn't any lasting damage but I might have knocked the removable SSD loose while it was busy.  It might have been frozen for a while before I tripped on the cord.

Here's the error message I saw when entering the recovery shell:

One or more of the mounts listed in /etc/fstab cannot yet be mounted

After trying several things here's what finally worked for me:

Press Esc to enter the recovery shell
Remount the / filesystem as read-write: mount -o remount,rw /
Continue the upgrade: dpkg --configure -a

After that it continued with the dist-upgrade, restarted, and everything is normal now.

This worked for me.. I think it was an error caused by a broken package during download of the Karmic Koala (9.10). and the steps mentioned by our friend worked... Here is a Popcorn to you..:popcorn:

---

### Post by NewbuntuUser777 on 2009-12-14
Well, here's the output of blkid for my netbook. I am having the same 
problem as op after installing the latest round of updates.  FWIW, I've 
been getting the unable to mount message since I upgraded to 9.10 netbook 
remix -- the "swap: waiting for uuid" problem seems related to recent 
batch of updates though).

/dev/sda1: UUID="A2F48F73F48F490D" TYPE="ntfs" 
/dev/sda3: LABEL="PE" UUID="CCED-990E" TYPE="vfat" 
/dev/sda5: UUID="d166ffe3-fc68-4e42-8a6a-87a2cd1420fe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" 


So, my swap doesn't have a uuid.  (I dual boot xp.)

What do I do now?

---

### Post by NewbuntuUser777 on 2009-12-14
I posted without taking time to think


I changed the swap uuid to match the uuid of the main ubuntu partition (sda5) since it's on the same drive

problem solved

---

### Post by artcancro on 2009-12-23
I've had two different machines break in this way after an upgrade to Karmic (ubu 9.10).  I didn't bother to determine whether the upgrade is inserting the wrong UUID in the grub configuration, or if the boot disk's UUID is spontaneously changing, but whatever it is, it's WRONG.

Fortunately, it's a fairly straightforward fix.  Interrupt the grub boot process, edit the boot command, change "root=UUID=xxxxxx" to "root=/dev/sda1" (or whatever) and let it boot.  Then after booting, make the same edit in /boot/grub/menu.lst wherever it appears.   You could also just put in the correct UUID for the volume if you wanted to.

Also, the documentation for grub is incorrect.  It says that "grub initializes the kernel Linux, which in turn initializes the operating system GNU."  My operating system is called Linux, not GNU.

---

### Post by sdaau on 2009-12-27
> **artcancro said:**
> 
Also, the documentation for grub is incorrect.  It says that "grub initializes the kernel Linux, which in turn initializes the operating system GNU."  My operating system is called Linux, not GNU.

Are you sure? [Linux and GNU - GNU Project - Free Software Foundation (FSF)]("http://www.gnu.org/gnu/linux-and-gnu.html")

Cheers!

---

### Post by skywalk on 2010-05-10
jeschvi, thanks for your comment. This solved my problem of swap waiting.

---

