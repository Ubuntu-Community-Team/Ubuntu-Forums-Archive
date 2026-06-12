---
title: "Grub error 22, fix does not work"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by nonpareilpearl on 2009-04-10
After I fixed my cmos checksum error (new battery :)), I have encountered another error: grub error 22

I believe I last updated to Ibex, but I don't really recall. Currently I'm using a Heron live cd.

I used the solution here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This is the output:
```
find /boot/grub/stage1
(hd0,0)
(hd0,1)
```

This is not too surprising since the last time I encountered a grub error I simply installed Ubuntu on another partition (of the same hard disk, as you can see).

I have now tried h0,0 and h0,1 but to no avail. Here is the output from each:
```
root (hd0,1)

setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

And:
root (hd0,0)

setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

Is there any other way to resolve grub error 22, or do I need to do a fresh install? To clarify I tried h0,1 first but when I rebooted I still got error 22 so then I tried hd0,0 - I didn't try them both in the same session.

---

### Post by nonpareilpearl on 2009-04-11
Bump?

---

### Post by meierfra. on 2009-04-11
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by nonpareilpearl on 2009-04-13
So far I've tried a couple of things to no avail.

To backtrack a bit before when I had the cmos error after I just let it restore everything to default my computer would try to boot, it just wouldn't get past POST. It would show the BIOS screen and will show all my hard drives attached, it just won't complete the boot process. I was hoping nothing happened to my mobo, so I borrowed a friend's 80G hard drive and was able to install and run Ubuntu off it with no problems (no other hard drives attached). So I then figured that it was my issue, and returned his drive and started trying to figure out what was going on with my installation.

I don't remember if it was shortly before or after, but around the time of the battery change I started to receive Grub error 22 (this was after, but not immediately after, the test I did with my friend's disk). That's when I started investigating the solution I posted above before giving up and trying to boot off USB with Damn Small Linux (still received Grub error 22).

So I finally borrowed another disk (this time I got a 500G Hitachi, but mine are all WD and are 750G, 250G, and 160G although I do not know which models off the top of my head). I was able to see all the hard drives, again, using the Live CD. I even played around and formatted/partitioned the 500G hard drive successfully. Then I went ahead and tried to install Ubuntu to this disk - and it seemed to install successfully. I tried to reboot again. This time no error, just hangs at some point during POST after I see the portion of the BIOS screen that tells me which hard drives are connected (and it sees them all).

I used the Live CD to run the script as you indicated using my USB device. The only currently connected drives are the 160G, 500G, 750G (I only have 3 SATA cables).

Although this setup has worked for a few years now with some minor modifications (originally just th 250G drive after I built it in 2006, then I added the 160G and 750G drives in 2007 and 2008 respectively) I'm worried that something has happened to some piece of hardware. The most significant change of merit happened earlier this year when I migrated all my hardware to a new case and power supply (Antec 900, OCZ 500W). Shortly before that I also moved to a new apartment (I indicated this in a previous post about the cmos error I believe). Right now I am worried that something in the move physically damaged the mobo/hard drives or if something else completely is going on. I know that the graphics card and processor are working fine as I have been using the Live CD continueously throughout this ordeal with no problems.

I'm out of ideas. Help :(

---

### Post by nonpareilpearl on 2009-04-13
I saw that there was a message that said my file was too large, so I am including it in the body of this message:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader? is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 204796620.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d39fe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247  83 Linux
/dev/sda2         102,398,310   204,796,619   102,398,310  83 Linux
/dev/sda3         204,796,620   317,444,399   112,647,780   b W95 FAT32
/dev/sda4         317,444,400   321,669,494     4,225,095  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003d07c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   970,711,559   970,711,497  83 Linux
/dev/sdb2         970,711,560   976,768,064     6,056,505   5 Extended
/dev/sdb5         970,711,623   976,768,064     6,056,442  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00078e52

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8019 MB, 8019509248 bytes
45 heads, 45 sectors/track, 7734 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf07d55cc

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               8,064    15,663,103    15,655,040   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="dd5ec778-d911-446c-baea-382d8b0d4e2f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="2c3edcd0-962a-47b2-b0ba-6243ccdf1556" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="4614-15BF" TYPE="vfat" 
/dev/sda4: UUID="15ff1f49-b9de-45f8-9a7d-7e7e7fafde61" TYPE="swap" 
/dev/sdb1: UUID="a262c721-c0a2-4ecb-a33c-81ce6dad5c51" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e8a5fd30-e4b9-43ad-b451-2b3edec45cc5" TYPE="swap" 
/dev/sdc1: UUID="471B-BB09" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdd1: LABEL="PATRIOT" UUID="CF99-7566" TYPE="vfat" 

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
/dev/sdd1 on /media/PATRIOT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=dd5ec778-d911-446c-baea-382d8b0d4e2f ro
# kopt_2_6=root=/dev/sdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd5ec778-d911-446c-baea-382d8b0d4e2f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3AE80183E8013E9F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=B0B446C7B4468FB0 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=781285A96AC28A7F /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=4614-15BF  /media/sdb3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=f1699c12-4cc2-4a25-be1c-3faa9dfc6483 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.7GB: boot/grub/menu.lst
   3.6GB: boot/grub/stage2
   3.7GB: boot/initrd.img-2.6.17-10-generic
   3.6GB: boot/initrd.img-2.6.17-11-generic
   3.7GB: boot/vmlinuz-2.6.17-10-generic
   3.7GB: boot/vmlinuz-2.6.17-11-generic
   3.6GB: initrd.img
   3.7GB: initrd.img.old
   3.7GB: vmlinuz
   3.7GB: vmlinuz.old

=========================== sda2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.17-12-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu 7.10, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet

title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3AE80183E8013E9F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=B0B446C7B4468FB0 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=dd5ec778-d911-446c-baea-382d8b0d4e2f /media/sdb1     ext3    defaults        0       2
# /dev/sdb3
UUID=4614-15BF  /media/sdb3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=471B-BB09  /media/sdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=15ff1f49-b9de-45f8-9a7d-7e7e7fafde61 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
=================== sda2: Location of files loaded by Grub: ===================


  61.7GB: boot/grub/menu.lst
  61.7GB: boot/grub/stage2
  61.1GB: boot/initrd.img-2.6.17-10-generic
  61.2GB: boot/initrd.img-2.6.17-12-generic
  61.2GB: boot/initrd.img-2.6.17-12-generic.bak
  61.2GB: boot/initrd.img-2.6.20-16-generic
  61.3GB: boot/initrd.img-2.6.20-16-generic.bak
  61.2GB: boot/initrd.img-2.6.22-14-generic
  61.3GB: boot/initrd.img-2.6.22-14-generic.bak
  61.2GB: boot/vmlinuz-2.6.17-10-generic
  61.2GB: boot/vmlinuz-2.6.17-12-generic
  61.1GB: boot/vmlinuz-2.6.20-16-generic
  61.3GB: boot/vmlinuz-2.6.22-14-generic
  61.2GB: initrd.img
  61.2GB: initrd.img.old
  61.3GB: vmlinuz
  61.1GB: vmlinuz.old

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
# kopt=root=UUID=a262c721-c0a2-4ecb-a33c-81ce6dad5c51 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a262c721-c0a2-4ecb-a33c-81ce6dad5c51 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a262c721-c0a2-4ecb-a33c-81ce6dad5c51 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sdb1 ro single 
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.20-16-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.17-12-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single 
initrd		/boot/initrd.img-2.6.17-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.17-10-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=2c3edcd0-962a-47b2-b0ba-6243ccdf1556 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 7.10, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a262c721-c0a2-4ecb-a33c-81ce6dad5c51 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=e8a5fd30-e4b9-43ad-b451-2b3edec45cc5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  36.3GB: boot/grub/menu.lst
  36.2GB: boot/grub/stage2
  36.2GB: boot/initrd.img-2.6.24-19-generic
  36.3GB: boot/vmlinuz-2.6.24-19-generic
  36.2GB: initrd.img
  36.3GB: vmlinuz
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sdc1: device is busy
umount: /tmp/BootInfo/sdc1: device is busy

```

---

### Post by meierfra. on 2009-04-13
Looks like, grub is pointing to the wrong hard drive. So you need to reinstall grub:

Boot from the LiveCD, open a terminal and type

```
sudo grub
```

and at the "grub>"  prompt

```
root (hd1,0)
setup (hd1)
quit
```

You also need to edit menu.lst


```
sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```

Change 

# groot=(hd1,0)

to

# groot=(hd0,0)

and  change all (there are three of them) 

root (hd1,0)

to 

root (hd0,0)

Save the file.
Reboot, but  set your bios to boot from  your 500GB Ubuntu 8.04 drive /dev/sdb

---

### Post by nonpareilpearl on 2009-04-14
Thank you for the response! I am at work now but I will try this when I get home for lunch in a few hours.

On a side note, GRUB is really beginning to irritate me with the various error issues I've had in the past (usually requiring me to reinstall/repair the whole installation and potentially lose data - one of those was my fault when I just added a hard drive and didn't think there would be an issue). I was wondering if there was any way to either use a different boot loaders (the only other one I saw was when I was trying to boot from USB with DSL, called [SYSLINUX]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX"), is for those using an MSDOS/FAT filesystem - which I'm not). I thought it may be useful if I could somehow repair *just* GRUB (the fix I mentioned in my first post never worked for me, but now I'm out of free partitions to install Ubuntu to so I really wanted to backup my data first).

---

### Post by nonpareilpearl on 2009-04-14
The fix worked beautifully, thank you!!!! Now I'm going to disconnect my friend's drive, reformat my boot drive (what seems to be continuously labeled as hd0), partition and install Ubuntu - here's to hoping it all goes well.

Thanks again!

---

### Post by meierfra. on 2009-04-14
> The fix worked beautifully, thank you!!!!

Great.
 
> reformat my boot drive (what seems to be continuously labeled as hd0), 

Grub, during booting, uses the boot priority order. So the boot drive is always (hd0), the second drive in the boot order is (hd1) and so on.

---

### Post by nonpareilpearl on 2009-04-16
Makes sense, I'll look into it more. Here's something I noticed after I was able to (finally :D) boot - although on my list of available options I had the latest install, as well a the previous two installs of Ubuntu (6.10, 7.10), I was only able to boot into the frest install. When I tried the other two I was given errors 17 and 15 and was able to return to the boot list. I was still able to access the 160G HD (had both versions on it), but I am curious as to what caused this problem (so I know whether or not I should be looking for something similar with my XP installation on the 250G HD).

---

### Post by meierfra. on 2009-04-16
> I had the latest install, as well a the previous two installs of Ubuntu (6.10, 7.10), I was only able to boot into the frest install.


You have to edit menu.lst. Since you are bootin  from /dev/sdb, /dev/sdb is (hd0).

So /dev/sda is now (hd1), (hd2) or (hd3), depending whether /dev/sda is second, third or fourthed in the boot order in the bios.

Lets's say  /dev/sda is (hd1).

Then  you have to change

title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sda1)
root		(hd0,0)

to

title		Ubuntu, kernel 2.6.17-11-generic (on /dev/sda1)
root		(hd1,0)


and 


title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda2)
root		(hd0,1)

to

title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda2)
root		(hd1,1)

Of course if /dev/sda is (hd2) you'll have to use "root (2,0)" and "root (hd2,1)"  and if /dev/sda is (hd3) then ...



To figure out whether /dev/sda1 is (hd1), (hd2) or (hd3), you could either just try out the various possibilities for ""root (hd?,?)" and see which one works, or your can press "c" at the grub menu at boot up and type:

```
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
```

This will list all the partitions on your various drives, and you should be able to figure out which one is what.

---

### Post by nonpareilpearl on 2009-04-20
Thanks for all the info! I don't remember having all these complications for my previous installs of Ubuntu (and Windows). I am about to reconnect my 250G HDD (with Windows) and wipe the 160G clean to install just Ubuntu (or, potentially, a Windows and an Ubuntu partition). In the past when I was working with version 6.10 an 7.10 I recall I just installed Windows first and then installed Ubuntu and everything worked fine. Will it be the same for Hardy, or will I need to menu.lst?

---

