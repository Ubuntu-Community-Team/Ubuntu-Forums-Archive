---
title: "Grub error 17"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by davidside on 2009-11-13
I attempted to use sfdisk to remove a primary partition inside of an extended partition. I now get grub error 17 when I boot up.

Output of fdisk:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10570    84855330    7  HPFS/NTFS
/dev/sda3           10571       13768    25687935    5  Extended
/dev/sda5           10571       11183     4923859+  83  Linux
/dev/sda6           11184       11218      281106   82  Linux swap / Solaris
/dev/sda7           11474       13768    18434556   83  Linux

---

### Post by kansasnoob on 2009-11-13
Use the Boot Info Script and post the results here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by davidside on 2009-11-13
Output of results.txt

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 200040672 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 170315080 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda7 and looks 
                       at sector 199976912 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   169,807,049   169,710,660   7 HPFS/NTFS
/dev/sda3         169,807,050   221,182,919    51,375,870   5 Extended
/dev/sda5         169,807,176   179,654,894     9,847,719  83 Linux
/dev/sda6         179,654,958   180,217,169       562,212  82 Linux swap / Solaris
/dev/sda7         184,313,808   221,182,919    36,869,112  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8672ab53

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32     4,030,463     4,030,432   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0913" TYPE="vfat" 
/dev/sda2: UUID="C8DC254EDC253858" TYPE="ntfs" 
/dev/sda5: UUID="5061ddff-b21e-4307-94aa-2ec6266ed056" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="5a58cd94-b937-4948-8451-2956f31eff92" TYPE="swap" 
/dev/sda7: UUID="e073c210-3fe4-4862-87b5-15a4be96aef8" TYPE="ext2" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="CE57-B60E" TYPE="vfat" 

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
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5061ddff-b21e-4307-94aa-2ec6266ed056

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/memtest86+.bin
quiet

title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro quiet splash 
#initrd        /boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro single 
#initrd        /boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, memtest86+ (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/memtest86+.bin  
#savedefault
#boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=5a58cd94-b937-4948-8451-2956f31eff92 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  87.1GB: boot/grub/menu.lst
  87.2GB: boot/grub/stage2
  87.0GB: boot/initrd.img-2.6.28-11-generic
  87.1GB: boot/initrd.img-2.6.28-16-generic
  87.1GB: boot/vmlinuz-2.6.28-11-generic
  87.1GB: boot/vmlinuz-2.6.28-16-generic
  87.1GB: initrd.img
  87.0GB: initrd.img.old
  87.1GB: vmlinuz
  87.1GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1




=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 /               ext2    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=07D6-0913  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C8DC254EDC253858 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=03abed51-ba0a-4562-92ee-10be8518d83b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda7: Location of files loaded by Grub: ===================


 102.2GB: boot/grub/menu.lst
 102.4GB: boot/grub/stage2
 102.4GB: boot/initrd.img-2.6.22-14-generic
 102.4GB: boot/initrd.img-2.6.22-14-generic.bak
 102.2GB: boot/initrd.img-2.6.27-7-generic
 102.3GB: boot/initrd.img-2.6.28-11-generic
 102.4GB: boot/vmlinuz-2.6.22-14-generic
 102.3GB: boot/vmlinuz-2.6.27-7-generic
 102.3GB: boot/vmlinuz-2.6.28-11-generic
 102.3GB: initrd.img
 102.2GB: initrd.img.old
 102.3GB: vmlinuz
 102.3GB: vmlinuz.old

```

---

### Post by kansasnoob on 2009-11-13
Give me a few minutes to digest this!

---

### Post by kansasnoob on 2009-11-13
First of all it's not possible for a primary partition to exist inside an extended partition. Logical partitions reside in extended partitions.

But it looks like sda2 is Win XP Media Center, and sda5 is an old Gutsy, and sda7 is Jaunty.

Both Gutsy and Jaunty menu lists are a mess, but Gutsy's less so, so we're going to restore grub to Gutsy. Boot a Live CD (any Live CD) and in Terminal run:

```
sudo grub
```

```
find /boot/grub/stage1
```

That should show an output like:

> (hd0,4)
(hd0,6)

(hd0,4) should be Gutsy so run:

```
root (hd0,4)
```

```
setup (hd0)
```

The output should look something like this:

> Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done. 

If so type:

```
quit
```

When you reboot you should be able to boot all three OS's. But we really should straighten out Jaunty's menu.lst and start using it!

I'm just too tired and slightly ticked off because I got a "verbal warning" from the bosses!

---

### Post by davidside on 2009-11-13
This worked! Thanks so much for taking the time to help me.

---

### Post by kansasnoob on 2009-11-13
> **davidside said:**
> This worked! Thanks so much for taking the time to help me.

If you ever plan on ditching that old Gutsy (which is no longer supported) give a shout so we can fix the Jaunty menu.lst and then we'll hand boot off to it!

I'm just too tired right now and need to follow up a bit on a couple other things.

---

### Post by kansasnoob on 2009-11-20
Addressing the following PM:

> About a week ago, you helped me with a Grub error and I appreciate it. I was wondering if you could help me with something else. I have both Gutsy and Jaunty installed. I would like to delete Gutsy, use that space for Jaunty and boot from Jaunty. I have included the original thread to help explain what I would like to do.

Have you changed anything since then?

Give me just a bit to read this all again and see what changes we need to make to the Jaunty menu.lst.

Also, just to be certain, are you currently able to boot Jaunty from the Gutsy boot menu?

---

### Post by kansasnoob on 2009-11-20
A bit of confusion here, look:

> sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 170315080 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda7 and looks 
                       at sector 199976912 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab


You see the Boot Info Script actually identifies both of those as Jaunty???????? If I were to choose one to get rid of I'd choose the one formatted as ext2, but then again I'm not sure which OS you want to keep for sure (maybe one or the other has problems I'm unaware of).

So do me a favor and boot into the operating system you want to keep (assuming you can boot into it), make sure it's updated (restart if requested), and post the output of the following commands:

```
df -H
```

```
cat /etc/issue
```

```
uname -a
```

```
cat /boot/grub/menu.lst
```

BTW, it rather looks like the OS on sda7 was originally Gutsy and has been updated to Jaunty. So actually my initial assessment was wrong!

It looks like sda5 (hd0,4 in grub lingo) is Jaunty after all. Anyway the above commands should help clear things up, just be certain you're booted into the OS you want to keep.

Regardless we need to make some minor changes to the menu.lst, then once we know we have things booting properly we'll decide what you should do as far as repartitioning.

Oh, and feel free to PM me again just to get my attention, but lets keep the bulk of the discussion here on the board. I may make a mistake that someone else catches.

---

### Post by davidside on 2009-11-20
I am logged on to the version that I'd like to keep. I have not changed or installed anything since we spoke last week.

Output of df -H:
```

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5              5.0G   3.7G   1.1G  79% /
tmpfs                  526M      0   526M   0% /lib/init/rw
varrun                 526M   111k   525M   1% /var/run
varlock                526M      0   526M   0% /var/lock
udev                   526M   177k   525M   1% /dev
tmpfs                  526M    78k   525M   1% /dev/shm
lrm                    526M   2.5M   523M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1              2.1G   2.1G    18M 100% /media/KINGSTON

```
Output of cat /etc/issue: 
```

Ubuntu 9.04 \n \l

```
Output of uname -a:
```

Linux davidside-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```
Output of menu.lst:
```

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
# kopt=root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5061ddff-b21e-4307-94aa-2ec6266ed056

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/memtest86+.bin
quiet

title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro quiet splash 
#initrd        /boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro single 
#initrd        /boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, memtest86+ (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/memtest86+.bin  
#savedefault
#boot

```

---

### Post by kansasnoob on 2009-11-20
I'll bet you can see what I wanted to verify there:

I know for sure we want to keep /dev/sda5 and that's where we previously installed grub so we're good there.

I also know for sure that we have 9.04 (Jaunty) and it's running kernel 2.6.28-11-generic. Something that jumps out at me there is the **2.6.28-11**.

My Jaunty is up to 2.6.28-16, so unless you're running a special laptop remix, or you've chosen to not accept kernel updates, I think you should be on either 2.6.28-15 or 2.6.28-16.

However another possible reason for that may be some needed changes to your menu.lst, so we'll fix that using a little copy-n-paste. First lets create a backup:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```


To edit it run the command:

```
gksudo gedit /boot/grub/menu.lst
```

Everything I want added to the menu.lst is in **bold** and everything I want removed is in **[COLOR="Red"]red[/COLOR]**. Scroll down to this area **(no changes need be made above that)**:

> ## ## End Default Options ##

[B][COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2[/COLOR][/B]



title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/memtest86+.bin
quiet

[B][COLOR="Red"]title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1[/COLOR][/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1[/B]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
**#**title        Dell Utility Partition
**#**root        (hd0,0)
**#**savedefault
**#**makeactive
**#**chainloader    +1


[B][COLOR="Red"]# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro quiet splash 
#initrd        /boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e073c210-3fe4-4862-87b5-15a4be96aef8 ro single 
#initrd        /boot/initrd.img-2.6.22-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
#title        Ubuntu 7.10, memtest86+ (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/memtest86+.bin  
#savedefault
#boot[/COLOR][/B]

It's a bit difficult to see but notice I've added a # to the beginning of all the lines regarding your Dell Utility Partition because that's something you'll seldom want to access. Should you ever want to you can simply run "gksudo gedit /boot/grub/menu.lst" again and remove those # (aka: comments).

When complete you should have this:

> ## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Dell Utility Partition
#root        (hd0,0)
#savedefault
#makeactive
#chainloader    +1


When done click on Save, then File > Quit. To be sure it looks right run:

```
cat /boot/grub/menu.lst
```

If all looks well then let's look into updates. Unless you're avoiding updates for a reason lets go to System > Administration > Software Sources and click on the Updates tab. Towards the bottom you'll see Release Upgrade.

**I do not** recommend upgrading to Karmic at this time due to bugs, so select **Never**.

Then go to Update Manager and check for updates. You may have a kernel update and be asked to restart after updated, just do so and we'll see what happens.

You'll likely have a new kernel listed in the boot menu so try it. If it fails to boot or presents other problems just choose the older kernel "2.6.28-11" on reboot.

If all goes well we'll talk about Startup Manager:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

We also need to talk about your partitioning now so post the output of:

```
&#65279;&#65279;sudo parted /dev/sda print
```

or better yet install Gparted:

```
sudo apt-get install gparted
```

Which will show up in System > Administration > Partition Editor. Then post a screenshot of gparted.

One more thing: tell me more about that 2 GB KINGSTON external.

---

### Post by davidside on 2009-11-20
I edited menu.lst and I just rebooted and everything appears to be fine.

I ran Update Manager and some files were installed. uname -a still displays:                                   **2.6.28-11-generic.**

I installed Startup Manager.

I installed GParted and I have attached the screenshot.

The Kingston is just a thumb drive that I use mostly for Windows. I just popped it out.

---

### Post by kansasnoob on 2009-11-20
I didn't tell you to "pop that out"!

If that drive was not properly unmounted in Win you'll likely have trouble mounting it next time!

Be that as it may I don't quite understand why you're not getting kernel updates. That concerns me so post the output of:

```
cat /etc/apt/sources.list
```

We'll get through this. After figuring out the kernel thing we'll get into the repartitioning.

For now make absolutely sure that there is no data on sda7 you wish to save! It's about 17.5 GB so go to Computer and double click the partition that looks closest to that size.

If there is any data, pictures, etc. that you want to save I need to know that!

We'll also have to move SWAP to the far right after deleting sda7 so we'll have to change some UUID's which is super easy.

I also need to know how much RAM you have so post the output of:

```
cat /proc/meminfo
```

Oh, and send me a new:

```
cat /boot/grub/menu.lst
```

It's not that I don't trust you. I hardly trust myself ;)

---

### Post by davidside on 2009-11-20
Output of sources.list:

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```
Output of meminfo:
```

MemTotal:        1025480 kB
MemFree:          124872 kB
Buffers:           31900 kB
Cached:           446972 kB
SwapCached:          352 kB
Active:           587804 kB
Inactive:         238016 kB
Active(anon):     337376 kB
Inactive(anon):    15192 kB
Active(file):     250428 kB
Inactive(file):   222824 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:        142164 kB
HighFree:            252 kB
LowTotal:         883316 kB
LowFree:          124620 kB
SwapTotal:        281096 kB
SwapFree:         280744 kB
Dirty:                16 kB
Writeback:             0 kB
AnonPages:        346732 kB
Mapped:            69312 kB
Slab:              24396 kB
SReclaimable:      15468 kB
SUnreclaim:         8928 kB
PageTables:         2880 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      793836 kB
Committed_AS:     764100 kB
VmallocTotal:     122880 kB
VmallocUsed:       38136 kB
VmallocChunk:      79660 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      892928 kB

```Output of menu.lst
```

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
# kopt=root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5061ddff-b21e-4307-94aa-2ec6266ed056

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
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5061ddff-b21e-4307-94aa-2ec6266ed056
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Dell Utility Partition
#root        (hd0,0)
#savedefault
#makeactive
#chainloader    +1

```I looked over sda7. There are no files that I want to keep.

---

### Post by Miljet on 2009-11-20
I would like to insert a comment in this thread. 
To kansasnoob, I am very impressed with the thoroughness and clarity of your responses. You are an example for all of us and a valuable asset to this community.

---

### Post by kansasnoob on 2009-11-21
Sorry, I dozed off. It happens when you get old.

That kernel thing still has me a bit troubled, but all of that looks fine. So when you have time, just to humor me, please post the output of:

```
apt-cache showpkg linux-libc-dev
```

```
apt-cache showpkg linux-image
```

```
apt-cache showpkg linux-headers
```

```
apt-cache showpkg linux-headers-generic
```

I keep thinking that may be a netbook remix or something but there should be some indication of that when we run "cat /etc/issue", "uname -r", or "uname -a". It'll usually be indicated by a **unr** or something to that effect.

We may be able to update the kernel in the boot menu just by running:

```
sudo update-grub
```

But generally when the kernel is updated you'd be prompted to restart and that would be "automagically" done.

That said sometimes kernel updates break things anyway, like wifi, graphics or audio card drivers, etc. I think some of the Dells that ship with Ubuntu actually have kernel updates somehow disabled just because of that.

Should that ever happen just select to boot the older kernel until you have the time and patience to fix anything that the kernel update hoses.

In fact Linux Mint, which is based on Ubuntu, notoriously holds back kernel updates just because of that. Anyway that doesn't effect our ability to repartition so here we go.

**Please read this all before proceeding and if you need more explanation just shout!** Always better to ask questions before we break something than after.

To do this you'll need to boot the Live CD, choosing Try Ubuntu without changes ........ , and use Gparted from the Live Desktop. I know you have Gparted installed in Ubuntu but you can't use it from your installed OS because all partitions must be unmounted.

Also, since this is a laptop, make sure you're either running off a wall outlet or you have a fully charged battery. The last thing we'd want to have happen is to lose power while resizing sda5.

Typically the first thing you must do is right click on the SWAP partition and select swapoff. Then you can right click on sda7 and select delete.

Now right click on the SWAP partition and select resize/move. You want to move it all the way to the right and I suggest a size of 1.1GB to 1.2GB based on the amount of RAM you have. You'll just drag the right edge all the way to the right and then drag the left edge to the right until you've obtained the desired size.

Next right click on sda5 and select resize/move. You want to just drag the right edge all the way to the right to use all of the newly created free space. Now at the bottom you should see a review of the pending operations.

If that all looks right then click on Apply (sometimes Apply is just a green check mark). I'd anticipate that taking about 20 to 30 minutes, but it could take a bit longer. At any rate just let it complete all tasks.

**[COLOR="Red"]******************************************************[/COLOR]**

When it's done you can just restart, remove the Live CD, and boot back into Ubuntu. You may notice that instead of a quiet splash screen at startup you have a long string of text. That's to be expected.

Anytime SWAP is resized, moved, or recreated it changes UUID's in fstab and initramfs. No problem we'll fix that.

First I like to create a simple text backup of two files. You can use Open Office, Abiword, or whatever you wish. Just run the commands:

```
cat /etc/fstab
```

```
cat /etc/initramfs-tools/conf.d/resume
```

Then copy-n-paste the results into a word document and save it. That way if you should hose one of the files you need to edit you have a backup to fall back on.

Now run the command:

```
sudo blkid -c /dev/null
```

**Note: never edit anything in blkid!**

Mine's ridiculously long but just as an example:

> lance@lance-desktop:~$ sudo blkid -c /dev/null
[sudo] password for lance: 
/dev/sda1: UUID="C02402022401FC62" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda3: LABEL="Lucid Root" UUID="9c10b8f7-89d3-4a72-a0ab-e89d061653b0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Jaunty Root" UUID="6ceb25f1-5904-490b-a7cc-d14b9d63c3b7" TYPE="ext3" 
/dev/sda6: LABEL="Jaunty Home" UUID="238b5ad8-c8fd-4c65-a190-1828af9fe54a" TYPE="ext3" 
/dev/sda7: LABEL="Gloria Root" UUID="51ebb887-909b-43cb-b022-1300ddd78074" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Gloria Home" UUID="2c9d2789-e4b6-46c3-b9c8-145951f916cc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="**2897adb6-b16f-4ba7-901f-2aec9e1c994d**" TYPE="swap" 
/dev/sda10: LABEL="Lucid Home" UUID="3128dea7-b986-4b45-8004-0b48bf97f9dd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Helena Root" UUID="513a5f97-cb72-4480-9ca1-53a86dd1088b" TYPE="ext4" 
/dev/sda12: LABEL="Helena Home" UUID="53fba285-705e-4120-9768-0cdf0e8c6e2c" TYPE="ext4" 


You notice I've highlighted the UUID for SWAP. That's the number we'll want to use. Be certain not to include the quotation marks when copy-n-pasting that to the fstab and initramfs files.

Next run:

```
gksudo gedit /etc/fstab
```

This screenshot probably explains things better than words can:

[ATTACH]137027[/ATTACH]

You see the UUID in my /etc/fstab:

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=238b5ad8-c8fd-4c65-a190-1828af9fe54a /home ext3 relatime 0 2
# Entry for /dev/sda9 :
UUID=**2897adb6-b16f-4ba7-901f-2aec9e1c994d** none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

Yours undoubtedly will not match the UUID in blkid so you want to replace the UUID for swap in /etc/fstab with the one displayed in blkid.

Clear as mud? **Do not change anything but the UUID**. When done be sure to click on Save, then File > Quit.

Now you want to do the same in this file:

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

It's a short one:

> RESUME=UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d

Once again just replace the UUID in that file with the one for swap displayed in blkid, remember to Save > File > Quit.

Now one more command:

```
sudo update-initramfs -u
```

That may take a few minutes to complete. **Do not close the terminal until the prompt indicates it's complete (ie: lance@lance-desktop:~$)**

When that's complete close the terminal and go to Gparted and if SWAP is "off" (it probably will be) right click on SWAP and select swapon.

That should be it. If all was successful you should once again have a quiet splash and SWAP should automatically be on at startup.

Not so bad huh?

---

### Post by davidside on 2009-11-21
Output of linux-libc-dev:
```

Package: linux-libc-dev
Versions: 
2.6.28-16.55 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages
                  MD5: d5d143e6dffc891f04a85464446f9451

2.6.28-11.42 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: d5d143e6dffc891f04a85464446f9451


Reverse Depends: 
  libc6-dev,linux-libc-dev
  ltp-network-test,linux-libc-dev
  librsbac-dev,linux-libc-dev
  ichthux-desktop,linux-libc-dev
  nvidia-96-kernel-source,linux-libc-dev
  nvidia-71-kernel-source,linux-libc-dev
  nvidia-180-kernel-source,linux-libc-dev
  nvidia-173-kernel-source,linux-libc-dev
  fglrx-kernel-source,linux-libc-dev
  libdrm-dev,linux-libc-dev 2.6.28-3.4
  libdrm-dev,linux-libc-dev 2.6.28-5.15
  libc6-dev,linux-libc-dev
Dependencies: 
2.6.28-16.55 - amd64-libs-dev (1 1.1) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) libdrm-dev (0 (null)) linux-kernel-headers (0 (null)) 
2.6.28-11.42 - amd64-libs-dev (1 1.1) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) libdrm-dev (0 (null)) linux-kernel-headers (0 (null)) 
Provides: 
2.6.28-16.55 - linux-kernel-headers 
2.6.28-11.42 - linux-kernel-headers 
Reverse Provides: 

```Output of linux-image
```

Package: linux-image
Versions: 
2.6.28.16.21 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages
                  MD5: bbb651153b198d4cc1090132ccf7582b

2.6.28.11.15 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: bbb651153b198d4cc1090132ccf7582b


Reverse Depends: 
  linux,linux-image 2.6.28.16.21
  linux,linux-image 2.6.28.11.15
  shorewall-common,linux-image
  dkms,linux-image
Dependencies: 
2.6.28.16.21 - linux-image-generic (5 2.6.28.16.21) 
2.6.28.11.15 - linux-image-generic (5 2.6.28.11.15) 
Provides: 
2.6.28.16.21 - 
2.6.28.11.15 - 
Reverse Provides: 
linux-image-2.6.28-15-virtual 2.6.28-15.49
linux-image-2.6.28-15-server 2.6.28-15.49
linux-image-2.6.28-15-generic 2.6.28-15.49
linux-image-2.6.28-16-virtual 2.6.28-16.55
linux-image-2.6.28-16-server 2.6.28-16.55
linux-image-2.6.28-16-generic 2.6.28-16.55
linux-image-2.6.28-15-virtual 2.6.28-15.52
linux-image-2.6.28-15-server 2.6.28-15.52
linux-image-2.6.28-15-generic 2.6.28-15.52
linux-image-2.6.28-14-virtual 2.6.28-14.47
linux-image-2.6.28-14-server 2.6.28-14.47
linux-image-2.6.28-14-generic 2.6.28-14.47
linux-image-2.6.28-13-virtual 2.6.28-13.45
linux-image-2.6.28-13-server 2.6.28-13.45
linux-image-2.6.28-13-generic 2.6.28-13.45
linux-image-2.6.28-3-rt 2.6.28-3.12
linux-image-2.6.28-6-386 2.6.28-6.20
linux-image-2.6.28-11-virtual 2.6.28-11.42
linux-image-2.6.28-11-server 2.6.28-11.42
linux-image-2.6.28-11-generic 2.6.28-11.42

```Output of linux-headers
```

Package: linux-headers
Versions: 

Reverse Depends: 
  kvm-source,linux-headers
  sl-modem-source,linux-headers
  em8300-source,linux-headers
  virtualbox-ose-source,linux-headers
  virtualbox-ose-guest-source,linux-headers
  lirc-modules-source,linux-headers
  kvm-source,linux-headers
  alsa-source,linux-headers
  nvidia-96-kernel-source,linux-headers
  nvidia-71-kernel-source,linux-headers
  nvidia-180-kernel-source,linux-headers
  nvidia-173-kernel-source,linux-headers
  fglrx-kernel-source,linux-headers
  dkms,linux-headers
Dependencies: 
Provides: 
Reverse Provides: 
linux-headers-2.6.28-15-server 2.6.28-15.49
linux-headers-2.6.28-15-generic 2.6.28-15.49
linux-headers-2.6.28-15 2.6.28-15.49
linux-headers-2.6.28-16-server 2.6.28-16.55
linux-headers-2.6.28-16-generic 2.6.28-16.55
linux-headers-2.6.28-16 2.6.28-16.55
linux-headers-2.6.28-15-server 2.6.28-15.52
linux-headers-2.6.28-15-generic 2.6.28-15.52
linux-headers-2.6.28-15 2.6.28-15.52
linux-headers-2.6.28-14-server 2.6.28-14.47
linux-headers-2.6.28-14-generic 2.6.28-14.47
linux-headers-2.6.28-14 2.6.28-14.47
linux-headers-2.6.28-13-server 2.6.28-13.45
linux-headers-2.6.28-13-generic 2.6.28-13.45
linux-headers-2.6.28-13 2.6.28-13.45
linux-headers-2.6.28-3-rt 2.6.28-3.12
linux-ports-headers-2.6.28-6 2.6.28-6.20
linux-headers-2.6.28-6-386 2.6.28-6.20
linux-headers-2.6.28-11-server 2.6.28-11.42
linux-headers-2.6.28-11-generic 2.6.28-11.42
linux-headers-2.6.28-11 2.6.28-11.42

```Output of linux-headers-generic
```

Package: linux-headers-generic
Versions: 
2.6.28.16.21 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages
                  MD5: 9c9742ab9c289b1e900fab477bc0070d

2.6.28.11.15 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: 9c9742ab9c289b1e900fab477bc0070d


Reverse Depends: 
  kvm-source,linux-headers-generic
  sl-modem-source,linux-headers-generic
  mythbuntu-desktop,linux-headers-generic
  xubuntu-desktop,linux-headers-generic
  virtualbox-ose-source,linux-headers-generic
  virtualbox-ose-guest-source,linux-headers-generic
  ubuntu-netbook-remix,linux-headers-generic
  lirc-modules-source,linux-headers-generic
  kvm-source,linux-headers-generic
  nvidia-96-kernel-source,linux-headers-generic
  nvidia-71-kernel-source,linux-headers-generic
  nvidia-180-kernel-source,linux-headers-generic
  nvidia-173-kernel-source,linux-headers-generic
  fglrx-kernel-source,linux-headers-generic
  ubuntu-desktop,linux-headers-generic
  kubuntu-desktop,linux-headers-generic
  dkms,linux-headers-generic
Dependencies: 
2.6.28.16.21 - linux-headers-2.6.28-16-generic (0 (null)) 
2.6.28.11.15 - linux-headers-2.6.28-11-generic (0 (null)) 
Provides: 
2.6.28.16.21 - 
2.6.28.11.15 - 
Reverse Provides: 

```I did not run the **sudo update-grub** command. I wasn't sure it was a good idea at this point.

The repartitioning went very smoothly and I attached a screenshot from GParted. I just have a minor issue. I have tried rebooting several times and I still get the long list of messages at the beginning.

---

### Post by kansasnoob on 2009-11-21
Well, you have kernel version 2.6.28-16 it's just never been updated in grub so whenever you're ready run "sudo update-grub".

Regarding the loss of the quiet splash post the output of these commands so I can double check:

```
sudo blkid -c /dev/null
```

```
cat /etc/fstab
```

```
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by davidside on 2009-11-21
Output of sudo blkid -c /dev/null
```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0913" TYPE="vfat" 
/dev/sda2: UUID="C8DC254EDC253858" TYPE="ntfs" 
/dev/sda5: UUID="5061ddff-b21e-4307-94aa-2ec6266ed056" TYPE="ext3" 
/dev/sda6: UUID="81382977-8613-4977-844a-440e4585268a" TYPE="swap"

```Output of cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5061ddff-b21e-4307-94aa-2ec6266ed056 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=81382977-8613-4977-844a-440e4585268a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Output of cat /etc/initramfs-tools/conf.d/resume
```

RESUME=UUID=81382977-8613-4977-844a-440e4585268a

```I also ran the sudo update-grub command.

---

### Post by kansasnoob on 2009-11-21
Well, that certainly all looks right.

Maybe go to Gparted and make sure that SWAP is "on", if not click swapon and then run this again:

```
sudo update-initramfs -u
```

It may take a couple minutes to run.

---

### Post by davidside on 2009-11-21
It still does the same thing. But I can live with it.

---

### Post by kansasnoob on 2009-11-22
Well I'm stumped, but I'd keep bumping this thread every 24 hours or so.

I'm sure someone will have an answer.

I may just be overlooking something, sometimes a different pair of eyes ..............

---

### Post by davidside on 2009-11-22
I want to thank you for taking so much of your time to help me out. Your instructions were clear and concise and helped give me a better understanding of Linux. It was very much appreciated.

---

### Post by kansasnoob on 2009-11-22
I did have a thought.

Did you already install Startup Manager?

I spoke briefly about that several posts back. It's somewhat explained here:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

You can see in this graphic:

[http://www.psychocats.net/ubuntu/images/sum09.png](http://www.psychocats.net/ubuntu/images/sum09.png)

Towards the bottom, Misc.

Show Bootloader Menu should be checked (that's where you select to boot Win or Ubuntu).

Show boot splash should also be checked (that's what you're missing).

Show text during boot should NOT be checked.

The rest under the Boot Options tab is pretty much self explanatory. If you uncheck the Use timeout then the menu will sit there infinitely until you make a selection. The numerical value is how many seconds it'll wait for you to make a selection if the box is checked.

And of course you can select which OS is the default boot.

What I originally meant to show you was that under the Advanced tab you can select how many kernel entries to display. Two is a safe choice.

You can also select whether to display the recovery and memtest options. IMO you should display the recovery options, but how often do you run a memtest?

---

### Post by davidside on 2009-11-22
The settings on Startup Manager are as they should be.

I actually do get the splash screen, then a black screen for a second and then a screen that says "Reading files need to boot" with a bunch of lines.

---

### Post by egalvan on 2009-11-22
Hey kansasnoob, as usual a great HowTo on the swap UUID problem.

Just a thought...

would this be easier?

---
get the swap UUID, and save it.

re-do the swap partition as needed.

write the original UUID back onto the swap partition.
---

No need to edit fstab or regenerate initramfs

what do  you think?

---

### Post by kansasnoob on 2009-11-22
> **egalvan said:**
> Hey kansasnoob, as usual a great HowTo on the swap UUID problem.

Just a thought...

would this be easier?

---
get the swap UUID, and save it.

re-do the swap partition as needed.

write the original UUID back onto the swap partition.
---

No need to edit fstab or regenerate initramfs

what do  you think?

The answer is, "I don't know".

I learned the method I use from coffeecat quite a long time ago and it's never let me down before.

My concern is that SWAP may not be "swapon" on subsequent reboots, that could have a negative effect on system performance.

---

### Post by egalvan on 2009-11-22
> **kansasnoob said:**
> The answer is, "I don't know".

I learned the method I use from coffeecat quite a long time ago and **it's never let me down before.**


yeah, same here,
I learned this method from you back in the Hardy days. 
Never failed me (true for so much of your advice on boot problems, along with caljohnsmith and meifera).

But it always seemed so long-winded...

Then I found out that UUID's could be changed willy-nilly, 
and realized that since the problems occurted because swap had it's UUID changed,
then simply replacing the original swap UUID would cure the problems
that came from the swap UUID change.

Actually, I was more wondering your opinion on which was easier to explain to a newbie, and faster to run/implement.

No fstab editing, or re-creating intiramfs.


> My concern is that SWAP may not be "swapon" on subsequent reboots, that could have a negative effect on system performance.

To see if swap is on, use the same mechanism you gave...
run gparted and check that swap is locked.

if swap is not locked, then something went wrong with the process.
either yours or mine.

Anyway, thanks!

---

### Post by kansasnoob on 2009-11-23
Thought I'd give this a bump.

FYI the problem is quiet splash disappears part way thru boot.

I'm sure I'm just overlooking something.

---

### Post by kansasnoob on 2009-11-25
Another bump.

Still curious what I may have overlooked regarding the loss of quiet splash.

---

