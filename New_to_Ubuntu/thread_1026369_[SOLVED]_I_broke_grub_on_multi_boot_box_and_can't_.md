---
title: "[SOLVED] I broke grub on multi boot box and can't get up."
date: 2008-12-31
forum: New to Ubuntu
---

### Post by ranch hand on 2008-12-31
I have 3 installs of Hardy.  One that we use, one to play with and learn on, and one on an external to see if I could get it to work.

The whole deal worked great for about 2 days and then I did something, I have no idea what, that made it so I can't boot to any of them.

I get error 17 cannot mount.

I can access all my installs through the live CD and my 2 backup partitions.

This is one line that is common to all of my fstab files:

UUID=966762ae-7027-4f45-9724-ba2965cfa642 /               ext2    relatime,errors=remount-ro 0       1

This does not look good to me.

What do I have to do to repair Grub so that I can use my box?
Thanks

---

### Post by RoyHobbs on 2008-12-31
Hi

I'm a newbie, however whenever I have had any problems with the Grub I use Super Grub:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It always seems to work for me, hope this helps

---

### Post by ranch hand on 2008-12-31
Seeing your join date, I would say we are about equal on the newness end of things.

The link looks interesting but only one mirror is working and it has a long list that I can't make heads or tails of as far as what I need.  To complicate matters I am on dial up so I hope this is not a big file.

There are a number of .gz files but nothing to say what the difference is or what size they are.  I checked properties  on them.

---

### Post by Michael.Godawski on 2008-12-31
hi,

i would download this iso file
[super_grub_disk_0.9774.iso]("http://forjamari.linex.org/frs/download.php/1133/super_grub_disk_0.9774.iso")


[LIST]
[*][https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[/LIST]

---

### Post by decoherence on 2008-12-31
i don't believe /etc/fstab is read by grub.

you're going to have to manually assign the root partition, at least for grub. maybe for init, too.

edit the root line of the kernel you want to boot. you want to change the "hd(0,0)" where 0,0 could be other numbers.

0,0 refers to the first disk and the first partition. 0,1 would be the first disk and second partition. 1,0 would be the second disk, first partition. 1,1 the second disk, second partition, and so on. grub counts from zero unlike init (and thus the rest of linux) which counts from 1, hence grub's "0,0" equals "/dev/sda1" on your typical ubuntu system. "1,2" would be "/dev/sdb3"

You need to tell grub what your root partition is in the form of *"X,X"*

Now, if Ubuntu hadn't implemented the UUID system, you'd be able to look at the kernel line to see what the root is in /dev/sd*xX* form. But as it is, with a UUID there rather than something useful, you'll have to try and remember, or just guess. or i guess use the livecd with fdisk to read the partition names... they'll be different, though so you'll have to take that in to account...

i think super grub disk will be easier.

---

### Post by Michael.Godawski on 2008-12-31
> 0,0 refers to the first disk and the first partition. 0,1 would be the first disk and second partition. 1,0 would be the second disk, first partition. 1,1 the second disk, second partition, and so on. grub counts from zero unlike init (and thus the rest of linux) which counts from 1, hence grub's "0,0" equals "/dev/sda1" on your typical ubuntu system. "1,2" would be "/dev/sdb3"

Thx, finally I got it. :)

---

### Post by caljohnsmith on 2008-12-31
Hi Ranch Hand, nice to bump into you again. :) In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by ranch hand on 2008-12-31
#

---

### Post by ranch hand on 2008-12-31
Sorry for the last post.  Thats what I got trying to follow the instructions on sending the results text.  What pound sign?  Seems to be the next question.

Just pasting the text seems to violate some forum rule about images fairly well.

---

### Post by caljohnsmith on 2008-12-31
It's OK to copy/paste the entire text into your message, if you can't find the code tag graphic that's OK.

---

### Post by ranch hand on 2008-12-31
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sda1 and 
                       looks at sector 305807 of the same hard drive for the 
                       stage2 file (a stage2 file is at this location on 
                       /dev/sda) and on partition #1 for menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sda3 and 
                       looks at sector 295935473 of the same hard drive for 
                       the stage2 file (a stage2 file is at this location on 
                       /dev/sda) and on partition #3 for menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition

sdb4: _________________________________________________________________________

    File system:       swap

sdb5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub is installed to the boot sector of /dev/sdb5 and 
                       looks at sector 436483786 of the same hard drive for 
                       the stage2 file (a stage2 file is at this location on 
                       /dev/sdb) and on partition #5 for menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004630f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   292527584   146263761   83  Linux
/dev/sda2       606887505   625137344     9124920    5  Extended
/dev/sda3   *   292527585   394925894    51199155   83  Linux
/dev/sda4       394925895   606887504   105980805   83  Linux
/dev/sda5       606887568   625137344     9124888+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       185904180   346666634    80381227+  83  Linux
/dev/sdb2              63   185904179    92952058+  83  Linux
/dev/sdb3       346666635   612879749   133106557+   5  Extended
/dev/sdb4       612879750   625137344     6128797+  82  Linux swap / Solaris
/dev/sdb5       346666698   612879749   133106526   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

Drive sdf: _____________________________________________________________________

fdisk -lu /dev/sdf:

sfdisk -V /dev/sdf:

/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="e2e3cd65-bc09-487f-be96-a83fcc282e38" TYPE="ext3" 
/dev/sda3: UUID="0b6718c5-d816-4bf3-a4ae-73423b53bafd" TYPE="ext2" 
/dev/sda4: UUID="dc125497-ef78-45f0-b61b-025b36fc1dd2" TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="ef275bbf-7102-4fba-8d94-10a1cc01388e" 
/dev/sdb1: UUID="367da58f-59e0-46a9-912f-3a7ca026ad53" TYPE="ext2" 
/dev/sdb2: UUID="5987f338-b628-4b80-a498-8bdf407afcd7" TYPE="ext2" 
/dev/sdb4: TYPE="swap" UUID="977b2186-2a3c-4ae5-8419-a0a6a6453735" 
/dev/sdb5: UUID="966762ae-7027-4f45-9724-ba2965cfa642" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5 on /media/disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-2 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sda3 on /media/disk-3 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-4 type ext3 (rw,nosuid,nodev,uhelper=hal)

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
timeout		10

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
# kopt=root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash vga=773

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ef275bbf-7102-4fba-8d94-10a1cc01388e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 18080
drwxr-xr-x  3 root root      4096 2008-12-30 20:10 .
drwxr-xr-x 21 root root      4096 2008-12-30 20:10 ..
-rw-r--r--  1 root root    422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root     80062 2008-11-24 22:47 config-2.6.24-22-generic
drwxr-xr-x  3 root ubuntu    4096 2008-12-30 20:10 grub
-rw-r--r--  1 root root   7502748 2008-11-30 17:58 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root   7502929 2008-11-30 17:58 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root    905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root   1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 3 root ubuntu   4096 2008-12-30 20:10 .
drwxr-xr-x 3 root root     4096 2008-12-30 20:10 ..
-rw-r--r-- 1 root ubuntu      9 2008-10-27 23:25 default
-rw-r--r-- 1 root ubuntu     15 2008-10-19 03:49 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-10-19 03:49 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-10-19 03:49 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-10-19 03:49 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-10-19 03:49 jfs_stage1_5
-rw-r--r-- 1 root root     4284 2008-12-30 20:10 menu.lst
-rw-r--r-- 1 root root     4284 2008-12-30 20:10 menu.lst~
-rw-r--r-- 1 root root     5088 2008-11-02 03:18 menu.lst.backup
-rw-r--r-- 1 root ubuntu   7324 2008-10-19 03:49 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-10-19 03:49 reiserfs_stage1_5
drwxr-xr-x 2 root root     4096 2008-11-02 03:18 splashimages
-rw-r--r-- 1 root ubuntu    512 2008-10-19 03:49 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-10-19 03:49 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-10-19 03:49 xfs_stage1_5

=========================== sda3/boot/grub/menu.lst: ===========================

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
default		6

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
#password --md5 $1$yPkFq$erPwPoMoHhAttgcc6bVsa.#
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
# kopt=root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
lock
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by ranch hand on 2008-12-31
Had to break this in 2 because of too many smilie faces for forum rules to handle.

It makes interesting reading that almost means something to me but not quite.


============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd / ext2 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=ef275bbf-7102-4fba-8d94-10a1cc01388e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

================================== sda3/boot: ==================================

total 18008
drwxr-xr-x  3 root root    4096 2008-12-30 19:56 .
drwxr-xr-x 21 root root    4096 2008-12-30 19:56 ..
-rw-r--r--  1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
drwxr-xr-x  3 root root    4096 2008-12-30 19:56 grub
-rw-r--r--  1 root root 7465320 2008-12-01 07:41 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7465297 2008-12-01 07:41 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic

=============================== sda3/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2008-12-30 19:56 .
drwxr-xr-x 3 root root   4096 2008-12-30 19:56 ..
-rw-r--r-- 1 root root    197 2008-10-27 22:29 default
-rw-r--r-- 1 root root     15 2008-10-27 22:29 device.map
-rw-r--r-- 1 root root   8056 2008-10-27 22:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-27 22:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-27 22:29 installed-version
-rw-r--r-- 1 root root   8608 2008-10-27 22:29 jfs_stage1_5
-rw-r--r-- 1 root root   5351 2008-12-30 19:56 menu.lst
-rw-r--r-- 1 root root   5351 2008-12-30 19:56 menu.lst~
-rw-r--r-- 1 root root   5326 2008-10-29 04:30 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-27 22:29 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-27 22:29 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-29 04:30 splashimages
-rw-r--r-- 1 root root    512 2008-10-27 22:29 stage1
-rw-r--r-- 1 root root 108356 2008-10-27 22:29 stage2
-rw-r--r-- 1 root root   9276 2008-10-27 22:29 xfs_stage1_5

=========================== sdb5/boot/grub/menu.lst: ===========================

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
# color cyan/blue white/blue

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
# kopt=root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
makeactive
chainloader	+1
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=966762ae-7027-4f45-9724-ba2965cfa642 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ef275bbf-7102-4fba-8d94-10a1cc01388e none            swap    sw              0       0
# /dev/sdb4
UUID=977b2186-2a3c-4ae5-8419-a0a6a6453735 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 11796
drwxr-xr-x  3 root root      4096 2008-12-30 02:45 .
drwxr-xr-x 21 root root      4096 2008-12-30 02:45 ..
-rw-r--r--  1 root root    420224 2008-06-18 16:47 abi-2.6.24-19-generic
-rw-r--r--  1 root root     74164 2008-06-18 16:47 config-2.6.24-19-generic
drwxr-xr-x  3 root ubuntu    4096 2008-12-31 04:03 grub
-rw-r--r--  1 root ubuntu 8367867 2008-12-30 02:45 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root    103204 2007-09-28 11:03 memtest86+.bin
-rw-r--r--  1 root root   1152332 2008-06-18 16:47 System.map-2.6.24-19-generic
-rw-r--r--  1 root root   1903960 2008-06-18 16:47 vmlinuz-2.6.24-19-generic

=============================== sdb5/boot/grub: ===============================

total 228
drwxr-xr-x 3 root ubuntu   4096 2008-12-31 04:03 .
drwxr-xr-x 3 root root     4096 2008-12-30 02:45 ..
-rw-r--r-- 1 root ubuntu    197 2008-12-30 02:45 default
-rw-r--r-- 1 root ubuntu     30 2008-12-30 02:45 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-12-30 02:45 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-12-30 02:45 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-12-30 02:45 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-12-30 02:45 jfs_stage1_5
-rw-r--r-- 1 root root     6301 2008-12-31 04:03 menu.lst
-rw-r--r-- 1 root root     6327 2008-12-31 02:40 menu.lst~
-rw-r--r-- 1 root root     9080 2008-12-30 15:40 menu.lst.backup
-rw-r--r-- 1 root ubuntu   7324 2008-12-30 02:45 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-12-30 02:45 reiserfs_stage1_5
drwxr-xr-x 2 root root     4096 2008-12-30 15:40 splashimages
-rw-r--r-- 1 root ubuntu    512 2008-12-30 02:45 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-12-30 02:45 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-12-30 02:45 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading

---

### Post by ranch hand on 2008-12-31
Just been looking at my /boot/grub/menu.lst and see that the default setting is quite different in the 3 of them.  One is 0, one is 4 and the other 6.

Even to me this must be wrong.  This would have to boot you into something like recovery mode on at least one of those.

---

### Post by caljohnsmith on 2008-12-31
OK, thanks for posting that, it helps clear up things; one thing that is not clear though is which drive you are booting from, because both drives have Grub correctly installed to them. To know for sure, how about rebooting, and when you get the Grub menu on start up, press "c" to get the command line, and do:
```
grub> geometry (hd0)
```
That will show a list of your partitions. If the last partition it lists is type "type 0x82" you are booting the sda drive, or if the last partition it lists is "type 0x83", you are booting the sdb drive. Please let me know which drive you are booting and we can work from there.

---

### Post by ranch hand on 2008-12-31
Ok.  This will take a bit of time.  I am on the Live  CD and have to configure my dial up modem in pppconfig and then network manager to get it working to get back up.

---

### Post by ranch hand on 2008-12-31
I am booting on sdb.  grub> geometry is a new one to me, neet.

I ran that on (hd1) which is the external drive and got one result that was different from any on (hd0).  This was for "partition number 4   filesystem unknown  Partition type 0x82"  this should be the swap partition, I think.

---

### Post by caljohnsmith on 2008-12-31
OK, great, now we know which drive you are booting, so we should be able to get your Grub problems straightened out. So from your Live CD try:
```
sudo mount /dev/sdb5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change the "# groot=(hd1,4)" line to:
```
# groot=[COLOR="Blue"](hd0,4)[/COLOR]
```
And then change all your Ubuntu entries as highlighted in blue:
```
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root [COLOR="Blue"](hd0,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root [COLOR="Blue"](hd0,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root [COLOR="Blue"](hd0,4)[/COLOR]
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda1)
root [COLOR="Blue"](hd1,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd /boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda1)
root [COLOR="Blue"](hd1,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd /boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root [COLOR="Blue"](hd1,0)[/COLOR]
kernel /boot/memtest86+.bin
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda3)
root [COLOR="Blue"](hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet
initrd /boot/initrd.img-2.6.24-22-generic
savedefault
makeactive
chainloader +1
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root [COLOR="Blue"](hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd /boot/initrd.img-2.6.24-22-generic
savedefault
boot



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root [COLOR="Blue"](hd1,2)[/COLOR]
kernel /boot/memtest86+.bin
savedefault
boot


```
Reboot, and I think you should be all set. Let me know how it goes or if you run into problems.

---

### Post by ranch hand on 2008-12-31
ubuntu@ubuntu:~$ sudo mount /devsdb5 /mnt
mount: special device /devsdb5 does not exist

I could sudo nautilus and access the files directly on that install.

---

### Post by caljohnsmith on 2008-12-31
> **ranch hand said:**
> ubuntu@ubuntu:~$ sudo mount /[COLOR="Blue"]devsdb5[/COLOR] /mnt
mount: special device /devsdb5 does not exist

I could sudo nautilus and access the files directly on that install.
Looks like you have a small typo, there should be a / between dev and sdb5 like:
```
sudo mount /dev/sdb5 /mnt
```
Please try again.

---

### Post by ranch hand on 2008-12-31
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004630f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18209   146263761   83  Linux
/dev/sda2           37778       38913     9124920    5  Extended
/dev/sda3   *       18210       24583    51199155   83  Linux
/dev/sda4           24584       37777   105980805   83  Linux
/dev/sda5           37778       38913     9124888+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1           11573       21579    80381227+  83  Linux
/dev/sdf2               1       11572    92952058+  83  Linux
/dev/sdf3           21580       38150   133106557+   5  Extended
/dev/sdf4           38151       38913     6128797+  82  Linux swap / Solaris
/dev/sdf5           21580       38150   133106526   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-31
For some reason your device names are changing, so instead do:
```
sudo mount /dev/sdf5 /mnt
```
And then do the gedit command from the previous post.

---

### Post by ranch hand on 2008-12-31
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
mount: special device /dev/sdb5 does not exist

This is actually mounted as 136.3 GB Media on the desktop right now.

I will unmount and try comand again.

Nope, same result.

---

### Post by ranch hand on 2008-12-31
That worked and I edited the file.  I will try rebooting to see if there is any change.

A side question.  Why gksudo gedit instead of sudo gedit?

---

### Post by ranch hand on 2008-12-31
I am on my primary installation!  Happy happy.  I booted to it and the one on the external with no problem.  The one on sda3 still won't go.  I will check the menu.lst file on the external (where we boot from) later.

I need to do some ranch stuff.

I would really like to have some expaination for what we have done here.  The reason for all these installs is to learn.  I have another partition on this HDD that I intend to put OSlinux on and the external is planned to have Intrepid on it.

I have been reading, as you know, here on the forums.  I, as a long time MS user should be complaining about the difficulties of using Linux/Ubuntu.  I love it.  I think MS went straight down hill after 98.

Yes Vista would do more.  I was amazed by the fact that this box, designed for Vista, ran faster on the 8.04.1 Live CD than it ever did under Vista.

I kept 98 going for 10 years on our old computer and concider myself a "power" user of 98.  I will finish the recovery of that machine.

It just won't do things well now, just too old and out of date.

Ubuntu will and I want to get as good as I can, as fast as I can on running this OS and Linux in general.

You have been a great help and basically saved my butt.  I really need this install, it is what we use.

I will be back later with an update on the sda3 deal.  Probably next year (tommorow evening).

Happy New Year.
Tom

---

### Post by ranch hand on 2008-12-31
I may, at some time try the super grub stuff and I believe there may be another simular thing.  What I want is to know how to do it without too much 3rd party intervention in the way of software.

Thanks for all the info.

---

### Post by caljohnsmith on 2008-12-31
Glad to hear that worked OK; to answer your questions, one should use "gksudo" rather than "sudo" when you run any GUI program (like gedit), because gksudo sets up the environment correctly so that none of your hidden system files in your home directory become owned by the root user for example. And to explain what we did, the main thing was to determine which of your HDDs you were booting on start up, because that HDD would be (hd0) to Grub. In other words, Grub sees the order of drives on start up as the same as the BIOS boot order, not how the drives are ordered as /dev/sd* when you boot into Ubuntu. So when you ran that "geometry" command on start up to see what partitions (hd0) had, you said it showed the last partition being of type "83" which is a linux partition, and your sdb drive is the one where the last partition is linux. Therefore, you must be booting the sdb drive. And since you only have one other drive, your sda drive then would be (hd1). That means all your menu.lst entries for the Ubuntu on your sdb drive must use (hd0) and not (hd1), because you are booting the sdb drive which makes it (hd0). Also that means your Ubuntu entries for the sda drive must use (hd1). 

Anyway, if you need any further help booting your Ubuntu installs from the sda drive, let me know; otherwise cheers and have a great New Year. :)

---

### Post by ranch hand on 2008-12-31
I am back this year.  Had a problem with the input control interface with the tech bovines that are compiling new kernals.  The pregnant buggers busted the fence to the hay corral.  So I am here for another little while to relax before joining my better half in town.

Broadus is 54 miles on rough roads, a little more than 1.5 hours drive in this weather.  We get mail 3 times a week.  We do not get DSL.

I checked the menu.lst file on the sda3 install.  Had 2 extra entries: makeactive and chainload +1.  I am on that install now.  I know how those got there.  The biggest threat to the security of this box struck again.  Yep, I put them there.  I took them off.  It works.

I had to gksudo gedit to get it to work, by the way.  When I tried sudo gedit it hung and then came up blank.  I guess I see the point now.

And I will be back with some more grub stuff.  As you may have guessed I am interested in chainloading.  I'll be starting a thread on that when I get up the gumption.  Definately next year.

Thanks again.

---

