---
title: "Updated and now can't mount partition"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Sydius on 2009-02-01
I did a bunch of updates last night, including some kernel updates.  It asked me to reboot, so I did, but I went to Windows instead because I wanted to play some games.  When I got around to trying to boot to Linux, I got an error 17 about not being able to mount the partition as soon as I try to select it from the grub list.

It's set to root (hd0,2) which is correct, I think, but when I go to "edit" and erase the 2 and hit tab, 2 isn't on the list (it skips it).  I don't know if that's because it's what was already selected or if that means there's a problem.

Any help?

---

### Post by quirks on 2009-02-01
Here is my guess:

You installed a new kernel and the installer put the binary in the middle or the end of the hard disk. When the mode of your hard disk is not set correctly in your BIOS, GRUB can only address the first 8GB of the hard disk. But because the kernel resides in a sector which is located above the 8GB mark, GRUB cannot find it. Look in your BIOS, if you can change the mode of your hard disk. I had this problem a while ago with an old computer. Once I changed the mode, it worked again.

Also, this thread might be helpful:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by caljohnsmith on 2009-02-01
I doubt you have a problem with a new kernel being out of range of your BIOS, because if it was, you would typically get a Grub error 18 rather than error 17. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Sydius on 2009-02-10
```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc4 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdc4 starts at sector 268414020. According to the info 
                       in the boot sector, sdc4 has 356722687 sectors, but 
                       according to the info from fdisk, it has 356723325 
                       sectors.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001adfa

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001adfa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a460a45

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   134,207,009   134,206,947   7 HPFS/NTFS
/dev/sdc2         134,207,010   134,608,634       401,625  83 Linux
/dev/sdc3         134,608,635   268,414,019   133,805,385   5 Extended
/dev/sdc5         134,608,698   154,143,674    19,534,977  83 Linux
/dev/sdc6         154,143,738   158,047,469     3,903,732  82 Linux swap / Solaris
/dev/sdc7         158,047,533   268,414,019   110,366,487  83 Linux
/dev/sdc4         268,414,020   625,137,344   356,723,325   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="04AA45057B489E1B" LABEL="raid" TYPE="ntfs" 
/dev/sdb1: UUID="04AA45057B489E1B" LABEL="raid" TYPE="ntfs" 
/dev/sdc1: UUID="C23449FC3449F447" TYPE="ntfs" 
/dev/sdc2: UUID="81bab140-b084-43f1-9a96-2d4a151d14d1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: UUID="7E54076154071B91" LABEL="Data" TYPE="ntfs" 
/dev/sdc5: UUID="cb73f775-1944-4107-9402-774371573905" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc6: UUID="653d19f4-da51-4d16-8e32-912f4dabb891" TYPE="swap" 
/dev/sdc7: UUID="9ddfd6c4-f4f9-472f-9ec1-48f76aca1bc5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

============================= sdc2/grub/menu.lst: =============================

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
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=cb73f775-1944-4107-9402-774371573905 ro

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-7-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro quiet splash 
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro  single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows XP Professional x64 Edition
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


=================== sdc2: Location of files loaded by Grub: ===================


  68.9GB: grub/menu.lst
  68.9GB: grub/stage2
  68.8GB: initrd.img-2.6.24-19-generic
  68.8GB: initrd.img-2.6.24-19-generic.bak
  68.7GB: initrd.img-2.6.27-11-generic
  68.7GB: initrd.img-2.6.27-7-generic
  68.7GB: initrd.img-2.6.27-9-generic
  68.8GB: vmlinuz-2.6.24-19-generic
  68.7GB: vmlinuz-2.6.27-11-generic
  68.7GB: vmlinuz-2.6.27-7-generic
  68.7GB: vmlinuz-2.6.27-9-generic

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cb73f775-1944-4107-9402-774371573905 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=81bab140-b084-43f1-9a96-2d4a151d14d1 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=9ddfd6c4-f4f9-472f-9ec1-48f76aca1bc5 /home           ext3    relatime        0       2
# /dev/sda6
UUID=653d19f4-da51-4d16-8e32-912f4dabb891 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================ sdc4/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect


```

---

### Post by caljohnsmith on 2009-02-10
It looks like the only issue is that your boot partition is sdc2 and not sdc3. Therefore, I think all you will need to do to get Ubuntu booting again is tweak your menu.lst a little, so from your Live CD how about doing:
```
sudo mount /dev/sdc5 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And change all your Ubuntu entries to use (hd0,1) instead of (hd0,2) similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		[COLOR="Blue"](hd0,1)[/COLOR]
kernel		/vmlinuz-2.6.27-11-generic root=UUID=cb73f775-1944-4107-9402-774371573905 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet
```
Also, to prevent future problems when you get a kernel upgrade, I would recommend correcting the "groot" line to use (hd0,1) too:
```
# groot=[COLOR="Blue"](hd0,1)[/COLOR]
```
Then reboot, and let me know how far you get. We can work from there if necessary.

---

### Post by Sydius on 2009-02-11
For some reason, following your commands led to an empty directory in /mnt/boot, but I was able to change the stuff from the grub boot menu list while starting the computer and was able to log in as I used to and then I changed that file as you suggested.  Now it works. :-D

Thanks!

---

### Post by caljohnsmith on 2009-02-11
> **Sydius said:**
> For some reason, following your commands led to an empty directory in /mnt/boot, but I was able to change the stuff from the grub boot menu list while starting the computer and was able to log in as I used to and then I changed that file as you suggested.  Now it works. :-D

Thanks!
My mistake, I see I had you mount your root partition rather than the boot partition. Glad you figured it out though; cheers and enjoy your Ubuntu install. :)

---

