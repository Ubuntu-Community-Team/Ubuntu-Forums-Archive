---
title: "Installation problem. Please help."
date: 2011-03-14
forum: New to Ubuntu
---

### Post by j0z on 2011-03-14
Please help.:(.
I can't find any thread which can help my problem.
I am a newbie.

I have dual boot windows vista and ubuntu 9.04.
Actually i have it for quite some times, i have not been using ubuntu.
i have been having problems with my ubuntu which i dont know why.
I cant upgrade my ubuntu as well.
it is said that i dont have enough memory capacity.
I allocated 10GB for ubuntu.

so i decided to uninstall it.
But after reading of how to uninstall and asking help from my friend.
I can't find my partition where i installed my ubuntu.
I have only 2 harddisk partition which are Local disk (C) and Drive D which is meant for recovery.
There is no partition for my ubuntu.
My friend said i installed my ubuntu on my windows, but i can't find it.

[B]How do i uninstall my ubuntu or is there any other way so i can upgrade it?
[/B]

It was not me who installed the ubuntu on my laptop. i asked my friend to help to install it on my laptop.
I believe he ran the LIVE CD from windows and after that he installed it. (i am not sure how)
(if you need any additional information from me, please tell me)

---

### Post by rowland on 2011-03-14
i'm new too, so maybe i wont be able to help too much... :
1: i heard that its probably better to install ubuntu, by booting the live CD (at startup) and installing from there, because there might appear kernel problems if you install from windows
2: if you cant find Ubuntu neither the SWAP in windows it may be because windows doesnt recognize them, therefore try booting the live CD again, and enter in GParted to see if it recognises the partitions
3: try restarting, and pressing the F8 (by default) to choose wich hard drive to boot. if you installed Windows on HDD1 and linux on HDD2, then you have to boot the HDD2. if you installed on the same HDD probably GRUB should appear, if not, i dont know :(
3: i'm out of ideas :P good luck

---

### Post by j0z on 2011-03-14
actually i want to uninstall it and re-install it again later..
and my question is it safe to directly uninstall it?
how shall uninstall it?
is there any other things that i need to consider and do before or after i uninstall? :(.

cos i heard it is not that simple to uninstall ubuntu.

---

### Post by Elfy on 2011-03-14
If you installed in Windows - look in the Add/Remove software thing in Control Panel. If it's not there you might have removed it already.

If it is there - uninstall it.

If it is not there - open the File manager and look for 'wubi' files in C:\

To reinstall in windows - use wubi again. However if you still only have the 9.04 disc - that is now end of life.

Try with either the latest or the LTS (Long term support version) they are both available from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Personally I would not reinstall with wubi but create a real dual-boot.

---

### Post by j0z on 2011-03-14
@forestpiskie

checked on add/remove program.
It is not there.
One friend of mine told me to do the same thing, but i found nothing there.
I didn't install it with wubi either.


(I am finding a way to uninstall this ubuntu, so i can re-install it with a better way)

---

### Post by rvchari on 2011-03-14
> **j0z said:**
> @forestpiskie

checked on add/remove program.
It is not there.
One friend of mine told me to do the same thing, but i found nothing there.
I didn't install it with wubi either.


(I am finding a way to uninstall this ubuntu, so i can re-install it with a better way)

if you have g-parted live cd, keep it handy and boot from that cd, will show up all your partition table.

if you dont have, down load and create an iso disc.
alternatively, if you are using virtual clone drive or something like that, you can still mount the cd from windows and check out your partition table.
try to delete or format all the ext2/ext3 and swap partitions. merge all the ubuntu based partitions and unify it. format with windows. you will have fat32 or ntfs partition to use with ubuntu out of ur box.

i havent done anything like that but that seems to be one possible way.

if your grub was installed on MBR then you have to remove grub. one easiest way is to simply re-install windows which will wipe out grub data from MBR (the easier way i found out long before i had access to such forums we now look to so frequently !)

---

### Post by Elfy on 2011-03-14
> **j0z said:**
> @forestpiskie

checked on add/remove program.
It is not there.
One friend of mine told me to do the same thing, but i found nothing there.
I didn't install it with wubi either.


(I am finding a way to uninstall this ubuntu, so i can re-install it with a better way)

Once you have a disc to boot and install with. Boot with the cd, use the "try ubuntu" option when it asks.

Run firefox - go here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Do as it says and then paste the results.

We'll be able to see exactly what's going on and what you have already.

---

### Post by j0z on 2011-03-14
@forestpiskie

I just finished doing what you said.
Should i just post whatever the result here?
Does it contain anything privacy that i should censored?
(I am sorry, I don't know anything)

---

### Post by j0z on 2011-03-14
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   576,794,615   576,792,568   7 HPFS/NTFS
/dev/sda2         597,766,144   625,135,615    27,369,472   7 HPFS/NTFS
/dev/sda3         576,797,760   597,762,584    20,964,825   5 Extended
/dev/sda5         576,797,823   597,762,584    20,964,762  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        75C723FF796F19D0                       ntfs                                     
/dev/sda2        BA1AA45C1AA41781                       ntfs       RECOVERY                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        77738eee-240b-4f2f-8c9c-7d8b9d394733   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/77738eee-240b-4f2f-8c9c-7d8b9d394733 ext3       (rw,nosuid,nodev,uhelper=udisks)


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
default        0

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
# kopt=root=UUID=77738eee-240b-4f2f-8c9c-7d8b9d394733 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77738eee-240b-4f2f-8c9c-7d8b9d394733

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        77738eee-240b-4f2f-8c9c-7d8b9d394733
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=77738eee-240b-4f2f-8c9c-7d8b9d394733 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        77738eee-240b-4f2f-8c9c-7d8b9d394733
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=77738eee-240b-4f2f-8c9c-7d8b9d394733 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        77738eee-240b-4f2f-8c9c-7d8b9d394733
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


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
UUID=77738eee-240b-4f2f-8c9c-7d8b9d394733 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 301.4GB: boot/grub/menu.lst
 301.3GB: boot/grub/stage2
 301.2GB: boot/initrd.img-2.6.28-11-generic
 298.7GB: boot/vmlinuz-2.6.28-11-generic
 301.2GB: initrd.img
 298.7GB: vmlinuz
```

---

### Post by Elfy on 2011-03-14
Welcome back - no there's not anything private in that.

If you want to reinstall - boot with the iso - I assume that you're not using the 9.04 version, there would be little point in reinstalling that now it is EOL.

When you reach the partition stage - choose advanced - pick sda5 - edit partition, format as ext4 or ext3 and use / as the mount point. This will install over the original install.

_If you have data in your ubuntu you wish to keep - back it up._

---

### Post by j0z on 2011-03-14
Yea.
I've got ubuntu 10.10.

What if i want to uninstall it(now or later)?
Will i have any problem?

---

### Post by Elfy on 2011-03-14
Uninstalling is as simple as removing the partition and then reinstalling the bootloader for whatever other OS you are using. 

If you remove the partition without reinstalling the bootloader - you'll not boot anything till you do reinstall it.

Loads of net references to reinstalling windows bootloaders - there are even loads on here.

---

### Post by j0z on 2011-03-14
@Forestpiskie

People telling me that if i uninstall my ubuntu it will affect my windows.
It might be as worse as i can't even boot my windows anymore.
Is that true?
That's what i am afraid of.


By the way, thank you so much. You're so helpful.

---

### Post by Elfy on 2011-03-14
When you installed ubuntu - you also installed grub - this is a bootloader.

If you uninstall ubuntu you uninstall the bootloader.

Reinstall the windows bootloader and you'll be able to boot it - at least you should be able to.

---

### Post by j0z on 2011-03-14
Now i see. :).
I will try to re-install it tonight.

Thank you very much.

---

