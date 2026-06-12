---
title: "Grub Dual Boot Problems Ubuntu and XP"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by spahr on 2009-11-07
I have separate hard drives for Ubuntu and XP.  I have been trying to config grub so that I can choose which system to boot from.  I went to sudo gedit /boot/grub/menu.lst and added the following at the bottom of the list:

title Windows XP
root (hd0,0)
makeactive
chainloader +1

I double checked to make sure root (hd0,0) was correct by running  - sudo fdisk -l.

XP hard drive is /dev/sda1

Now when I boot, I see the option for XP, but when I choose it I receive the following error message...error 13: invalid or unsupported executable format.

Can anyone tell me what I am doing wrong?  

Thanks in advance, 
spahr

---

### Post by LewRockwell on 2009-11-07
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by spahr on 2009-11-07
Ubuntu still starts if I choose it.  XP however does not.  I am looking for feedback about my approach.  Does it appear I have done everything correctly?

---

### Post by LewRockwell on 2009-11-07
> **spahr said:**
> Ubuntu still starts if I choose it.  XP however does not.  I am looking for feedback about my approach.  Does it appear I have done everything correctly?

did you have your hardware set up exactly as you have it now when you installed ubuntu and grub?

if your drives are on the same cable then they will probably need to be set properly as far as "slave" and "master" goes

.

---

### Post by LewRockwell on 2009-11-07
> **spahr said:**
> Ubuntu still starts if I choose it.  XP however does not.  I am looking for feedback about my approach.  Does it appear I have done everything correctly?

Super Grub Disk will find and start Windows if it's not corrupted

.

---

### Post by spahr on 2009-11-07
No, to be safe, I disconnected my XP hard drive  when I installed Ubuntu and then reconnected after the set up.  Since then, I have mounted the XP hard drive and can view the files on it thru Ubuntu.  I am using sata hds.

---

### Post by kansasnoob on 2009-11-07
> **spahr said:**
> I have separate hard drives for Ubuntu and XP.  I have been trying to config grub so that I can choose which system to boot from.  I went to sudo gedit /boot/grub/menu.lst and added the following at the bottom of the list:

title Windows XP
root (hd0,0)
makeactive
chainloader +1

I double checked to make sure root (hd0,0) was correct by running  - sudo fdisk -l.

XP hard drive is /dev/sda1

Now when I boot, I see the option for XP, but when I choose it I receive the following error message...error 13: invalid or unsupported executable format.

Can anyone tell me what I am doing wrong?  

Thanks in advance, 
spahr

Assuming that (hd0,0) is correct I'd try:

> title        Windows XP
root        (hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

It's called drive "mapping".

---

### Post by LewRockwell on 2009-11-07
> **spahr said:**
> No, to be safe, I disconnected my XP hard drive  when I installed Ubuntu and then reconnected after the set up.  Since then, I have mounted the XP hard drive and can view the files on it thru Ubuntu.  I am using sata hds.

you might try hd1,0 since your windows drive is probably being recognized as hd1 by grub

.

---

### Post by spahr on 2009-11-07
I have tried that and the screen just freezes.

---

### Post by kansasnoob on 2009-11-07
> **spahr said:**
> I have tried that and the screen just freezes.

You tried "mapping" or what?

---

### Post by kansasnoob on 2009-11-07
Please just post the output of the following commands:

```
sudo fdisk -l
```

```
grub-install -v
```

```
ls /boot/grub
```

```
cat /boot/grub/menu.lst
```

---

### Post by spahr on 2009-11-07
I'm not sure what you mean by mapping (with Ubuntu) is that the same as mounting?

---

### Post by kansasnoob on 2009-11-07
> **spahr said:**
> I'm not sure what you mean by mapping (with Ubuntu) is that the same as mounting?

Did you read my post #7?

---

### Post by spahr on 2009-11-07
sudo fdisk - l
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d570d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77824   625121248+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37213721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121600   976751968+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23539ed8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18662   149902483+  83  Linux
/dev/sdc2           18663       19457     6385837+   5  Extended
/dev/sdc5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdd: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders
Units = cylinders of 16002 * 512 = 8193024 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1955    15641929    c  W95 FAT32 (LBA)

grub-install-v
grub-install (GNU GRUB 0.97)

ls /boot/grub
default     e2fs_stage1_5  installed-version  menu.lst   menu.lst.backup  reiserfs_stage1_5  stage1  xfs_stage1_5
device.map  fat_stage1_5   jfs_stage1_5       menu.lst~  minix_stage1_5   splashimages       stage2

cat /boot/grub/menu.lst
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d570d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77824   625121248+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37213721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121600   976751968+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23539ed8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18662   149902483+  83  Linux
/dev/sdc2           18663       19457     6385837+   5  Extended
/dev/sdc5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdd: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders
Units = cylinders of 16002 * 512 = 8193024 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1955    15641929    c  W95 FAT32 (LBA)
beth@bethsubuntu:~$ 
beth@bethsubuntu:~$ ^V
beth@bethsubuntu:~$ grub-install -v
grub-install (GNU GRUB 0.97)
beth@bethsubuntu:~$ ls /boot/grub
default     e2fs_stage1_5  installed-version  menu.lst   menu.lst.backup  reiserfs_stage1_5  stage1  xfs_stage1_5
device.map  fat_stage1_5   jfs_stage1_5       menu.lst~  minix_stage1_5   splashimages       stage2
beth@bethsubuntu:~$ cat /boot/grub/menu.lst
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
timeout        5

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
# kopt=root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a60c23e-1dca-46b9-884b-dc0a7987d719

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
# defoptions=splash vga=795

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro splash vga=795 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro splash vga=795 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/memtest86+.bin
quiet

title        Windows XP
root        (hd0,0)
makeactive
chainloader    +1

---

### Post by spahr on 2009-11-07
I'm sorry...not I did not.  I didn't realize there are now 2 pages of posts.  I just joined this forum an hour ago and this is my first post..  I will try your advice in #7 now

---

### Post by kansasnoob on 2009-11-07
**[COLOR="Red"]OOPS! Wait, I see you have more drives than I thought![/COLOR]**

The bottom of the menu.lst should be like this (additions in bold):

> title Ubuntu 9.04, memtest86+
uuid 0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel /boot/memtest86+.bin
quiet

[B]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Windows XP
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 [/B]


---

### Post by spahr on 2009-11-07
I feel like an idiot...now it boots directly to XP and I do not have an "Ubuntu"option to choose from.  I am assuming this is due to "savedefault".  How do I set up so I can choose Ubuntu or XP?  I not sure how to even get into Ubuntu now to change anything.

---

### Post by kansasnoob on 2009-11-07
Well, this is more complicated than I thought, 4 hard drives and both sda1 and sdb1 have boot flags (*):

> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d570d56

Device Boot Start End Blocks Id System
**/dev/sda1 * 1 77824 625121248+ 7 HPFS/NTFS**

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37213721

Device Boot Start End Blocks Id System
[B]/dev/sdb1 * 1 121600 976751968+ 7 HPFS/NTFS
[/B]
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23539ed8

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 18662 149902483+ 83 Linux
/dev/sdc2 18663 19457 6385837+ 5 Extended
/dev/sdc5 18663 19457 6385806 82 Linux swap / Solaris

Disk /dev/sdd: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders
Units = cylinders of 16002 * 512 = 8193024 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdd1 1 1955 15641929 c W95 FAT32 (LBA)


So what's what? Do you have two Windows operating systems?

---

### Post by spahr on 2009-11-07
I have three hds...640 GB has XP / 1000 GB storage only no OS / 160 GB has Ubuntu

---

### Post by LewRockwell on 2009-11-07
> **kansasnoob said:**
> Well, this is more complicated than I thought, 4 hard drives and both sda1 and sdb1 have boot flags (*):



So what's what? Do you have two Windows operating systems?


three boot flags

sda1

sdb1

sdc1

---

### Post by LewRockwell on 2009-11-07
> **spahr said:**
> I have three hds...640 GB has XP / 1000 GB storage only no OS / 160 GB has Ubuntu

sdd1 ?

.

---

### Post by LewRockwell on 2009-11-07
> **spahr said:**
> I feel like an idiot...now it boots directly to XP and I do not have an "Ubuntu"option to choose from.  I am assuming this is due to "savedefault".  How do I set up so I can choose Ubuntu or XP?  I not sure how to even get into Ubuntu now to change anything.

you can use the LiveCD test-drive function to boot into Ubuntu and edit the menu.lst file

your machine has decided to observe one of your other boot flags and boot directly into XP

you can also remove the boot flags via the partition editor while running Ubuntu via the LiveCD

.

---

### Post by LewRockwell on 2009-11-07
don't worry, you'll figure it out AND get some ed-you-cation at the same time

lol

.

---

### Post by spahr on 2009-11-07
I don't know why there are three.  The one on sdb1 doesn't make sense.  It's only a back up, storage, drive.

---

### Post by kansasnoob on 2009-11-07
> **spahr said:**
> I have three hds...640 GB has XP / 1000 GB storage only no OS / 160 GB has Ubuntu

So sdd must be a flash drive or a memory card?

When you say it boots straight to XP does a grub boot menu even show up now? Possibly with only the Windows XP option or does no grub menu show up at all?

If sda is the true Windows boot drive I can now see that sdc is the Ubuntu drive so **I had the mapping wrong!**

I think it should have been:

> title Ubuntu 9.04, memtest86+
uuid 0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel /boot/memtest86+.bin
quiet

[B]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1[/B] 

Regardless, if you can't boot Ubuntu we'll have to work on this from the Live CD, that is booting the Live CD and choosing "Try Ubuntu without changes to disc", but you might try booting the live CD and choosing "Boot first hard disc" and seeing if it goes to Windows or Ubuntu.

But this is complex enough I really need to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It works equally well from either the Ubuntu desktop or the live CD.

---

### Post by spahr on 2009-11-07
I just rebooted and this time grub loaded and I have a choice between Ubuntu and XP.  However, when I choose XP I still get .error 13: invalid or unsupported executable format.

I have added "bold" notes to the bottom of my menu list.

---

### Post by spahr on 2009-11-07
I updated the menu list with your most recent mappings and still receive an error message when I choose XP.

---

### Post by spahr on 2009-11-07
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d570d56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,250,242,559 1,250,242,497   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37213721

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23539ed8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   299,805,029   299,804,967  83 Linux
/dev/sdc2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdc5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="18CCE5A7CCE57F7E" LABEL="Main HD" TYPE="ntfs" 
/dev/sdb1: UUID="C654E38C54E37D95" LABEL="Back Up HD" TYPE="ntfs" 
/dev/sdc1: UUID="0a60c23e-1dca-46b9-884b-dc0a7987d719" TYPE="ext3" 
/dev/sdc5: UUID="61067a07-30b2-4994-ae19-5b1794a8dcdb" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/beth/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=beth)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout        5

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
# kopt=root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a60c23e-1dca-46b9-884b-dc0a7987d719

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
# defoptions=splash vga=795

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro splash vga=795 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro splash vga=795 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title         Windows XP
rootnoverify     (hd0,0)
savedefault
makeactive
map         (hd0) (hd2)
map         (hd2) (hd0)
chainloader    +1

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=61067a07-30b2-4994-ae19-5b1794a8dcdb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  91.4GB: boot/grub/menu.lst
  91.5GB: boot/grub/stage2
  91.4GB: boot/initrd.img-2.6.28-11-generic
  91.4GB: boot/initrd.img-2.6.28-15-generic
  91.4GB: boot/initrd.img-2.6.28-16-generic
  91.4GB: boot/vmlinuz-2.6.28-11-generic
  91.4GB: boot/vmlinuz-2.6.28-15-generic
  91.4GB: boot/vmlinuz-2.6.28-16-generic
  91.4GB: initrd.img
  91.4GB: initrd.img.old
  91.4GB: vmlinuz
  91.4GB: vmlinuz.old

---

### Post by kansasnoob on 2009-11-07
I really need to see the results from this:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by LewRockwell on 2009-11-07
please place long posts inside code boxes

```
> **spahr said:**
> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d570d56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,250,242,559 1,250,242,497   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37213721

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,503,999 1,953,503,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23539ed8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   299,805,029   299,804,967  83 Linux
/dev/sdc2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdc5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="18CCE5A7CCE57F7E" LABEL="Main HD" TYPE="ntfs" 
/dev/sdb1: UUID="C654E38C54E37D95" LABEL="Back Up HD" TYPE="ntfs" 
/dev/sdc1: UUID="0a60c23e-1dca-46b9-884b-dc0a7987d719" TYPE="ext3" 
/dev/sdc5: UUID="61067a07-30b2-4994-ae19-5b1794a8dcdb" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/beth/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=beth)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout        5

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
# kopt=root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a60c23e-1dca-46b9-884b-dc0a7987d719

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
# defoptions=splash vga=795

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro splash vga=795 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro splash vga=795 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0a60c23e-1dca-46b9-884b-dc0a7987d719
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title         Windows XP
rootnoverify     (hd0,0)
savedefault
makeactive
map         (hd0) (hd2)
map         (hd2) (hd0)
chainloader    +1

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=61067a07-30b2-4994-ae19-5b1794a8dcdb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  91.4GB: boot/grub/menu.lst
  91.5GB: boot/grub/stage2
  91.4GB: boot/initrd.img-2.6.28-11-generic
  91.4GB: boot/initrd.img-2.6.28-15-generic
  91.4GB: boot/initrd.img-2.6.28-16-generic
  91.4GB: boot/vmlinuz-2.6.28-11-generic
  91.4GB: boot/vmlinuz-2.6.28-15-generic
  91.4GB: boot/vmlinuz-2.6.28-16-generic
  91.4GB: initrd.img
  91.4GB: initrd.img.old
  91.4GB: vmlinuz
  91.4GB: vmlinuz.old
```

thanks

.

---

### Post by LewRockwell on 2009-11-07
> **LewRockwell said:**
> you can use the LiveCD test-drive function to boot into Ubuntu and edit the menu.lst file

you can also remove the boot flags via the partition editor while running Ubuntu via the LiveCD

did you remove those other boot flags yet?

.

---

### Post by spahr on 2009-11-07
I just noticed a thumb drive my child had in the computer and have removed it.  It makes sense now why you thought there were 4.  Sorry about that...

---

### Post by LewRockwell on 2009-11-07
> **spahr said:**
> I just noticed a thumb drive my child had in the computer and have removed it.  It makes sense now why you thought there were 4.  Sorry about that...

just as long as there isn't oatmeal in the optical drives...lol

.

---

### Post by spahr on 2009-11-07
Thats all I need right now...lol

---

### Post by kansasnoob on 2009-11-07
Well, according to this:

> => Windows is installed in the MBR of /dev/sda
=> Windows is installed in the MBR of /dev/sdb
=> Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

The XP bootloader is still installed to the sda MBR so instead of mapping like I'd thought this **[COLOR="Red"]may[/COLOR]** work better:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title        Chainload First Hard Disk's MBR
root        (hd0)
chainloader    +1

**[COLOR="Red"]That's a HUGE maybe![/COLOR]**

---

### Post by spahr on 2009-11-07
I tried it and at first it looks like XP may load...goes further than it normally did when I chose "chainload first  hard disks MBR.  But it loops around and asks me to choose again.  I finally chose Ubuntu.  

I just want to thank you for trying so hard to help me.  I really don't know what else to do at this point.  You have put considerable time into this trying to help.  I don't expect you to continue working on this as I'm sure you have other things to do.  I really appreciate you help.  If you think of anything new, please post and I will try.  But, please do not think you have to keep working on this.  

Thanks so much...

---

### Post by kansasnoob on 2009-11-07
If you're still game I'd like to try one more thing. In my last "mapping" attempt I intentionally changed root to rootnoverify, so I think it's worth trying:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title Windows XP
root (hd0,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

If that doesn't work I'm somewhat stumped anyway.

The only other thing I'd know to do is reinstall grub .......... errm, let me explain a bit. The boot info script shows:

> # / was on **/dev/sda1** during installation
UUID=0a60c23e-1dca-46b9-884b-dc0a7987d719 / ext3 relatime,errors=remount-ro 0 1
# swap was on **/dev/sda5** during installation

So I'm guessing you had the Windows drives disconnected while installing Ubuntu to the new drive (sdc). Not at all a bad idea really but sometimes finding the correct connection configuration and setting the BIOS boot sequence to match can be almost mind boggling.

Anyway what I'm thinking may work (no guarantees) is reinstalling grub and choosing to install it to the mbr of sda1. The drawback of course would be that doing so overwrites the Windows MBR so if you ever remove Ubuntu then XP will no longer boot until it's OEM MBR is restored which is fairly simple and even if you don't have the XP install/repair disk CNET has after-market repair discs for free that will work.

It's not incredibly difficult but there is always some risk involved. I'd also want to know what "mix" of drives we're working with, all SATA, all IDE, or a mix of the two?

I really wish we'd hear from someone else. There used to be two people here that were absolutely fantastic at these boot problems.

One is meierfra who actually created the Boot Info Script which is a great tool, but I really hate PMing folks.

The other is caljohnsmith who I used to correspond with and I fear he fell victim to ill health as our last communication several months ago indicated that he'd been recently hospitalized.

BTW you're not an idiot!

Now I was an idiot for not reading the output of your fdisk -l more closely before spewing my first suggestion.

I do believe the proper boot command in the menu.lst could fix this, I'm just out of ideas.

---

### Post by kansasnoob on 2009-11-07
If you're so inclined you could try sending meierfra a very brief PM asking if he might have time to take a quick look at this thread.

[http://ubuntuforums.org/member.php?u=552151](http://ubuntuforums.org/member.php?u=552151)

Also feel free to PM me, just keep it brief and we'll keep the bulk of our communications here at the forums so others can see how incredibly stupid I can be:p

---

### Post by spahr on 2009-11-08
Good morning, I tried your latest suggestion for the menu.list and receive the same error message.

I did have my XP disk disconnected when I installed Ubuntu.  Since I'm so new to all of this I did so for safety reasons...

All of my hard drive are SATA.

I'm a little concerned about reinstalling GRUB, only because I cant afford to have XP down right now.  I do have my XP cd so I would be able to repair if needed.  I jsut don't know how to do that.

Again, I really appreciate eveything you have done for me.  All though the boot issue is still a problem...I have learned a lot from you here in a short time.  Thank you!

I may  contact meierfra to see if he would consider looking into this for me.

Thanks again!

---

### Post by kansasnoob on 2009-11-08
I'm still in hopes someone else really brilliant will see this and have a suggestion.

I can't help but feel that I'm overlooking something incredibly simple.

---

### Post by spahr on 2009-11-08
No worries...it's all part of the learning process.  I am still considering contacting meierfra - I want to do a little research on my end before doing so. 

Thanks again for everything.  This was my first forum experience and you have been great.  I will update the post if / when I get this working.

---

### Post by yanceypd on 2009-11-08
Ther are a lot of posts here just want to make sure the data drive isn't the last one on a cable and that the jumper pins aren't set to master.

---

### Post by cslav on 2009-11-08
hi!...you my have inadvertently erased the MBR (master boot record) for XP.  You can recover this by installing your system disk for XP and proceed to recovery mode.  From there you can select the DOS command FIXMBR, and you should be good to go from there.  Hope this may help.

---

### Post by kansasnoob on 2009-11-09
Thought I'd give this a shameless bump to see if some fresh eyes can see what I'm doing wrong.

I actually do have an idea and I'll try to post it here much later today. I just don't have time to be painstakingly accurate right now.

---

### Post by oldfred on 2009-11-09
Drive order in BIOS is vital to how the system boots. The system will only boot from the MBR in the first drive as defined by the BIOS.

You can (and I maintain you should) have boot in other drives MBR if their is a operating system on that drive. that way you can switch drives in BIOS if the first fails and use the other drive without having to find a recovery CD.

When you installed Ubuntu without the windows drive it was either the first or second drive and installed its grub boot to the MBR. It would normally find windows and automatically add the windows boot but because the windows was not there it has to be manually added. Now the drive order becomes critical. If the windows drives is first it will boot to windows and not see grub. If the Ubuntu drive is first it will boot ubuntu and then you can add the windows stanza with the map commands to make windows think it is first. The may may be 1 or 2 to 0 since there are three drives.

Often the normal install keeps windows on the first drive and installs grub over the windows MBR. Grub then points to the second drive or later partition to boot.

Make the Ubuntu drive first in BIOS so grub boots. One of the windows stanza with the map commands previously posted should work depending on which drive windows is in the BIOS order. Entry map be hd1 depending on drive order. Makeactive is not required if the boot flag (*) is on.

title Windows XP
rootnoverify (hd0,0)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by spahr on 2009-11-11
Thanks to all that have tried to help.  When trying to boot to where I have Ubuntu installed, I change the bios boot priority to that drive.

I have this currently added to the grub menu list:  

When I choose Windows XP, I receive an error message.  From there I select Ubuntu and the system starts Ubuntu just fine.

title Windows XP
rootnoverify (hd0,0)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

Windows XP will boot fine if I select that hd in the bios boot priority.

It sounds like everything would have been ok had I kept my XP hd connected during the Ubuntu install.  

Some people have mentioned that I could have erased the MBR (master boot record) for XP.  If that were the case wouldn't that mean XP wouldn't boot, period?

---

