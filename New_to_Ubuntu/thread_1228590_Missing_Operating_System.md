---
title: "Missing Operating System"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Tamachan87 on 2009-08-01
I've been dual-booting Ubuntu 9.04 and Vista for a while in a rather ham-handed way (I have to hit F12 at boot at tell it which HDD to boot from) but recently Ubuntu's been acting up.

I did my usual boot and it simply said "Missing Operating System". No Grub error, no error number, just "Missing Operating System". If I use SuperGrub to reinstall the Grub menu it'll appear but still not boot (and won't boot into Vista either, for some reason) however if I tell SuperGrub to simply boot into Linux then everything's hunky dory (I'm using it now).

Any idea what's going on? Complete newbie here.

:popcorn:

---

### Post by la3875 on 2009-08-01
Well... I'm by no means an expert but have been dual booting with two drives without incident since 5.10. I recommend you head over to Hermanzone to see if there is a solution. It has been a great resource for me setting up both dual boot and recovering my MBR for Windows.

Best

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Sef on 2009-08-01
Applications > Accessories > Terminal

then copy and paste this command in the Terminal:

```
sudo fdisk -l
```

copy and paste the results here.

---

### Post by Tamachan87 on 2009-08-01
Here:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f5f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29650   238163593+  83  Linux
/dev/sda2           29651       30401     6032407+   5  Extended
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbeb0cd11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8775e600

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30402   244195328    7  HPFS/NTFS

```

The NTFS drive is Vista and the 1TB HDD is just for storing files.

---

### Post by Shig on 2009-08-01
It looks like the master boot record on your first hard drive has gotten munged.
Re-installing Grub will fix that up, but unless your configuration files that are there match the hard disk layout then you will have a lot of trouble getting into other operating systems.

Here is a great post linking many other posts, that all have thorough instructions for reconfiguring dual-boot on separate drives using Grub:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Hope this helps!

---

### Post by Sef on 2009-08-01
Not sure why you have all three set to boot, but I see something else that may or may not be a problem depending on how it is set up.   Windows needs to be on the first primary partition, is it?

---

### Post by louieb on 2009-08-01
Have you had a recent hardware change? Like adding the 1TB data drive? or changeling where the drives plug into the motherboard? Did the problem start right after that? 

The missing operating system message just means there is no boot code in the MBR of the boot drive.

Run this script the information in the results.txt will help get things sorted out. If questions attach the results.txt in your next post.   [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

---

### Post by Tamachan87 on 2009-08-01
The boot order goes CD/DVD, then the Windows drive, then the 1TB HDD (dunno why) then the Linux drive. If I just turn my computer on it'll boot straight into Vista no problems. I have no idea why the 1TB HDD is set to boot, it has no OS on it. It's visible in both Vista and Ubuntu, so I use it to share files between OS's.

And the spare HDD was there from before I installed Ubuntu.

---

### Post by Tamachan87 on 2009-08-01
Results.txt

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002f5f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   476,327,249   476,327,187  83 Linux
/dev/sda2         476,327,250   488,392,064    12,064,815   5 Extended
/dev/sda5         476,327,313   488,392,064    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbeb0cd11

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8775e600

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   488,392,703   488,390,656   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0970c93c-95fe-4166-a850-615bc24df04f" TYPE="ext3" 
/dev/sda5: UUID="34ce7d34-863b-46db-a9ce-1bec7fb429fb" TYPE="swap" 
/dev/sdb1: UUID="B68AB4A88AB46711" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc1: UUID="E88E28368E27FBA6" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/richard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richard)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=richard)
/dev/sdb1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0970c93c-95fe-4166-a850-615bc24df04f

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
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0970c93c-95fe-4166-a850-615bc24df04f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0970c93c-95fe-4166-a850-615bc24df04f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34ce7d34-863b-46db-a9ce-1bec7fb429fb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 207.6GB: boot/grub/menu.lst
 207.6GB: boot/grub/stage2
 207.5GB: boot/initrd.img-2.6.28-11-generic
 207.6GB: boot/initrd.img-2.6.28-13-generic
  50.2GB: boot/initrd.img-2.6.28-14-generic
 207.5GB: boot/vmlinuz-2.6.28-11-generic
 207.6GB: boot/vmlinuz-2.6.28-13-generic
 207.6GB: boot/vmlinuz-2.6.28-14-generic
  50.2GB: initrd.img
 207.6GB: initrd.img.old
 207.6GB: vmlinuz
 207.6GB: vmlinuz.old

============================== sdc1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 
 
## ## End Default Options ## 
 
 
 
title        Ubuntu 9.04, kernel 2.6.28-14-generic 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic 
quiet 
 
 
title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro  single 
initrd        /boot/initrd.img-2.6.28-14-generic 
 
 
title        Ubuntu 9.04, kernel 2.6.28-13-generic 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic 
quiet 
 
 
title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro  single 
initrd        /boot/initrd.img-2.6.28-13-generic 
 
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro quiet splash  
initrd        /boot/initrd.img-2.6.28-11-generic 
quiet 
 
 
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0970c93c-95fe-4166-a850-615bc24df04f ro  single 
initrd        /boot/initrd.img-2.6.28-11-generic 
 
 
title        Ubuntu 9.04, memtest86+ 
uuid        0970c93c-95fe-4166-a850-615bc24df04f 
kernel        /boot/memtest86+.bin 
quiet
```

---

### Post by louieb on 2009-08-01
Just trying to figure out whats going on,  Very confusing. 
>  => Windows is installed in the MBR of /dev/sda
but fdisk shows  Ubuntu is on sda1. 
also noticed a menu.lst generated by EBCD on the windows drive 1st partition.  sdc. Did the problems start after trying  out EBCD?    

> Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.



and GRUB stage1 code is in the MBR of the other 2 drives and is looking in the  boot drive 3 for Ubuntu on sdc.  

Sounds like the boot order has changed.  Either by you going into bios and changing the order. or by EBCD. 

Got to think about this one for a while.  Ideally you would want the MBR of the VISTA drive to load vista.  And the MBR of the Ubuntu drive to load GRUB inside the Ubuntu install. 

1st thing I would do is shutdown, unplug the Ubuntu and 1TB drives then see if it will boot - don't think it will - if it does then there is something wrong with the Boot info script. 

If it doesn't boot  use the Super GRUB disk to fix the MBR of the window drive to boot VISA - Reboot and test. 

Then I would shutdown unplug the window drive plug in the Ubuntu drive Use Super GRUB to fix its MBR. Reboot and test. 

One thing to remember boot order is important to GRUB it uses boot order to tell which drive is which.  
Ubuntu used UUID to tell which partitions it needs to boot so boot order is not important. 

After plugging all the drives back in test to see if it all works again. IF not then may have to play with the boot order is BIOS. 

On some PC's  permanent changes  to boot order can be made in BIOS setup. While temporary changes are made by the select boot device option at startup.

---

### Post by Tamachan87 on 2009-08-01
> **louieb said:**
> Did the problems start after trying  out EBCD? 

Yeah, I was trying to make it easier to dual boot but I've sorted the problem out, thanks.

Turns out the order which the drives appeared in the F12 Boot screen had been switched, I just didn't notice it. After selecting the right one it booted into Ubuntu fine.

Thanks again.

---

### Post by daveyllennod on 2009-08-01
i've tried tping in the code there or copy and paste rather as I dont seem to have that final symbol on my keyboard,

however When I do that it asks me  for my password and when i try typing it, the terminal cuts me off saying sorry incorrect password attempt?

Is my terminal not working or is my password not set properly, i assume its the password I set when i first installed

daveyllennod

---

### Post by daveyllennod on 2009-08-01
apologies, wrong thread

---

