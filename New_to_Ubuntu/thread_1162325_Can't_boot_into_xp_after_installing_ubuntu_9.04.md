---
title: "Can't boot into xp after installing ubuntu 9.04"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by bzzzzz on 2009-05-17
I've spent the weekend trying to clone my hard drive from a 40GB drive onto a 160GB drive.  On the original 40GB hard drive I have XP installed on the first partition and 8.04 installed on the second partition.  I've searched around the forum but have yet to discover a solution to my problem. 

I started off trying to use clonezilla to clone my hard drive, but the result didn't look much like my original hard drive and so I gave up on that and had a go at using the following tutorial and Gparted to clone the hard drive.

[http://ubuntuforums.org/showthread.php?t=302717](http://ubuntuforums.org/showthread.php?t=302717)

I even made the partitions for XP and 8.04 a little larger.  I'm going to use the rest of the hard drive to experiment with other operating systems.
Everything worked as described including the bit where I tried to boot but just got the flashing cursor.  I then followed the instructions to setup the grube on (hd0,1) and to my joy I could now boot into Windows XP.
The problems started when I tried to boot into my 8.04 - every time it came back with an Error 22, which I think means that the partition can't be found. 

After unsuccessfully playing around with the grub I decided to give up on that maybe the best option was to install 9.04 and then hopefully copy the files I wanted across. 

After installing 9.04 I get the option of booting either 8.04 or 9.04 (Windows had disappeared) and I can open either of the operating systems.  

I then found something on these forums which suggested changing the menu.lst file in the grub folder and adding 

title		Windows XP
root		(hd0,0)
saveddefault
makeactive
chainloader	+1

to the end of that file using gedit.

after doing this I then get an option on booting to get Windows XP.  When I click this it then gives me an option of booting either 8.04 or XP.  However when I select either of these I get an Error 15 message.  Which seems to suggest it can't find either of the boot files.  

I'll continue to try and sort this myself but I am at risk of going round in circles and would be grateful any help to point me in the right direction.

Thanks

---

### Post by starcannon on 2009-05-17
I think your going to need to run grub from the liveCD, at least this is how I would tackle it. If its okay I'll just post a link to a walk through (its the one I use when I need to do stuff similar to this)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I know its not exactly titled the same as your topic, but it should work for you anyway. Take a bit of time to read or at least skim the entire article, its a lot of info. Ultimately you need grub to know where everything is, and my guess is that windows is not located at 0,0 or something to that effect. 

GL

---

### Post by presence1960 on 2009-05-17
To get a better idea of your exact set up boot from the Live CD and download the Boot Info script to your desktop. Then open a terminal- Applications > Accessories > Terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the Desktop. Post the contents of that file here.

It would help if i gave you the link to download the script : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by ranch hand on 2009-05-17
The gparted tutorial that you used is a little out of date and used a gparted live cd.

Your live cd will do the job.

Grub can be straightened out.  Being as powerful as it is you do need to know what you are doing.

Do what presence1960 is asking you to do.  It will get all the info that is needed.

---

### Post by bzzzzz on 2009-05-18
Thanks for the help.  I'll give those things a bash this evening when I get home from work.

In the mean time I thought it important to point out a correction to the original post.  

I stated that when I selected Windows XP from the list I was then presented with the option of booting 8.04 or XP and that selection of these gave the error 15.  In actual fact selection of 8.04 gives the error 15 message, but selection of XP flashes up (I had to do this several times so that I could read it, it's only on the screen for a tenth of a second) "Starting Up .... GRUB Loading Stage 2" and then switches back to the menu offering 8.04 or XP.

Thanks again for the help and I'll try those things tonight.

---

### Post by bzzzzz on 2009-05-18
In the next post I have posted the Results.txt.


Before I post this I thought that I should say that I have managed to fix one of my issue.  

Previously I would be offered the following operating systems 9.04, 8.04 and Windows XP.  When selecting XP I would then get a second list of operating systems including 8.04 and Windows XP.  XP would say "Starting up ... GRUB Loading Stage2" for a fraction of a second then flip back to the menu offering me XP and 8.04.  If I selected 8.04 I would I would get an Error 15 message.  

I managed to find the boot/grub/menu.lst in the 8.04 partition and this seemed to be directing the 8.04 to (hd0,4).  I corrected this to read (hd0,1) and I can now boot from this second menu into 8.04.  

What I still can't do is get into XP

---

### Post by bzzzzz on 2009-05-18
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 44471926 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 44471926 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bb2e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750    88,068,329    47,102,580  83 Linux
/dev/sda3          88,068,330   312,576,704   224,508,375   5 Extended
/dev/sda5          88,068,393   139,267,484    51,199,092  83 Linux
/dev/sda6         303,355,458   312,576,704     9,221,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="91e45990-9567-4b18-81a3-7adc335cf0c8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="e5a84486-304f-4736-9b1f-b1fea409fe67" TYPE="swap" 

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
# kopt=root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
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


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=385cdeea-1d14-468d-8e6b-11cf23e59fa6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  22.8GB: boot/grub/menu.lst
  22.7GB: boot/grub/stage2
  22.6GB: boot/initrd.img-2.6.24-23-generic
  22.6GB: boot/initrd.img-2.6.24-23-generic.bak
  22.6GB: boot/initrd.img-2.6.24-24-generic
  22.6GB: boot/initrd.img-2.6.24-24-generic.bak
  22.6GB: boot/vmlinuz-2.6.24-23-generic
  22.6GB: boot/vmlinuz-2.6.24-24-generic
  22.6GB: initrd.img
  22.6GB: initrd.img.old
  22.6GB: vmlinuz
  22.6GB: vmlinuz.old

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
# kopt=root=UUID=91e45990-9567-4b18-81a3-7adc335cf0c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=91e45990-9567-4b18-81a3-7adc335cf0c8

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
uuid		91e45990-9567-4b18-81a3-7adc335cf0c8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=91e45990-9567-4b18-81a3-7adc335cf0c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		91e45990-9567-4b18-81a3-7adc335cf0c8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=91e45990-9567-4b18-81a3-7adc335cf0c8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		91e45990-9567-4b18-81a3-7adc335cf0c8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro single 
initrd		/boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro single 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04.2, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Windows XP
root		(hd0,0)
saveddefault
makeactive
chainloader	+1

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=91e45990-9567-4b18-81a3-7adc335cf0c8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e5a84486-304f-4736-9b1f-b1fea409fe67 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  67.4GB: boot/grub/menu.lst
  67.4GB: boot/grub/stage2
  67.5GB: boot/initrd.img-2.6.28-11-generic
  67.3GB: boot/vmlinuz-2.6.28-11-generic
  67.5GB: initrd.img
  67.3GB: vmlinuz

---

### Post by presence1960 on 2009-05-18
which GRUB menu comes up when you boot? Is it the one with 9.04 as first option or the one with 8.04 as the first option? The one with 9.04 would be better set up chainloading 8.04 this way when your kernels update there won't be a problem. Let's see which GRUB menu you get when you boot and then we'll try editing them.

I can see the problem with your 8.04 entries in the menu.lst from sda5. should be fixable.

---

### Post by presence1960 on 2009-05-18
I would change this in your sda5 menu.lst
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro quiet splash
initrd /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro single
initrd /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=7ac2330e-e0ff-4b26-8975-47ac8fe3f9ae ro single
initrd /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Ubuntu 8.04.2, memtest86+ (on /dev/sda2)
root (hd0,1)
kernel /boot/memtest86+.bin
savedefault
boot

title Windows XP
root (hd0,0)
saveddefault
makeactive
chainloader +1
```

to:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2

title           Hardy 8.04
rootnoverify    (hd0,1)
chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		Microsoft Windows XP 
rootnoverify	(hd0,0)
chainloader	+1
```

when you choose Hardy at boot it will bring up the menu.lst from sda2. This method will keep both menu.lst files up to date whenever you receive an updated kernel on either Hardy or Jaunty. You won't have to do editing after an update. Both Hardy's and Jaunty's menu.lst will be correct after a kernel update.

---

### Post by bzzzzz on 2009-05-19
The menu with 9.04 boots up first.

8.04 is no longer a problem.  It now boots from the first menu and the second.

The only problem is that windows doesn't appear in the first menu and doesn't do anything other than flash back to the second menu after a tenth of a second.

What I will try to do now is add the Windows option to my first menu as you have it, without the 

savedefault
makeactive 
 
and having the rootnoverify command in place of root.

---

### Post by bzzzzz on 2009-05-19
Ok I've copied and pasted the menu list as you describe.

It looks quite a bit neater now, with both hardy and xp switching back to my old menu list.

Problem remains that I get nowhere when I try to boot xp.

---

### Post by presence1960 on 2009-05-19
I didnt see this earlier but in the results.txt file you posted your Windows appears to be not right. Here is a snip from the top of my results.txt file:

```
 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

   

```

notice at the top for sda1 it has the OS info. Now look at your sda1 info:

```
=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________ _______________________

File system:
Boot sector type: Grub
Boot sector info: Grub0.97 is installed in the boot sector of sda1 and
looks at sector 44471926 of the same hard drive for
the stage2 file. A stage2 file is at this location on
/dev/sda. Stage2 looks on partition #2 for
/boot/grub/menu.lst.
Mounting failed:
mount: unknown filesystem type ''

sda2: __________________________________________________ _______________________



```

you have a problem with windows. It is not showing on the sda1 info. You may have to wait to see if someone else knows what may fix this, if there is a fix. I think your windows may be toast. You may have to reinstall Windows. If you do that you will then have to boot from the Ubuntu Live CD after installing Windows to restore GRUB as Windows will overwrite GRUB. I would backup a copy of your sda5 menu.lst so to make it easy to edit if necessary. You can restore GRUB like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

P.S. I know reinstalling Windows is a time consuming project, but with Windows that is par for the course.

---

### Post by bzzzzz on 2009-05-19
Thanks for that.

I have no problem reinstalling Windows time consuming though it might be.  However is there a way I can at least access my files.

The most concerning thing about all this is that it was installing jaunty that seemed to overwrite all the necessary scripts for windows to boot.

Perhaps I made an error when installing Jaunty.  

During installation I was given the option of installing Jaunty onto the whole hard drive, a section of the hard drive or anywhere that was free on the hard drive.

Initially I tried to partition the hard drive and install Jaunty on that partition, but when this failed I tried to install Jaunty to the rest of the hard drive - I subsequently reduced the size of the partition.

This does not appear to have affected the Jaunty at all, however XP seems totally frozen out.

---

### Post by presence1960 on 2009-05-19
Boot into Jaunty or Hardy. Under places go to Computer. If your Windows files are still there you will be able to access them from the file browser.

As far as the install that is why I always use the manual option at the partitioner screen. usually I create the partitions with the Live CD or gparted Live CD prior to install. Then on install I use "manual" option and pick which partition(s) to install to.

---

### Post by bzzzzz on 2009-05-19
This is another problem.  

I can't see my xp files at all on Jaunty or Hardy.  I'm going to have a go at using my xp disk to see if I can boot in that way tonight.  My only fear is that I'll have to reset the grub again after windows tries to alter the settings again.

---

### Post by bzzzzz on 2009-05-19
Okay in real trouble now.

I used the xp disk to tried to fixboot and fixmbr.  Neither xp nor ubuntu boot at all now.  

I think I've wiped grub completely. 

Is there any way to replace or repair this.  The partitions still seem to exist when I look at the Partition Editor, but I can't access any of the partitions.

Thanks

---

### Post by clive littlewood on 2009-05-19
Hi

Download supergrub disc and run this at boot.

This should reset your grub and get you back to your original state.

Hope this helps

Clive

---

### Post by bzzzzz on 2009-05-19
Thanks Clive.

That's pretty useful.

I've now got my Hardy booting, but couldn't boot into Jaunty.

To be honest I'm not too bothered about Jaunty because I've got nothing on it and am happy to do a new install.  

I would like to try and resurrect my windows xp though.

---

### Post by bzzzzz on 2009-05-19
I had a backup of my xp partition so I decided to copy that over to the section that I have on my hard drive for xp (that i can't access) using a gparted live cd.  

As soon as I do that I can't boot a single thing.

That's fine because I then just need to open a terminal (using the gparted live cd) and do

**sudo grub**
then
**find /boot/grub/stage1**

I then find that I have boot records in hd0,1 and hd0,4

I then type
**root (hd0,1)**
then **setup (hd0)**
and **quit**

Problem is I can't even see 9.04.  

I'm quite happy to reinstall 9.04 again as I have nothing on it, but I'm a little afraid that in doing so I'll completely lose xp again.  

I'll sit and wait for advice now.

---

### Post by ranch hand on 2009-05-19
It sounds to me like there is something really funky in your XP partition.

I think I would back up everything you have any use for on all partitions and wipe that drive and start over.

Install XP first as MS feelings get hurt if it is not first and becomes cranky.  Use a primary partition for XP.

Format the rest of the drive as an extended partition and put everything else in there.

While things boot a little quicker the closer they are to the front of the drive, I would load your main Linux OS last so that it is where you are booting from without editing or other proceedures.

Take your time and HAVE FUN.

---

### Post by presence1960 on 2009-05-19
> **bzzzzz said:**
> I had a backup of my xp partition so I decided to copy that over to the section that I have on my hard drive for xp (that i can't access) using a gparted live cd.  

As soon as I do that I can't boot a single thing.

That's fine because I then just need to open a terminal (using the gparted live cd) and do

**sudo grub**
then
**find /boot/grub/stage1**

I then find that I have boot records in hd0,1 and hd0,4

I then type
**root (hd0,1)**
then **setup (hd0)**
and **quit**

Problem is I can't even see 9.04.  

I'm quite happy to reinstall 9.04 again as I have nothing on it, but I'm a little afraid that in doing so I'll completely lose xp again.  

I'll sit and wait for advice now.

If you want Jaunty restore GRUB from Live CD:

> sudo grub
find /boot/grub/menu.lst

to restore Jaunty GRUB do this next:
root (hd0,4)
setup (hd0)
quit

you restored Hardy's GRUB which is on sda2 (hd0,1), Jaunty's GRUB is on sda5 (hd0,4)

I wasn't surprised you couldn't see anything on your windows partition because of the contents of your results.txt file you posted. I would reinstall Windows to sda1 and then restore GRUB as outlined above. Your Jaunty install is fine, you just need to restore it's GRUB.

---

### Post by bzzzzz on 2009-05-20
If i do this will i destroy my xp installation?

oh well i'll give it a bash

---

### Post by presence1960 on 2009-05-20
> **bzzzzz said:**
> if i do this will i destroy my xp installation?

Oh well i'll give it a bash

no.

---

### Post by bzzzzz on 2009-05-21
I followed the instructions.

Booted from live disk.

Went into terminal then ran the following commands

sudo grub
find /boot/grub/stage1
root (hd0,4)
setup (hd0)
quit

I notice that my find command looked for stage1 whereas yours looked for menu.lst.  Is this important.

The good news xp and hardy still boot, 
bad news is jaunty still gets stuck.

---

### Post by presence1960 on 2009-05-21
> **bzzzzz said:**
> I followed the instructions.

Booted from live disk.

Went into terminal then ran the following commands

sudo grub
find /boot/grub/stage1
root (hd0,4)
setup (hd0)
quit

I notice that my find command looked for stage1 whereas yours looked for menu.lst.  Is this important.

The good news xp and hardy still boot, 
bad news is jaunty still gets stuck.

should be find /boot/grub/stage1 - mistype on my part sorry. If all else fails you can always reinstall Jaunty.

---

### Post by bzzzzz on 2009-05-21
I've decided to go for the re-install jaunty option.

My problem is that I can't work out how to install it in the selected partition.

I've used gparted to select the partition that I want to install it to, however the install disk doesn't manage to complete the installation.  It says I need to make changes to the root or something.

Please can I have some help installing Jaunty to a certain partition - what preparations do I need to make to the partition before it will install.  Thanks for the help.

---

### Post by ranch hand on 2009-05-21
The partitioner on the install disk is probably asking you to choose a root ( / ) partition.  Just click on the partition you want Jaunty to go in an click on edit and select ( / ) which is root for the mount point.

---

### Post by bzzzzz on 2009-05-21
Forgive me for sounding a bit stupid, but where should I put the root.

Last time I tried to do this I ended up with a system that could boot into ubuntu but not into xp.  

I don't want that to happen again.

I currently have 

hd0,0 xp
hd0,1 hardy
hd0,4 jaunty

should i set hd0,4 as root?

---

### Post by ranch hand on 2009-05-21
If you are reinstalling Jaunty - yes.

---

### Post by bzzzzz on 2009-05-21
Okay I've got it all working now.

Thanks for all the help guys.

---

### Post by ranch hand on 2009-05-21
Great

---

### Post by presence1960 on 2009-05-21
> **bzzzzz said:**
> Okay I've got it all working now.

Thanks for all the help guys.

Excellent!

---

