---
title: "Help Please! Problems with Ubuntu and WIndows Vista"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by calderp on 2009-01-23
Sorry I posted this first in x64 but I think it probably belongs here? 

Help Please! Problems with Ubuntu and WIndows Vista
Hi
So I was fed up enough with windows vista to try the switch to linux but am having a couple problems. I am running 8.10 on a new Toshiba Satellite laptop. In order to install Ubuntu I used the Linux partition manger (I forget the name, but think it started with G? From what I found online it is the most commonly used), then installed Ubuntu onto my new parition. Ubuntu is running fine but my first problem is that I am not able to boot into Vista. I had thought that in doing this I would be able to dual-boot, but I don't have an option for Vista during Gnome boot-up. Any idea why?

The second, more important problem, is that Ubuntu is not recognizing (or I cannot find) most of the hard drive partition that has Vista on it so I'm not able to access any of my music or files.
I read some threads related to this but couldn't make much sense of them. I did get the impression that in order to help it would be useful to see this:
calderp@paulpc:~$ sudo fdisk -l
[sudo] password for calderp:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f9a64c1

Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
/dev/sda2 192 336 1160192+ 5 Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3 * 337 29096 231014700 82 Linux swap / Solaris
/dev/sda4 29097 30401 10482412+ 83 Linux
/dev/sda5 192 336 1160192 7 HPFS/NTFS
calderp@paulpc:~$
calderp@paulpc:~$

I'm guessing that 'Partition 2 does not end on cylinder boundary.' would be my problem?

If anyone can help with either of these problems (but primarily the hard drive issue) it would be wonderful. I have essentially no knowledge of linux so you'll have to explain things pretty simply I'm afraid but I'm generally good with computers so it shouldn't be too hard.
I'm sure this question has been raised before so I apologize for that but I couldn't find a thread that made enough sense for me to get it to work...
Thanks Again

---

### Post by caljohnsmith on 2009-01-23
It looks like your Vista partition might be on sda5, but that's a logical partition, not a primary partition; normally Windows needs to be on a primary partition in order to boot, although it is possible to boot Windows from a logical partition with Grub. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
sudo mount /dev/sda5 /mnt && ls -l /mnt
```
And we can work from there if you want.

---

### Post by The Cog on 2009-01-23
I googled for partition type 27 and came up with this:
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)
It seems that sda1 is a hidden recovery partition of some sort.
There is an NTFS partition on sda5 though. Unless you created that, it is probably your Vista partition. I don't know why you can't boot it. 

as for mounting it, pull down the places menu and see if there's an item in there that opens the vista partition for you. If not, try these commands to see if you can mount the vista partition - they make a directory (folder) to mount it tom then mount the partition contents into that directory:
> sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
If the mount command doesn't work then post the error message here.

P.S.
Blimey, did it really take me 18 minutes to write that answer? caljohnsmith's answer wasn't there when I started. That's what comes of watching the telly at the same time.

---

### Post by calderp on 2009-01-23
Thanks for the quick responses. First off, I should explain how the drive is partitioned a little better. Sorry I didn't do this earlier.
At start windows vista drive manager showed 2 paritions, one of like 250gig which was the windows partition, and one of a gig or two that was some other partition (some sort of windows emergency/recovery partition?). I tried to shrink the Vista partition but couldn't, so I used PerfectDisk and then repartitioned using Linux. In doing so, I took 10gigs off of the main vista parition and made it into a seperate partition, which is what I have installed Ubuntu on. Then, I went into Vista again and when I looked at the HDD manger again, it showed my original 2 partitions (Vista + the other one I think is an emergency/repair partition) as well as my new 10gig partition (Ubuntu not yet installed). It also showed 1gig of un-partitioned space that had randomly appeared, so just for kicks I used the Vista partition manager to make that into a new partition.
The point of this is, I think that maybe that sda5 is just that 1gig partition? When I got to Computer in Ubuntu I see 3 drives plus my DVD drive. They are 'New Volume' 'Toshiba System Volume' and 'Filesystem'
'New Volume' is 1.1gig and essentially empty (just has a system volume information folder  and recycle folder in it)
'Toshiba System Volume' is 1.3gig and has about 170megs of space used, but nothing on it that I recognize. Basically just a system volume inofrmation folder and a SOURCES folder.
'Filesystem' is more confusing. When I rightclick-properties I get:
Contents: 169,691 items, totalling 11.0 GB
(some contents unreadable)
and 
Free Space: 7.5 GB
This is don't understand, as I didn't make an 18gig partition anywhere on the drive.

Anyway, with that additional background, here's what happened when I tried the commands you suggested:

sda1 and sda5 mounted ok and when I browsed them in media they turned out to be the same as two of the drives that show up under Computer.

sda5 appears to be the drive I have in Computer called 'New Volume' which I think is the 1gig partition I made?
sda1 is 'Toshiba System Volume' which is maybe the original Vista partition that I thought was for recovery?
When I tried to mount sda2 I got the error message "mount: you must specify the filesystem type" and when I go to my new sda2 folder under media it is empty but it does say at the bottom "0 items free space 7.5GB"
I was afraid to try mounting sda3 but based on how big it appears to be when I run the sfdisk -d command, I am guessing that my Vista partition is sda3? This confuses me, as I'm nearly positive that I installed Ubuntu on my new, blank 10GB partition. Should I try mounting sda3 to see what happens, or is this a bad idea?

Anyway, I can't really make sense of this, but hopefully one of you can? Sorry that this is pretty garbled, I'm very unfamiliar with Ubuntu and my knowledge of partitions and such is limited enough when dealing with them through an OS I know...

Code follows (sorry, it's pretty messy):

calderp@paulpc:~$ sudo mkdir /media/sda5
[sudo] password for calderp: 
calderp@paulpc:~$ sudo mount /dev/sda5 /media/sda5 
calderp@paulpc:~$ sudo mkdir /media/sda2
calderp@paulpc:~$ sudo mount /dev/sda2 /media/sda2
mount: you must specify the filesystem type
calderp@paulpc:~$ sudo mount /dev/sda5 /media/sda5 
fuse: mount failed: Device or resource busy
calderp@paulpc:~$ sudo mkdir /media/sda2
mkdir: cannot create directory `/media/sda2': File exists
calderp@paulpc:~$ sudo mkdir /media/sda1
calderp@paulpc:~$ sudo mount /dev/sda1 /media/sda1 
calderp@paulpc:~$ sudo mount /dev/sda5 /media/sda5 
fuse: mount failed: Device or resource busy
calderp@paulpc:~$ sudo mount /dev/sda2 /media/sda2
mount: you must specify the filesystem type
calderp@paulpc:~$ sudo mount /dev/sda2 /media/sda5 
mount: you must specify the filesystem type
calderp@paulpc:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f9a64c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
/dev/sda2         3076095     5396479     1160192+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3   *     5397840   467427239   231014700   82  Linux swap / Solaris
/dev/sda4       467427240   488392064    10482412+  83  Linux
/dev/sda5         3076096     5396479     1160192    7  HPFS/NTFS
calderp@paulpc:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3076095, size=  2320385, Id= 5
/dev/sda3 : start=  5397840, size=462029400, Id=82, bootable
/dev/sda4 : start=467427240, size= 20964825, Id=83
/dev/sda5 : start=  3076096, size=  2320384, Id= 7
calderp@paulpc:~$ sudo mount /dev/sda5 /mnt && ls -l /mnt
total 0
drwxrwxrwx 1 root root 0 2009-01-22 01:43 $RECYCLE.BIN
drwxrwxrwx 1 root root 0 2009-01-22 01:42 System Volume Information
calderp@paulpc:~$ 



Thanks again for the help caljohnsmith and the cog. You two are lifesavers.

---

### Post by caljohnsmith on 2009-01-23
Upon looking at your partition table more closely, it does not look good at all. Your only NTFS partition is sda5, and since it is only about 1.1 GB, that certainly can't be your Vista partition. Your Ubuntu partition is about 10.5 GB, but your swap partition is a whopping 231 GB. And since the swap partition is marked as bootable, I would guess that might be your lost Vista partition. Please post:
```
sudo mount /dev/sda3 /mnt && ls -l /mnt
```
If the above command returns a mount error, you might be in big trouble if you want to recover your Vista partition. Do you have a lot of important documents in Vista you need to recover? Also, I think it would be good to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully shed some light on where your Vista might be.

---

### Post by calderp on 2009-01-23
uh.oh.

I don't have a lot of important files, but I do have a lot of music which was recently given to me by a friend and which I was really hoping to keep. But when I installed Ubuntu I realized I might lose it, so if I do it's not the end of the world.
```

calderp@paulpc:~$ sudo mount /dev/sda3 /mnt && ls -l /mnt
[sudo] password for calderp: 
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type
```

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda5 starts at sector 3076096.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap

sda4: _________________________________________________________________________

    File system:       jfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f9a64c1

Partition  Boot        Start          End         Size  Id System

/dev/sda1              2,048    3,074,047    3,072,000  27 
/dev/sda2          3,076,095    5,396,479    2,320,385   5 Extended
/dev/sda5          3,076,096    5,396,479    2,320,384   7 HPFS/NTFS
/dev/sda3    *     5,397,840  467,427,239  462,029,400  82 Linux swap / Solaris
/dev/sda4        467,427,240  488,392,064   20,964,825  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="58DE8F0CDE8EE19C" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda3: UUID="a7a50052-e130-48fb-8fdd-08303bf8a685" TYPE="swap" 
/dev/sda4: UUID="0a67f140-7ae2-4553-a985-bcb94b613dab" TYPE="jfs" 
/dev/sda5: UUID="00FAEA9FFAEA8FE8" LABEL="New Volume" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type jfs (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/calderp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=calderp)
/dev/scd0 on /media/disk type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sda5 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/TOSHIBA SYSTEM VOLUME type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=0a67f140-7ae2-4553-a985-bcb94b613dab ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a67f140-7ae2-4553-a985-bcb94b613dab

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		0a67f140-7ae2-4553-a985-bcb94b613dab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0a67f140-7ae2-4553-a985-bcb94b613dab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		0a67f140-7ae2-4553-a985-bcb94b613dab
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=0a67f140-7ae2-4553-a985-bcb94b613dab ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0a67f140-7ae2-4553-a985-bcb94b613dab
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0a67f140-7ae2-4553-a985-bcb94b613dab ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0a67f140-7ae2-4553-a985-bcb94b613dab
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0a67f140-7ae2-4553-a985-bcb94b613dab ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0a67f140-7ae2-4553-a985-bcb94b613dab
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=0a67f140-7ae2-4553-a985-bcb94b613dab /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=a7a50052-e130-48fb-8fdd-08303bf8a685 none            swap    sw              0       0

=================== sda4: Location  of files loaded by Grub: ===================


 239.8GB: boot/grub/menu.lst
 241.0GB: boot/grub/stage2
 239.5GB: boot/initrd.img-2.6.27-7-generic
 239.5GB: boot/initrd.img-2.6.27-9-generic
 239.5GB: boot/vmlinuz-2.6.27-7-generic
 239.4GB: boot/vmlinuz-2.6.27-9-generic
 239.5GB: initrd.img
 239.5GB: initrd.img.old
 239.4GB: vmlinuz
 239.5GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-23
OK, how about we try to use "testdisk" to see if it can repair your Vista partition's boot sector enough that you could at least mount it and grab your important files. First do:
```
sudo sfdisk -c /dev/sda 3 7
```
Then make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda3 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". Then again try:
```
sudo umount /mnt
sudo mkdir /mnt/sda3
sudo mount /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
```
And please post the full output. We can work from there.

---

### Post by calderp on 2009-01-23
Progress, maybe?
after performing all those steps in Testdisk I end up seeing this:
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 3 * HPFS - NTFS            336   0  1 29095 254 63  462029400 [SQ004828V03]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
```

Which seems like it would be good?
Also, when I go to directories in Testdisk I get:
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

 3 * HPFS - NTFS            336   0  1 29095 254 63  462029400 [SQ004828V03]
Use Right arrow to change directory, c to copy, q to quit
Directory /

dr-xr-xr-x     0     0         0 21-Jan-2009 19:07 .
dr-xr-xr-x     0     0         0 21-Jan-2009 19:07 ..
dr-xr-xr-x     0     0         0  2-Sep-2008 09:19 Boot
-r--r--r--     0     0    333203  2-Sep-2008 09:20 bootmgr
-r--r--r--     0     0      8192  2-Sep-2008 09:20 BOOTSECT.BAK
dr-xr-xr-x     0     0         0 13-Sep-2008 06:12 DOCS
dr-xr-xr-x     0     0         0  2-Sep-2008 09:20 Documents and Settings
dr-xr-xr-x     0     0         0 13-Sep-2008 05:33 MSOCache
-r--r--r--     0     0   4466864128 13-Sep-2008 05:23 pagefile.sys
dr-xr-xr-x     0     0         0  2-Sep-2008 09:19 Program Files
dr-xr-xr-x     0     0         0  2-Sep-2008 09:19 Program Files (x86)
dr-xr-xr-x     0     0         0  2-Sep-2008 09:19 ProgramData
dr-xr-xr-x     0     0         0  1-Sep-2008 18:07 System Volume Information
dr-xr-xr-x     0     0         0 22-Jan-2009 04:09 Temp
dr-xr-xr-x     0     0         0  2-Sep-2008 09:19 Users
dr-xr-xr-x     0     0         0  2-Sep-2008 09:19 Windows

```

Which are all my directories in the Vista partition.

But... When I try the code it still doesn't want to mount:
```

[sudo] password for calderp: 
umount: /mnt: not mounted
calderp@paulpc:~$ sudo mount /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
/dev/sda3 looks like swapspace - not mounted
mount: you must specify the filesystem type

```

Thanks again, I (obviously) couldn't do any of this without the help!

---

### Post by caljohnsmith on 2009-01-23
Try going through the testdisk procedure again, but this time choose "Backup BS" instead of "Rebuild BS". If testdisk allows you to restore the backup boot sector (Backup BS), then try mounting the partition again.

---

### Post by calderp on 2009-01-23
Would backup BS be [Dump]? I Don't see a backup BS but the subtitle for [Dump] is " Dump boot sector and backup boot sector"

```

[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                    Dump boot sector and backup boot sector
```

---

### Post by The Cog on 2009-01-24
caljohnsmith is way ahead of me on this one, but one thing I can think of that you can try until he gets back is to specify the filesystem type to the mount command. It seems to think it's swap but you might be able to override that by hand:
```
sudo mount -t ntfs -o ro /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
```

---

### Post by caljohnsmith on 2009-01-24
If testdisk does not give you a choice to do "Backup BS", it may be that your Vista boot sector boot code is OK. Similar to what The Cog suggested, how about trying the following:
```
sudo mkdir /mnt/sda3
sudo mount -t ntfs-3g -o force /dev/sda3 /mnt/sda3
ls -l /mnt/sda3
```
The first command you can omit if you still have the sda3 directory in /mnt, but please post the output of the other commands. Also, do you have a Vista Install CD? If the above commands fail, how about booting your Vista CD, go to the command line, and do:
```
bootrec /fixboot

```
And then try mounting sda3 again. If you don't have a Vista Install CD, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes or if you run into problems.

---

### Post by calderp on 2009-01-24
Ok, so first I tried the cog's code:

```
calderp@paulpc:~$ sudo mount -t ntfs -o ro /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
[sudo] password for calderp: 
fuse: mount failed: Device or resource busy

```

Is it possible to freeze activity on the swap partition for a moment so that it wouldn't be busy, and might mount? Probably not.

The first bit of code from caljohnsmith also had problems:

```
calderp@paulpc:~$ sudo mount -t ntfs-3g -o force /dev/sda3 /mnt/sda3
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

Should I run the chkdsk /f command? I can't boot into Vista so I can't really follow all those instructions.

I do have a Vista boot cd so I am going to try the last idea now, and post again in a minute with results. Sorry that I was a bit slow this morning :)

---

### Post by caljohnsmith on 2009-01-24
Instead of "chkdsk /f", try doing the following from the Vista CD:```

chkdsk /r
```
That is more complete than the chkdsk /f command because it will also ferret out bad sectors. Also, when you are in Ubuntu, go ahead and do:
```
sudo swapoff -a
gksudo gedit /etc/fstab
```
And comment-out the line in your fstab for the swap partition. After doing the chkdsk and bootrec /fixboot, let me know if that helps or not, and we can work from there.

---

### Post by calderp on 2009-01-24
Ok so when I ran the code after booting off the Vista cd and going to the command line:

```
bootrec /fixboot
```

I got a response that the operation completed successfully.

But when I try to mount it:
calderp@paulpc:~$ sudo mount -t ntfs-3g -o force /dev/sda3 /mnt/sda3
[sudo] password for calderp: 
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
calderp@paulpc:~$ ls -l /mnt/sda3
total 0

and when I tried cog's code again:
```
calderp@paulpc:~$ sudo mount -t ntfs -o ro /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
ls: reading directory /mnt/sda3: Input/output error
total 0
calderp@paulpc:~$ 

```

Now going to try chkdsk /r

Should I try to mount the drive after commenting it out in fstab, when I get back from running chkdsk in vista?
Thanks!

---

### Post by calderp on 2009-01-24
Dang! When I tried chkdsk /r I got an error saying:

The type of filesystem is NTFS
Cannot lock current drive
Windows cannot run disk checking on this volume because it is write protected.

And just because, I tried mounting and got the same error:

```
calderp@paulpc:~$ sudo mount -t ntfs -o ro /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
[sudo] password for calderp: 
ls: reading directory /mnt/sda3: Input/output error
total 0

```

---

### Post by caljohnsmith on 2009-01-24
OK, before you go further, how about running testdisk again, but run it from a directory where you can copy your important Vista files to:
```
mkdir ~/Vista_recovery
cd ~/Vista_recovery
sudo testdisk
```
Then go through the steps to get to the point where you can get a directory listing of the Vista partition (using "p") like you did previously, but navigate through the Vista directories and use "c" to copy your important files to the Vista_recovery directory in which you ran testdisk. Let me know how that goes.

---

### Post by calderp on 2009-01-24
Hmm.. So the first thing I noticed are that the sectors aren't identical when they were before. Not sure why that would be / if it matters.


```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 3 * HPFS - NTFS            336   0  1 29095 254 63  462029400 [SQ004828V03]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



```

And then, uh-oh, I no longer have the directories I saw earlier...
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

 3 * HPFS - NTFS            336   0  1 29095 254 63  462029400 [SQ004828V03]
Use Right arrow to change directory, c to copy, q to quit
Directory /

dr-xr-xr-x     0     0         0 21-Jan-2009 19:07 .
dr-xr-xr-x     0     0         0 21-Jan-2009 19:07 ..



```

Which reminds me that last night before I went to bed I tried to do the backup thing and, only seeing "Dump boot sector and backup boot sector" as an option under [Dump], I ran [Dump]. It didn't seem to do anything at the time and I forgot... Did I screw everything up? When I try to copy what shows up, I get no files.

---

### Post by caljohnsmith on 2009-01-24
If the sectors aren't identical, try doing the "Rebuild BS" again, and then try mounting the partition after that. If it still fails, run testdisk again, but this time try the "Repair MFT" option from the same screen where the "Rebuild BS" is available. Also see if you can get a directory listing after doing the "Repair MFT" option while you are in testdisk. After that, try mounting the partition, and let me know if anything changes.

---

### Post by calderp on 2009-01-24
So it rebuilt ok, and then RepairMFT ran ok, but the directory list still looks like this:
```
 3 * HPFS - NTFS            336   0  1 29095 254 63  462029400 [SQ004828V03]
Use Right arrow to change directory, c to copy, q to quit
Directory /

dr-xr-xr-x     0     0         0 21-Jan-2009 19:07 .
dr-xr-xr-x     0     0         0 21-Jan-2009 19:07 ..


```

and when I try to mount it, I get:
```
calderp@paulpc:~$ sudo mount -t ntfs-3g -o force /dev/sda3 /mnt/sda3
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

So then I tried the fstab comment out thing, because I didn't do that before when the chkdsk failed, and then I tried to mount and again it doesn't work, but I get a different error:

```
[CODE]calderp@paulpc:~$ gksudo gedit /etc/fstab
calderp@paulpc:~$ 
calderp@paulpc:~$ sudo mount -t ntfs -o ro /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
fuse: mount failed: Device or resource busy
calderp@paulpc:~$ 


```[/CODE]
 I'm so sorry that this is taking up so much of your time, but again, thank you so much for helping!

Now that I have commented out the swap file in fstab, should I try chkdsk again from Vista boot?
Also, if there is a way for you to get root on my machine and try a couple things, that would be totally ok with me if you thought it might help :)

---

### Post by caljohnsmith on 2009-01-24
I'm afraid your Vista partition might be munged beyond what we can repair, at least with the tools I'm aware of. I also feel bad because last night I forgot to have you immediately do "sudo swapoff -a" and also remove the swap partition reference from your /etc/fstab, so there's a possibility the Vista partition may have been munged even more since last night. If you really want to try and recover your files from the Vista partition, you could use "photorec" which comes in the testdisk package; but the problem is that it recovers every single file it can find in the partition, and often has to rename them with some generic name. Thus you end up with thousands of files to sort through, and the file names often have no relevance to what the files were previously. You'll also need another drive to save all the recovered files to, at least 230 GB worth of space since that is about how big your Vista partition is. So what do you want to do now? Do you want to spend time doing file recovery, or would you rather just cut your losses as it is?

---

### Post by calderp on 2009-01-24
Well shucks. I suppose I'll just cut my losses, there really wasn't much on there that is important, just some media that I can eventually get back. I copied my really important documents to a DVD before I tried all this. I'll just wipe everything and start clean. It's still worth it to stop having to deal with Vista, I've been extremely impressed with Ubuntu so far!
Thank you so much for all your help, it's really amazing to have people like you who will take so much time to help out a noob. It's what I've always loved about open-source communities :)

---

### Post by caljohnsmith on 2009-01-24
Good luck with your reinstall, and sorry we couldn't recover your Vista partition. Let me know how that goes or if you run into problems.

---

### Post by calderp on 2009-01-24
Wow! Happy ending after all. Vista actually did something right. I booted into the Vista CD and used their repair utility, after about an hour of processing it finished and when I loaded up Ubuntu, all my files are now in a drive that popped up :) Hopefully they'll stay there and I think my next step will be to back everything up, wipe everything clean, and then do a re-install to clear up any lingering partitioning issues there might be.
Thanks again!

---

### Post by caljohnsmith on 2009-01-24
That's really great news; glad to hear the Vista CD was able to recover the partition. Keep me posted on how your reinstall goes. :)

---

### Post by The Cog on 2009-01-25
That's good news. But I have a few nagging worries.

Firstly, what does diso fdisk -l say these days? Is the NTFS partition ID still marked as type swap? If so, I would think that needs fixing.

Secondly, does this mean your Ubuntu still has no swap partition? You may want to try and create a swap partition, or you may feel that after all the hassle so far you don't want to mess with it again now.

---

### Post by calderp on 2009-01-25
Thanks for the concern, cog. So it looks like it is no longer a swap but now I don't have a swap? How important is a swap directory, and how big does it need to be? Could I use my 1GB partition that isn't doing anything? I'm a little leery of messing with things much more, but if the swap is really important, I might wait until I can find an external HDD, back up everything, and then wipe the disk and re-install. On the other hand, if it would be relatively simple and probably not too risky to try and create a swap partition now, I could do that. The only thing I'm worried about is that Ubuntu only seems to recognize my big partition because Vista is now ok with it, but I'm worried that doing anything will confuse Vista again and cause me to lose access.

```
calderp@paulpc:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f9a64c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2             192         336     1160192+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         337       29096   231014700    7  HPFS/NTFS
/dev/sda4           29097       30401    10482412+  83  Linux
/dev/sda5             192         336     1160192    7  HPFS/NTFS
calderp@paulpc:~$ 

```

---

### Post by caljohnsmith on 2009-01-25
I would go ahead and use your 1 GB sda5 partition for swap, since you said you're not using it right now for anything else. How about running gparted (System > Admin > Partition Editor) from the Live CD, and use that to format the sda5 partition as "swap". Once you've done that, how about booting back into Ubuntu, and do:
```
sudo blkid -c /dev/null
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
sudo swapon -a
sudo blkid -c /dev/null
free
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
And please post the output of all the above commands.

---

### Post by calderp on 2009-01-25
Well, that seemed to go well. How does this look?
```
calderp@paulpc:~$ sudo blkid -c /dev/null
[sudo] password for calderp: 
/dev/sda1: UUID="58DE8F0CDE8EE19C" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda3: UUID="0000000000000000" LABEL="SQ004828V03" TYPE="ntfs" 
/dev/sda4: UUID="0a67f140-7ae2-4553-a985-bcb94b613dab" TYPE="jfs" 
/dev/sda5: UUID="c014ffc4-8a94-41d5-8251-41736aa2c949" TYPE="swap" 
calderp@paulpc:~$ sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
Setting up swapspace version 1, size = 1160188 KiB
no label, UUID=a7a50052-e130-48fb-8fdd-08303bf8a685
calderp@paulpc:~$ sudo swapon -a
calderp@paulpc:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="58DE8F0CDE8EE19C" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda3: UUID="0000000000000000" LABEL="SQ004828V03" TYPE="ntfs" 
/dev/sda4: UUID="0a67f140-7ae2-4553-a985-bcb94b613dab" TYPE="jfs" 
/dev/sda5: UUID="a7a50052-e130-48fb-8fdd-08303bf8a685" TYPE="swap" 
calderp@paulpc:~$ free
             total       used       free     shared    buffers     cached
Mem:       3919768     678848    3240920          0       1652     231792
-/+ buffers/cache:     445404    3474364
Swap:            0          0          0
calderp@paulpc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=0a67f140-7ae2-4553-a985-bcb94b613dab /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda3
#UUID=a7a50052-e130-48fb-8fdd-08303bf8a685 none            swap    sw              0       0
calderp@paulpc:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=a7a50052-e130-48fb-8fdd-08303bf8a685
calderp@paulpc:~$ 

```

Is 1GB sufficient for swap space?

---

### Post by caljohnsmith on 2009-01-25
It looks like it went OK, except the "free" command is not showing your swap space yet. How about rebooting, and please post:
```
sudo fdisk -lu
free
sudo swapon -s
```
Also, how much RAM do you have? Do you ever plan on trying to "hibernate" your computer, or is that a non-issue?

EDIT: Never mind, I see your computer has 4 GB of RAM (I had one of my brain-dead moments, sorry :)). In that case you won't be able to hibernate your computer with 1 GB of swap space, but if you don't care about that, then 1 GB of swap would probably be adequate. It's up to you if you want to make swap bigger.

---

### Post by calderp on 2009-01-26
```
calderp@paulpc:~$ sudo fdisk -lu
[sudo] password for calderp: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f9a64c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
/dev/sda2         3076095     5396479     1160192+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3   *     5397840   467427239   231014700    7  HPFS/NTFS
/dev/sda4       467427240   488392064    10482412+  83  Linux
/dev/sda5         3076096     5396479     1160192   82  Linux swap / Solaris
calderp@paulpc:~$ free
             total       used       free     shared    buffers     cached
Mem:       3919768    2031116    1888652          0     187028    1104600
-/+ buffers/cache:     739488    3180280
Swap:            0          0          0
calderp@paulpc:~$ sudo swapon -s
Filename				Type		Size	Used	Priority
calderp@paulpc:~$ free
             total       used       free     shared    buffers     cached
Mem:       3919768    2031260    1888508          0     187284    1104936
-/+ buffers/cache:     739040    3180728
Swap:            0          0          0
calderp@paulpc:~$ 


```

There's the code. Looks like it's still not showing the swap file?
Also, I have no need for hibernation so I think I'll leave things as they are unless everything starts to slow down.

---

### Post by caljohnsmith on 2009-01-26
OK, I believe I found the problem; I didn't notice it before but your swap partition is actually commented out in your fstab still. How about opening your fstab:
```
gksudo gedit /etc/fstab
```
Delete the # (as shown highlighted in red) at the beginning of the swap line, and also you might as well change the "sda3" to "sda5" since your swap partition is actually sda5 now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=0a67f140-7ae2-4553-a985-bcb94b613dab /               jfs     relatime,errors=remount-ro 0       1
# /dev/[COLOR="Blue"]sda5[/COLOR]
[COLOR="Red"]#[/COLOR]UUID=a7a50052-e130-48fb-8fdd-08303bf8a685 none            swap    sw              0       0
```
Then reboot, do "free" again, and hopefully it should show your swap space finally.

---

### Post by calderp on 2009-01-26
```
calderp@paulpc:~$ free
             total       used       free     shared    buffers     cached
Mem:       3919768     722072    3197696          0        864     253204
-/+ buffers/cache:     468004    3451764
Swap:      1160184          0    1160184
calderp@paulpc:~$ 
calderp@paulpc:~$ 

```

Alright! Thanks so much caljohnsmith. You've been a wonderful introduction to Linux, I'm excited to be using it.

---

### Post by caljohnsmith on 2009-01-26
Glad to hear swap is finally working, sorry I didn't realize earlier that you still had the swap partition commented out in your fstab. Cheers and hope the rest of your Ubuntu experience goes smoother than the start. :)

---

