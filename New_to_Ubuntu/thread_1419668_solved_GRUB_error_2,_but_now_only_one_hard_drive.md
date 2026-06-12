---
title: "solved GRUB error 2, but now only one hard drive"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by vkunkel on 2010-03-02
[LEFT]I just solved the problem of the error that kept popping up every time i tried to boot into Ubuntu:

GRUB loading stage 1.5 error 2

I disconnected one of my SATA hard drives, so essentially GRUB was only looking at one drive.

I reinstalled Live disk, and then rebooted, and the problem was solved;).
But now I only have half the hard drive space (120 G instead of 240G)

i tried plugging back in the unplugged hard drive, to see if i could fool the system. This did not work. The system went past the boot stage, but then hung:(.

I also tried to partition the replugged hard drive, still nothing. Any suggestions?
[/LEFT]

---

### Post by Peter09 on 2010-03-02
It may be that the harddrive is faulty - have you any other systems to test it on?

---

### Post by presence1960 on 2010-03-02
Plug both disks in and do this so I can get more info about your setup & boot process:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by vkunkel on 2010-03-02
Im in Australia, with a different time zone, I will attempt your suggestion after I finish work (8 hours time) Thanks.

---

### Post by presence1960 on 2010-03-02
> **vkunkel said:**
> Im in Australia, with a different time zone, I will attempt your suggestion after I finish work (8 hours time) Thanks.

No rush, I am not going to a fire.

---

### Post by vkunkel on 2010-03-03
Just a few of my own observations of the script below:

[LIST=1]
[*]The version installed on MBR is Grub, but I assumed Ubuntu 9.10 installed GRUB2, which is what I'm told when I enter: grub-install -v, I get "grub-install (GNU GRUB 1.97~beta4)" from live CD
[*]From the GParted application, the /dev/mapper/isw_dhcbjcdcjf_RAID_Volume1 has not been partitioned, but I have partitioned /dev/sdb, the hard drive that I had physically unplugged. I am assuming the installation of ubuntu set up its required partitions on /dev/sda
[*]The output refers to /dev/mapper/isw_dhcbjcdcjf_RAID_Volume1, /dev/mapper/isw_dhcbjcdcjf_RAID_Volume11, and /dev/mapper/isw_dhcbjcdcjf_RAID_Volume12 (is this confusing?)
[*]there is some error in /dev/mapper/...:bad superblock, missing codepage
[/LIST]
 
 ```
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of 
    /dev/mapper/isw_dhcbjcdcjf_RAID_Volume1 and looks on the same drive in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

isw_dhcbjcdcjf_RAID_Volume11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/mapper/isw_dhcbjcdcjf_RAID_Volume11,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


isw_dhcbjcdcjf_RAID_Volume12: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: isw_dhcbjcdcjf_RAID_Volume1 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dhcbjcdcjf_RAID_Volume1: 240.1 GB, 240067805184 bytes
255 heads, 63 sectors/track, 29186 cylinders, total 468882432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe893e893

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11                 63   228,797,729   228,797,667  83 Linux
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume12        228,797,730   234,436,544     5,638,815   5 Extended
Invalid MBR Signature found
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 5687ac93-5fb0-4f30-a2d0-3d142670b222   ext4                                     
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume1p1 5687ac93-5fb0-4f30-a2d0-3d142670b222   ext4                                     
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dhcbjcdcjf_RAID_Volume1
isw_dhcbjcdcjf_RAID_Volume11
isw_dhcbjcdcjf_RAID_Volume1p1
isw_dhcbjcdcjf_RAID_Volume1p2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on isw_dhcbjcdcjf_RAID_Volume12



=======Devices which don't seem to have a corresponding hard drive==============

sdb: "sil" and "isw" formats discovered (using isw)! sda: "sil" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: only one argument allowed for this option
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
hexdump: /dev/mapper/isw_dhcbjcdcjf_RAID_Volume12: No such file or directory
hexdump: /dev/mapper/isw_dhcbjcdcjf_RAID_Volume12: No such file or directory
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: only one argument allowed for this option
```

---

### Post by presence1960 on 2010-03-03
If you do not have RAID setup now you need to get rid of the RAID settings. Go into BIOS and disable RAID. Boot the Ubuntu Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
dmraid -E -r /dev/sda
```
After that open gparted and you should see that "/dev/mapper/isw_dhcbjcdcjf_RAID_Volume1" is gone and replaced with sda. Then run another boot info script with both hard disks attached.

---

### Post by vkunkel on 2010-03-03
Results from terminal were: 
ubuntu@ubuntu:~$ dmraid -E -r /dev/sda
ERROR: you must be root
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda
ERROR: sil: writing sda_2.dat[Bad address]
ERROR: sil: writing sda_3.dat[Bad address]
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
/dev/sda: "sil" and "isw" formats discovered (using isw)!
Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :y

Which has now given me:
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume1
/dev/sda
/dev/sdb
/dev/sdc

from gparted

---

### Post by vkunkel on 2010-03-03
sorry, forgot to post # code, will post Results again

---

### Post by vkunkel on 2010-03-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Lilo is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of 
    /dev/mapper/isw_dhcbjcdcjf_RAID_Volume1

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_dhcbjcdcjf_RAID_Volume11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe893e893

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   228,797,729   228,797,667  83 Linux
/dev/sda2         228,797,730   234,436,544     5,638,815   5 Extended
/dev/sda5         228,797,793   234,436,544     5,638,752  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 1018 MB, 1018953728 bytes
208 heads, 52 sectors/track, 46 cylinders, total 497536 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             52       497,535       497,484   b W95 FAT32


Drive: isw_dhcbjcdcjf_RAID_Volume1 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dhcbjcdcjf_RAID_Volume1: 120.0 GB, 120033902592 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441216 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005d074

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11                 63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 6634B5F164A29295                       ntfs                                     
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume1p1 6634B5F164A29295                       ntfs                                     
/dev/sda1        5687ac93-5fb0-4f30-a2d0-3d142670b222   ext4                                     
/dev/sda5        3cea9b82-fbdb-4bcf-a2ce-a1f1d928be01   swap                                     
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        4C6C-F088                              vfat       MR K'S MP3                    

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dhcbjcdcjf_RAID_Volume1
isw_dhcbjcdcjf_RAID_Volume11
isw_dhcbjcdcjf_RAID_Volume1p1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
# kopt=root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/menu.lst
    .4GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.31-14-generic
    .8GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
    .8GB: initrd.img
    .5GB: initrd.img.old
    .6GB: vmlinuz
    .5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sdb: "sil" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: only one argument allowed for this option
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
ERROR: only one argument allowed for this option
```

---

### Post by psusi on 2010-03-03
Were you intending to use these disks in a raid or not?  You have already destroyed the raid metadata on the first disk, you need to do the same to the second:

sudo dmraid -E /dev/sdb

Then you need to figure out how you want to configure the disks and format and reinstall.

---

### Post by vkunkel on 2010-03-03
Rentered sudo dmraid -E -r /dev/sda

with the results:

ERROR: sil: writing sda_2.dat[Bad address]
ERROR: sil: writing sda_3.dat[Bad address]
ERROR: sil: only 2/4 metadata areas found on /dev/sda, electing...
Do you really want to erase "sil" ondisk metadata on /dev/sda ? [y/n] :y

Reentered again with results:


no raid disks and with names: "/dev/sda"

---

### Post by psusi on 2010-03-03
No, I said sd**b**.  And you still have not said whether or not you wanted to use the drives in a raid array.

---

### Post by vkunkel on 2010-03-03
No, I did not want to use the disks in a raid array, but I assume its possible to later change them back to raid, or would that require backing up data then reinstalation of ubuntu?

---

### Post by vkunkel on 2010-03-03
I will attempt to partition drives and reinstall ubuntu

---

### Post by vkunkel on 2010-03-03
I have removed raid from sdb
Boot info script results before installing:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe893e893

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   228,797,729   228,797,667  83 Linux
/dev/sda2         228,797,730   234,436,544     5,638,815   5 Extended
/dev/sda5         228,797,793   234,436,544     5,638,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005d074

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 1018 MB, 1018953728 bytes
208 heads, 52 sectors/track, 46 cylinders, total 497536 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             52       497,535       497,484   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 6634B5F164A29295                       ntfs                                     
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume1p1 6634B5F164A29295                       ntfs                                     
/dev/sda1        5687ac93-5fb0-4f30-a2d0-3d142670b222   ext4                                     
/dev/sda5        3cea9b82-fbdb-4bcf-a2ce-a1f1d928be01   swap                                     
/dev/sdc1        4C6C-F088                              vfat       MR K'S MP3                    

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dhcbjcdcjf_RAID_Volume1
isw_dhcbjcdcjf_RAID_Volume11
isw_dhcbjcdcjf_RAID_Volume1p1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
# kopt=root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume11 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_dhcbjcdcjf_RAID_Volume15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/menu.lst
    .4GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.31-14-generic
    .8GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
    .8GB: initrd.img
    .5GB: initrd.img.old
    .6GB: vmlinuz
    .5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1



=======Devices which don't seem to have a corresponding hard drive==============

sdd 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
```

---

### Post by psusi on 2010-03-03
> **vkunkel said:**
> No, I did not want to use the disks in a raid array, but I assume its possible to later change them back to raid, or would that require backing up data then reinstalation of ubuntu?

Requires backup and reinstall, so you need to decide now.  If you AREN'T going to use them in a raid, then what ARE you going to do with them?  Use one for /home?

---

### Post by vkunkel on 2010-03-03
> **psusi said:**
> Requires backup and reinstall, so you need to decide now. If you AREN'T going to use them in a raid, then what ARE you going to do with them? Use one for /home?

I was going to have dual boot system: use one hard drive (120G) for ubuntu, and the other for Windows (120 G)

---

### Post by psusi on 2010-03-03
> **vkunkel said:**
> I was going to have dual boot system: use one hard drive (120G) for ubuntu, and the other for Windows (120 G)

Ahh, then now that you have gotten rid of the broken raid setup, you should just install windows to the first drive, then install Ubuntu on the second.

---

### Post by vkunkel on 2010-03-03
> **psusi said:**
>  you should just install windows to the first drive, then install Ubuntu on the second.
does it matter which order eg ubuntu first drive, windows second?

---

### Post by vkunkel on 2010-03-03
ubuntu boots with both drives plugged in now :D. Thanks psusi, thanks prescence1960.

Although, now I am left wondering if I should have a go at creating a duel boot system on a RAID array?

I still also have to install Windows sometime on the other drive. 

Thanks again

vkunkel

---

### Post by psusi on 2010-03-03
It is easier to install Windows first on the first drive, THEN install Ubuntu.  You run into problems trying other ways.  None of them can't be fixed, but it is more trouble.

And yes, you can raid the drives and split it into two partitions, installing windows in one and Ubuntu in the other, though there are still one or two gotchas to watch out for doing that.

---

