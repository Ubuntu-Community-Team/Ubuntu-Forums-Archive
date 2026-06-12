---
title: "Partition problem with grub, wont boot"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by PLANETARY on 2009-01-20
I have an P4 Asus p4p800 and it has a 500gb sata and 200gb pata. I decided to install kubuntu 8.10 on my sata drive and /home on the sata. my sata is faster. I have had a dual boot on the pata with no problems (xp kubuntu) but now that I set it up this way I get 'Grub 1.5 loading error 17'

I also put both / and /home on the sata drive and still get error 17

Why doesnt it know whats going on?
I dont know enough to resolve this, I heard about super grub but I ask for advisement.

what should I post and what should I do?

Thanks

---

### Post by zvacet on 2009-01-21
Maybe [this]("http://users.bigpond.net.au/hermanzone/p15.htm#17") will be helpful to you.

---

### Post by cjv8888 on 2009-01-21
> **PLANETARY said:**
> I have an P4 Asus p4p800 and it has a 500gb sata and 200gb pata. I decided to install kubuntu 8.10 on my sata drive and /home on the pata. my sata is faster. I have had a dual boot on the pata with no problems (xp kubuntu) but now that I set it up this way I get 'Grub 1.5 loading error 17'

I also put both / and /home on the sata drive and still get error 17

Why doesnt it know whats going on?
I dont know enough to resolve this, I heard about super grub but I ask for advisement.

what should I post and what should I do?

Thanks

Please open a terminal and post the following:

> sudo fdisk -l

> gksudo gedit /boot/grub/menu.lst

---

### Post by PLANETARY on 2009-01-21
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0207a2e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4   *        6684       24321   141677235    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8165       60801   422806702+   7  HPFS/NTFS
/dev/sdb2            2311        8164    47022255   83  Linux
/dev/sdb3               1         486     3903763+   5  Extended
/dev/sdb4             487        2310    14651280   83  Linux
/dev/sdb5               1         486     3903700+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

second code doesn't work. i tried sudo instead of gksudo and that doesn't work.

---

### Post by caljohnsmith on 2009-01-21
PLANETARY, are you booting the sda or sdb drive on start up? Also, do you get the Grub error 17 before seeing a Grub menu, or before seeing the text "Press ESC to see menu", or do you get the error after selecting an OS in the Grub menu? In order to troubleshoot your problem, it would help to have more info about your setup related to booting, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what might be causing your Grub error 17.

---

### Post by cjv8888 on 2009-01-21
```
second code doesn't work. i tried sudo instead of gksudo and that doesn't work.
```

I see. You are booting off the live CD.
So you can go into Places/500 GB volume then go into 
/boot/grub/menu.lst
then just copy the menu.lst and you can post it here

---

### Post by PLANETARY on 2009-01-21
**My plan is to have / on sdb (500gig sata) on 20gb partition and /home another partition on the same disk, ~400gb, sdb. I also want Window XP on a 20gig partion on sdb as well. The sda (200gb pata) will be formated in fat32 for all my music.
I HAVE A PARTITION ON EACH HD WITH UNSORTED STUFF ON IT THAT I WANT TO KEEP(~80gb on sda and ~400gb on sdb), WILL ORGANIZE ACCORDING TO PLAN LATER. I SAY THIS SO IT DOESN'T CONFUSE YOU GUYS.

When I boot after its done posting computer stuff. It startes to load grub. it goes something like 

starting grub stage 1.5  
loading 
error 17

okay here is my results
Thanks 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0207a2e6

/dev/sda4     *  107,362,395  390,716,864  283,354,470   b W95 FAT32

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

/dev/sdb1        131,154,660  976,768,064  845,613,405   7 HPFS/NTFS
/dev/sdb2         37,110,150  131,154,659   94,044,510  83 Linux
/dev/sdb3                 63    7,807,589    7,807,527   5 Extended
/dev/sdb5                189    7,807,589    7,807,401  82 Linux swap / Solaris
/dev/sdb4          7,807,590   37,110,149   29,302,560  83 Linux

blkid -c /dev/null: ____________________________________________________________

/dev/sda4: UUID="4908-CA17" TYPE="vfat" 
/dev/sdb1: UUID="E2484D14484CE93D" LABEL="stuff" TYPE="ntfs" 
/dev/sdb2: UUID="ce4b8c5e-fd2c-412f-94da-9288cf22e0ae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="1e6111f4-db26-4792-8cba-33ddb7324387" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="b7261347-2ee4-4b1e-91a6-06951a8cf10e" TYPE="swap" 
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

=========================== sdb4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1e6111f4-db26-4792-8cba-33ddb7324387 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e6111f4-db26-4792-8cba-33ddb7324387

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
uuid		1e6111f4-db26-4792-8cba-33ddb7324387
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1e6111f4-db26-4792-8cba-33ddb7324387 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1e6111f4-db26-4792-8cba-33ddb7324387
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1e6111f4-db26-4792-8cba-33ddb7324387 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1e6111f4-db26-4792-8cba-33ddb7324387
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=1e6111f4-db26-4792-8cba-33ddb7324387 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=ce4b8c5e-fd2c-412f-94da-9288cf22e0ae /home           ext3    relatime        0       2
# /dev/sdb5
UUID=b7261347-2ee4-4b1e-91a6-06951a8cf10e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb4/boot: ==================================

total 11956
drwxr-xr-x  3 root root    4096 2009-01-21 04:00 .
drwxr-xr-x 20 root root    4096 2009-01-21 04:00 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-21 04:00 grub
-rw-r--r--  1 root root 8186153 2009-01-21 04:00 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb4/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-21 04:00 .
drwxr-xr-x 3 root root   4096 2009-01-21 04:00 ..
-rw-r--r-- 1 root root    197 2009-01-21 04:00 default
-rw-r--r-- 1 root root     30 2009-01-21 04:00 device.map
-rw-r--r-- 1 root root   8108 2009-01-21 04:00 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-21 04:00 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-21 04:00 installed-version
-rw-r--r-- 1 root root   8712 2009-01-21 04:00 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2009-01-21 04:00 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-21 04:00 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-21 04:00 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-21 04:00 stage1
-rw-r--r-- 1 root root 121460 2009-01-21 04:00 stage2
-rw-r--r-- 1 root root   9556 2009-01-21 04:00 xfs_stage1_5

=================== sdb4: Location  of files loaded by Grub: ===================


  11.5GB: boot/grub/menu.lst
  11.5GB: boot/grub/stage2
  11.5GB: boot/initrd.img-2.6.27-7-generic
  11.5GB: boot/vmlinuz-2.6.27-7-generic
  11.5GB: initrd.img
  11.5GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by PLANETARY on 2009-01-21
more goodies,

The boot/grub/menu list

```
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
# kopt=root=UUID=1e6111f4-db26-4792-8cba-33ddb7324387 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e6111f4-db26-4792-8cba-33ddb7324387

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
uuid		1e6111f4-db26-4792-8cba-33ddb7324387
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1e6111f4-db26-4792-8cba-33ddb7324387 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1e6111f4-db26-4792-8cba-33ddb7324387
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1e6111f4-db26-4792-8cba-33ddb7324387 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1e6111f4-db26-4792-8cba-33ddb7324387
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by cjv8888 on 2009-01-22
Try changing the hard disk boot priority in your BIOS.

---

### Post by PLANETARY on 2009-01-22
I did, did not work

---

### Post by caljohnsmith on 2009-01-22
For some reason the Grub installed to the MBR (Master Boot Record) of your sdb drive is pointing to your sdb3 swap partition instead of the sdb4 main Ubuntu partition for its boot files, so that would explain why you are getting a Grub error 17. Hopefully that's the only problem, so how about doing:
```
sudo grub
grub> root (hd1,3)
grub> setup (hd1)
grub> quit
```
Reboot, make sure your sdb drive is set to boot first, and let me know how far you get. We can work from there if you want.

---

### Post by PLANETARY on 2009-01-22
Thank you guys so much. up and running!!!

---

