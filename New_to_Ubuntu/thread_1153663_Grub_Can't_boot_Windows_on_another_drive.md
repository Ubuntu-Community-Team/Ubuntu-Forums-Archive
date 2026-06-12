---
title: "Grub: Can't boot Windows on another drive"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by flatland2d on 2009-05-09
I upgraded from 7.10 to 9.04 and I'm having trouble getting grub to boot to my Windows drive.  It used to work perfectly before, but I forgot to make note of my old grub settings before upgrading.  I need some help figuring this out.

This computer has two hard drives.  I have Ubuntu and Windows installed on one drive.  I don't use this installation of Windows anymore - it's just there for storage of old files.

I'm trying to boot to a newer installation of Windows on another hard drive.  The problem is that no matter what I set for root (hd0,0 or hd1,0) it always boots the old version of Windows on the drive with Ubuntu.

Here is a piece of my menu.lst file:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional Old
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional New
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

So both "Old" and "New" are booting to hd0,0.  Any idea what is wrong?

---

### Post by bumanie on 2009-05-09
Can you post the output of > sudo fdisk -l please. This will show the drives and partitions on your computer.

---

### Post by flatland2d on 2009-05-09
Sure.  Here it is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69286928

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25838   207543703+   7  HPFS/NTFS
/dev/sdb2           25839       38376   100711485   83  Linux
/dev/sdb3           38377       38913     4313452+   5  Extended
/dev/sdb5           38377       38913     4313421   82  Linux swap / Solaris

Sda1 is the Windows partition I'm trying to boot to.  I had this drive unplugged while installing Ubuntu to ensure I didn't mess anything up on it.

---

### Post by bumanie on 2009-05-09
> Sda1 is the Windows partition I'm trying to boot to. I had this drive unplugged while installing Ubuntu to ensure I didn't mess anything up on it.
That will be the problem, grub has installed itself to the windows installation/ntfs storage partition (or whatever is on sdb1). As you haven't posted the entire /boot/grub/menu.lst, it is impossible to know for sure that grub has installed correctly on the ubuntu install, but I suspect it will have. You should be able to delete the "new" xp entry from the grub list, save the modified list and the computer should dual boot properly again. If not, please post the full /boot/grub/menu.lst
To edit /boot/grub/menu.lst > gksudo gedit /boot/grub/menu.lstDelete the "New" xp entry and save, reboot and see if that works. As long as ubuntu has grub installed correctly, it should work again, unless remnants of grub remain on (hd1,0). If that happens, please say what sdb1 is eg full installation, data partition or whatever.

---

### Post by caljohnsmith on 2009-05-09
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by flatland2d on 2009-05-09
So here's a quick rundown again of what I did.  Hard drive 1 (arbitrary here) has Windows and Ubuntu.  Hard drive 2 has another Windows that is the normal OS for this system.  This is the one I want to boot to.

I decided to upgrade from 7.10 to 9.04.  Just formatted the Ubuntu partition instead of doing the version update.  Hard drive 2 was not connected at this time.  I modified menu.lst for grub to add back the drive that wasn't connected at install.  No matter what I try, I can't boot to this drive.  It boots to hda(0,0) no matter if I select the "Old" or "New" Windows installs.

Output of boot info script.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69286928

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   415,087,469   415,087,407   7 HPFS/NTFS
/dev/sdb2         415,087,470   616,510,439   201,422,970  83 Linux
/dev/sdb3         616,510,440   625,137,344     8,626,905   5 Extended
/dev/sdb5         616,510,503   625,137,344     8,626,842  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CC64C6A464C6911E" TYPE="ntfs" 
/dev/sdb1: UUID="3AF8F276F8F2302D" TYPE="ntfs" 
/dev/sdb2: UUID="69c04e12-d66f-4e9d-b36b-f653d55d8888" TYPE="ext4" 
/dev/sdb5: UUID="de95aa9b-35f1-4fad-87fd-8a256194bd20" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/ryan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ryan)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdb2/boot/grub/menu.lst: ===========================

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
default		5

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
# kopt=root=UUID=69c04e12-d66f-4e9d-b36b-f653d55d8888 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=69c04e12-d66f-4e9d-b36b-f653d55d8888

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
uuid		69c04e12-d66f-4e9d-b36b-f653d55d8888
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=69c04e12-d66f-4e9d-b36b-f653d55d8888 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		69c04e12-d66f-4e9d-b36b-f653d55d8888
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=69c04e12-d66f-4e9d-b36b-f653d55d8888 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		69c04e12-d66f-4e9d-b36b-f653d55d8888
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional Old
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Microsoft Windows XP Professional New
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1



=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=69c04e12-d66f-4e9d-b36b-f653d55d8888 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=de95aa9b-35f1-4fad-87fd-8a256194bd20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 215.2GB: boot/grub/menu.lst
 214.2GB: boot/grub/stage2
 214.5GB: boot/initrd.img-2.6.28-11-generic
 214.4GB: boot/vmlinuz-2.6.28-11-generic
 214.5GB: initrd.img
 214.4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

Thanks for all the help so far!  I really appreciate it.

---

### Post by caljohnsmith on 2009-05-09
OK, so you are trying to boot the Windows that is on the drive that does not have Ubuntu on it, correct? If that's true, how about trying the following entry in your menu.lst:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try that entry from your Grub menu, and let me know exactly what happens. We can work from there if you want.

John

---

### Post by raymondh on 2009-05-09
am posting because I want to follow this thread ....

cal ...seems like a lot of boot/grub problems lately huh?

---

### Post by FattyCNS on 2009-05-10
I'm having similar problems after an upgrade to Jaunty. The boot of Windows will fail with an "NTLDR Missing" error. Boot info script results below:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004d937

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937  83 Linux
/dev/sda2         976,752,000 1,953,520,064   976,768,065  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a950a95

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,059,834    78,059,772   7 HPFS/NTFS
/dev/sdb2          78,059,835   156,344,579    78,284,745   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8102d181

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sdc2         122,881,185   234,436,544   111,555,360   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd30d0af

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   244,197,071   244,197,009   7 HPFS/NTFS
/dev/sdd2         244,204,065   246,147,929     1,943,865  82 Linux swap / Solaris
/dev/sdd3         246,147,930   488,392,064   242,244,135  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="20e0ac3f-5859-440d-93d1-a8590270745c" TYPE="ext3" 
/dev/sda2: UUID="9092083b-869e-434e-9d1b-11d753885588" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="0620822A20822133" TYPE="ntfs" 
/dev/sdb2: UUID="4A508035508029B1" LABEL="Data0" TYPE="ntfs" 
/dev/sdc1: UUID="A670FDA370FD7A7F" LABEL="Data1" TYPE="ntfs" 
/dev/sdc2: UUID="88600CCE600CC542" LABEL="Data2" TYPE="ntfs" 
/dev/sdd1: UUID="6030F90530F8E2C8" LABEL="Data" TYPE="ntfs" 
/dev/sdd2: TYPE="swap" 
/dev/sdd3: UUID="c5880bb5-da52-4f1d-8cda-acd4863a4147" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdd3 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fatty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fatty)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin


=========================== sdd3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c5880bb5-da52-4f1d-8cda-acd4863a4147 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c5880bb5-da52-4f1d-8cda-acd4863a4147

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
uuid		c5880bb5-da52-4f1d-8cda-acd4863a4147
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c5880bb5-da52-4f1d-8cda-acd4863a4147 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c5880bb5-da52-4f1d-8cda-acd4863a4147
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c5880bb5-da52-4f1d-8cda-acd4863a4147 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c5880bb5-da52-4f1d-8cda-acd4863a4147
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdd3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd3 during installation
UUID=c5880bb5-da52-4f1d-8cda-acd4863a4147 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=20e0ac3f-5859-440d-93d1-a8590270745c /home           ext3    relatime        0       2
/dev/sdd2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd3: Location of files loaded by Grub: ===================


 166.5GB: boot/grub/menu.lst
 166.4GB: boot/grub/stage2
 166.4GB: boot/initrd.img-2.6.28-11-generic
 166.5GB: boot/vmlinuz-2.6.28-11-generic
 166.4GB: initrd.img
 166.5GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-05-10
FattyCNS, since we don't know how your drives are arranged in your BIOS boot order, we can't know for sure which Windows Grub entry is correct for your setup; therefore, the easiest course of action is to simply try the remaining two different possible combinations. How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add the following entries for Windows:
```
title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title       Windows XP (hd3)
rootnoverify     (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
Then reboot, try each of the above Windows entries from your Grub menu, and let me know exactly what happens. We can work from there if you want.

John

---

### Post by FattyCNS on 2009-05-10
Thanks John.

Using the hd2 option gives me an "NTLDR Missing" error and hd3 gives me "Error 13: Invalid or unsupported executable format".

Matt

---

### Post by caljohnsmith on 2009-05-10
Matt, I overlooked the fact that you might be booting the Windows sdb drive on start up since it also has Grub installed to its MBR. If you are booting that drive on start up, the following Grub entry should work to boot Windows:
```
title Windows XP
rootnoverify (hd0,0)
chainloader +1
```
Let me know what happens when you try the above entry, and we can work from there.

John

---

### Post by FattyCNS on 2009-05-10
That did the trick. :)

Thanks for the help John!

---

### Post by Opt-Crysys on 2009-05-10
OK well, I am completely new to this, had some problems in the past, and now I cannot boot Windows xp, can you help me aswell, and when I try to start the info script it says it isn't a file or directory. I have 2 HHD and Ubuntu is on a different one then the windows. When I try to boot in Grub, it loads Windows up to the point of starting up and then restarts the comp.

---

### Post by Opt-Crysys on 2009-05-10
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb37eb37e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      9,285,570   290,133,899   280,848,330   7 HPFS/NTFS
/dev/sda2                  63     9,285,569     9,285,507   b W95 FAT32
/dev/sda3         290,133,900   309,668,939    19,535,040  83 Linux
/dev/sda4         309,668,940   312,576,704     2,907,765  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88809aa0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,902,514   149,902,452  83 Linux
/dev/sdb2         149,902,515   156,360,644     6,458,130   5 Extended
/dev/sdb5         149,902,578   156,360,644     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="88F84544F84531AC" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERY" UUID="423B-2BDF" TYPE="vfat" 
/dev/sda3: UUID="84e40341-f5eb-46e5-b849-2e90ac3b8af6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" 
/dev/sdb1: UUID="9e280154-a65b-4e8c-9b3a-b5784ae91735" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="d0b79d68-e63e-4411-a24f-bcd896da764d" 
/dev/sdc1: LABEL="WD PASSPORT" UUID="4AFA-1B88" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nenad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nenad)
/dev/sdc1 on /media/WD PASSPORT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=nenad)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


========================== sda3/boot/grub/grub.conf: ==========================

default 0

timeout 30

title=Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

title=Gentoo Linux
root (hd0,2)
kernel /boot/kernel-2.6.18-gentoo-r5 root=/dev/hda3 vga=0x317

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>			<mountpoint>	<type>		<opts>		<dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
#/dev/BOOT		/boot		ext2		noauto,noatime	1 2
/dev/hda3		/		ext3		noatime		0 1
/dev/hda4		none		swap		sw		0 0
#/dev/hda1		/mnt/windows	ntfs		ro,umask=0133,dmask=000		0 0
/dev/cdrom		/mnt/cdrom	iso9660		noauto,ro	0 0
#/dev/fd0		/mnt/floppy	auto		noauto		0 0

# NOTE: The next line is critical for boot!
proc			/proc		proc		defaults	0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm			/dev/shm	tmpfs		nodev,nosuid,noexec	0 0
/dev/hda1 /mnt/windows ntfs-3g locale=en_US.utf8 0 0

=================== sda3: Location of files loaded by Grub: ===================


 157.6GB: boot/grub/grub.conf
 157.6GB: boot/grub/menu.lst
 157.6GB: boot/grub/stage2

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Gentoo Base System version 1.12.1 (on /dev/sda3)
root		(hd0,2)
kernel		/boot/kernel-2.6.18-gentoo-r5 root=/dev/hda3 vga=0x317 
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9e280154-a65b-4e8c-9b3a-b5784ae91735 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d0b79d68-e63e-4411-a24f-bcd896da764d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   7.2GB: boot/grub/menu.lst
   7.3GB: boot/grub/stage2
   7.3GB: boot/initrd.img-2.6.24-16-generic
   7.2GB: boot/initrd.img-2.6.24-16-generic.bak
   7.3GB: boot/initrd.img-2.6.24-23-generic
   7.3GB: boot/initrd.img-2.6.24-23-generic.bak
   7.2GB: boot/initrd.img-2.6.24-24-generic
   7.3GB: boot/initrd.img-2.6.24-24-generic.bak
   7.3GB: boot/vmlinuz-2.6.24-16-generic
   7.3GB: boot/vmlinuz-2.6.24-23-generic
   7.3GB: boot/vmlinuz-2.6.24-24-generic
   7.2GB: initrd.img
   7.3GB: initrd.img.old
   7.3GB: vmlinuz
   7.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

ok got that to work

---

### Post by flatland2d on 2009-05-10
> **caljohnsmith said:**
> OK, so you are trying to boot the Windows that is on the drive that does not have Ubuntu on it, correct? If that's true, how about trying the following entry in your menu.lst:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try that entry from your Grub menu, and let me know exactly what happens. We can work from there if you want.

John

That worked perfectly!  Thanks so much for the help!  You are awesome.

I read up on the "map" command so I think I know what's it's doing.  I didn't have to do this last time I installed (when I did 7.10) but who knows what I may have down different at that time.

---

### Post by CFBauer on 2009-05-12
I'm getting the "Error 13: Invalid or unsupported executable format" trying to boot into Windows after an upgrade to Jaunty as well. I'm going to keep working on it, but if anyone has any suggestions I'd appreciate it. 

Apparently I have an extended partition now, which is news to me. A lotta stuff going on here I only partially understand ;).

Here's my stuff:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeed5eed5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    32,772,599    32,772,537   7 HPFS/NTFS
/dev/sda2          32,772,600   488,392,064   455,619,465   f W95 Ext d (LBA)
/dev/sda5          32,772,663   268,414,019   235,641,357   7 HPFS/NTFS
/dev/sda6         268,414,083   483,974,189   215,560,107  83 Linux
/dev/sda7         483,974,253   488,392,064     4,417,812  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0eb277a0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   197,165,744   197,165,682  83 Linux
/dev/sdb2         197,165,745   234,436,544    37,270,800  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D8309E25309E0B20" LABEL="Windows HD" TYPE="ntfs" 
/dev/sda5: UUID="DEB872C6B8729D29" LABEL="Programs" TYPE="ntfs" 
/dev/sda6: UUID="af26ee47-7ed8-4415-b74a-0e3a1dab487e" TYPE="ext3" 
/dev/sda7: UUID="b7038085-acfe-4465-bc7c-c6f1154a9956" TYPE="swap" 
/dev/sdb1: UUID="16ed371c-1e50-4eb1-9e25-d00baa87617a" TYPE="ext3" 
/dev/sdb2: UUID="b17de417-86fe-4e70-813a-4e1486134cb8" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-12-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sdb1 on /home/Video type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b17de417-86fe-4e70-813a-4e1486134cb8

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=b17de417-86fe-4e70-813a-4e1486134cb8 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=af26ee47-7ed8-4415-b74a-0e3a1dab487e /home           ext3    relatime        0       2
# /home/Video was on /dev/sdb1 during installation
UUID=16ed371c-1e50-4eb1-9e25-d00baa87617a /home/Video     ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=b7038085-acfe-4465-bc7c-c6f1154a9956 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 115.5GB: boot/grub/menu.lst
 115.5GB: boot/grub/stage2
 114.4GB: boot/initrd.img-2.6.28-11-generic
 114.5GB: boot/initrd.img-2.6.28-12-generic
 114.5GB: boot/vmlinuz-2.6.28-11-generic
 114.5GB: boot/vmlinuz-2.6.28-12-generic
 114.5GB: initrd.img
 114.4GB: initrd.img.old
 114.5GB: vmlinuz
 114.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by CFBauer on 2009-05-14
bump :)

---

### Post by cjv8888 on 2009-05-14
> **CFBauer said:**
> I'm getting the "Error 13: Invalid or unsupported executable format" trying to boot into Windows after an upgrade to Jaunty as well. I'm going to keep working on it, but if anyone has any suggestions I'd appreciate it. 

Apparently I have an extended partition now, which is news to me. A lotta stuff going on here I only partially understand ;).

Here's my stuff:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeed5eed5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    32,772,599    32,772,537   7 HPFS/NTFS
/dev/sda2          32,772,600   488,392,064   455,619,465   f W95 Ext d (LBA)
/dev/sda5          32,772,663   268,414,019   235,641,357   7 HPFS/NTFS
/dev/sda6         268,414,083   483,974,189   215,560,107  83 Linux
/dev/sda7         483,974,253   488,392,064     4,417,812  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0eb277a0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   197,165,744   197,165,682  83 Linux
/dev/sdb2         197,165,745   234,436,544    37,270,800  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D8309E25309E0B20" LABEL="Windows HD" TYPE="ntfs" 
/dev/sda5: UUID="DEB872C6B8729D29" LABEL="Programs" TYPE="ntfs" 
/dev/sda6: UUID="af26ee47-7ed8-4415-b74a-0e3a1dab487e" TYPE="ext3" 
/dev/sda7: UUID="b7038085-acfe-4465-bc7c-c6f1154a9956" TYPE="swap" 
/dev/sdb1: UUID="16ed371c-1e50-4eb1-9e25-d00baa87617a" TYPE="ext3" 
/dev/sdb2: UUID="b17de417-86fe-4e70-813a-4e1486134cb8" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-12-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
/dev/sdb1 on /home/Video type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b17de417-86fe-4e70-813a-4e1486134cb8

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b17de417-86fe-4e70-813a-4e1486134cb8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b17de417-86fe-4e70-813a-4e1486134cb8
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=b17de417-86fe-4e70-813a-4e1486134cb8 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=af26ee47-7ed8-4415-b74a-0e3a1dab487e /home           ext3    relatime        0       2
# /home/Video was on /dev/sdb1 during installation
UUID=16ed371c-1e50-4eb1-9e25-d00baa87617a /home/Video     ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=b7038085-acfe-4465-bc7c-c6f1154a9956 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 115.5GB: boot/grub/menu.lst
 115.5GB: boot/grub/stage2
 114.4GB: boot/initrd.img-2.6.28-11-generic
 114.5GB: boot/initrd.img-2.6.28-12-generic
 114.5GB: boot/vmlinuz-2.6.28-11-generic
 114.5GB: boot/vmlinuz-2.6.28-12-generic
 114.5GB: initrd.img
 114.4GB: initrd.img.old
 114.5GB: vmlinuz
 114.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

try changing the end of the menu.lst to
> 
title		Microsoft Windows XP Professional
rootnoverify     (hd0,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

---

### Post by CFBauer on 2009-05-14
> **cjv8888 said:**
> try changing the end of the menu.lst to

Didn't quite do it. ;)

I also tried some random variations based on suggestions earlier in this thread, no luck yet. Still the same error 13. Thanks for the suggestion.

---

### Post by cjv8888 on 2009-05-14
> **CFBauer said:**
> Didn't do it. ;)

I tried some random variations based on suggestions earlier in this thread, no luck yet. Still the same error 13. Thanks for the suggestion.

In that case, I suggest checking out the Error 13 from Hermann's Grub Page [URL="http://users.bigpond.net.au/hermanzone/p15.htm#13"]here.
[/URL]

---

### Post by CFBauer on 2009-05-14
> **cjv8888 said:**
> In that case, I suggest checking out the Error 13 from Hermann's Grub Page [URL="http://users.bigpond.net.au/hermanzone/p15.htm#13"]here.
[/URL]
Thanks for the suggestion. I installed and tried out TestDisk, as was recommended. I didn't commit any changes yet, this stuff is intimidating.

---

