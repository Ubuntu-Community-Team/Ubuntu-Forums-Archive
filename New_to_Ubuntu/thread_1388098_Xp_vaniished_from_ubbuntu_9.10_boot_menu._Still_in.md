---
title: "Xp vaniished from ubbuntu 9.10 boot menu. Still in menu.lst"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by nu2u904 on 2010-01-22
9.10 dual boot worked fine. Then Xpp diappeared. Xp still in menu.lst part below:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by mlentink on 2010-01-22
was this an upgrade or a fresh install? 
If it was the latter, you're using GRUB 2 which does not use menu.lst anymore

---

### Post by nu2u904 on 2010-01-22
> **mlentink said:**
> was this an upgrade or a fresh install? 
If it was the latter, you're using GRUB 2 which does not use menu.lst anymore
Thank  you mlentink. This 9.10 was an upgrade from 9..04. It allowed me to successfully dual boot until this week at which time Xp option disappeared from the boot menu and I was unable to boot into windows. I followed advice and did a sudo  update grub to no avail. Xp option is still missing.

---

### Post by ranch hand on 2010-01-22
You had better run this script and post the results file that ends up on your desktop;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

With the upgrade route you get files from both grub0.97 and grub1.97beta4.  I have no idea why that was thought to be a good idea but that is what it is.

You have finally, probably, fallen into a corruption caused by this.  Let us see the results of that script and we will sort this out.

If you are going to update 9.04 to 9.10 again (another box perhaps) remove grub and then install grub2 (it will be grub1.96) before the upgrade and it will go very well.

---

### Post by nu2u904 on 2010-01-23
> **ranch hand said:**
> You had better run this script and post the results file that ends up on your desktop;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

With the upgrade route you get files from both grub0.97 and grub1.97beta4.  I have no idea why that was thought to be a good idea but that is what it is.

You have finally, probably, fallen into a corruption caused by this.  Let us see the results of that script and we will sort this out.

If you are going to update 9.04 to 9.10 again (another box perhaps) remove grub and then install grub2 (it will be grub1.96) before the upgrade and it will go very well.
Thank you ranch hand. I downloaded the script and then followed command. This is what I got.

donald@donald-desktop:~$ sudo ~/Desktop/boot_info_script*.sh
[sudo] password for donald: 
sudo: /home/donald/Desktop/boot_info_script048.sh: command not found

What's wrong?

Earlier menu.lst
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
root

---

### Post by ranch hand on 2010-01-23
Well I am too whipped to deal wit hthat right now, brain dead.  I will get back to it in the morning.

Meanwhile you could run;
```

grub-install -v

```
to tell us what your box thinks it is using for a grub version.

---

### Post by meierfra. on 2010-01-23
Check that you actually have the script on the desktop and then use

```
sudo [COLOR="Red"]bash[/COLOR] ~/Desktop/boot_info_script*.sh
```


Also try

```
 sudo update-grub2 
```

---

### Post by nu2u904 on 2010-01-23
> **ranch hand said:**
> Well I am too whipped to deal wit hthat right now, brain dead.  I will get back to it in the morning.

Meanwhile you could run;
```

grub-install -v

```to tell us what your box thinks it is using for a grub version.
Thanks ranch hand :

donald@donald-desktop:~$ grub-install -v
grub-install (GNU GRUB 0.97)
donald@donald-desktop:~$

---

### Post by ranch hand on 2010-01-23
Well, it would still be nice to get the results from that script.  Copy command from the post by meierfra.  You left out "bash".

Your box thinks you are running on grub-legacy.  I bet that the script will show grub1.97 installed on the MBR.

If so we can fix this quite easily but we need to know what we are working with.

---

### Post by nu2u904 on 2010-01-23
> **ranch hand said:**
> Well, it would still be nice to get the results from that script.  Copy command from the post by meierfra.  You left out "bash".

Your box thinks you are running on grub-legacy.  I bet that the script will show grub1.97 installed on the MBR.

If so we can fix this quite easily but we need to know what we are working with.
Thank you ranch hand. Here are the RESUKTS:

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4faaccd1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,693,999     8,693,937   b W95 FAT32
/dev/sda2    *      8,694,000   371,180,879   362,486,880   7 HPFS/NTFS
/dev/sda3         371,180,880   390,715,919    19,535,040   5 Extended
/dev/sda5         371,180,943   389,778,479    18,597,537  83 Linux
/dev/sda6         389,778,543   390,715,919       937,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PRESARIO_RP" UUID="6F0C-69A4" TYPE="vfat" 
/dev/sda2: UUID="7864CF1764CED752" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda5: UUID="8ba45376-8bc4-4b84-afe2-957f2068b13a" TYPE="ext3" 
/dev/sda6: UUID="ef2521ee-04d1-4d24-b949-bd123a2abbf9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/donald/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=donald)
/dev/sr0 on /media/AMBITION_TO_MEA type udf (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,umask=0077)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

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
# kopt=root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8ba45376-8bc4-4b84-afe2-957f2068b13a

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

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        8ba45376-8bc4-4b84-afe2-957f2068b13a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
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
UUID=8ba45376-8bc4-4b84-afe2-957f2068b13a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ef2521ee-04d1-4d24-b949-bd123a2abbf9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 190.0GB: boot/grub/menu.lst
 190.0GB: boot/grub/stage2
 190.0GB: boot/initrd.img-2.6.28-16-generic
 190.0GB: boot/initrd.img-2.6.31-14-generic
 190.0GB: boot/initrd.img-2.6.31-15-generic
 190.0GB: boot/initrd.img-2.6.31-16-generic
 190.0GB: boot/initrd.img-2.6.31-17-generic
 190.0GB: boot/vmlinuz-2.6.28-16-generic
 190.0GB: boot/vmlinuz-2.6.31-14-generic
 190.0GB: boot/vmlinuz-2.6.31-15-generic
 190.0GB: boot/vmlinuz-2.6.31-16-generic
 190.0GB: boot/vmlinuz-2.6.31-17-generic
 190.0GB: initrd.img
 190.0GB: initrd.img.old
 190.0GB: vmlinuz
 190.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by meierfra. on 2010-01-23
It looks like XP got  pushed of the  computer screen by the new kernels, and you just have to use the "down arrow" key to scroll down to the XP entry.

I suggest to clean up  your Grub menu. Having two sets of kernels should be all you ever need:

Open "menu.lst" via
```
gksudo gedit /boot/grub/menu.lst
```

Change 

# howmany=all


to 

# howmany=2

Save the file. Back in the terminal

```
 sudo update-grub 
```

Reboot. Now your  XP entry should fit on the screen again.

---

### Post by ranch hand on 2010-01-23
> **meierfra. said:**
> It looks like XP got  pushed of the  computer screen by the new kernels, and you just have to use the "down arrow" key to scroll down to the XP entry.

I suggest to clean up  your Grub menu. Having two sets of kernels should be all you ever need:

Open "menu.lst" via
```
gksudo gedit /boot/grub/menu.lst
```Change 

# howmany=all


to 

# howmany=2

Save the file. Back in the terminal

```
 sudo update-grub 
```Reboot. Now your  XP entry should fit on the screen again.
Yup, sounds good to me.  That is a bunch of old kernels.

something th at you could do instead that would have the same result would be to go to synaptic and remove the kernels that are old.  Some folks like to keep the kernel before the one you are using "in case".  You are using up a lot of drive spacefor kernels you have no use for.

---

### Post by meierfra. on 2010-01-23
> something that you could do [COLOR="Red"]instead [/COLOR]that would have the same result 

I  would do it "in addition". Keeps the Grub menu clean, without having to delete kernels after each kernel updated.

> lot of drive spacefor kernels 
I'm  just to lazy to delete  kernels.  6 sets of kernels at 15MB each. Makes 90 MB on an 200GB drive.

---

### Post by ranch hand on 2010-01-23
> **meierfra. said:**
> I  would do it "in addition". Keeps the Grub menu clean, without having to delete kernels after each kernel updated.


I'm  just to lazy to delete  kernels.  6 sets of kernels at 15MB each. Makes 90 MB on an 200GB drive.
And, as a bonus, allows you to loose things on your overly crowded menu.

---

### Post by nu2u904 on 2010-01-24
> **meierfra. said:**
> It looks like XP got  pushed of the  computer screen by the new kernels, and you just have to use the "down arrow" key to scroll down to the XP entry.

I suggest to clean up  your Grub menu. Having two sets of kernels should be all you ever need:

Open "menu.lst" via
```
gksudo gedit /boot/grub/menu.lst
```

Change 

# howmany=all


to 

# howmany=2

Save the file. Back in the terminal

```
 sudo update-grub 
```

Reboot. Now your  XP entry should fit on the screen again.
Thank you meierfra and ranch hand for your winning solutions. I did this and it worked fine. Would it be wise to remove the other instances of the kernal and if so what is the procedure?

---

### Post by natravis on 2010-01-24
There are quite a few places all over the web that detail this, but here it is again:

[LIST]
[*]Open synaptic (System -> Administration -> Synaptic Package Manager)
[*]Search for "linux-image-" without quotes
[*]Remove all but the latest two (look at the last number in the name)
[*]It will look something like linux-image-2.6.31-17 (where 17 is the important number)
[/LIST]

---

