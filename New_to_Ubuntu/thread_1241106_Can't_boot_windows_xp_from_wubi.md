---
title: "Can't boot windows xp from wubi"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by blwhud on 2009-08-15
I was having trouble installing wubi from the internet, so I used the desktop CD.  All seemed to go well, but my machine was auto booting windows and not giving me the option to boot ubuntu.  So, I changed the default auto boot to ubuntu, it booted, installed and all seemed fine until I wanted to boot windows (XP). When I rebooted, windows was not an option. I installed the Startup-Manager to change the default back to windows, but again there is no windows option under "Default operating system".  Have I done something bad?

---

### Post by Megaptera on 2009-08-15
Did you partition your XP before installing Ubuntu? What install option did you use for Ubuntu - if you can recall ??

Using partition manager in Ubuntu, can you see XP on your hard drive somewhere? Possibly as 'OS' or 'C' ...

---

### Post by blwhud on 2009-08-15
No, I did not partition anything... I thought I was installing wubi which does not require any partitioning.

I can still see my windows dirs under /host   (Program Files, WINDOWS, Documents and Settings, etc)

---

### Post by louieb on 2009-08-15
Windows XP has a file **c:\boot.ini **- believe thats the file you need to fix. 

> I changed the default auto boot to ubuntu

How did you do that? Haven't used WUBI is that an install option?  

Anyway follow [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and put the results.txt file in your next post. Use code tags.  (instructions say to run from live CD but they will work from your WUBI install also)

The information will give a clearer picture of what needs to be done to fix.

---

### Post by blwhud on 2009-08-15
Quote:
                                                 I changed the default auto boot to ubuntu                                 
How did you do that? 

From windows, I selected the control panel, then system, then change the default auto boot from windows to ubuntu.

Sorry, I'm a newby with these posts and how to post things.
  The RESULTS.txt file is 306 lines long, so I hope I've done the "code" tag thing correctly.

 ```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x32843284

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="41d48c0f-ced5-498c-a62e-b1e2c851cc52" TYPE="ext3" 
/dev/sda1: UUID="46682428E41563CF" TYPE="ntfs" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/beck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=beck)
/dev/sr0 on /media/Ubuntu 9.04 i386 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
timeout        3

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
# kopt=root=UUID=46682428E41563CF loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=46682428E41563CF loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=46682428E41563CF loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=46682428E41563CF loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=46682428E41563CF loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Ubuntu
rootnoverify    (hd0,0)
savedefault
chainloader    +1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
default=C:\wubildr.mbr 
 
[operating systems] 
C:\wubildr.mbr="Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect 

================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda1: Location of files loaded by Grub: ===================


  24.4GB: ubuntu/disks/boot/grub/menu.lst
  26.3GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  26.4GB: ubuntu/disks/boot/initrd.img-2.6.28-14-generic
  25.0GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
  24.6GB: ubuntu/disks/boot/vmlinuz-2.6.28-14-generic
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by louieb on 2009-08-15
You did fine. 
This is your boot.ini 
```

[boot loader] 
default=C:\wubildr.mbr 
 
[operating systems] 
C:\wubildr.mbr="Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect 


```This is mine (no WUBI here)
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
Believe all you have to do is add the timeout=30 back in to c:\boot.ini.
Can do it from Ubuntu. or when you reboot the computer. Press F8 when windows is about to start to get the boot menu.

---

### Post by blwhud on 2009-08-15
Ok, so I added the timeout=30 to my boot.ini file, and it did let me choose windows to boot, but the boot failed with the following message:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file


I then tried to boot ubuntu and go a fsck error.  I was able to run this manually...it found a couple of inode errors and some other errors which I let it fix, and ubuntu came up normally.
I am now going to do some searching and see if I can figure out the other windows problem (it still will not boot)...

---

### Post by louieb on 2009-08-15
Thats kind of strange. hal.dll missing that is.  Have you browsed to see if its there? 

What did you use to edit boot.ini. If Linux I wonder if windows got confused.

In Linux a text line ends with a cr (carriage return) byte
In windows the line ends with a cr/lf pair (carriage return/line feed) 2 bytes. 

the only way I know to tell is to use the cat command

```
cat -A <path to c: drive>\boot.ini
```lines with linux ends will have a **$** sign at the end
lines with windows ens will show **^M$ ** at the end

---

### Post by blwhud on 2009-08-15
I did not initially have a windows cr/lf pair at the end of the line that I added in boot.ini at first, but I have fixed that.  
Also, the hal.dll file did not exist in the /host/WINDOWS/system32 directory, but I found a copy in the directory /host/WINDOWS/ServicePackFiles/i386/hal.dll and copied it to the system32 directory.

But I still get the same error when trying to boot windows.  If I take out the "timeout=30" line, then I can't keep ubuntu from starting.  Pressing F8 doesn't keep ubuntu from coming  up, and I can't figure out if there is a different key to get to the boot menu.

---

### Post by blwhud on 2009-08-15
I take that back, I can get to the boot mode, but without the "timeout=30" line, here are the options that I have to choose from:

ubuntu 9.04, kernel 2.6.28-14-generic
ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
ubuntu 9.04, kernel 2.6.28-11-generic
ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
ubuntu 9.04, memtest86+
(other operating systems: )
ubuntu

Windows is not an option.  I usually choose the last one, (ubuntu) , but I chose the first one this last time and didn't notice any diference.

---

### Post by louieb on 2009-08-16
It is F8 - want to get windows to boot into safe mode. and run chkdsk. 

The menu you got was grubs by that time it is too late.  

In a normal dual boot grub would come up 1st - then you would start pressing F8 after selecting windows.

But with a WUBI install windows has control of the MBR and it gets loaded 1st then passes control to Grub.  Saw one article that said shutdown computer and wait 30 seconds before turning it on again.     

Looks like the menu you saw was sda1/ubuntu/disks/boot/grub/menu.lst

---

### Post by blwhud on 2009-08-16
Yes, F8 works and I can get to the right menu now, but windows will not even boot in safe mode. I still get the same hal.dll error message.  
I am going to do some searching and see if I can maybe get into debug mode and find out what is really wrong with windows...

---

### Post by blwhud on 2009-08-16
Ok....so I found my problem.... turns out that the problem was with my boot.ini file:
 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect
 
should be:
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
 
Not sure when WINDOWS changed to WINNT
 
Thanks for all your help :)

---

### Post by louieb on 2009-08-17
> **blwhud said:**
> 
Not sure when WINDOWS changed to WINNT
Thanks for all your help :)

:guitar: lol did not even think about that being a part of the path. Great Good Luck.

BTW: Scrool to the bottom of the thread and add a solved tag: so other will know.

---

