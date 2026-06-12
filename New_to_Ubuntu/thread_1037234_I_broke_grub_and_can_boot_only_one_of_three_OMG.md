---
title: "I broke grub and can boot only one of three OMG"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by ranch hand on 2009-01-11
I decided to look at super grub disk.  Downloaded it.  Put in CDrom.  Rebooted.

This was a big mistake.  I read the help page and looked at the menus.  Pulled the CD being very happy that it booted and seemed to be all there.

Now just about everything in my boot up is screwed.  One partition with an install on it is not is fstab.  I can read the file system on all three installs.

fdisk lists all three and claims only the one not in fstab boots.  I am not booting from there.

I have to go to town tonight but will be back sometime tomorrow to move cows to corrals for shipping.  I will then give any particulars folks want.

There seems so much out of whack that I am glad I got this, my primary to boot.  Had to use the LiveCD to do that.

---

### Post by caljohnsmith on 2009-01-11
Hi Ranch Hand, in order to figure out how Super Grub modified your booting process, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your current booting problem might be. Also, please let me know which of your Ubuntu installs you want to control the booting process on start up, and we can work from there if you want. :)

---

### Post by ranch hand on 2009-01-11
Caljohnsmith I just got in from chasing cows and fixing fence.  Have to leave for town, will do that tomorrow.

There really is no # here at all.   I had no idea that there should be until you mentioned it the other day.  I have no idea why I don't have one.  I am running FF 3.0.5.
Where on the page is this mythical beast supposed to reside?

I have cute religious symbols, I can manage attachments, I can read the last posts, I can read the rules for the thread.  I can't see a #.

I'd send screenshots but I really have to go.

---

### Post by caljohnsmith on 2009-01-11
How about taking a look at the screen shot from this post, Ranch Hand:

[http://ubuntuforums.org/showpost.php?p=6479234](http://ubuntuforums.org/showpost.php?p=6479234)

Does it look like that in your web browser?

---

### Post by ranch hand on 2009-01-12
In short, no.

Everything on the screen shot is simular except the text box.  All I get is a blank text box.

---

### Post by caljohnsmith on 2009-01-12
> **ranch hand said:**
> In short, no.

Everything on the screen shot is simular except the text box.  All I get is a blank text box.
Are you using the "quick reply" message box at the bottom of the thread? If so, that would explain why you don't have the code tags graphic # symbol in your message box. Try clicking the "New Reply" button at the bottom left of the thread, and you should get a reply dialog box with all the features. Let me know how that goes.

---

### Post by ranch hand on 2009-01-12
I checked my CP/ options.  I had it set for basic, which is quite a bit faster to load.  I changed it and there the little bugger is.

I set those when the connection was even slower than it is now.  Winmodem under Vista would do 2.9Kb on a real good day.  Never looked at it again.

This modem, by the way, would do 3.9KB on an average day under Vista with all the drivers, etc.  With nothing added to it, it goes at 4.1Kb to 4.4Kb on average days under Ubuntu.

---

### Post by ranch hand on 2009-01-12
I have a few minutes so back to business.  Why do I need to boot from the live CD?

---

### Post by caljohnsmith on 2009-01-12
> **ranch hand said:**
> I have a few minutes so back to business.  Why do I need to boot from the live CD?
My mistake, I didn't notice where you mentioned you can boot into your primary Ubuntu install. It's fine to run the script from there if you want. So are you just having problems booting into your two other Ubuntu installs right now?

---

### Post by Elfy on 2009-01-12
You can turn your cp back to basic - ther are just a few basic BB codes which will get you by, you put one at the beginning of any portion of text and the other at the end.

I rarely use the tools to do it to be honest

[noparse]```
[/noparse] and [noparse]
```[/noparse] puts a code box around text


[noparse]> [/noparse] and [noparse][/noparse] puts a quote box around text

[noparse]**[/noparse] and [noparse]**[/noparse] for bold

[noparse]_[/noparse] and [noparse]_[/noparse] for underline

[noparse]*[/noparse] and [noparse]*[/noparse] for italic

---

### Post by ranch hand on 2009-01-12
I can boot into my primary by editing the menu from hd1,0 to hd0,0.  This does indicate that I am probably booting from that HDD and probably sda3.

This morning when I booted up the menu had 2 entries and I edited the other and got into the install on sda3.  When I rebooted, there was 1 entry and I did not have to edit to have it boot to here (sda1).

---

### Post by ranch hand on 2009-01-12
I tried posting the results;
# first
# last
# first and last
[code][code] last
[code][code] first
(code)(code) last
(code)(code) first
[code][code] first and last
[code] first and [code] last
etc
Get error that there are too many images in post must correct them.

I will post it in 2 parts straight post.

---

### Post by ranch hand on 2009-01-12
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda1 
                       and looks at sector 305807 of the same hard drive for 
                       the stage2 file and on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda3 
                       and looks at sector 295935473 of the same hard drive 
                       for the stage2 file and on partition #3 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
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
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdb5 
                       and looks at sector 436483786 of the same hard drive 
                       for the stage2 file and on partition #5 for 
                       /boot/grub/menu.lst.
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

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5 on /media/disk-2 type ext2 (rw,nosuid,nodev,uhelper=hal)

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
default         0

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
# kopt=root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,04)

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
# defoptions=quiet vga=773

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
savedefault
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

---

### Post by ranch hand on 2009-01-12
=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=ef275bbf-7102-4fba-8d94-10a1cc01388e  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdf5                                  /media/sdf5    ext2         defaults                    0  0  
/dev/sdf2                                  /media/sdf2    ext2         defaults                    0  0  
/dev/sdf1                                  /media/sdf1    ext2         defaults                    0  0  

================================== sda1/boot: ==================================

total 18356
drwxr-xr-x  3 root root    4096 2009-01-10 22:02 .
drwxr-xr-x 21 root root    4096 2009-01-10 22:02 ..
-rw-r--r--  1 root root  422838 2008-11-27 15:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80051 2008-11-27 15:13 config-2.6.24-23-generic
drwxr-xr-x  3 root  999    4096 2009-01-11 03:24 grub
-rw-r--r--  1 root root 7783580 2009-01-09 19:00 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7502860 2009-01-09 18:45 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 04:06 memtest86+.bin
-rw-r--r--  1 root root  905633 2008-11-27 15:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1921976 2008-11-27 15:13 vmlinuz-2.6.24-23-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 3 root  999   4096 2009-01-11 03:24 .
drwxr-xr-x 3 root root   4096 2009-01-10 22:02 ..
-rw-r--r-- 1 root  999      9 2008-10-27 17:25 default
-rw-r--r-- 1 root  999     15 2008-10-18 21:49 device.map
-rw-r--r-- 1 root  999   8056 2008-10-18 21:49 e2fs_stage1_5
-rw-r--r-- 1 root  999   7904 2008-10-18 21:49 fat_stage1_5
-rw-r--r-- 1 root  999     16 2008-10-18 21:49 installed-version
-rw-r--r-- 1 root  999   8608 2008-10-18 21:49 jfs_stage1_5
-rw-r--r-- 1 root root   4321 2009-01-11 03:24 menu.lst
-rw-r--r-- 1 root root   4320 2009-01-11 02:14 menu.lst~
-rw-r--r-- 1 root root   5088 2008-11-01 21:18 menu.lst.backup
-rw-r--r-- 1 root  999   7324 2008-10-18 21:49 minix_stage1_5
-rw-r--r-- 1 root  999   9632 2008-10-18 21:49 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-01 21:18 splashimages
-rw-r--r-- 1 root  999    512 2008-10-18 21:49 stage1
-rw-r--r-- 1 root  999 108356 2008-10-18 21:49 stage2
-rw-r--r-- 1 root  999   9276 2008-10-18 21:49 xfs_stage1_5

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
savedefault
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd1,0)
kernel		/boot/memtest86+.bin 
savedefault 
savedefault
boot


=============================== sda3/etc/fstab: ===============================

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
drwxr-xr-x  3 root root    4096 2008-12-30 12:56 .
drwxr-xr-x 21 root root    4096 2008-12-30 12:56 ..
-rw-r--r--  1 root root  422838 2008-11-24 15:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80062 2008-11-24 15:47 config-2.6.24-22-generic
drwxr-xr-x  3 root root    4096 2009-01-11 01:33 grub
-rw-r--r--  1 root root 7465320 2008-12-01 00:41 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7465297 2008-12-01 00:41 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 04:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-11-24 15:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921176 2008-11-24 15:47 vmlinuz-2.6.24-22-generic

=============================== sda3/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2009-01-11 01:33 .
drwxr-xr-x 3 root root   4096 2008-12-30 12:56 ..
-rw-r--r-- 1 root root    197 2008-10-27 16:29 default
-rw-r--r-- 1 root root     15 2008-10-27 16:29 device.map
-rw-r--r-- 1 root root   8056 2008-10-27 16:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-27 16:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-27 16:29 installed-version
-rw-r--r-- 1 root root   8608 2008-10-27 16:29 jfs_stage1_5
-rw-r--r-- 1 root root   5396 2009-01-11 01:33 menu.lst
-rw-r--r-- 1 root root   5329 2009-01-08 20:45 menu.lst~
-rw-r--r-- 1 root root   5326 2008-10-28 22:30 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-27 16:29 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-27 16:29 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-28 22:30 splashimages
-rw-r--r-- 1 root root    512 2008-10-27 16:29 stage1
-rw-r--r-- 1 root root 108356 2008-10-27 16:29 stage2
-rw-r--r-- 1 root root   9276 2008-10-27 16:29 xfs_stage1_5

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
default		saved

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
makeactive
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro single
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
quiet
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root		(hd1,2)
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

total 19220
drwxr-xr-x  3 root root    4096 2009-01-10 20:28 .
drwxr-xr-x 22 root root    4096 2009-01-05 12:05 ..
-rw-r--r--  1 root root  420395 2008-11-24 15:19 abi-2.6.24-22-generic
-rw-r--r--  1 root root   74177 2008-11-24 15:19 config-2.6.24-22-generic
drwxr-xr-x  3 root root    4096 2009-01-11 03:00 grub
-rw-r--r--  1 root root 7974024 2009-01-10 20:28 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7976909 2009-01-09 12:51 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 05:03 memtest86+.bin
-rw-r--r--  1 root root 1153201 2008-11-24 15:19 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1905656 2008-11-24 15:19 vmlinuz-2.6.24-22-generic

=============================== sdb5/boot/grub: ===============================

total 228
drwxr-xr-x 3 root root   4096 2009-01-11 03:00 .
drwxr-xr-x 3 root root   4096 2009-01-10 20:28 ..
-rw-r--r-- 1 root root    197 2008-12-29 19:45 default
-rw-r--r-- 1 root root     30 2008-12-29 19:45 device.map
-rw-r--r-- 1 root root   8056 2008-12-29 19:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-29 19:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 19:45 installed-version
-rw-r--r-- 1 root root   8608 2008-12-29 19:45 jfs_stage1_5
-rw-r--r-- 1 root root   6296 2009-01-11 03:00 menu.lst
-rw-r--r-- 1 root root   6292 2009-01-11 02:10 menu.lst~
-rw-r--r-- 1 root root   9080 2008-12-30 08:40 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-12-29 19:45 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-29 19:45 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-30 08:40 splashimages
-rw-r--r-- 1 root root    512 2008-12-29 19:45 stage1
-rw-r--r-- 1 root root 108356 2008-12-29 19:45 stage2
-rw-r--r-- 1 root root   9276 2008-12-29 19:45 xfs_stage1_5

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

### Post by Elfy on 2009-01-12
heh - my fault forgot the / on the last code tag - it's there now, you can edit the post if you want put them in at beginning and end and see how much difference it makes to a post size :)

---

### Post by ranch hand on 2009-01-12
```
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Drive sdf does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda1 
                       and looks at sector 305807 of the same hard drive for 
                       the stage2 file and on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sda3 
                       and looks at sector 295935473 of the same hard drive 
                       for the stage2 file and on partition #3 for 
                       /boot/grub/menu.lst .
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
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
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdb5 
                       and looks at sector 436483786 of the same hard drive 
                       for the stage2 file and on partition #5 for 
                       /boot/grub/menu.lst.
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

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5 on /media/disk-2 type ext2 (rw,nosuid,nodev,uhelper=hal)

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
default         0

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
# kopt=root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,04)

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
# defoptions=quiet vga=773

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
savedefault
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=ef275bbf-7102-4fba-8d94-10a1cc01388e  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdf5                                  /media/sdf5    ext2         defaults                    0  0  
/dev/sdf2                                  /media/sdf2    ext2         defaults                    0  0  
/dev/sdf1                                  /media/sdf1    ext2         defaults                    0  0  

================================== sda1/boot: ==================================

total 18356
drwxr-xr-x  3 root root    4096 2009-01-10 22:02 .
drwxr-xr-x 21 root root    4096 2009-01-10 22:02 ..
-rw-r--r--  1 root root  422838 2008-11-27 15:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80051 2008-11-27 15:13 config-2.6.24-23-generic
drwxr-xr-x  3 root  999    4096 2009-01-11 03:24 grub
-rw-r--r--  1 root root 7783580 2009-01-09 19:00 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7502860 2009-01-09 18:45 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 04:06 memtest86+.bin
-rw-r--r--  1 root root  905633 2008-11-27 15:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1921976 2008-11-27 15:13 vmlinuz-2.6.24-23-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 3 root  999   4096 2009-01-11 03:24 .
drwxr-xr-x 3 root root   4096 2009-01-10 22:02 ..
-rw-r--r-- 1 root  999      9 2008-10-27 17:25 default
-rw-r--r-- 1 root  999     15 2008-10-18 21:49 device.map
-rw-r--r-- 1 root  999   8056 2008-10-18 21:49 e2fs_stage1_5
-rw-r--r-- 1 root  999   7904 2008-10-18 21:49 fat_stage1_5
-rw-r--r-- 1 root  999     16 2008-10-18 21:49 installed-version
-rw-r--r-- 1 root  999   8608 2008-10-18 21:49 jfs_stage1_5
-rw-r--r-- 1 root root   4321 2009-01-11 03:24 menu.lst
-rw-r--r-- 1 root root   4320 2009-01-11 02:14 menu.lst~
-rw-r--r-- 1 root root   5088 2008-11-01 21:18 menu.lst.backup
-rw-r--r-- 1 root  999   7324 2008-10-18 21:49 minix_stage1_5
-rw-r--r-- 1 root  999   9632 2008-10-18 21:49 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-11-01 21:18 splashimages
-rw-r--r-- 1 root  999    512 2008-10-18 21:49 stage1
-rw-r--r-- 1 root  999 108356 2008-10-18 21:49 stage2
-rw-r--r-- 1 root  999   9276 2008-10-18 21:49 xfs_stage1_5

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
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
savedefault
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd1,0)
kernel		/boot/memtest86+.bin 
savedefault 
savedefault
boot


=============================== sda3/etc/fstab: ===============================

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
drwxr-xr-x  3 root root    4096 2008-12-30 12:56 .
drwxr-xr-x 21 root root    4096 2008-12-30 12:56 ..
-rw-r--r--  1 root root  422838 2008-11-24 15:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   80062 2008-11-24 15:47 config-2.6.24-22-generic
drwxr-xr-x  3 root root    4096 2009-01-11 01:33 grub
-rw-r--r--  1 root root 7465320 2008-12-01 00:41 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7465297 2008-12-01 00:41 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 04:06 memtest86+.bin
-rw-r--r--  1 root root  905617 2008-11-24 15:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1921176 2008-11-24 15:47 vmlinuz-2.6.24-22-generic

=============================== sda3/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2009-01-11 01:33 .
drwxr-xr-x 3 root root   4096 2008-12-30 12:56 ..
-rw-r--r-- 1 root root    197 2008-10-27 16:29 default
-rw-r--r-- 1 root root     15 2008-10-27 16:29 device.map
-rw-r--r-- 1 root root   8056 2008-10-27 16:29 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-27 16:29 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-27 16:29 installed-version
-rw-r--r-- 1 root root   8608 2008-10-27 16:29 jfs_stage1_5
-rw-r--r-- 1 root root   5396 2009-01-11 01:33 menu.lst
-rw-r--r-- 1 root root   5329 2009-01-08 20:45 menu.lst~
-rw-r--r-- 1 root root   5326 2008-10-28 22:30 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-27 16:29 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-27 16:29 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-28 22:30 splashimages
-rw-r--r-- 1 root root    512 2008-10-27 16:29 stage1
-rw-r--r-- 1 root root 108356 2008-10-27 16:29 stage2
-rw-r--r-- 1 root root   9276 2008-10-27 16:29 xfs_stage1_5

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
default		saved

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
makeactive
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro single
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
quiet
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root		(hd1,2)
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

total 19220
drwxr-xr-x  3 root root    4096 2009-01-10 20:28 .
drwxr-xr-x 22 root root    4096 2009-01-05 12:05 ..
-rw-r--r--  1 root root  420395 2008-11-24 15:19 abi-2.6.24-22-generic
-rw-r--r--  1 root root   74177 2008-11-24 15:19 config-2.6.24-22-generic
drwxr-xr-x  3 root root    4096 2009-01-11 03:00 grub
-rw-r--r--  1 root root 7974024 2009-01-10 20:28 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7976909 2009-01-09 12:51 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 05:03 memtest86+.bin
-rw-r--r--  1 root root 1153201 2008-11-24 15:19 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1905656 2008-11-24 15:19 vmlinuz-2.6.24-22-generic

=============================== sdb5/boot/grub: ===============================

total 228
drwxr-xr-x 3 root root   4096 2009-01-11 03:00 .
drwxr-xr-x 3 root root   4096 2009-01-10 20:28 ..
-rw-r--r-- 1 root root    197 2008-12-29 19:45 default
-rw-r--r-- 1 root root     30 2008-12-29 19:45 device.map
-rw-r--r-- 1 root root   8056 2008-12-29 19:45 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-29 19:45 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-29 19:45 installed-version
-rw-r--r-- 1 root root   8608 2008-12-29 19:45 jfs_stage1_5
-rw-r--r-- 1 root root   6296 2009-01-11 03:00 menu.lst
-rw-r--r-- 1 root root   6292 2009-01-11 02:10 menu.lst~
-rw-r--r-- 1 root root   9080 2008-12-30 08:40 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-12-29 19:45 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-29 19:45 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-30 08:40 splashimages
-rw-r--r-- 1 root root    512 2008-12-29 19:45 stage1
-rw-r--r-- 1 root root 108356 2008-12-29 19:45 stage2
-rw-r--r-- 1 root root   9276 2008-12-29 19:45 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading
/dev/sdf: No medium found

sfdisk: cannot open /dev/sdf for reading
```

---

### Post by ranch hand on 2009-01-12
That worked very nicely and I can use the plain box format.  This really is faster on this connection.

Thanks a bunch.

---

### Post by caljohnsmith on 2009-01-12
OK, so it looks like there are a few issues to take care of. How about trying the following:
```
sudo mount /dev/sda3 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change the menu.lst as follows:
```
title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root [COLOR="Blue"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet
initrd /boot/initrd.img-2.6.24-22-generic
savedefault
quiet

title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root [COLOR="Blue"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd /boot/initrd.img-2.6.24-22-generic
savedefault
title Ubuntu 8.04.1, memtest86+
root [COLOR="Blue"](hd0,2)[/COLOR]
kernel /boot/memtest86+.bin
savedefault
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sda1)
root [COLOR="Blue"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd /boot/initrd.img-2.6.24-23-generic
savedefault
quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root [COLOR="Blue"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd /boot/initrd.img-2.6.24-23-generic
savedefault


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root [COLOR="Blue"](hd0,0)[/COLOR]
kernel /boot/memtest86+.bin
savedefault
boot
```
Next you'll need to reinstall Grub to your sdb drive, because currently it is looking on sda1 for its boot files, when it should be looking on sdb5:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
If any of the commands return an error, please post the output. Otherwise go ahead and reboot, and let me know exactly what happens. We can work from there. :)

---

### Post by ranch hand on 2009-01-12
I can boot to the 2 on my internal HDD.  Can't to the 1 on the external.

I am set to boot from the CD, USB then HDD.

What worked before was to set the 2 on the HDD to (hd1,0) and (hd1,2).

I edited the file:

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash quiet
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
savedefault
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin 
savedefault 
savedefault
boot

```

When I booted grub was calling for these 2 at (hd1,0) and (hd1,2).  It worked and it matches the /boot/grub/menu.lst for sdb5 which I think should be (hd0,4).

---

### Post by caljohnsmith on 2009-01-12
OK, I thought you were booting the sdb drive on start up, because that's what we figured out in one of your [previous threads]("http://ubuntuforums.org/showthread.php?t=1026369&page=2"). I think we should check again just to make sure, so how about rebooting, and when you get the Grub menu, press "c" to get the Grub command line, and then do:
```
grub> geometry (hd0)
```
And that will show a list of your partitions. If the last partition it lists is type "type 0x82" you are booting the sda drive, or if the last partition it lists is "type 0x83", you are booting the sdb drive. Please let me know again which drive you are booting and we can work from there.

---

### Post by ranch hand on 2009-01-12
Well, that is neet, all 4 partitions are type 0x83 on (hd0) - sdb.

---

### Post by caljohnsmith on 2009-01-12
OK, so if you are booting the sdb drive on start up, you should be getting the menu.lst from sdb5. Did you run the Grub commands at the end of post #18? Just want to make sure they didn't return any errors. Also, part of the problem is it would help I think to change your menu.lst so that it makes reference to which install you are booting, because it is ambiguous right now. How about doing:
```
sudo umount /mnt
sudo mount /dev/sdb5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change the menu.lst as follows:
```
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic [COLOR="Blue"](on /dev/sdb5)[/COLOR]
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
makeactive
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic [COLOR="Blue"](on /dev/sdb5)[/COLOR] (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro single
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, [COLOR="Blue"](on /dev/sdb5)[/COLOR] memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
```
Then reboot, and try the entries above in the Grub menu, and let me know what happens. We can work from there.

---

### Post by ranch hand on 2009-01-12
Yes, I ran those and the /boot/grub/menu.lst shows it.

As for the /boot/grub/menu.lst for sdb5 (hd0,4), that is the way it reads now.

I am whipped and can't remember the error on boot for that install.  I will reboot and report.

---

### Post by ranch hand on 2009-01-12
An attempt to boot (hd0,4) results in;

Error 12 Invalid device requested.

---

### Post by caljohnsmith on 2009-01-12
OK, I think I finally found the problem:
```
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sdb5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=966762ae-7027-4f45-9724-ba2965cfa642 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
[COLOR="Red"]makeactive[/COLOR]
quiet

```
I didn't notice that you had the "makeactive" line in that entry; that unfortunately won't work because Grub can not set the boot flag (i.e. make the partition "active") on a logical partition, and sdb5 is a logical partition. How about removing the "makeactive" line from your sdb5 menu.lst, reboot, and then let me know what happens. We can work from there.

---

### Post by ranch hand on 2009-01-13
I actually have done that and tried to reboot.  Got this:

/etc/gdm/Xsession: Beginning session start up
setting IM through /etc/X11/xinit/xinput.d/all_ALL linked to
/etc/X11/xinit/xinput.d/default
mkd: private socket dir: Permission denied

That was after a notice that the session had lasted less than 10 seconds and there might be a problem if I hadn't loged out.

I tried a gnome session, same, a xscript session, same, what ever the others options are, same.

Rebooted in recovery and had some luck inthe repair files part but it wants to get all the recommended updates 88.4 Mb and I didn't have time to run that.

So I put makeactive back in until I have time to screw with that install again.

What the commands in post 18 have done is allow me to boot from sda3 if I turn off the external.  This is a good thing.

I would like to try and get a stable install on the external without having it mixxed with the installs on the HDD internal.  I thought I would just install on the external with the internal unplugged although this does screw up the clock (had to switch HDDs when setting up ubuntu so that I could use vista for internet).

I have learned a good deal about grub and the use of soft ware to fix problems that can be fixxed in terminal.  This is about the luck I had in MS with that.

The current problem, I may fix for the education, but I think another install is going to go on there.  I bought a sellection of discs from linuxCD ( beats trying to download a 4.4Kb).  Includes 8.10 and I may put that on there but there are 6 others.

I think I want another HDD.

Anyway, unless you think this crrent problem is related I am going to mark it solved as removing the makeactive did fix it as far as booting goes.

I thank you again.  I am sorry if I am rambling.  Very icey today and had to ship cattle.  What a day.  I'm whipped.

---

### Post by caljohnsmith on 2009-01-13
Glad to hear that the sdb5 install is at least booting from Grub now, although it's too bad you're having problems with that install. Good luck and take care.

---

### Post by ranch hand on 2009-01-13
I'll check tommorow on this thread and see if the thread tools menu is all there.  Solved is not currently an option and the thanks medalions are missing too.

They must have been down so long for a reason.

---

