---
title: "Keep old menu.lst - or what?"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-01-07
I recently upgraded my LTS version from 8.04 to 10.04.
Somewhere along the line, I was asked whether I wanted to keep my old menu.lst or some other option I didn't look very closely at.
Since my menu.lst has several custom items I want to keep & since keeping the old one was the default option, I clicked through to keep it, without much thought.

After the upgrade, at the next boot, the grub screen was exactly the old version, with only 8.04 kernels which no longer work.

At that point, Ubuntu was just about dead in the water, certainly for any beginner.

I managed to fix things by booting 10.10 which I run in parallel to LTS, and manually editing LTS's menu.lst.

Some questions:
1. What exactly are the menu.lst options offered during an upgrade & what are their results?
2. Does anybody think it is OK that accepting default options results in killing Ubuntu?
3. Has this been fixed for future upgrades?

Thanks!

---

### Post by wilee-nilee on 2011-01-07
Never ignore what is being updated or upgraded in a OS. The menu.list is grub-legacy it is the bootloader, it is what makes the computer startup. The replacement was grub2, not a problem staying with grub-legacy but you should basically be aware of this function in the OS.

The update from Hardy to Lucid also left you with ext3 rather ext4 partitions. I think most experienced users, did fresh installs rather then this upgrade, there were to many changes to rely on a clean upgrade, and even if you did you had a set up that was not completely up to date.

---

### Post by 2CV67 on 2011-01-09
> **wilee-nilee said:**
> I think most experienced users, did fresh installs rather then this upgrade, there were to many changes to rely on a clean upgrade..
I hope that is not the general position of the Ubuntu community.
Surely the whole point of the LTS versions is to have something reliable which is upgradable every 3 years by an average non-geek user?
I would think people using LTS versions don't want to get involved with fresh installs & all the fiddling that implies.

Coming back to my original post, could somebody please clarify what are the options for menu.lst during the upgrade (sorry, I did not record them) & what are the results of each option?

Thanks!

---

### Post by oldos2er on 2011-01-09
See post #6 in this thread: [http://art.ubuntuforums.org/showthread.php?t=1537062](http://art.ubuntuforums.org/showthread.php?t=1537062)

You might want to consider upgrading to grub2 also.

---

### Post by oldfred on 2011-01-09
Anytime you do an install, you should read the release notes, because of the grub to grub2 changes it has info on customized grub menus:

GRUB menu.lst: install the maintainer's version vs. keep the local version
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

---

### Post by 2CV67 on 2011-01-10
Thanks, oldos2er & oldfred, for those should-be-helpful links, but I have to admit things are not yet clear (for next time?).

Lucid release notes (I had never seen them - am I alone?) do say > if you choose to "keep the local version currently installed," your system will not be set up to boot from any newly-installed kernels but don't mention that it won't boot from any old kernels either, so you are stuck.
Is that inevitable if you choose that default option without further action?

I am still searching for better information on > install the package maintainer's version
What exactly would that be?
Just losing detail stuff like timeouts?
Or losing XP & my other Ubuntu partition as well?

Up till now, updates (new kernels) & upgrades seemed to work perfectly, keeping my menu.lst modifications & just adding new kernels above the recent old ones, inside the Automagic list for each partition.
Is this no longer possible?

Are all future updates & upgrades going to be problematic like this?

I don't want to move to Grub2 yet, as I suspect that will be a whole new can of worms for a multi-boot set-up & might well leave me with nothing at all bootable.

---

### Post by kansasnoob on 2011-01-10
> I don't want to move to Grub2 yet, as I suspect that will be a whole new can of worms for a multi-boot set-up & might well leave me with nothing at all bootable.

It really shouldn't, I multiboot a lot:

> Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.10 (10.10) on /dev/sda12
Found Peppermint (peppermint) on /dev/sda13
Found Ubuntu 10.10 (10.10) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu natty (development branch) (11.04) on /dev/sda16
Found Ubuntu natty (development branch) (11.04) on /dev/sda17
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda3
Found Ubuntu 10.10 (10.10) on /dev/sdb1
done


I'd hate having to edit a menu.lst all the time now :)

BTW I know that looks ridiculous but I do a lot of testing and virtual machines don't tell me how something actually works with my hardware.

Anyway if you really have these three OS's:

> Multi-boot XP/10.04(LTS)/10.10

I'd assume that 10.10 has grub2 if it was a fresh install :confused:

I don't like to guess but if that's correct you should be able to hand booting off to 10.10's grub2 and see how you like it. (NOTE: grub2 does however read some info from other OS's existing legacy-grub menu.lsts so you could still find a need to fix your borked menu.lst in 10.04)!

Ultimately I'd want to see the output of the Boot Info Script as described in the following link before making any specific recommendations:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It simply provides enough info that we can eliminate "guessing" from the equation :)

---

### Post by Paqman on 2011-01-10
> **2CV67 said:**
> I hope that is not the general position of the Ubuntu community.
Surely the whole point of the LTS versions is to have something reliable which is upgradable every 3 years by an average non-geek user?
I would think people using LTS versions don't want to get involved with fresh installs & all the fiddling that implies.


It's a common opinion among users, but the official method of moving to a new version is indeed to do an upgrade rather than a fresh install. Upgrades used to be a bit flaky, but these days are very reliable. Nevertheless, the old advice still gets dished out.

Grub 2 is very good for multi-boot systems, though. It's certainly a lot better at automatically detecting and configuring non-Linux OSes. You can [test how well Grub2 works on your system]("https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2"), then commit to the upgrade with one command if it works.

Of course, you don't have to upgrade yet. Grub legacy can boot ext4 partitions fine, although you'll most likely have to upgrade to Grub2 if you ever want to switch to btrfs.

---

### Post by oldos2er on 2011-01-10
> **2CV67 said:**
> I am still searching for better information on 
"install the package maintainer's version"

Installing the package maintainer's version would give you a default menu.lst with the new kernels added. Any changes you made to menu.lst would be lost. You could create a backup copy before running your upgrade, then afterwards re-edit menu.lst.

> Up till now, updates (new kernels) & upgrades seemed to work perfectly, keeping my menu.lst modifications & just adding new kernels above the recent old ones, inside the Automagic list for each partition.
Is this no longer possible?

Updates and upgrades are two different things. I'm guessing that because of the many changes in the kernel that took place between 8.04 and 10.04, this is why you couldn't boot 10.04 with an 8.04 kernel (if that makes sense). The kernel updates that occurred with 8.04 are of course meant to work with that version only.

Grub2 is more intelligent about multi-OS systems than grub legacy. It does have a learning curve though (it is configured in a completely different way).

---

### Post by oldfred on 2011-01-10
My mom had an old saying, You cannot sweep the sea back with a broom. I think she meant it was time to convert to grub2.:)

I tried to not upgrade to grub2 when it first came out. I was chainloading to grub installed in each other systems partition. Grub2 really does not like to be installed to a partition, so I was not happy. Yes, grub2 is more complex as it tries to be more capable with new systems. Old grub legacy has not been maintained for years. And each distribution may have tweaks to grub 0.97 that are different than others 0.97.

Early versions of grub2 had issues, almost all are fixed and the osprober is very good at finding and setting up boot of other systems, no more manual editing required, but you can in 40_custom if you want.

I used to upgrade and a couple of years ago with video drivers did not accept maintainers version and had a heck of a time getting system to work. I then decided if I edit any system file I copy it into /home so it gets backed up and always accept maintainer's versions of files. More often than not they have resolved whatever issue I had and I do not need my settings, but occasionally have had to go back and re-add something.

---

### Post by 2CV67 on 2011-01-10
Thanks everybody for your continuing interest.
> **kansasnoob said:**
> 
I'd assume that 10.10 has grub2 if it was a fresh install 

Ultimately I'd want to see the output of the Boot Info Script as described in the following link before making any specific recommendations:

It simply provides enough info that we can eliminate "guessing" from the equation :)

My 10.10 still has legacy grub, since it has been upgraded progressively from 8.04.

Attached is the output from Boot Info Script.
My setup with different menu.lst's for each Ubuntu variant was supposed to be the right answer so that new kernels would get into grub OK from each update.
Will Grub2 handle that OK?
Note: sdb is just an external HD used for backups.

Thanks again!

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 181726901 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,816,554   114,816,492   c W95 FAT32 (LBA)
/dev/sda2         232,396,290   234,436,544     2,040,255  82 Linux swap / Solaris
/dev/sda3         211,302,945   232,396,289    21,093,345  83 Linux
/dev/sda4         114,816,555   211,302,944    96,486,390   5 Extended
/dev/sda5         129,194,730   211,302,944    82,108,215  83 Linux
/dev/sda6         114,816,681   129,194,729    14,378,049  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sdb2          61,432,560   156,296,384    94,863,825  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2B1B-1302                              vfat       XP                            
/dev/sda2        5a626c9d-6484-489b-9a9a-c215110b5952   swap                                     
/dev/sda3        f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e3bbb061-9a3d-4c6e-960a-03d42b490670   ext3                                     
/dev/sda6        5998da7e-4123-4481-80f0-99a6f3c5e244   ext3       LTS Ubuntu Drive              
/dev/sda: PTTYPE="dos" 
/dev/sdb1        150D-1B41                              vfat       LACIE                         
/dev/sdb2        a19cc0e6-2b6b-4fad-b591-99a1d74ac5bf   ext3       Lacie_linux                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext3       (rw,relatime,commit=0)
/dev/sdb1        /media/LACIE_            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb2        /media/Lacie_linux_      ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn


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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

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
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro

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
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

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
# howmany=3

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

title		Ubuntu 10.10, kernel 2.6.35-24-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.35-24-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.32-27-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-27-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#Put in by Chris to chainload Ubuntu LTS
title Ubuntu LTS on sda6
#root (hd0,5)
#chainloader +1
configfile (hd0,5)/boot/grub/menu.lst

#just the end.




=============================== sda3/etc/fstab: ===============================

proc /proc proc defaults 0 0
UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c / ext3 relatime,errors=remount-ro 0 1
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670 /home ext3 relatime 0 2
#UUID=48A5-D628 /media/SHARE vfat utf8,umask=007,gid=46 0 2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda3: Location of files loaded by Grub: ===================


 111.5GB: boot/grub/menu.lst
 113.5GB: boot/grub/stage2
 114.5GB: boot/initrd.img-2.6.32-27-generic
 114.4GB: boot/initrd.img-2.6.35-24-generic
 113.8GB: boot/vmlinuz-2.6.32-27-generic
 114.4GB: boot/vmlinuz-2.6.35-24-generic
 114.4GB: initrd.img
 114.5GB: initrd.img.old
 114.4GB: vmlinuz
 113.8GB: vmlinuz.old

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
# kopt=root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# defoptions=splash

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
# howmany=4

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro single
initrd		/boot/initrd.img-2.6.24-27-generic


title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# -file system- -mount point- -type- -options-       -dump-  -pass-
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/menu.lst
  60.6GB: boot/grub/stage2
  60.5GB: boot/initrd.img-2.6.24-27-generic
  60.5GB: boot/initrd.img-2.6.24-27-generic.bak
  60.4GB: boot/initrd.img-2.6.24-28-generic
  60.4GB: boot/initrd.img-2.6.24-28-generic.bak
  59.6GB: boot/initrd.img-2.6.32-27-generic
  60.4GB: boot/vmlinuz-2.6.24-27-generic
  60.5GB: boot/vmlinuz-2.6.24-28-generic
  60.4GB: boot/vmlinuz-2.6.32-27-generic
  59.6GB: initrd.img
  60.4GB: initrd.img.old
  60.4GB: vmlinuz
  60.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

---

### Post by wilee-nilee on 2011-01-10
> **Paqman said:**
> It's a common opinion among users, but the official method of moving to a new version is indeed to do an upgrade rather than a fresh install. Upgrades used to be a bit flaky, but these days are very reliable. Nevertheless, [B]the old advice still gets dished out.
[/B]
Grub 2 is very good for multi-boot systems, though. It's certainly a lot better at automatically detecting and configuring non-Linux OSes. You can [test how well Grub2 works on your system]("https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2"), then commit to the upgrade with one command if it works.

Of course, you don't have to upgrade yet. Grub legacy can boot ext4 partitions fine, although you'll most likely have to upgrade to Grub2 if you ever want to switch to btrfs.

You as a experienced user know that this 8.04 to 10.04 had major changes to it, not in older LTS upgrades.

You are showing the same bias you claim. This is straight forward stuff at the least the ext type has changed, and should be known by any user it is all over the forum.

Canonical is making major changes each release now for example the unity desktop in natty.

Really if anybody expects open source to be plug and play and update and upgrade with out hiccups, I have a bridge for sale. here is a price you pay with free software it is called education. Educate yourself in what your doing and be prepared for the worse possible case=be backed up.

---

### Post by kansasnoob on 2011-01-11
I'll start with a review of what I see from that, but my very first question is:

What can you boot right now?

Anyway you have Win XP on sda1, 10.10 is on sda3, and 10.04.1 is on sda6.

The MBR is assigned to 10.10 so it controls boot, and 10.04.1's grub is installed to it's PBR and chainloaded through a custom entry in 10.10's menu.lst.

Something I find odd is the placement of the Windows entry in 10.10's menu.lst:

```
#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

[B][COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP dition familiale
root (hd0,0)
savedefault
makeactive
chainloader +1

# This is a divider, added to separate the menu items below from the Debian
# ones.[/COLOR][/B]
title Other operating systems:
root

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro
```

I assume you did that so Windows would appear first on the boot menu, eh?

I suppose if it worked that's OK but sometimes making edits to a menu.lst ahead of the "## ## End Default Options ##" can result in kernel updates NOT being automatically added to the menu.lst. Basically, if both 10.10 and Windows are booting as you like, I'd not worry about that - in other words - *if it ain't broke don't fix it* ;)

Just out of curiosity, in case you decide to upgrade to grub2, how important is it to you to have Windows appear first in the boot menu?

Which OS would you prefer to try grub2 with? I ask that because grub2 does read some info from an existing OS's menu.lst so regardless of which OS you choose to convert you should plan ahead.

I'll be out a lot the next couple of days due to snow but I'll try to keep checking back.

---

### Post by 2CV67 on 2011-01-15
I was away for a few days too...

I put XP up there for simplicity.
My first Grub screen, which only shows for 3 seconds, so most users don't even notice it, jumps to the latest 10.10 kernel.
If I don't want that, Page-up gives me XP.
Page-down gives me LTS Ubuntu, via a second Grub screen.
I like it like that, but it's not a must-have.
No updates or upgrades have had any problem keeping XP & LTS at the extremes whilst Automagically adding new kernels & deleting old kernels in between.
I wonder what arrangement Grub2 would propose.

At the moment, from that first screen, I can boot XP & the latest 10.10 kernel 2.6.35-24-generic and the previous kernel 2.6.32-27-generic, which is labelled 10.10 but was originally 10.04.
I can also get to my other grub screen via the LTS chainloader.
All that happened OK during the 10.04>10.10 upgrade.
Just as it should!

From my second screen, I can boot XP and can now boot 10.04.1 LTS, kernel 2.6.32-27-generic, but only since I added that kernel manually to menu.lst, in place of the 8.04 kernel left by the 8.04>10.04 upgrade & which would not boot.
The other 8.04 kernel still there will not boot either.
Which is what I am "complaining" about!

I keep reading Grub2 information & always give up in despair before the end!
If I ever decide to shift to Grub2 with the current PC, I suppose I would start from 10.10 which is my main OS.
LTS is really just there as a lifebelt for when the main OS fails, usually after updates/upgrades.
Sad reflection on Ubuntu...

---

### Post by oldfred on 2011-01-15
When you decide to make the leap to grub2 read the threads by drs305, he has a lot of good customizing advice.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


You can create your own custom menu.
From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

General menuentry Construction Rules:

    * The first line must start with menuentry and end with {
    * The area between the quotation symbols is what will appear on the GRUB 2 menu. Edit as desired.
    * The last line of the menuentry must be }
    * Do not leave empty spaces at the end of lines
    * The set root= line should point to the GRUB 2 /boot location ( sdXY )
    * The root reference in in the linux line should point to the system partition.
          o If GRUB 2 cannot find the referenced kernel, try replacing the UUID with the device name (example: /dev/sda6 ).

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit Ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

You can directly boot a partition's most current kernel with a entry like this:

Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by 2CV67 on 2011-01-27
Today, my LTS version 10.04 got 67 updates, including new kernel 2.6.32-28.

During the installation of these updates, the famous menu.lst question came up again.
So apparently we get this joy every update, not just every upgrade!

After my sad experience with keeping my old menu.lst I decided this time to accept the developer's version.

On completion, I needed to reboot & that went OK as far as the grub screen, which showed the new & old kernels & XP.

But when I selected any of the LTS Ubuntu kernels, I got:
"Error 22 - no such partition"!!!!

Fortunately I could use my "spare" Ubuntu 10.10 with its separate grub screen, to get at the LTS menu.lst & all the older copies.
The new version had all the kernels on "root - (hd0,6)" whereas previous menu.lsts show "root - (hd0,5)".
So it was easy enough to correct them all back to (hd0,5) & everything works OK.
But why???

So that means both the menu.lst options at every update result in a no-boot situation!

You may think that is not too bad, but I don't.

---

### Post by JKyleOKC on 2011-01-27
You will get that menu.lst question not on every update/upgrade, but only on those that add or make major changes to a kernel image.

Every time I've gotten it, there has been an option on the very first screen of the question to compare the existing file to the proposed "maintainer's version" content, so you can see exactly what changes will happen if you choose the newer version. I always take that option, which gives me a screen that shows both versions of the lines that will change. Existing lines that will be removed start with "---" and new lines that will be added start with "+++" so you can see what will happen. The first couple of lines in this display are almost always comments that include the version number and date, which make it obvious how the display is laid out..

With all the custom changes you've made, your comparison screen(s) may be difficult to read, though. For instance, your moving the Windows entry up might well cause all of it to be shown as "---" lines, followed by the comments in the new version as "+++" lines and the new Windows entry to be another group of "+++" lines much later in the display.

The reason for doing this whenever the kernel updates/upgrades is quite simple: to make it possible to use the new kernel. If you don't add it to the grub menu, you cannot boot into it.

The inability to boot into your older kernel versions is quite likely to be due to an almost invisible change in the partition designations during the boot process. The letters "a," "b," "c," and so on are assigned in the sequence that drives are discovered: "sda" is the first one, "sdb" the second, and so on. Grub's (hd x,y) notation gets its "x" value directly from the final letter that was assigned a few microseconds earlier. Thus if the new boot image discovers a different drive as "sda" then grub will look on that drive for its files, and of course they won't be there.

This used to happen all too often; one would expect that the start-up process would always examine the hardware in the same sequence, but that's never guaranteed to happen. Some of the changes between the 2008 version 8.04 and the 2010 version 10.4 made parts of the process run in parallel rather than one after the other, and this could easily cause the detection order to change (only an upstart guru could say with certainty whether that happened, but it's possible and even likely).

That's why the recommendation is made to change the drive identities in the /etc/fstab file from using "/dev/sda" to using "UUID=..." since the UUID won't change even if the "sd?" name does. Since things worked once you changed the "hd x,y" entries in menu.lst for the "unbootable" kernels, this is probably what happened to you -- and unless you change the fstab file, it will probably happen again on every update-grub action.

You may already know that you can change the grub "default" setting to be any of the entries, not just the "0" value that it gets when installed. That may eliminate the need to move the Windows entries around on the menu. Personally, my dual-boot systems use a "default" value of "saved" and all include the "savedefault" line for each entry, so that it always comes back to the entry I used on the previous boot...

Hope this helps remove some of the odor you're detecting in the process!

---

### Post by 2CV67 on 2011-07-17
I just upgraded my "other" Ubuntu from 10.10 to 11.04 & was expecting to run into menu.lst problems as above, but it all went without a hitch (and with no questions asked...).
Still using vintage grub & my custom menu.lst was correctly updated just like in the good old days.

Great relief!

Thanks, somebody!

---

