---
title: "GRUB, Error 21"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by jerrydc on 2010-04-08
In the last few days, when I hit the power-on button in order to come out of hibernation I get a msg, "GRUB Loading stage 1.5
                   "GRUB Loading, please wait
                    "Error 21"

I wait, nothing happens, I make the three-fingered salute and then my computer boots up.  I have been using Ubuntu for about a year, now on 9.10.

A friend created a dual boot on the one hard drive when this computer was new about a year ago.  Have hardly ever opened Vista, certainly not for many months.

Have tried to find 0ut what GRUB is, what error 21 is but no luck.  That is how much of a newbie I am.

Would appreciate learning what is suddenly happening.

---

### Post by Psumi on 2010-04-08
For users helping this user, please note that LBA may not be changable on new computers.

As for the OP, CMOS = BIOS.

GRUB is your bootloader, it allows you to boot into your system. Error 21 from GRUB means that it cannot find your boot disk.

Also, your GRUB is not up to date, or you have two GRUBs.

---

### Post by jerrydc on 2010-04-08
Why would GRUB be not up-to-date when I have Synaptic Package Manager automatically notifying me and installing updates?  As a matter of fact, wasn't there a big update just a few weeks ago?  Could whatever that was have created a problem that did not exist before?  Could I now have two competing GRUBS when I didn't previously?

I just looked in Synaptic Package Monitor and see I have two grub programs(?) listed: grub and grub-common.  Does that mean anything?

What might LBA be, or more important where is a good glossary? Entering GRUB or error 21 in the search box on the forum gave no information.

Thank you.

---

### Post by Psumi on 2010-04-08
The reason I suspect you having an out of date grub is that GRUB2 (in 9.10) doesn't give the stage 1.5 notice.

You must've incorrectly upgraded from 9.04.

The suspicion that you have two grubs is from your TWO loading grub messages.

Having grub and grub-common is fine.

---

### Post by bcbc on 2010-04-08
When you upgrade to karmic from 9.04 it doesn't replace legacy grub with grub2 - so that's not a problem.

Have you made any changes lately - removed hardware, changed your swap, modified partitions etc.?

The actual error is:
```
21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 
```

Edit: here's the legacy grub manual for future reference: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Also here's a thread where a similar problem occurred to someone who modified their swap partition: [http://ubuntuforums.org/showthread.php?t=1314091](http://ubuntuforums.org/showthread.php?t=1314091)

---

### Post by jerrydc on 2010-04-09
I've made no changes of any kind for many months. I haven't changed my "swap" because I don't know what that is.  I haven't ever touched my partition.

The upgrade to Karmik (9.10), which happened several months ago, I believe, did create problems but that was quickly straightened out by an Ubuntu pro (defined as an IT pro who is an Ubuntu enthusiast).

The only thing new that I can think of was an update (or whatever it was called) just a few weeks ago, downloaded by my package monitor.  I don't know how to name this update or exactly when it occurred.

To bcbc:  Have looked at the manual and the thread.

Can something be done about my issue?  Should something be done?  Or may I ignore it and simply put up with a minor inconvenience?

Thank you.

---

### Post by bcbc on 2010-04-09
> **jerrydc said:**
> Or may I ignore it and simply put up with a minor inconvenience?

I wouldn't. 

Can you post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") (instructions in link, use the # sign to post within ```
 tags).
Also run the following in terminal and copy and paste results:
[CODE]cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by jerrydc on 2010-04-13
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
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

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6060db34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sda2          78,156,225    82,060,019     3,903,795  82 Linux swap / Solaris
/dev/sda3          82,060,020   195,382,529   113,322,510  83 Linux
/dev/sda4         195,382,530   312,576,704   117,194,175   5 Extended
/dev/sda5         195,382,593   308,672,909   113,290,317  83 Linux
/dev/sda6         308,672,973   312,576,704     3,903,732   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xda30382d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    12,290,047    12,288,000  27 Hidden HPFS/NTFS
/dev/sdb2    *     12,290,048   402,915,047   390,625,000   7 HPFS/NTFS
/dev/sdb3         402,926,265   406,813,994     3,887,730  82 Linux swap / Solaris
/dev/sdb4         406,813,995   976,768,064   569,954,070  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D6BFCB38D4F250DD                       ntfs                                     
/dev/sda2        a7f5d4ed-7535-48fe-84ba-e7d59c393a28   swap                                     
/dev/sda3        363e58a1-0fd0-4f59-8d14-cb0da047fbdd   ext3                                     
/dev/sda5        2fe02c53-698f-419a-8090-9e2d360b6419   ext3                                     
/dev/sda6        C733-9989                              vfat                                     
/dev/sdb1        EE56784356780E99                       ntfs       RECOVERY                      
/dev/sdb2        5CC6799DC679785A                       ntfs                                     
/dev/sdb3        48380239-4a3e-4c3b-beb6-622c9d99ce4c   swap                                     
/dev/sdb4        e44d54d5-5dd6-46d0-ba78-4f7792b89674   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb4        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdb2        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
default        saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=363e58a1-0fd0-4f59-8d14-cb0da047fbdd ro

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

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=363e58a1-0fd0-4f59-8d14-cb0da047fbdd ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=363e58a1-0fd0-4f59-8d14-cb0da047fbdd ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=363e58a1-0fd0-4f59-8d14-cb0da047fbdd ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=363e58a1-0fd0-4f59-8d14-cb0da047fbdd ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=363e58a1-0fd0-4f59-8d14-cb0da047fbdd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2fe02c53-698f-419a-8090-9e2d360b6419 /home           ext3    relatime        0       2
# /dev/sda2
UUID=a7f5d4ed-7535-48fe-84ba-e7d59c393a28 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  51.3GB: boot/grub/menu.lst
  51.2GB: boot/grub/stage2
  51.3GB: boot/initrd.img-2.6.24-19-generic
  51.3GB: boot/initrd.img-2.6.24-19-generic.bak
  51.2GB: boot/initrd.img-2.6.24-22-generic
  51.3GB: boot/initrd.img-2.6.24-22-generic.bak
  51.3GB: boot/vmlinuz-2.6.24-19-generic
  51.3GB: boot/vmlinuz-2.6.24-22-generic
  51.2GB: initrd.img
  51.3GB: initrd.img.old
  51.3GB: vmlinuz
  51.3GB: vmlinuz.old

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        30

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e44d54d5-5dd6-46d0-ba78-4f7792b89674

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        e44d54d5-5dd6-46d0-ba78-4f7792b89674
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows Vista (loader)
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb4 during installation
UUID=e44d54d5-5dd6-46d0-ba78-4f7792b89674 /               ext4    relatime,errors=remount-ro 0       1
# /windows was on /dev/sdb2 during installation
UUID=5CC6799DC679785A /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# swap was on /dev/sda2 during installation
UUID=a7f5d4ed-7535-48fe-84ba-e7d59c393a28 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=48380239-4a3e-4c3b-beb6-622c9d99ce4c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb4: Location of files loaded by Grub: ===================


 212.7GB: boot/grub/menu.lst
 210.0GB: boot/grub/stage2
 211.4GB: boot/initrd.img-2.6.28-15-generic
 213.7GB: boot/initrd.img-2.6.28-16-generic
 217.3GB: boot/initrd.img-2.6.31-14-generic
 216.1GB: boot/initrd.img-2.6.31-15-generic
 216.4GB: boot/initrd.img-2.6.31-16-generic
 216.1GB: boot/initrd.img-2.6.31-17-generic
 218.9GB: boot/initrd.img-2.6.31-19-generic
 213.5GB: boot/initrd.img-2.6.31-20-generic
 212.0GB: boot/vmlinuz-2.6.28-15-generic
 210.3GB: boot/vmlinuz-2.6.28-16-generic
 217.2GB: boot/vmlinuz-2.6.31-14-generic
 215.8GB: boot/vmlinuz-2.6.31-15-generic
 213.6GB: boot/vmlinuz-2.6.31-16-generic
 215.0GB: boot/vmlinuz-2.6.31-17-generic
 224.0GB: boot/vmlinuz-2.6.31-19-generic
 214.6GB: boot/vmlinuz-2.6.31-20-generic
 213.5GB: initrd.img
 218.9GB: initrd.img.old
 214.6GB: vmlinuz
 224.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by jerrydc on 2010-04-13
RESUME=UUID=a7f5d4ed-7535-48fe-84ba-e7d59c393a28

Thanks

---

### Post by bcbc on 2010-04-13
It looks like you have two swap files in use /dev/sda2 (approx 2GB) and /dev/sdb3 (slightly smaller). 

Karmic tries to resume from /dev/sda2 (UUID=a7f5d4ed-7535-48fe-84ba-e7d59c393a28 ) as per /etc/initramfs-tools/conf.d/resume. 

The first thing I would try is loading karmic with only a single swap partition and see if that works. *I am assuming you have <2GB ram*.

Boot karmic, open a terminal:
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
This will backup fstab and open to edit - add a '#' to comment out the line setting up swap on /dev/sdb3 as follows:
```
# swap was on /dev/sdb3 during installation
[COLOR="Red"]#[/COLOR] UUID=48380239-4a3e-4c3b-beb6-622c9d99ce4c none            swap    sw              0       0
```

Save, exit, then restart swap:
```
sudo swapoff -a
sudo swapon -a
sudo swapon -s
```
The last command should list your active swap partitions - make sure it's just /dev/sda2. One last check:
```
free
```
This will show your memory and your swap. Make sure you don't have more memory than swap. Now attempt to hibernate and see if it works.

---

### Post by jerrydc on 2010-04-16
Do the numbers in the total column indicate I have more memory than swap?  If so, what should I do?  After sending this, I'll hibernate and send another msg telling you what happened.

Package Manager installed several updates yesterday.  I have no idea, of course, whether these insertions between the info I orginally gave you and the lines below that I just put in affect the saga we are engaged in.

thanks again for your time and effort.

jerry

# 

jerry@jerry-desktop:~$ sudo cp /etc/fstab /etc/fstab.backup
[sudo] password for jerry: 
jerry@jerry-desktop:~$ gksudo gedit /etc/fstab
jerry@jerry-desktop:~$ sudo swapoff -a
jerry@jerry-desktop:~$ sudo swapon -a
jerry@jerry-desktop:~$ sudo swapon -s
Filename                Type        Size    Used    Priority
/dev/sda2                               partition    1951888    0    -1
jerry@jerry-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2049752    1906548     143204          0     179292    1407044
-/+ buffers/cache:     320212    1729540
Swap:      1951888          0    1951888
jerry@jerry-desktop:~$ ^C
jerry@jerry-desktop:~$

---

### Post by jerrydc on 2010-04-17
no problem returning from hibernate or powering off.

---

### Post by bcbc on 2010-04-17
> **jerrydc said:**
> no problem returning from hibernate or powering off.

That's great! I am a little surprised since the 'free' command seemed to indicate you are short on swap, however if it's working, no point in messing with it.

---

### Post by jerrydc on 2010-04-18
Thank you.  I'll leave it alone.  I must say, however, that the codes you asked me to write and the results you wanted me to post would have been impossible for me without the help of a friend who knows Linux but not as much as you do on my particular question.  He spent at least an hour on the phone coaching me through the steps you suggested.  This was complicated stuff for me and, I believe, any beginner.

Much appreciated.

---

### Post by bcbc on 2010-04-19
> **jerrydc said:**
> Thank you.  I'll leave it alone.  I must say, however, that the codes you asked me to write and the results you wanted me to post would have been impossible for me without the help of a friend who knows Linux but not as much as you do on my particular question.  He spent at least an hour on the phone coaching me through the steps you suggested.  This was complicated stuff for me and, I believe, any beginner.

Much appreciated.

You're welcome...

The whole hibernation thing in Ubuntu is overly complex, and there are a lot of people having problems with it - if that's any comfort.

---

### Post by jerrydc on 2010-04-19
Thanks again.  Problem solved.

---

### Post by jerrydc on 2010-04-20
Sorry.  I spoke too soon.  I powered off and then booted up a half hour or so later and got the full GRUB and error 21 msg again.  Booting from hibernation has been no problem but Shut Down and power on has been.  An suggestions, please.

---

### Post by bcbc on 2010-04-21
> **jerrydc said:**
> Sorry.  I spoke too soon.  I powered off and then booted up a half hour or so later and got the full GRUB and error 21 msg again.  Booting from hibernation has been no problem but Shut Down and power on has been.  An suggestions, please.

Intermittent error 21's... could be a hard drive or bios issue. Have you checked your disks (System, Administration, Disk utility? see if you are getting any errors). This is an area I know little about.

Edit: my guess is that sometimes the bios isn't recognizing your second drive. When you get this problem is it always after a cold start, and do you have to reboot and then the second time it works? Or is it truly random?

---

### Post by jerrydc on 2010-05-29
Sorry to take so long to get back to you.  A friend spent hours doing technical stuff that I don't understand.  The problem was solved.  The new version of Ubuntu was loaded successfully.  If this issue is important to you, I'll try to get the friend to send a msg explaining what he did.

I'd mark this solved if I knew how to do that.

---

