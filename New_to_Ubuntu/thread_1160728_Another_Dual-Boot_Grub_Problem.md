---
title: "Another Dual-Boot Grub Problem"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-05-15
My once pure computer has now been tainted by Windoze :( The missus isn't quite ready to let go.
Anyway, when installing windows onto an old 40GB PATA disk (500 GB SATA is reserved for 9.04) I found that I would have to put the CD in another PATA attached CD drive because it didn't work right with SATA & crashed on install. It worked better once I installed the chipset drivers, network interface drivers, drivers for this that & the other thing. For the record, Ubuntu "Just Worked"

THE PROBLEM:

As Windows was unaware of the 500 GB disk, I think it put a new MBR on the 40GB disk & the only way I can choose which OS to boot is to go into the BIOS & have one disk boot before the other one. I don't want to reinstall ubuntu, so how can I have it detect the newly installed Windoze & add it to GRUB under "Other Operating Systems"?

Thanks :)

---

### Post by radiocognition on 2009-05-15
> **alanwalterthomas said:**
> My once pure computer has now been tainted by Windoze :( The missus isn't quite ready to let go.
Anyway, when installing windows onto an old 40GB PATA disk (500 GB SATA is reserved for 9.04) I found that I would have to put the CD in another PATA attached CD drive because it didn't work right with SATA & crashed on install. It worked better once I installed the chipset drivers, network interface drivers, drivers for this that & the other thing. For the record, Ubuntu "Just Worked"

THE PROBLEM:

As Windows was unaware of the 500 GB disk, I think it put a new MBR on the 40GB disk & the only way I can choose which OS to boot is to go into the BIOS & have one disk boot before the other one. I don't want to reinstall ubuntu, so how can I have it detect the newly installed Windoze & add it to GRUB under "Other Operating Systems"?

Thanks :)

You can use your Ubuntu live cd to recover your previous ubuntu install by reinstalling GRUB.  More detailed instructions can be found here. [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by alanwalterthomas on 2009-05-16
Thanks for the reply :)
Unfortunately, the following didn't work from the live cd:
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit
Rather, I imagine it worked, but it didn't have the desired effect.
I had to press esc to get into the grub menu during boot, & there was no mention of windows.
Is there anything I might do to have grub detect the OS that has its own MBR on the other hd?

Just to be clear - windows didn't overwrite grub or the MBR on the linux disk. It installed on its own disk without touching the linux disk.

---

### Post by ntu on 2009-05-16
I have found this way good for dual booting windows and linux on 2 hdds:
[http://www.pperry.f2s.com/linux-dualboot-2hd.htm](http://www.pperry.f2s.com/linux-dualboot-2hd.htm)

---

### Post by radiocognition on 2009-05-16
Let me clarify, are you sure that the device that you installed ubuntu on is hd0,0 ?   If you read the tutorial, they mention that you have to mount your drive and search for the partition that you installed your system on to correctly reinstall GRUB.  You also are going to have to have your windows partition mounted for the installer to successfully detect the other operating system (if it is on another disk, you may have forgotten to do this)

---

### Post by alanwalterthomas on 2009-05-16
I read through the first few pages without hitting much paydirt.
I'm sure the Linux SATA drive is hd(0,0). It was installed first. There's one partition on it + swap (&extended around swap, not sure why the automatic installer did that...?) that shows up in gparted as /dev/sda1 (ext4) /dev/sda2 (extended) /devsda5 (swap). The other disk shows up on gparted as /dev/sdb or /dev/sdb1 (ntfs).

I tried the same steps as before after mounting both drives (I clicked on both in Places, opened a couple files, that should do it right?) but when I rebooted grub still hadn't recognised windows.

The output of find /boot/grub/stage1 was (hd0,0) & the output of setup (hd0) was:
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5)" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

What can I do now? Thanks,

P.S. If I go as far as the partitioning stage with the live cd installer, ubuntu recognises XP on the second hard disk, so it isn't totally blind to it.

---

### Post by radiocognition on 2009-05-16
This might be helpful [http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by presence1960 on 2009-05-16
to see exactly how your system is setup please download the Boot Info script to your desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then run in terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a Results.txt file with all the info. Post the contents of that file here.

From the sound of it it may just be a simple editing of GRUB. This script will give all necessary info about your setup.

P.S. This script was created by community member meierfra.

---

### Post by alanwalterthomas on 2009-05-17
Below are the script's results:
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007fa63

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   970,486,649   970,486,587  83 Linux
/dev/sda2         970,486,650   976,768,064     6,281,415   5 Extended
/dev/sda5         970,486,713   976,768,064     6,281,352  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c48d0a9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,172,289    78,172,227   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f086f13d-504d-4f32-b01b-b0de420f232e" TYPE="ext4" 
/dev/sda5: UUID="fab20358-3085-4932-ac98-e4c778214d75" TYPE="swap" 
/dev/sdb1: UUID="36C4A90FC4A8D303" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/alan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alan)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=f086f13d-504d-4f32-b01b-b0de420f232e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f086f13d-504d-4f32-b01b-b0de420f232e

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
uuid		f086f13d-504d-4f32-b01b-b0de420f232e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f086f13d-504d-4f32-b01b-b0de420f232e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f086f13d-504d-4f32-b01b-b0de420f232e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f086f13d-504d-4f32-b01b-b0de420f232e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f086f13d-504d-4f32-b01b-b0de420f232e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=f086f13d-504d-4f32-b01b-b0de420f232e /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fab20358-3085-4932-ac98-e4c778214d75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.8GB: boot/grub/menu.lst
   1.7GB: boot/grub/stage2
   1.9GB: boot/initrd.img-2.6.28-11-generic
   1.8GB: boot/vmlinuz-2.6.28-11-generic
   1.9GB: initrd.img
   1.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by presence1960 on 2009-05-17
add this after your Ubuntu entries in menu.lst

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP 
rootnoverify   (hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

You can run in terminal ```
gksu gedit /boot/grub/menu.lst
``` to edit the file.

---

### Post by alanwalterthomas on 2009-05-28
Thanks, the above worked.
I'd still like to change the behaviour a little. As is, grub will count to 0 from 3 & boot Ubuntu. I'd like to have the grub menu appear so that I can choose the OS without having to press esc first.
Any thoughts on how to do that?
Thanks,

---

### Post by presence1960 on 2009-05-28
open a terminal and run ```
sudo apt-get install startupmanager
```
This is a GUI program that will allow you to do what you want and a lot more. After install you can run it in terminal>  gksu startupmanager or you can find it in System > Administration > Startup-Manager

---

### Post by alanwalterthomas on 2009-05-29
Thanks! That's perfect!

---

### Post by presence1960 on 2009-05-29
> **alanwalterthomas said:**
> Thanks! That's perfect!

Glad to be of service. Enjoy!

---

