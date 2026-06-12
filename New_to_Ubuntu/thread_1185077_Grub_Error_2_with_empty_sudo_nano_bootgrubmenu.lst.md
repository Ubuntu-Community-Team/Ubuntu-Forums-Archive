---
title: "Grub Error 2 with empty sudo nano /boot/grub/menu.lst"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by SilverDragon on 2009-06-11
So I installed Ubuntu 9.04 64 bit and everything seemed fine. I transferred all of my data onto the hard drive from my flash drive, ran the update manager, installed ubuntu restricted extras and enabled restricted drivers. (I've been running ubuntu since 7.04 so this is pretty routine) Then after maybe the 3rd time I rebooted I got Grub Error 2 and I could not boot up.

I tried using this guide:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but after running ```
find /boot/grub/stage1
```

I get ```
Error 15: File not found
```

I then thought maybe I could just go into the /boot/grub/menu.lst and go from there.

I ran ```
sudo nano /boot/grub/menu.lst

```

Well that file is empty and I don't think it should be :grin:

I think I know what the problem is though.

When I was installing Ubuntu from a flash drive I think it asked me to install Grub somewhere and I think it defaulted to my flash drive. This would explain why once I wiped it and rebooted I got the Grub Error.

I'm not sure why that happened because I've installed Ubuntu from a flash drive on several machines and they all run fine.

I think I'm wondering if there is a way to restore /boot/grub/menu.lst so I can at least access the partion on a live CD to get my data off of it.

---

### Post by furialis on 2009-06-11
If you can boot with a LiveCD, you'll most likely have access to the hard drive and you can back up your files to USB.

You should download [Super Grub Disk]("http://www.supergrubdisk.org/")

It should help you out.

---

### Post by 73ckn797 on 2009-06-11
What about running Super Grub Boot Disk and let it restore grub without having to reinstall.

Go here:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

There is an echo here:D

---

### Post by SilverDragon on 2009-06-12
Super Grub Disk sounds like a good idea.

I got ```

Grub Error 18: Selected cylinder exceeds maximum supported by BIOS
``` but I eventually fixed that by making a 200MB partion on my 16GB flash drive. (Google is great)

So I reboot and Super Grub Disk starts up fine but then when I select it I get ```
 Error 25: Disk Read Error
``` At this point I'm a little worried and I go into GParted to check that partition and I'll attach the screenshot.

I also tried copying the /boot files from another machine running Ubuntu but that didn't work (I did not really think it would anyway)

Then I tried installing Ubuntu on my 16GB flash drive to see if maybe Grub would be reinstalled. Well Grub was reinstalled but there is no option to boot into my hard drive, only the flash drive.

---

### Post by SilverDragon on 2009-06-13
I thought I would add the fdisk -l output (It seems to be helping other people) ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009180d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux

Disk /dev/sdb: 16.4 GB, 16441481728 bytes
255 heads, 63 sectors/track, 1998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000edbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1909    15334011   83  Linux
/dev/sdb2            1910        1998      714892+   5  Extended
/dev/sdb5            1910        1998      714861   82  Linux swap / Solaris

```

I also tried using testdisk based on this thread:

[http://ubuntuforums.org/showthread.php?t=1186411](http://ubuntuforums.org/showthread.php?t=1186411)

but that wasn't successful. 

At this point I'm considering upgrading to a 500GB 7200rpm drive that I have been looking at on Newegg and putting my current 250GB 5400rpm drive into an external enclosure to try to salvage the data off of it. My 1 year warranty with System76 is almost over anyway.

---

### Post by 73ckn797 on 2009-06-13
Have you booted with SGB to see whether that will fix things?

---

### Post by SilverDragon on 2009-06-13
Yeah. Super Grub Disk loaded up fine but when I selected it I got ```
Error 25: Disk Read Error
```

I didn't think there was much I could do from there.

---

### Post by 73ckn797 on 2009-06-13
Here is another option to check the hard drive. It is the smartmontools package. I discovered it and it helped me find the drive was failing. The second link is for a bootable disk that will work. You may want to read up on the utility and choose the appropriate method of using it.

Link home page: [http://smartmontools.sourceforge.net/index.html](http://smartmontools.sourceforge.net/index.html)
Link: [http://smartmontools.sourceforge.net/download.html#live-cd](http://smartmontools.sourceforge.net/download.html#live-cd)

I checked and was able to boot using LiveCD and going to terminal and entering:
```
 sudo apt-get install smartmontools
```It installed and I was able to run in terminal using ```
smartctl
```  There are other commands needed to follow the one here but you can figure that out. There is a graphical program to use it from within Ubuntu but you would first have to be able to boot into Ubuntu which would be a problem in your case.

---

### Post by SilverDragon on 2009-06-13
Thanks for the helpful information.

Using smartmontools my hard drive passed the short test. When I have time tomorrow I'll run the extended/long test.

With the second link I'm actually using Fedora 11 on a Live cd right now but my 250GB hard drive doesn't automatically mount.  I think I'll try a few other options at a different time but I ran out of blank cds for now.

I'll probably add screenshots of me using testdisk too because those may be of some use.

---

### Post by SilverDragon on 2009-06-16
I have now also tried 

sudo fsck -v -t ext4 /dev/sda

```

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device> 
```

and also: 

sudo mkdir /mnt/temp

sudo mount -t ext4 /dev/sda /mnt/temp

based on this guide: [http://ubuntuforums.org/archive/index.php/t-316488.html](http://ubuntuforums.org/archive/index.php/t-316488.html)

```
 mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` 

I've looked around for solutions to that solution but most of them just required making sure the cables were plugged in. I guess I'll try opening my laptop and doing that in the near future.

---

### Post by 73ckn797 on 2009-06-17
When you ran Super Grub Boot Disk did you use the fix grub option or did you try to boot grub only?

---

### Post by SilverDragon on 2009-06-17
Well when I booted up in to Super Grub Disk there was only one option which was Super Grub Disk. I hit enter and I got an error ```
Error 25: Disk Read Error
```

I also realized I ran the fsck on the wrong partition: ```
sudo fsck -v -t ext4 /dev/sda1

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 47883/15269888 files, 1949679/61049000 blocks
```

Am I going about the right way to mount it from my previous posts?

To my knowledge I am making a temporary mounting spot and then trying to mount it to there but getting an error message.

---

### Post by unutbu on 2009-06-17
SilverDragon, yes, I think you are going about this the right way.
What happens when you try 
```

sudo mount /dev/sda1 /mnt
```

If that does not work, please run [boot_info_script](" http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file here.

---

### Post by SilverDragon on 2009-06-17
```
sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

```

So I tried: ```
 sudo mount ext4 /dev/sda1 /mnt
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

The results: ```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009180d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.4 GB, 16441481728 bytes
255 heads, 63 sectors/track, 1998 cylinders, total 32112269 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000edbf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    30,668,084    30,668,022  83 Linux
/dev/sdb2          30,668,085    32,097,869     1,429,785   5 Extended
/dev/sdb5          30,668,148    32,097,869     1,429,722  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="909f4be8-5fd2-40c2-acc8-74faf49fe772" TYPE="ext3" 
/dev/sdb5: UUID="0f4a448a-f01f-48cd-836c-16d681dac9ed" TYPE="swap" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=909f4be8-5fd2-40c2-acc8-74faf49fe772 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=909f4be8-5fd2-40c2-acc8-74faf49fe772

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
uuid		909f4be8-5fd2-40c2-acc8-74faf49fe772
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=909f4be8-5fd2-40c2-acc8-74faf49fe772 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		909f4be8-5fd2-40c2-acc8-74faf49fe772
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=909f4be8-5fd2-40c2-acc8-74faf49fe772 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		909f4be8-5fd2-40c2-acc8-74faf49fe772
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=909f4be8-5fd2-40c2-acc8-74faf49fe772 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0f4a448a-f01f-48cd-836c-16d681dac9ed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   6.1GB: boot/grub/menu.lst
   6.1GB: boot/grub/stage2
   5.7GB: boot/initrd.img-2.6.28-11-generic
   5.7GB: boot/vmlinuz-2.6.28-11-generic
   5.7GB: initrd.img
   5.7GB: vmlinuz
```

That is a lot of information. The 250 GB sda1 partition is the one I am trying to recover data off of and the 16 GB partition is Ubuntu installed on a flash drive just so I wouldn't be running off a Live cd all the time.

---

### Post by 73ckn797 on 2009-06-17
> **SilverDragon said:**
> Well when I booted up in to Super Grub Disk there was only one option which was Super Grub Disk. I hit enter and I got an error ```
Error 25: Disk Read Error
```I also realized I ran the fsck on the wrong partition: [code]sudo fsck -v -t ext4 /dev/sda1

I cannot recall if using SGB will recognize the ext4 file system. I have ext3 and never had to use SGB when I was using the ext4 on another drive.

---

### Post by unutbu on 2009-06-18
SilverDragon, let's try the following:

Boot from the 16GB flash drive or a Jaunty LiveCD. 

Open a terminal and type
```
sudo mount -t ext4 /dev/sda1 /mnt    # This should mount the sda1 partition at /mnt
```

If this command is successful, then you should be able to pull your data off of /mnt.

If you would like to install the boot files (and GRUB) on the sda hard drive so that 
sda can boot without the 16GB flash drive, let me know and I can guide you through that process. But the first step in any case is to mount sda1.

Let us know how it goes.

---

### Post by SilverDragon on 2009-06-18
```
sudo mount -t ext4 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I guess if I can't mount it I can't install the boot files and Grub onto it :( I liked that idea though.

I also tried taking out the hard drive and putting it back in because that seemed to fix the problem for some people with the errors I've been receiving.

---

### Post by unutbu on 2009-06-18
SilverDragon, what happens when you run
```

sudo mount -t ext3 /dev/sda1 /mnt
```

and if that does not work, try:
```

sudo mount -t ext2 /dev/sda1 /mnt
```

If neither work, what is the output of
```

sudo tune2fs -l /dev/sda1
```

---

### Post by SilverDragon on 2009-06-18
```
sudo mount -t ext3 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
sudo mount -t ext2 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
sudo tune2fs -l /dev/sda1
tune2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          6d37e491-7342-47c7-8497-dcaf13086615
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              15269888
Block count:              61049000
Reserved block count:     3052450
Free blocks:              59099321
Free inodes:              15222005
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1009
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Jun 11 18:05:51 2009
Last mount time:          Thu Jun 11 18:43:46 2009
Last write time:          Wed Jun 17 10:49:00 2009
Mount count:              0
Maximum mount count:      36
Last checked:             Wed Jun 17 10:49:00 2009
Check interval:           15552000 (6 months)
Next check after:         Mon Dec 14 09:49:00 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Default directory hash:   half_md4
Directory Hash Seed:      f2b372ae-927d-4469-9687-39fd74bd1a9c
Journal backup:           inode blocks

```

What exactly does the last command do?

---

### Post by unutbu on 2009-06-18
SilverDragon, I'm a bit worried I might not know how to solve your problem.
However, would you please try the following:

```
sudo mount -t ext4 /dev/sda1 /mnt
dmesg | tail
```

Post the output of "dmesg | tail".

Also, did you install Jaunty on sda1 from a LiveCD? Was it the same LiveCD that you used to install Jaunty on the 16GB flash drive?

Finally, do you have a backup of the data that is on sda1?

I think there must be a way to mount sda1 since fsck said sda1 is clean and tune2fs seems to recognize sda1 as having an ext4 filesystem. But at the moment I can't guess what's preventing sda1 from successfully mounting.

PS. (The "tune2fs -l /dev/sda1" command was simply to see if tune2fs could recognize sda1 as have an ext* filesystem. It can also report if the filesystem has certain problems, but the output raised no red flags as far as I could tell.)

---

### Post by SilverDragon on 2009-06-18
unutbu, thanks for all of your help so far.

```
dmesg | tail
[  837.409845] wlan0: deauthenticated
[  837.416954] iwlagn: index 0 not used in uCode key table.
[  838.408391] wlan0: direct probe to AP 00:0f:3d:5d:1a:b2 try 1
[  838.411811] wlan0 direct probe responded
[  838.411820] wlan0: authenticate with AP 00:0f:3d:5d:1a:b2
[  838.415990] wlan0: authenticated
[  838.415998] wlan0: associate with AP 00:0f:3d:5d:1a:b2
[  838.418595] wlan0: RX ReassocResp from 00:0f:3d:5d:1a:b2 (capab=0x431 status=0 aid=1)
[  838.418602] wlan0: associated
[  907.585920] ext4: No journal on filesystem on sda1

```

I installed Jaunty on sda1 through my 16 GB flash drive by using the USB Startup Disk Creator on another Ubuntu 9.04 machine because I wanted to install a 64 bit version. The .iso I obtained through a torrent and I md5sumed(if that's a word) to make sure it was 100% correct. I also checked the "disc" for errors when installing from the USB. There was a strange part during the installation about installing the bootloader but I didn't think much of it because I had installed Ubuntu through a USB device before so I thought it was no big deal.

I might have a back up on an old IDE hard drive but it's not recent at all. I was going to copy my data back on after reformatting the flash drive but I guess that one reboot was costly.

If I had a recent back up I would have reformatted my hard drive immediately, haha :)

I can't figure out why I can't mount it either because it seems like it should mount fine.

I am going to order an external enclosure for my 2.5 inch hard drive and try to mount it from there.

If that doesn't work and the problem is not fixed by then I think I'll order a 3.5 external enclosure and try to salvage my data off of one of my old hard drives.

Once again thanks for your help so far.

---

### Post by unutbu on 2009-06-19
Well, I'd be kind of surprised if this works, but it would not hurt to try:

Boot from the flash drive.
Edit /boot/grub/menu.lst. Add this to the end of the file:
```

title		Test1
uuid		6d37e491-7342-47c7-8497-dcaf13086615
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6d37e491-7342-47c7-8497-dcaf13086615 ro
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Test2
uuid		909f4be8-5fd2-40c2-acc8-74faf49fe772
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6d37e491-7342-47c7-8497-dcaf13086615 ro
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```
Then reboot. At the GRUB menu, try to boot from "Test1" and if that does not work, try "Test2".

Explanation: The output of tune2fs says the UUID of sda1 is 6d37e491-7342-47c7-8497-dcaf13086615. So on the "kernel" line above, I've changed the UUID to point at sda1 using this UUID.
If Test1 or Test2 works, this will mount sda1 at /.

The line 
```
uuid		6d37e491-7342-47c7-8497-dcaf13086615
```
tells GRUB to look on sda1 for /boot/vmlinuz-2.6.28-11-generic and /boot/initrd.img-2.6.28-11-generic. 
The line ```

uuid		909f4be8-5fd2-40c2-acc8-74faf49fe772
```
tells GRUB to look for those files in sdb1.

---

### Post by SilverDragon on 2009-06-19
Booting from Test1 ```
Boot from (hd0,0) ext4 6d37e491-7342-47c7-8497-dcaf13086615

Error 15: File not found

Press any key to continue...
```

Booting from Test2 ```
 Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
``` and then dropped into Busybox.

---

### Post by unutbu on 2009-06-19
The errors while booting Test1 and Test2 both show GRUB is having problems mounting sda1. 

When booted from the flash drive, what output do you get from these commands?
```

sudo mount -t ext4dev /dev/sda1 /mnt
apt-cache policy grub

```

I keep returning to the facts that [list][*]fsck says sda1 is fine, and [*]tune2fs says sda1 is fine, and somehow, [*]GRUB on the 16GB flash drive at one point had no problem booting sda1.
[/list]All this makes me believe there is nothing wrong with sda1, only with the tools we are using to mount and boot sda1. 

ext4 is a relatively new filesystem format. I know very little about ext4. That may be the problem here. 

Maybe for some strange reason, the Jaunty that is installed on the 16GB flash drive currently can not mount ext4?

If you have a second (empty) flash drive, it might be illuminating to do the following experiment:

With the second flash drive attached to the machine run System>Admin>Partition Editor (GParted)

and create an ext4 partition (e.g. sdc1) on it.

Quit GParted. In the terminal type
```

mount
```

to see if sdc1 is mounted.
Type

```
sudo umount /dev/sdc1                # to unmount it
sudo mount -t ext4 /dev/sdc1 /mnt    # to see if you can mount an ext4 partition
sudo tune2fs -l /dev/sdc1
```

Does Jaunty on the 16GB flash drive successfully mount sdc1, or do you get the same error messages as you get when attempting to mount sda1?

---

### Post by SilverDragon on 2009-06-25
```
sudo mount -t ext4dev /dev/sda1 /mnt
mount: unknown filesystem type 'ext4dev'

```

```
apt-cache policy grub
grub:
  Installed: 0.97-29ubuntu53
  Candidate: 0.97-29ubuntu53
  Version table:
 *** 0.97-29ubuntu53 0
        500 http://ubuntu.media.mit.edu jaunty/main Packages
        100 /var/lib/dpkg/status

```

> GRUB on the 16GB flash drive at one point had no problem booting sda1.

But now I have Ubuntu on the 16GB  flash drive not just Grub. Wouldn't that affect it?

I received my 2.5 hard drive external enclosure in the mail the other day and my hard drive in it but when I opened it in GParted it was pretty much the same except it was under /dev/sdb I believe.

I also tried plugging the drive in to a Windows machine and installing Ext2fsd to access the drive. It looked like it was going to work until I clicked on the drive and it told me it was unformatted :(

I haven't got around to making a partition on a secondary flash drive because I need to get it my only other one back from my sister which should be soon. If not, I'll just buy another one when I buy a 3.5 hard drive enclosure to see if my really old back ups would be adequate.

---

### Post by unutbu on 2009-06-25
SilverDragon, while booted from a Jaunty LiveCD,
how about try
```

sudo umount /dev/sda1
sudo e2fsck -C0 -pfv /dev/sda1
```


This will run fsck again on sda1. The "-f" flag tells fsck to check the filesystem even if it seems clean. 
```

-C0 draw a completion bar
-p  auto repair ('preen') the filesystem
-f  force checking even if the filesystem seems clean
-v  verbose mode
```

---

### Post by SilverDragon on 2009-06-26
```
sudo e2fsck -C0 -pfv /dev/sda1
/dev/sda1:                                                                      '..' in /lost+found/#41886/changelog.gz (354) is /lost+found (11), should be /lost+found/#41886 (41886).


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```

So I ran it without the -p option.

```

sudo e2fsck -C0 -fv /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
'..' in /lost+found/#41886/changelog.gz (354) is /lost+found (11), should be /lost+found/#41886 (41886).
Fix<y>? yes

Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
                                                                               
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

   47883 inodes used (0.31%)
      49 non-contiguous files (0.1%)
      32 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 658/663/657
         Extent depth histogram: 44520/70
 1949679 blocks used (3.19%)
       0 bad blocks
       7 large files

   40139 regular files
    4476 directories
     510 character device files
     188 block device files
     416 fifos
   67168 links
    2097 symbolic links (2097 fast symbolic links)
      48 sockets
--------
  115042 files

```

Then I tried mounting it again but I got the same error message as before.

---

### Post by unutbu on 2009-06-26
According to 
[http://www.softpedia.com/progChangelog/TestDisk-Changelog-20124.html](http://www.softpedia.com/progChangelog/TestDisk-Changelog-20124.html), testdisk's support for ext4 was introduced in version 6.11. Jaunty's testdisk is version 6.10. 
If you haven't tried testdisk version 6.11 ([http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2))
perhaps give it another try. After doing the "Deeper Search", try pressing "p" to see if testdisk can read the files on sda1.


```

wget http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2
tar xvjf testdisk*.bz2
sudo testdisk-6.11.3/linux/testdisk_static
```

Choose "No Log", "Proceed", "Intel", "Analyse", "Quick Search", "Deeper Search".
Use the up/down arrows to select partitions, and press "p" to see if testdisk can read the filesystem on each partition (particularly sda1).

Please report back with a screenshot of what the "Deeper Search" returns, and which partitions have readable filesystems inside.

---

### Post by SilverDragon on 2009-06-27
In the screenshot -2 I tried to copy my files over on my sister's computer because there's not enough room on my flash drive. It copied over (25 GB) of data into a lost + found folder but it looked like all gibberish to me. 25 GB should be about the amount of space taken up on that partition with music,pictures, documents, and system files.

Also, last time I tried this it just told me: ```
No file found, filesystem seems damaged. 
``` I guess fscking the partition made some progress.

---

### Post by unutbu on 2009-06-27
In the last screenshot, the result of the deeper search, notice the "D" at the start of each line. The "D" stands for Deleted. We want that "D" to be a "P" for Primary partition.

So in that screen, use the up/down arrow to highlight the second line
```

D Linux            0   1   1 30400 254 61  488392000
```

Then use the left/right arrows to change the "D" into a "P". 
Press Enter to continue, and select the option to write the new partition table to disk.

Then quit testdisk, and in the terminal type
```

sudo partprobe    # inform/update the OS of partition table changes
sudo mount -t ext4 /dev/sda1 /mnt
```

Can you mount the partition the normal way now?

If so, we should be able to get you boot from that drive again...

---

### Post by SilverDragon on 2009-06-28
I tried setting the 2nd line and the other line with Linux as P and *(Primary bootable) all one at a time. Doing a deep search that many times took a while :)

```
sudo mount -t ext4 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

That was the error message every time.

I also tried booting from Test1 as set up before with no success.

Wrong fs makes sense, bad superblock makes sense, but what would a bad option be?

---

