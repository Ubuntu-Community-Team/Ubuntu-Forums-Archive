---
title: "Wierd partitioning/bootloader issue"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by karl-arthur on 2010-11-14
Hi all,

My Ubuntu-partition seems to have disappeared, yet it shows up in Grub. Needless to say, I'd very much like it back, so any suggestions will be appreciated. I'll try to explain what led to this situation.

I have a netbook (HP) with Jolicloud, Windows 7 and Ubuntu 10.4 on different partitions. Recently, I've been running low on storage space on the Ubuntu one, which is the one I primarily use, so I wanted to move some space from windows to ubuntu. I used gparted in Jolicloud to resize and move the windows partition, and than proceeded to test windows to see if everything was ok. It was not, and windows went into repair mode. For some reason, I decided to run the HP recovery tool instead, which unfortunately did me no good, and led to Grub Error 22 upon reboot.

I plugged in a Jolicloud live USB, and reinstalled jolicloud, including Grub. It didn't show my already installed jolicloud when it came time to choose a partition to install in, instead claiming that the area left over from the windows resize, plus what had been jolicloud, to be free space. Everything else was correctly displayed. So I installed jolicloud onto that space. Everything went fine, I rebooted in to Ubuntu, which worked after a disk check, and then fixed windows without problems (it also did a disk check on reboot).  

At this point I was fed up with (scared of) partitioning and bootloaders, so I decided to log back into ubuntu, to do other stuff. But although I'd made no changes since the last time, when it worked fine, this time I got Grub error 15 (file not found). Grub shows all the various kernels as before. Now, in Jolicloud, gparted shows no partitions at all, just one block of unallocated space, but the windows partitioning tool shows the right partitions, except that the one that should have been Ubuntu is shown as consisting of free space.

I thought about reinstalling jolicloud yet again, hoping that would somehow give me a new Grub that read things properly. But the installer would only let me deal with that single unallocated space, so I decided not to. Now the only thing I can think of is reinstalling ubuntu with wubi in it's previous, now empty-seeming partition.

Any ideas I can try before doing that? I'd love not having to set up my system again, as I have spent quite some time setting it up to function properly with different types of hardware etc. 

I'm sorry if my description of what happened is unclear at any point, I'm not very experienced with partitioning, as you might have guessed. Feel fre to ask, and I'll specify as best I can. 

Thanks

Karl

---

### Post by Hippytaff on 2010-11-14
if you download and run this script - [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
it will show you some useful info, if you post the results.txt people will be able to help you sort it :-)

---

### Post by karl-arthur on 2010-11-14
Thanks for answering so quickly. Results.txt is attached. I'll start reading through it myself and see if I can make any sense of it. 

Karl

---

### Post by Hippytaff on 2010-11-14
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Jolicloud robby
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26556584

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             417,690   125,306,999   124,889,310   7 HPFS/NTFS
/dev/sda3         125,307,000   460,165,859   334,858,860   5 Extended
/dev/sda5         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)
/dev/sda6         454,382,523   460,165,859     5,783,337  82 Linux swap / Solaris
/dev/sda7         125,307,126   234,067,049   108,759,924  83 Linux
/dev/sda8         234,067,113   238,790,159     4,723,047  82 Linux swap / Solaris
/dev/sda4         460,173,312   488,183,807    28,010,496   7 HPFS/NTFS

the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2A267F77267F42BD                       ntfs       SYSTEM                        
/dev/sda2        A276F13B76F110B1                       ntfs                                     
/dev/sda4        2A2A1D132A1CDD9F                       ntfs       RECOVERY                      
/dev/sda5        4CE8-F9D2                              vfat       HP_TOOLS                      
/dev/sda6        6f8af499-c532-4741-8e24-6e9baec6bb35   swap                                     
/dev/sda7        77ef023f-c443-4745-88fc-d571e1d16394   ext4                                     
/dev/sda8        d3bb340d-803d-4d40-ab60-0eacd55b3d2c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sda2        /media/Volume            (ntfs)     fuseblk (rw,nosuid,nodev,sync,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,sync,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/HP_TOOLS          vfat       (rw,nosuid,nodev,sync,uhelper=hal,uid=1000)


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

## debug [on | off | normal | status | INTEGER]
# Turn on/off or display/set the debug level.
debug        off

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title        Jolicloud robby (v1.0 Release), kernel 2.6.32.9-1-jolicloud
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.32.9-1-jolicloud root=/dev/sda7 ro quiet splash 
initrd        /boot/initrd.img-2.6.32.9-1-jolicloud
quiet

title        Jolicloud robby (v1.0 Release), kernel 2.6.32.9-1-jolicloud (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.32.9-1-jolicloud root=/dev/sda7 ro  single
initrd        /boot/initrd.img-2.6.32.9-1-jolicloud

title        Jolicloud robby (v1.0 Release), memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Windows Vista (loader)
rootnoverify    (hd0,3)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro splash quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single splash 
initrd        /boot/initrd.img-2.6.32-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro splash quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single splash 
initrd        /boot/initrd.img-2.6.32-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro splash quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single splash 
initrd        /boot/initrd.img-2.6.32-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro splash quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single splash 
initrd        /boot/initrd.img-2.6.32-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro splash quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single splash 
initrd        /boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro splash quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single splash 
initrd        /boot/initrd.img-2.6.32-21-generic
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext4    relatime,errors=remount-ro 0       1
/dev/sda8       none            swap    sw              0       0
/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 115.8GB: boot/grub/menu.lst
 115.8GB: boot/grub/stage2
 115.8GB: boot/initrd.img-2.6.32.9-1-jolicloud
 115.8GB: boot/vmlinuz-2.6.32.9-1-jolicloud
 115.8GB: initrd.img
 115.8GB: vmlinuz

```

For ease of use :-)

---

### Post by Hippytaff on 2010-11-14
Did you install jolicloud after ubuntu. Try
```

sudo update-grub

```

---

### Post by karl-arthur on 2010-11-14
I did install Jolicloud after Ubuntu, and I do wish now that I'd chosen to install it without new bootloader. But update-grub, done from within Jolicloud, doesn't seem to have made any difference. Is there a way to force Grub 2 back? Would it help?

---

### Post by karl-arthur on 2010-11-14
Okay, I see that sudo apt-get install grub2 will work. So my new question is: Will that help, or make everything much, much worse?

---

### Post by Hippytaff on 2010-11-14
Ok, I'm not sure of the best course of action here. I've called in the cavalry :-)

---

### Post by karl-arthur on 2010-11-14
Ok, thanks for helping so far.

---

### Post by oldfred on 2010-11-14
I am not sure I am the cavalry. I know nothing about Jolicloud

> the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
Do you have anything important in sda5? Either way I would first back up and  delete sda5. That may correct it all. But you do not have a Ubuntu install.

You do have two swaps as if two systems were installed, but sda5 is too small to be an install even if it was correctly set up. The other possibility was the sda4 NTFS partition is not really NTFS?

If you want to see what old partitions were but you may not be able to totally recover without destroying something else.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by karl-arthur on 2010-11-14
I think sda5 is the HP recovery tool that messed up everything in the first place, and that sda3 is where Ubuntu is supposed to be. Although it should be the other way around, no? Would you recommend deleting sda5 (remove or format?) in gparted?

I'll look at the testdisk links you provided, though. Thanks for the pointers.

---

### Post by karl-arthur on 2010-11-14
Ok, so in Testdisk (analyse) i am told that there is a space conflict between partitions 3 and 5. Choosing quick search gives me a list of partitions that appears to be just as they in fact were before the problems began, and by pressing p I can browse the folders of the lost partition. Everything seems to be there. However, in this view all the partitions are marked D (for deleted). What does that mean? And how do I proceed from here? I'm currently waiting for test disk's "deeper search" to finish, but the instructions are harder to understand from then on.

---

### Post by Hippytaff on 2010-11-14
I've never used it but this wiki might help
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by karl-arthur on 2010-11-14
This is what came of "deeper search" in testdisk:

```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
D HPFS - NTFS             25 126 37    50 220 41     407552
D HPFS - NTFS             25 126 38  7799 126 24  124889297
D HPFS - NTFS             25 126 38 14863 165 22  238374912
D HPFS - NTFS             25 126 38 28644 118 18  459763712
D HPFS - NTFS             26   0  1  7799 254 50  124889297
D HPFS - NTFS             26   0 14  7799 254 63  124889297
D FAT16 LBA             3844  24 27  3971  23 26    2040192
D Linux                 7800   2  1 14569 254 59  108759920
D Linux                10350   2  1 14672 254 58   69448864
D Linux Swap           14570   1  1 14863 254 40    4723024
D Linux Swap           14673   1  1 14863 254 47    3068336
D Linux                14864   1  1 28283 254 58  215592232
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 208 MB / 199 MiB

```

As you can see, all the partitions are marked D for deleted. Should I mark all of them Logical (and one Primary bootable? Which one?), or just deal with the missing one? I've verified that it is the last one I want. 

Thanks a lot for helping me get this far. I wish I'd known about Testdisk a few years ago.

---

### Post by oldfred on 2010-11-14
You cannot undelete all of them. It is showing the history and undeleting may overwrite all the data in your current partitions.

For example you have 7 partitions starting from 0 to 26 CHS with different endings that may overlap with some of the others shown later. It looks like you edited the first partition several times.

It is time to look at your current partitions and compare to these and see which may be missing. But you cannot have overlapping areas or I think testdisk will not let you do it.

---

### Post by karl-arthur on 2010-11-14
I guess I've edited the first partition more than once, once when the computer was new and I needed to free space for ubuntu, and now, when I wanted to move some of it's free space to ubuntu. Was that a bad idea?

Anyway, the linux partition on the bottom of the list is the one I want. So I just mark that as logical and cross whatever fingers I may have?

---

### Post by karl-arthur on 2010-11-14
So it turns out I left out a few lines from the output of deeper search before. I was going to post them here, but by force of habit,I used ctrl-c to do so. For the second time, actually. It doesn't copy in the terminal, you know, just closes testdisk. Both times. Shocker. Anyway, the search takes about an hour to run, so I'll set it off again and go to bed (it's two am here). But just to recap:

The omitted lines (going from memory) were one more linux swap partition (belonging to the missing linux partition, I guess), and two partitions similar to the top ones quoted above, one marked as primary and one as primary bootable. 

Am I correct to understand that all these partitions listed by deeper search (at least the ones marked D) are just listings of "partition-positions" that have become obsolete in repartitioning? And that therefore I should mark the one I'm missing L, leave the others alone and write a new partition table?

Or do I have to go through the above list, eliminating erased "ancestors" of existing partitions before marking the ones I think I still have L, and then try to write the table and hope for the best? Or have I misunderstood altogether what testdisk is and does? Questions, so many questions ;)

Anyway, community support rocks. I'll be back tomorrow, either with results of whatever advice appears here while I'm away, or with more questions. Good night, all.

---

### Post by oldfred on 2010-11-14
I never have had to do a test disk recovery of a partition. But I think you just want to undelete the missing one as long as it does not overlap something else you want.

---

### Post by Hippytaff on 2010-11-15
> 
ctrl-c 

for furture reference if you do CTRL+SHIFT+C in a terminal it will copy. :-)

---

### Post by karl-arthur on 2010-11-15
Hi again,

Since last night I've, surprisingly, managed to reverse my partition situation. That is, I'm posting from a live USB (ubuntu 10.4), in which gparted sees my old (previously missing) ubuntu partition, but shows what should be windows and jolicloud as unallocated space. The reason I'm in the live usb is that I tried what I said I'd try in testdisk, namely to mark the missing partition Logistical, write partition table, and reboot. That rewarded me with an ever so promising Grub Error 22. 

I've mounted and browsed my old ubuntu partition, it seems to have the folder structure correct to a point, but a lot of files are missing. The size and remaining space, however, matches what was the case before all of this shenanigans went down. I've managed to transfer the few personal files I didn't have backed up elsewhere to an external harddrive. 

At this point I'm almost happy to format the entire disk and start over. But before doing that I should make at least one desperate move to try to salvage something, right? So the way I see it there are three options, in descending order of chance of succsess:

1) Let Ubuntu install it self in largest continious free space and hope that on reboot I'll have two functioning Ubuntus to boot into, one spanking new and one old and haggard. 

2) Try to save windows, the only OS I can't easily get back, as I don't have a CD for it. (I still blame its recovery partition for this whole thing, so I won't be using that anymore.) I'd try by running Testdisk from the Live USB, mark the partition matching Windows' Logical, presumably get a new Grub 22, but hope the thing shows up in the live USB.

3) Try to restore all the partitions by memory in testdisk from live usb. Estimated chance of success: about none at all.

So what do you think my odds are for any of these options?

---

### Post by Hippytaff on 2010-11-15
I'd say, go for the best case senario first, and after if all else fails do a fresh install.

---

### Post by oldfred on 2010-11-15
We like to fix things (sometimes it helps us all to understand), but we will spend days fixing things when you can reinstall in a hour or so.:)

So your choice.

If you want to know what is where and we may be able to see if boot files are missing or not.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Generally after any partition changes you will have to reinstall grub. Error 22 sounds like old grub, not grub2.

---

### Post by karl-arthur on 2010-11-16
Hi again.

Fortunately my day-to-day computing is pretty cloud-based, so I can afford to spend a few days aiming for perfect solutions at the cost of quick recovery. This is my results.txt from a live USB:

```
        

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         238,790,160   454,382,459   215,592,300   f W95 Ext d (LBA)
/dev/sda5         238,790,223   454,382,454   215,592,232  83 Linux
/dev/sda2    *    460,173,312   488,183,807    28,010,496   7 HPFS/NTFS
/dev/sda3         488,183,808   488,395,119       211,312   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1007 MB, 1007157248 bytes
114 heads, 55 sectors/track, 313 cylinders, total 1967104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              1     1,967,103     1,967,103   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        2A2A1D132A1CDD9F                       ntfs       RECOVERY                      
/dev/sda3        4CE8-F9D2                              vfat       HP_TOOLS                      
/dev/sda5        2ddd421a-d83b-4c1c-ac8a-ab23d86361e5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E35-ABDA                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 2ddd421a-d83b-4c1c-ac8a-ab23d86361e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2a267f77267f42bd
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set a276f13b76f110b1
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 2a2a1d132a1cdd9f
	chainloader +1
}
menuentry "Jolicloud robby (v1.0 Release), kernel 2.6.32.9-1-jolicloud (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1923125d-4c01-4722-a6d2-01463fcd0a9d
	linux /boot/vmlinuz-2.6.32.9-1-jolicloud root=/dev/sda7 ro quiet splash
	initrd /boot/initrd.img-2.6.32.9-1-jolicloud
}
menuentry "Jolicloud robby (v1.0 Release), kernel 2.6.32.9-1-jolicloud (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1923125d-4c01-4722-a6d2-01463fcd0a9d
	linux /boot/vmlinuz-2.6.32.9-1-jolicloud root=/dev/sda7 ro single
	initrd /boot/initrd.img-2.6.32.9-1-jolicloud
}
menuentry "Jolicloud robby (v1.0 Release), memtest86+ (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1923125d-4c01-4722-a6d2-01463fcd0a9d
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=2ddd421a-d83b-4c1c-ac8a-ab23d86361e5 /               ext4    errors=remount-ro 0       1
UUID=6f8af499-c532-4741-8e24-6e9baec6bb35 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 122.4GB: boot/grub/core.img
 138.7GB: boot/grub/grub.cfg
 153.9GB: boot/initrd.img-2.6.32-21-generic
 137.2GB: boot/initrd.img-2.6.32-22-generic
 182.3GB: boot/initrd.img-2.6.32-23-generic
 184.0GB: boot/initrd.img-2.6.32-24-generic
 140.0GB: boot/initrd.img-2.6.32-25-generic
 217.0GB: boot/initrd.img-2.6.32-26-generic
 139.9GB: boot/vmlinuz-2.6.32-21-generic
 137.1GB: boot/vmlinuz-2.6.32-22-generic
 154.5GB: boot/vmlinuz-2.6.32-23-generic
 184.0GB: boot/vmlinuz-2.6.32-24-generic
 186.2GB: boot/vmlinuz-2.6.32-25-generic
 215.8GB: boot/vmlinuz-2.6.32-26-generic
 217.0GB: initrd.img
 140.0GB: initrd.img.old
 215.8GB: vmlinuz
 186.2GB: vmlinuz.old

```

Right now I'm leaning towards attempting a full recovery through extensive testdisk manipulation, and will be eagerly awaiting good advice based on the above. But windows recovery is my first priority, as I have no way of getting that back without paying microsoft a lot more than I'm willing to.

Also, as I said I've managed to recover all my important files (they are all there, it turns out, just hidden because of permissions, easily fixed with sudo chmod), but would appreciate some advice for recovering non-files (settings, apps etc.). I have a deja dup backup from about a month back, would restoring that on a fresh install recover users, apps and settings, or just files? Any folders in or outside of /home I should grab while I still can?

Thanks again for helping.

---

### Post by oldfred on 2010-11-16
You still have grub legacy in the MBR and should just be able to reinstall grub2 to the MBR to boot Ubuntu.

But your windows has changed?
```
Newer
sda2: __________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd
Older
sda2: __________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD [COLOR=Red]/Windows/System32/winload.exe[/COLOR]

```Without the winload.exe windows will not boot.

Reinstall grub2 -Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by karl-arthur on 2010-11-16
Okay, I now have my old ubuntu partition back, plus a brand new one. As for windows, I have a partition that nautilus can't mount, gparted gives a stern warning about, and Grub can't see. It can see a recovery partition, though, but I'm too scared to try it. I think I'll quit messing around before I start damaging the hardware. Although, if windows is definitely dead, I would like to move the gigs it's occupying into Ubuntu, and perhaps replace the new ubuntu with jolicloud again. But I'll wait a while, hopefully until I'm able to buy a new computer. Then I won't be so dependent on this one working properly all the time. 

Thanks for all your help, oldfred and Hippytaff. It's much appreciated!

---

### Post by Hippytaff on 2010-11-16
If you do```

 sudo update-grub
```
grub might pick up windows. 

Glad you got it back to a state your happy with. Oldfred deserves you thanks - was way beyond my skills :-)

---

