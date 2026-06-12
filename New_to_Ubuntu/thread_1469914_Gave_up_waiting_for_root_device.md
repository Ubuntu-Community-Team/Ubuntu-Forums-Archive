---
title: "Gave up waiting for root device"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Feuer frei on 2010-05-02
Greetings everyone,

I have a SCSI Drive computer,  Its a Fujitsu Siemens Celsius 600 Dual Xeon Processor I have had this error since I first installed Ubuntu but it went away when I upgraded from 9.04 to 9.10. However now it is back after going to 10.04. 

I don't know how to capture boot up info on Ubuntu so I hope I got this copied correctly.

When I start this system I get the following:


Gave up waiting for root device. Common problems: a20a13F30d0
- Boot args (cat /proc/cmdline)
- Check rootdelay = (did the system wait long enough?)
- Checkroot = (did the system wait for the right device/)
- Missing modules (cat /proc/modules; /dev)
ALERT! / dev/disk/by-uuid/39ec1770-1e59-49c8-874d-1a20a13f30d0 does not exist dropping to shell!
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11)
built-in shell (ash)
Enter 'help' for list of built-in commands
(initramfs)

Then I type in 'EXIT" and it will slowly boot up most of the time.


At this point I don't have a clue what to do I  just feel  lucky I was able to bungle my way this far and burn an iso image and install Ubuntu. 



Any help would be appreciated
Thank you!

---

### Post by mikewhatever on 2010-05-02
When it boots, open a terminal windows and post the outputs of the following commands:

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
cat /boot/grub/grub.cfg
```

---

### Post by Feuer frei on 2010-05-02
xxxxx@xxxxxx-desktop:~$ sudo fdisk -1
[sudo] password for xxxxx: 
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

xxxxx@xxxxx-desktop:~$ sudo blkid
/dev/sda1: UUID="39ec1770-1e59-49c8-874d-1a20a13f30d0" TYPE="ext3" 
/dev/sda5: UUID="dee08192-1daa-47e1-a36e-b010ea69f533" TYPE="swap" 
/dev/sdb1: UUID="F0C4E018C4DFDF42" TYPE="ntfs" 
/dev/sdc1: UUID="2EC4EC82C4EC4E21" TYPE="ntfs" 
/dev/sdd1: UUID="D8C0F8BDC0F8A2C4" TYPE="ntfs" 
/dev/sde1: UUID="DC6404F26404D166" TYPE="ntfs" 
xxxxx@xxxxx-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dee08192-1daa-47e1-a36e-b010ea69f533 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
xxxxx@xxxxx-desktop:~$ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory
xxxxx@xxxxx-desktop:~$

---

### Post by mikewhatever on 2010-05-03
Alright, have another go at the commands that hadn't produced the correct output:

```
sudo fdisk -l #That is a smsll L and not 1
cat /boot/grub/menu.lst
```

Meanwhile, I'll go ask google about the problem.

---

### Post by RoboJ1M on 2010-05-03
I'm also getting this problem, I'll post the output of my machine.
Major foobar. :(

---

### Post by RoboJ1M on 2010-05-03
```
Gave up waiting for root device
/dev/mapper/vg_main-lv_root does not exist

```
I can't "exit"

fdisk - command not found

blkid
```
/dev/sda1: UUID="d19d2b13-7be0-853f-cc1c-0fb0c28f7934" TYPE="linux_raid_member"
/dev/sdb1: UUID="d19d2b13-7be0-853f-cc1c-0fb0c28f7934" TYPE="linux_raid_member"
/dev/sdc1: UUID="d19d2b13-7be0-853f-cc1c-0fb0c28f7934" TYPE="linux_raid_member"
/dev/sdd1: UUID="6f6b2793-ecd0-499d-8986-da5c10d27f84" TYPE="ext4"
```

cat /etc/fstab
no such file

same for grub.cfg

**Feuer frei**

All those NTFS drives, are they USB? sdb,c,d and e. 
sdd on mine is USB.
I've seen passing reference to a problem where people can't boot Ubuntu with USB drives attached. Unfortunately mines the /boot partition so I can't test.

Regards,

J.

---

### Post by mikewhatever on 2010-05-03
There is an interesting post on the issue.
[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

---

### Post by wilee-nilee on 2010-05-03
> **RoboJ1M said:**
> ```
Gave up waiting for root device
/dev/mapper/vg_main-lv_root does not exist

```
I can't "exit"

fdisk - command not found

blkid
```
/dev/sda1: UUID="d19d2b13-7be0-853f-cc1c-0fb0c28f7934" TYPE="linux_raid_member"
/dev/sdb1: UUID="d19d2b13-7be0-853f-cc1c-0fb0c28f7934" TYPE="linux_raid_member"
/dev/sdc1: UUID="d19d2b13-7be0-853f-cc1c-0fb0c28f7934" TYPE="linux_raid_member"
/dev/sdd1: UUID="6f6b2793-ecd0-499d-8986-da5c10d27f84" TYPE="ext4"
```

cat /etc/fstab
no such file

same for grub.cfg

**Feuer frei**

All those NTFS drives, are they USB? sdb,c,d and e. 
sdd on mine is USB.
I've seen passing reference to a problem where people can't boot Ubuntu with USB drives attached. Unfortunately mines the /boot partition so I can't test.

Regards,

J.

Your going to want to start your own thread, the problems with your computer do not = those of the OP. When you start a thread post the boot script, in code tags #.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The OP should really do this as well, IE the bootscript.

mikewhatever is a very good prognosticator so, I'm surprised to not see a request for the ubiquitous script.

Since in the end making sure we understand exactly whats going on and where it is at is imperative to not borking the whole HD.

---

### Post by Feuer frei on 2010-05-03
xxxxx@xxxxx-desktop:~$ sudo fdisk -1 #That is a smsll L and not 1
[sudo] password for xxxxx: 
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

xxxxx@xxxxx-desktop:~$ cat /boot/grub/menu.lst
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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--xxx'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password xxxxxxxx
#      password --xxx xxxxxxxxxxxxxxxxxxxxxx/
# password xxxxxxxxxxx

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
# kopt=root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=39ec1770-1e59-49c8-874d-1a20a13f30d0

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-11-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-9-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-9-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-7-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
xxxxxxxxxx-desktop:~$ 


[COLOR=Black]**RoboJ1m**[/COLOR]

Those other NTFS are SCSI drives

---

### Post by Feuer frei on 2010-05-03
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

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

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 18.4 GB, 18373349376 bytes
255 heads, 63 sectors/track, 2233 cylinders, total 35885448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    34,298,774    34,298,712  83 Linux
/dev/sda2          34,298,775    35,873,144     1,574,370   5 Extended
/dev/sda5          34,298,838    35,873,144     1,574,307  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    38,909,429    38,909,367   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    38,909,429    38,909,367   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    38,909,429    38,909,367   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63    38,909,429    38,909,367   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        39ec1770-1e59-49c8-874d-1a20a13f30d0   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        dee08192-1daa-47e1-a36e-b010ea69f533   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F0C4E018C4DFDF42                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2EC4EC82C4EC4E21                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        D8C0F8BDC0F8A2C4                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        DC6404F26404D166                       ntfs                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


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
# e.g. password xxxxxxxx
#      password --xxxxxxxxxxxxxxxxxxxxxxxxx
# password xxxxxxx

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
# kopt=root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=39ec1770-1e59-49c8-874d-1a20a13f30d0

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-11-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-9-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-9-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-7-generic
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dee08192-1daa-47e1-a36e-b010ea69f533 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/menu.lst
   6.4GB: boot/grub/stage2
   6.9GB: boot/initrd.img-2.6.27-11-generic
   6.4GB: boot/initrd.img-2.6.27-7-generic
   6.9GB: boot/initrd.img-2.6.27-9-generic
   6.5GB: boot/initrd.img-2.6.28-16-generic
   7.0GB: boot/initrd.img-2.6.31-21-generic
   7.2GB: boot/initrd.img-2.6.32-21-generic
   6.4GB: boot/vmlinuz-2.6.27-11-generic
   6.4GB: boot/vmlinuz-2.6.27-7-generic
   6.4GB: boot/vmlinuz-2.6.27-9-generic
   6.7GB: boot/vmlinuz-2.6.28-16-generic
   6.8GB: boot/vmlinuz-2.6.31-21-generic
   6.5GB: boot/vmlinuz-2.6.32-21-generic
   7.2GB: initrd.img
   7.0GB: initrd.img.old
   6.5GB: vmlinuz
   6.8GB: vmlinuz.old

---

### Post by wilee-nilee on 2010-05-04
Made it easier to read for others.
```

Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> Windows is installed in the MBR of /dev/sdb
=> Windows is installed in the MBR of /dev/sdc
=> Windows is installed in the MBR of /dev/sdd
=> Windows is installed in the MBR of /dev/sde

sda1: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sdc1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sdd1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sde1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 18.4 GB, 18373349376 bytes
255 heads, 63 sectors/track, 2233 cylinders, total 35885448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 63 34,298,774 34,298,712 83 Linux
/dev/sda2 34,298,775 35,873,144 1,574,370 5 Extended
/dev/sda5 34,298,838 35,873,144 1,574,307 82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 63 38,909,429 38,909,367 7 HPFS/NTFS


Drive: sdc ___________________ __________________________________________________ ___

Disk /dev/sdc: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdc1 63 38,909,429 38,909,367 7 HPFS/NTFS


Drive: sdd ___________________ __________________________________________________ ___

Disk /dev/sdd: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdd1 63 38,909,429 38,909,367 7 HPFS/NTFS


Drive: sde ___________________ __________________________________________________ ___

Disk /dev/sde: 19.9 GB, 19923993088 bytes
255 heads, 63 sectors/track, 2422 cylinders, total 38914049 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sde1 63 38,909,429 38,909,367 7 HPFS/NTFS


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/sda1 39ec1770-1e59-49c8-874d-1a20a13f30d0 ext3
/dev/sda2: PTTYPE="dos"
/dev/sda5 dee08192-1daa-47e1-a36e-b010ea69f533 swap
/dev/sda: PTTYPE="dos"
/dev/sdb1 F0C4E018C4DFDF42 ntfs
/dev/sdb: PTTYPE="dos"
/dev/sdc1 2EC4EC82C4EC4E21 ntfs
/dev/sdc: PTTYPE="dos"
/dev/sdd1 D8C0F8BDC0F8A2C4 ntfs
/dev/sdd: PTTYPE="dos"
/dev/sde1 DC6404F26404D166 ntfs
/dev/sde: PTTYPE="dos"

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sda1 / ext3 (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password xxxxxxxx
# password --xxxxxxxxxxxxxxxxxxxxxxxxx
# password xxxxxxx

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=39ec1770-1e59-49c8-874d-1a20a13f30d0

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro single
initrd /boot/initrd.img-2.6.32-21-generic

title Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.31-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash
initrd /boot/initrd.img-2.6.31-21-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.31-21-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro single
initrd /boot/initrd.img-2.6.31-21-generic

title Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro single
initrd /boot/initrd.img-2.6.28-16-generic

title Ubuntu 10.04 LTS, kernel 2.6.27-11-generic
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 10.04 LTS, kernel 2.6.27-9-generic
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.27-9-generic (recovery mode)
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 10.04 LTS, kernel 2.6.27-7-generic
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 10.04 LTS, kernel 2.6.27-7-generic (recovery mode)
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 10.04 LTS, memtest86+
uuid 39ec1770-1e59-49c8-874d-1a20a13f30d0
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=39ec1770-1e59-49c8-874d-1a20a13f30d0 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=dee08192-1daa-47e1-a36e-b010ea69f533 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


6.5GB: boot/grub/menu.lst
6.4GB: boot/grub/stage2
6.9GB: boot/initrd.img-2.6.27-11-generic
6.4GB: boot/initrd.img-2.6.27-7-generic
6.9GB: boot/initrd.img-2.6.27-9-generic
6.5GB: boot/initrd.img-2.6.28-16-generic
7.0GB: boot/initrd.img-2.6.31-21-generic
7.2GB: boot/initrd.img-2.6.32-21-generic
6.4GB: boot/vmlinuz-2.6.27-11-generic
6.4GB: boot/vmlinuz-2.6.27-7-generic
6.4GB: boot/vmlinuz-2.6.27-9-generic
6.7GB: boot/vmlinuz-2.6.28-16-generic
6.8GB: boot/vmlinuz-2.6.31-21-generic
6.5GB: boot/vmlinuz-2.6.32-21-generic
7.2GB: initrd.img
7.0GB: initrd.img.old
6.5GB: vmlinuz
6.8GB: vmlinuz.old

```

---

### Post by tsaowang on 2010-05-04
Hello,

I have had the exact same problem from the day when Lucid Lynx was released.
I have been looking everywhere on the net to find a solution and found this :

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

I haven't tested yet (at least today), after several installations of Karmic<->Lucid, the only OS that is working for me is Xubuntu 10.04 (don't ask me why, because I should encounter the same issue)

Hope this can help

---

