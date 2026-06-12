---
title: "New Problem- Grub Error 17"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by nittanywildcat on 2008-12-21
I have searched for an hour to try to solve this problem, to no avail.

I successfully (?) installed Ubuntu onto my mother's PC (see my previous thread for that incident).  When it went to reboot, immediately after the Dell startup, it hits GRUB Loading stage1.5.  Error 17.

So, I searched forever for a solution.  I don't have Dell Media Center, so that's not a problem.  Ubuntu doesn't even start, so I can't press escape to get into some setup.  I have a completely different BIOS compared to everyone else, apparently (for a Dell Inspiron 9300)...so I can't go in and change partition things.

So I took another suggestion and reinstalled ubuntu.  On my partitions, I selected Windows XP to be ~30 GB NTFS on /sda2, Ubuntu 8.10 / to be ~49 GB EXT3 on /sda5, /boot to be ~300 MB EXT3 on /sda6, and swap on ~800 MB on /sda7.


I am still getting it.  Oh, and I can boot the LiveCD, but can't get a command line to save my life to edit GRUB.


Suggestions?

---

### Post by IamReck on 2008-12-21
Error 17:

 Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.       You have /boot on there for 300 MB?  Don't know why you would do that.  I don't really understand this error to be honest, but its a start.

Can you also provide a link to your previous problem?

---

### Post by IamReck on 2008-12-21
And just for the record, all your Data should still be there, so no worries about that.

Are you sure the Live CD installed Ubuntu correctly?

---

### Post by nittanywildcat on 2008-12-21
Here is my previous problem:  [http://ubuntuforums.org/showthread.php?t=1017909](http://ubuntuforums.org/showthread.php?t=1017909)


For /boot, I just picked a number...I didn't want to risk it being too small.

I'm fairly confident the livecd installed it correctly.  I don't see why it wouldn't, everything was confirmed to be correct when it restarted.  The problem, as I've researched it (and what you have posted Reck), is that GRUB is not recognizing the correct partition to boot up (it attempts to guess, but is guessing the wrong one)...and it is a common error.

I'm about ready to pull my hair out, being this close and not being able to start it up.

---

### Post by IamReck on 2008-12-21
Did Windows work before all of this?

Your Windows partition could be messed up, and that could be what GRUB isn't recognizing.

Also was there a guide or something that told you to make a /boot partition, usually you just have a / and a /home partition.  Never heard of that.

---

### Post by IamReck on 2008-12-21
/boot also must be on the first 8.5 GB of the Hard Drive, just read that from some Googling.

From your description it seems it is at the end, which could be causing the problem.

---

### Post by nittanywildcat on 2008-12-21
> **IamReck said:**
> /boot also must be on the first 8.5 GB of the Hard Drive, just read that from some Googling.

From your description it seems it is at the end, which could be causing the problem.

When I partitioned, I did select "beginning", not "end"...is that not what this is?

---

### Post by handydan918 on 2008-12-21
> **IamReck said:**
> Did Windows work before all of this?

Your Windows partition could be messed up, and that could be what GRUB isn't recognizing.

Also was there a guide or something that told you to make a /boot partition, usually you just have a / and a /home partition.  Never heard of that.
There is nothing wrong with a /boot partition. In fact, it's a kinda "old school" standard. That way it's easier to back up an restore /boot. Not too sure about putting /boot on sda6, however, or anything besides a primary, for that matter.

---

### Post by IamReck on 2008-12-21
Did you shrink the Windows NTFS partition using the Live CD, when you were setting up your partition?

---

### Post by IamReck on 2008-12-21
I have never heard of making a separate boot partition when installing, I always have just done / and /home.  Do you know the value of a /boot partition, or do you have a resource explaining, I just looked at mine and all it has is GRUB information and some Linux kernel stuff.

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by nittanywildcat on 2008-12-26
Hi again...sorry, I was so frustrated I took a few days off from it.

But caljohn, I did do what you said, and here are the results:

```
============================= Boot Info Summary: ==============================

Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #4 for its boot files.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 96390.
    Operating System:  XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sda6 and 
                       looks at sector 154304945 of the same hard drive for 
                       the stage2 file (a stage2 file is at this location on 
                       /dev/sda) and on partition #6 for menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub

sda7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================
fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       96390    58701509    29302560    7  HPFS/NTFS
/dev/sda4        58701510   156296384    48797437+   5  Extended
/dev/sda5        58701573   153966959    47632693+  83  Linux
/dev/sda6       153967023   154722014      377496   83  Linux
/dev/sda7       154722078   156296384      787153+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

_______________________________________________________________________________
blkid -c /dev/null:

/dev/sda2: UUID="06649ECE649EC03B" TYPE="ntfs" 
/dev/sda5: UUID="159db241-66b5-4917-884d-d08178863d27" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="95460211-4121-4d0d-a2b9-b9ee6e48ac81" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="18aeb726-1f09-4d3b-bf78-f2b3757b3912" TYPE="swap" 
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

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=159db241-66b5-4917-884d-d08178863d27 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=95460211-4121-4d0d-a2b9-b9ee6e48ac81 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=18aeb726-1f09-4d3b-bf78-f2b3757b3912 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 8
drwxr-xr-x  2 root root 4096 2008-12-21 12:25 .
drwxr-xr-x 20 root root 4096 2008-12-21 12:38 ..

============================= sda6/grub/menu.lst: =============================

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
# kopt=root=UUID=159db241-66b5-4917-884d-d08178863d27 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=95460211-4121-4d0d-a2b9-b9ee6e48ac81

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
uuid		95460211-4121-4d0d-a2b9-b9ee6e48ac81
kernel		/vmlinuz-2.6.27-7-generic root=UUID=159db241-66b5-4917-884d-d08178863d27 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		95460211-4121-4d0d-a2b9-b9ee6e48ac81
kernel		/vmlinuz-2.6.27-7-generic root=UUID=159db241-66b5-4917-884d-d08178863d27 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		95460211-4121-4d0d-a2b9-b9ee6e48ac81
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


================================== sda6/grub: ==================================

total 184
drwxr-xr-x 2 root root   1024 2008-12-21 12:38 .
drwxr-xr-x 4 root root   1024 2008-12-21 12:38 ..
-rw-r--r-- 1 root root    197 2008-12-21 12:38 default
-rw-r--r-- 1 root root     15 2008-12-21 12:38 device.map
-rw-r--r-- 1 root root   8108 2008-12-21 12:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-21 12:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-21 12:38 installed-version
-rw-r--r-- 1 root root   8712 2008-12-21 12:38 jfs_stage1_5
-rw-r--r-- 1 root root   4585 2008-12-21 12:38 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-21 12:38 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-21 12:38 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-21 12:38 stage1
-rw-r--r-- 1 root root 121460 2008-12-21 12:38 stage2
-rw-r--r-- 1 root root   9556 2008-12-21 12:38 xfs_stage1_5

=============================== StdErr Messages: ===============================

```

---

### Post by nittanywildcat on 2008-12-26
> **IamReck said:**
> Did you shrink the Windows NTFS partition using the Live CD, when you were setting up your partition?

Yes.

---

### Post by caljohnsmith on 2008-12-26
OK, for some reason the Grub in your MBR is looking on sda4 for its boot files, and yet sda4 is an extended partition; that would probably explain why you are getting the Grub error 17. Also, your Windows sda2 boot.ini file is incorrect, because you not longer have an sda1 partition it looks like. But the first step would be to get Grub working, so try the following:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if you get the Grub menu OK; if not, let me know the error you get.

---

### Post by nittanywildcat on 2008-12-26
worked perfectly...thanks! :)

---

### Post by caljohnsmith on 2008-12-26
> **nittanywildcat said:**
> worked perfectly...thanks! :)
You're most welcome, but can you boot Windows from Grub? I don't think you can boot Windows right now with the way your Windows boot.ini file is configured. But instead of changing the boot.ini file, you could just create a primary partition in front of the Windows partition with the small amount of unallocated space you have there, and then you should be able to boot Windows after that. Or if you don't want to make a partition with that space, I could help you modify your Windows boot.ini file so that it should work. Let me know if you would like any further help. :)

---

### Post by nittanywildcat on 2008-12-26
Windows is corrupted on her machine (XP SP3, plus loads of virii), so as a temporary stop-gap, I've installed ubuntu to get her working

---

### Post by loudog23 on 2008-12-28
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

here is mine,
Note that, previsouly it was setup as:
sda1 WinXp Ntfs
sda2 Xubuntu /
sda3 Extended
sda5 /Home

I remove the ntfs partititon (bye bye Windows), the xubuntu and swap
I then made new ext3 "/" for Ubuntu, new swap, and will re-use my old /home. so Now its:
sda1 Ubuntu /
sda2 Swap
sda3 Extended
sda5 Linux (to be set as /home)

also, in grub, find /boot/grub/stage1 give me file not found

I get Grub loading 1.5, Error 17 and here is my resuslts:
> ============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab /boot

sda2: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1570156f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   119266559    59633248+  83  Linux
/dev/sda2       119266560   123170354     1951897+  82  Linux swap / Solaris
/dev/sda3       201294450   586067264   192386407+   5  Extended
/dev/sda5       201294513   586067264   192386376   83  Linux

sfdisk -V /dev/sda:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="66d98993-2460-4a20-861a-1ca396ead2a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="8c3c18e5-db36-4935-95a7-939c398af07c" TYPE="swap" 
/dev/sda5: UUID="0ad452ff-4a3c-41ab-a8d2-5b953a7792df" SEC_TYPE="ext2" TYPE="ext3" 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=66d98993-2460-4a20-861a-1ca396ead2a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ad452ff-4a3c-41ab-a8d2-5b953a7792df /home           ext3    relatime        0       2
# /dev/sda2
UUID=8c3c18e5-db36-4935-95a7-939c398af07c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11948
drwxr-xr-x  2 root root    4096 2008-12-29 00:08 .
drwxr-xr-x 20 root root    4096 2008-12-29 00:08 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
-rw-r--r--  1 root root 8180349 2008-12-29 00:08 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== StdErr Messages: ===============================

No errors were reported.


From what i see, My old grub seting are still in there so grub is looking on part2 (that was old Xubuntu, and now is swap) for his file.

I cannot setup (hd0) either he return me with Error 12: Invalid device requested.

I did a ext3 check drive, all is ok, my installation returned me an succesful instalation.

I was not able to boot since installation, im running the live CD right now.

Sine i removed Windows, i don't need any dual boot manager or whatsoever, i know u can't remove grub (but replace it). So a simple way to just make my system boot ubuntu each time would be fine. I don't mind using Grub menu either, just something that works.

---

### Post by loudog23 on 2008-12-28
, i tried this

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 

also, im using sata drive... as i saw this might complicate the situation.

---

### Post by caljohnsmith on 2008-12-28
Loudog23, according to the output of the script you ran, you are missing your /boot/grub directory with all of Grub's files. How about doing the following from your Live CD:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
apt-get install grub
update-grub
cat /boot/grub/menu.lst
exit
```
And please post the output of all the above commands (copy/paste your terminal session). If you don't get any errors, go ahead and reboot and let me know how far you get. We can work from there.

---

### Post by loudog23 on 2008-12-28
Since i was re-installing and refreshing my Unbuntu, removing Windows and having backups, i just reformatted my ole HDD.

If the error come u again, ill keep this in mind.
thx

---

### Post by Airhead315 on 2009-01-07
Evening everyone.

I recently installed ubuntu and received Error 17 also. My original configuration was Windows Vista with two 500gb hard drives. I needed linux for a class I will be taking next semester so I pulled out an old sata 87gb hard drive and stuck it in the 3rd sata port(all drives are sata). I went through the install process and when it got to the partitioning section I changed it to install ubuntu onto the 87gb hard drive rather than the default master 500gb drive(that has vista on it). After install I booted the system and received Error 17. 

At that point I found this thread: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") 

and followed the instructions to reinstall GRUB. This did not resolve the issue and I still receieved Error 17. I then found this thread and followed caljohnsmith's instructions for generating the results file. This is what the Results file contained after running the script:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f0e68be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS

sfdisk -V /dev/sda:

Warning: partition 1 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13031302

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   154191869    77095903+  83  Linux
/dev/sdb2       154191870   160826714     3317422+   5  Extended
/dev/sdb5       154191933   160826714     3317391   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f0e68bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976771071   488384512    7  HPFS/NTFS

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="30BCC0BCBCC07E3A" TYPE="ntfs" 
/dev/sdb1: UUID="efecf701-52f5-4f44-9947-e2d2384bef68" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="3bf72fa2-021d-492e-a4d4-b358b0d22c08" TYPE="swap" 
/dev/sdc1: UUID="20A6C959A6C92FD8" TYPE="ntfs" 
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

================================== sda1/Boot: ==================================

total 540
drwxrwxrwx 1 root root   4096 2008-10-24 15:54 .
drwxrwxrwx 1 root root  24576 2009-01-07 19:45 ..
-rwxrwxrwx 1 root root  24576 2009-01-07 22:44 BCD
-rwxrwxrwx 1 root root  21504 2009-01-07 22:27 BCD.LOG
-rwxrwxrwx 2 root root      0 2002-01-01 15:14 BCD.LOG1
-rwxrwxrwx 2 root root      0 2002-01-01 15:14 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2002-01-01 15:14 bootstat.dat
drwxrwxrwx 1 root root      0 2008-10-24 15:54 cs-CZ
drwxrwxrwx 1 root root      0 2008-10-24 15:54 da-DK
drwxrwxrwx 1 root root      0 2008-10-24 15:54 de-DE
drwxrwxrwx 1 root root      0 2008-10-24 15:54 el-GR
drwxrwxrwx 1 root root      0 2008-10-24 15:54 en-US
drwxrwxrwx 1 root root      0 2008-10-24 15:54 es-ES
drwxrwxrwx 1 root root      0 2008-10-24 15:54 fi-FI
drwxrwxrwx 1 root root      0 2008-10-24 15:54 Fonts
drwxrwxrwx 1 root root      0 2008-10-24 15:54 fr-FR
drwxrwxrwx 1 root root      0 2008-10-24 15:54 hu-HU
drwxrwxrwx 1 root root      0 2008-10-24 15:54 it-IT
drwxrwxrwx 1 root root      0 2008-10-24 15:54 ja-JP
drwxrwxrwx 1 root root      0 2008-10-24 15:54 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-10-24 15:54 nb-NO
drwxrwxrwx 1 root root      0 2008-10-24 15:54 nl-NL
drwxrwxrwx 1 root root      0 2008-10-24 15:54 pl-PL
drwxrwxrwx 1 root root      0 2008-10-24 15:54 pt-BR
drwxrwxrwx 1 root root      0 2008-10-24 15:54 pt-PT
drwxrwxrwx 1 root root      0 2008-10-24 15:54 ru-RU
drwxrwxrwx 1 root root      0 2008-10-24 15:54 sv-SE
drwxrwxrwx 1 root root      0 2008-10-24 15:54 tr-TR
drwxrwxrwx 1 root root      0 2008-10-24 15:54 zh-CN
drwxrwxrwx 1 root root      0 2008-10-24 15:54 zh-HK
drwxrwxrwx 1 root root      0 2008-10-24 15:54 zh-TW

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
# kopt=root=UUID=efecf701-52f5-4f44-9947-e2d2384bef68 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=efecf701-52f5-4f44-9947-e2d2384bef68

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
uuid		efecf701-52f5-4f44-9947-e2d2384bef68
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=efecf701-52f5-4f44-9947-e2d2384bef68 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		efecf701-52f5-4f44-9947-e2d2384bef68
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=efecf701-52f5-4f44-9947-e2d2384bef68 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		efecf701-52f5-4f44-9947-e2d2384bef68
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=efecf701-52f5-4f44-9947-e2d2384bef68 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=3bf72fa2-021d-492e-a4d4-b358b0d22c08 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11952
drwxr-xr-x  3 root root    4096 2009-01-07 22:58 .
drwxr-xr-x 20 root root    4096 2009-01-07 22:58 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-07 22:58 grub
-rw-r--r--  1 root root 8180049 2009-01-07 22:58 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-07 22:58 .
drwxr-xr-x 3 root root   4096 2009-01-07 22:58 ..
-rw-r--r-- 1 root root    197 2009-01-07 22:58 default
-rw-r--r-- 1 root root     60 2009-01-07 22:58 device.map
-rw-r--r-- 1 root root   8108 2009-01-07 22:58 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-07 22:58 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-07 22:58 installed-version
-rw-r--r-- 1 root root   8712 2009-01-07 22:58 jfs_stage1_5
-rw-r--r-- 1 root root   4619 2009-01-07 22:58 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-07 22:58 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-07 22:58 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-07 22:58 stage1
-rw-r--r-- 1 root root 121460 2009-01-07 22:58 stage2
-rw-r--r-- 1 root root   9556 2009-01-07 22:58 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

Thanks for any help you might be able to provide!
Aaron

---

### Post by caljohnsmith on 2009-01-07
Hi Aaron, can you change your BIOS to boot the Ubuntu drive on start up? If so, the solution to your problem could be really simple; if you install Grub to the MBR (Master Boot Record) of your Ubuntu drive, then you should be able to boot it if all goes well. If that sounds OK with you, you can install Grub to the MBR of the Ubuntu drive by doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```
Reboot, set your BIOS to boot the 82 GB Ubuntu drive, and if all goes well you should be able to boot into Ubuntu. If that works OK, then when you get into Ubuntu, how about opening your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entries at the very end of the file:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
One of those entries should work to boot Windows from your Grub menu, but if neither work, let me know exactly what happens when you try each of them and we can work from there.

---

### Post by Airhead315 on 2009-01-07
Well, you are officially the best at this. I did exactly as you said, the first one you listed worked just fine. I changed it to say Windows Vista and I removed the other entry and also removed the default Vista/Longhorn listing that was there previously. Now I am greated with GRUB and can select either ubuntu or windows...exactly what I wanted.

Thanks for all your help!

---

### Post by caljohnsmith on 2009-01-07
Glad that worked OK, and sorry I forgot you were using Vista when I typed out those Grub entries for Windows. At least that's easy to fix, so I'm glad you sorted it all out; cheers and have fun with Vista and Ubuntu. :)

---

