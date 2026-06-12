---
title: "dual boot worked yesterday, now ntldr says its missing"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by stinger30au on 2009-08-13
G'day

i have found a wierd problem with dual boot 9.04

xp pro on ide hdd 0 and ubuntu

dual boot worked fine yesterday

today dual boot works and ubuntu works fine

windows if you start it it says

NTLDR missing

*BUT*

if you go to the windows hdd and look 

NTLDR file is there and it is 244.2kilobytes long

windows also started off the dual boot about half a dozen times
 before it spat the dummy and give this error
what gives???

any ideas?

---

### Post by Paqman on 2009-08-13
It sounds like Grub can't find NTLDR. Can you post the contents of /boot/grub/menu.lst and the output of:
```

fdisk -l

```
and
```
sudo blkid
```

---

### Post by stinger30au on 2009-08-13
this command

fdisk -l



gave me no output

sudo blkid
[sudo] password for frank: 
/dev/sda1: UUID="709C6B919C6B5120" LABEL="data" TYPE="ntfs" 
/dev/sdb1: UUID="2E587B6C587B3227" LABEL="data2" TYPE="ntfs" 
/dev/sdc1: UUID="46802C4B802C43B1" LABEL="home" TYPE="ntfs" 
/dev/sdc5: UUID="5912bc8e-1a23-494f-8b51-e716cb41e238" TYPE="ext3" 
/dev/sdc6: TYPE="swap" UUID="eec265f6-eef7-4c99-a32c-6a8730f1dfcc" 

and the menu list file says this

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
# kopt=root=UUID=5912bc8e-1a23-494f-8b51-e716cb41e238 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5912bc8e-1a23-494f-8b51-e716cb41e238

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
uuid        5912bc8e-1a23-494f-8b51-e716cb41e238
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5912bc8e-1a23-494f-8b51-e716cb41e238 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        5912bc8e-1a23-494f-8b51-e716cb41e238
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5912bc8e-1a23-494f-8b51-e716cb41e238 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5912bc8e-1a23-494f-8b51-e716cb41e238
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5912bc8e-1a23-494f-8b51-e716cb41e238 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5912bc8e-1a23-494f-8b51-e716cb41e238
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5912bc8e-1a23-494f-8b51-e716cb41e238 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5912bc8e-1a23-494f-8b51-e716cb41e238
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

---

### Post by gabry79Italy on 2009-08-14
Try:
sudo -s
apt-get install ntfsprogs
ntfsfix /dev/sdc1
exit
reboot your pc into windows

---

### Post by Mark Phelps on 2009-08-14
> **gabry79Italy said:**
> Try:
sudo -s
apt-get install ntfsprogs
ntfsfix /dev/sdc1
exit
reboot your pc into windows

I'll be interested in hearing if this works because, according to the ntfsfix man entry:

ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows. 

Thus, unless it's really a basic problem, all ntfsfix will do is "mark" the partition so that, when MS Windows boots the next time, it will run a chkdsk on it.

So ... since the op apparently can NOT boot into MS windows (because it can't find the NTLDR), how exactly are they supposed to then run chkdsk?

---

### Post by stinger30au on 2009-08-14
> **gabry79Italy said:**
> Try:
sudo -s
apt-get install ntfsprogs
ntfsfix /dev/sdc1
exit
reboot your pc into windows

installed the program and tried this

ntfsfix /dev/sdc1

got this error

Refusing to operate on read-write mounted device /dev/sdc1.

tried this
sudo ntfsfix /dev/sdc1

Refusing to operate on read-write mounted device /dev/sdc1.

any ideas?

---

### Post by stinger30au on 2009-08-15
just did a quick google and found this

[http://support.microsoft.com/kb/320397](http://support.microsoft.com/kb/320397)

---

### Post by stinger30au on 2009-08-15
[this is interesting]("http://ubuntuforums.org/archive/index.php/t-487214.html")

[dunno this will help]("http://www.fixya.com/support/t235087-ntldr_missing")

this might be the go too

sudo apt-get install startupmanager

this post looks like it might be the goods
[http://ubuntuforums.org/showthread.php?t=979623](http://ubuntuforums.org/showthread.php?t=979623)

ah ha, must be like this

sudo fdisk -l

---

### Post by gabry79Italy on 2009-08-15
sudo -s
umount /dev/sdc1
ntfsfix /dev/sdc1
exit

---

### Post by LewRockwell on 2009-08-15
pssst

supergrubdisk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by stinger30au on 2009-08-15
sudo fdisk -l
[sudo] password for frank: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd783d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd783d784

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7bcc7bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         157        5859    45809347+   7  HPFS/NTFS
/dev/sdc2            5860        9733    31117905    5  Extended
/dev/sdc5            5860        9568    29792511   83  Linux
/dev/sdc6            9569        9733     1325331   82  Linux swap / Solaris

+++++++++++++++++++++++++++++++++

 umount /dev/sdc1
root@frank-desktop:~# ntfsfix /dev/sdc1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdc1 was processed successfully.
root@frank-desktop:~# exit
exit

---

### Post by stinger30au on 2009-08-15
> **gabry79Italy said:**
> sudo -s
umount /dev/sdc1
ntfsfix /dev/sdc1
exit

did that, see my previous post

reboot, same thing, NTLDR missing

but if you look at the hdd via nautilus, it is definitely there

---

### Post by stinger30au on 2009-08-15
fixx it , it works like a charm

i went to  a post i found yestersay here

[http://ubuntuforums.org/showthread.php?t=979623](http://ubuntuforums.org/showthread.php?t=979623)

and i did this

 				 				**Re: Dual Boot "NTLDR is missing" Win XP Error.** 			
 			 			 		   		 		 		Since Windows XP is on the same drive as Ubuntu, just replace your existing Windows entry in your menu.lst with:
 	Code:
 	title Windows XP
root (hd0,0)
chainloader +1 
And I should mention, you can modify your menu.lst with:
 	Code:
 	gksudo gedit /boot/grub/menu.lst 
Give that a shot and let us know how it goes. :smile:
+++++++++++++++++++++++++++++++++++++++++
i also made a backup of the menu.lst file first before modify

now xp boots again and ubuntu boots together just fine

both o/s are on the first ide hdd in this pc

i wonder why xp magically stopped booting

strange

anyhoo, its fixxed now, thanks for all the help

---

