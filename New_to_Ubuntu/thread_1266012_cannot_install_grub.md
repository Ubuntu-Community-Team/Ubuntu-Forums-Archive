---
title: "cannot install grub"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by jdstunner on 2009-09-14
I cannot get grub to reinstall on my computer. The situation at hand:

I installed XP, fully configured the OS, installed Ubuntu, reboot, XP doesn't boot anymore.

I tried various tweaks in the menu.lst file noted in other threads. 

Finally I used the XP cd to load the Recovery Console, run *fixmbr* and boot into XP. Now grub is gone. 

I then loaded my Ubuntu Live CD, and performed these steps:
```

mkdir /ubuntu
mount /dev/sdc2 /ubuntu 
chroot /ubuntu /bin/bash
grub
root (hd2,1)
```and I get this output
[I]
Error 21: Selected disk does not exist

[/I]This is the output from fdisk -l:

SIDENOTE:
#My Ubuntu 9.04 dist is installed on /dev/sdc2 - I want this to be Primary boot OS
#XP is installed on /dev/sdc1 - Secondary boot OS
#Ubuntu 8.04 is installed on /dev/sdb1 - this is a backup OS for /dev/sdb - NOT USED
#/dev/sda is a fat32 storage drive


```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010b2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    b  W95 FAT32

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000523f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        2918     3903795   82  Linux swap / Solaris
/dev/sdb3            2919      121601   953321197+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ea02e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sdc2            9729       19457    78148192+  83  Linux

```However, if I run fdisk -l while chrooted, i get this output:

*cannot open /proc/partitions*

I looked inside the directory /proc... it is empty.

---

### Post by zvacet on 2009-09-14
Try [this.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by jdstunner on 2009-09-14
Thanks for the reply.

I tried the instructions provided in the link. Here is what I typed:

```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdc2 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd2,1)
setup (hd2)
```

Here is the kicker. Now I am right back to where I started. Grub is in the MBR and Win XP will not boot. If I run the XP Recovery Console and run *fixmbr* then it erases Grub and only boots XP. :confused:

If in the preceeding code, I use *setup (hd2,1)* ; it still boots to XP instead of grub.

---

### Post by teutonic on 2009-09-14
> **jdstunner said:**
> Thanks for the reply.

I tried the instructions provided in the link. Here is what I typed:

```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sdc2 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd2,1)
setup (hd2)
```Here is the kicker. Now I am right back to where I started. Grub is in the MBR and Win XP will not boot. If I run the XP Recovery Console and run *fixmbr* then it erases Grub and only boots XP. :confused:

If in the preceeding code, I use *setup (hd2,1)* ; it still boots to XP instead of grub.


Hi. I'm noob, but I beleive you simply need to edit the grub menu.lst to offer the XP os as a boot option. I've even seen how to add it somewhere deep in all the posts lol will research a bit further ...  this is  a quote from a linux forum 


Edit your /boot/grub/menu.lst and add the following:

     Code:
     title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1 
you need to do this because windows doesn`t boot from the secondary IDE,
the entry to boot my windows partition is
     Code:
     title Windows
root (hd0,1)
chainloader +1 
But I have both Debian and Windows in the same drive.
Grub counts as hd0 the HD conected to the 1st IDE, with the map option you change the order so you can boot windows, or something like that, so I think you shouldn`t make the second HD bootable too, but if this doesn`t work try it!


end of quote.
By the way whenever I loose the GRUB boot manager ( regularly as I experiment a lot ) I restore the grub menu like this :

1. Boot to unbuntu liveCD  (run ubuntu from CD mode )
2. mount C: ( double click in file manager )
3. Run Terminal>sudo grub
4.grub> root (hd0,5)  ( my ubuntu is on /dev/sda6 - one hard drive ( hd0) lots of partitions - find ubuntu partiton with ubuntu partition manager from live cd and take one away from the number for the grub command ))
5.setup (hd0)

I get a nice message in the grub editor in terminal showing a bunch of stuff happening and then a reboot and the loaders back

Finally - I use a gui grub editor in ubuntu to turn off the 15 second default OS timeout 'feature' and change the screen style
[http://www.kde-apps.org/content/show.php?content=75442](http://www.kde-apps.org/content/show.php?content=75442)

[IMG]http://www.ukimagehost.com/uploads/c3cc5119da.jpg[/IMG]

---

### Post by jdstunner on 2009-09-14
Thank you for the reply.

My menu.lst is as follows:

```
title        Ubuntu 9.04 - MAIN OS
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2 - MEDIADRIVE BACKUP OS
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
# This entry has been edited. Commented out lines are default. root and makeactive were added. 
title        WIN XP BLACK
root            (hd2,0)
makeactive
## rootnoverify    (hd2,0)
## savedefault
## map        (hd0) (hd2)
## map        (hd2) (hd0)
chainloader    +1
```

---

### Post by teutonic on 2009-09-14
> **jdstunner said:**
> Thank you for the reply.

My menu.lst is as follows:

```
title        Ubuntu 9.04 - MAIN OS
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2 - MEDIADRIVE BACKUP OS
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
# This entry has been edited. Commented out lines are default. root and makeactive were added. 
title        WIN XP BLACK
root            (hd2,0)
makeactive
## rootnoverify    (hd2,0)
## savedefault
## map        (hd0) (hd2)
## map        (hd2) (hd0)
chainloader    +1
```

Ok. I see an XP os entry at the end. My next advice is experimenter mode. I have images to restore when things fail - dont know if you do.

That said, I would remove the hashes ## from the XP entry so it looks like this:

title        WIN XP BLACK
root            (hd2,0)
makeactive
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1[/code][/quote]

The hashes make the entries 'remarks'. Removing the hashes would make the 'makeactive' entries 'live' and not 'remarks'. If that makes any sense. lol.

---

### Post by jdstunner on 2009-09-14
I could have provided a better explanation of the output there.

[I]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
**# This entry has been edited. Commented out lines are default. root and makeactive were added. **
title        WIN XP BLACK
[B]root            (hd2,0)
makeactive[/B]
## rootnoverify    (hd2,0)
## savedefault
## map        (hd0) (hd2)
## map        (hd2) (hd0)
chainloader    +1[/I]

The lines that are wrapped (if they appear that way when I post, they are now) are single lines so they only need one #. 

The lines that grub made when I first installed Ubuntu are the lines marked with ##.

*root *and *makeactive *were added by me in an attempt to try someone's solution.

The default lines do not work either.

I think that the GRUB installed is writing over the Win Boot Loader in the MBR. I don't know how to prevent this or even if it is the problem, but it seems that way. How can I ensure the Win boot loader and the grub boot loader are seperate? And to make the GRUB boot loader load first and chain load into XP? I can get one or the other, but not both.

---

### Post by ukripper on 2009-09-14
Use supergrubdisk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) . It will help you detect grub image in MBR.

---

### Post by jdstunner on 2009-09-14
ive downloaded super grub disc...

you mentioned using it to find the grub image in the mbr

Correct me if I am wrong, but when i do a find in the grub shell

*find /boot/grub/menu.lst*

[I]find /boot/grub/stage1

[/I]etc...

these commands find both of my grub entries

(hd1,0)
(hd2,1)

1,0 is not to be used. It is part of a media drive so I can boot my media drive from any pc. 

2,1 contains the ubuntu partition i want to boot primarily

2,0 contains the xp partition that i want to boot as well

---

### Post by oldfred on 2009-09-14
What drive boots first in BIOS? and is grub then installed on your sda which is just a data disk?

You either need root & makeactive or rootnoverify - both work for WinXP. If your XP is not sda you need the map commands to map windows back to the first drive. It wants to be first.

It may make more sense to boot the current third drive first and install grub to that drive, then the map commands for windows would not be required. I would also suggest having a grub on your current sdb ubuntu 8.10 drive so if you every have to boot it standalone then it will boot. This is based on one suggestion that every drive have a boot entry for that drives operating system, so in case of hard drive failure there is a fallback without major issues.

---

### Post by jdstunner on 2009-09-14
thank you for the reply oldfred... it wouldn't let me add a reply so i started a new thread with more information on the problem. 

sdc does boot first... if i boot sdb, the grub that is installed on sdb for ubuntu 8.04 takes over and loads. i want to boot sdc and have the option to boot 9.04 or xp

---

### Post by oldfred on 2009-09-14
If sdc boots first then the windows entry should be this?

title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
chainloader +1

Only if it does not boot first do you need the map commands.

Unless you want windows only do not run the fixboot command as that reload the window boot that will not see ubuntu at all.

I think I have also seen similiar issues resolved by this command - backup your current menu.lst as this will overwrite it and it should see all you bootable partitions.

sudo update-grub

---

### Post by jdstunner on 2009-09-14
but xp is installed on hd(2,1)

wouldn't this be the correct mapping for rootnoverify?

which I have tried, with no success.

i could try hd(0,1) but that it doesn't make sense to me as to why this would work.

---

### Post by oldfred on 2009-09-14
Did you try the command to get grub to rewrite the menu.lst?

sudo update-grub

---

### Post by jdstunner on 2009-09-14
I have not... but I will now! Please revel in the contents of my results.txt while I load up my ubuntu cd

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010b2c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   234,436,544   234,436,482   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000523f8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,070,079    39,070,017  83 Linux
/dev/sdb2          39,070,080    46,877,669     7,807,590  82 Linux swap / Solaris
/dev/sdb3          46,877,670 1,953,520,064 1,906,642,395  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ea02e9f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,280,319   156,280,257   7 HPFS/NTFS
/dev/sdc2         156,280,320   312,576,704   156,296,385  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="53E3-EBFA" TYPE="vfat" 
/dev/sdb1: UUID="65d4b91f-fea1-43b8-aaf0-d891300444c9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="d9503515-5f4f-41d7-815e-98e323971399" TYPE="swap" 
/dev/sdb3: LABEL="mediadrive" UUID="5c1925bf-71f5-4218-a99b-41d72ae0440d" TYPE="ext3" 
/dev/sdc1: UUID="E4D47786D4775A2E" TYPE="ntfs" 
/dev/sdc2: UUID="40f69a3e-9ce9-4e11-a2e4-4121cd845973" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /data type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb3 on /mediadrive type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jim)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jim)


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
# kopt=root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=5c1925bf-71f5-4218-a99b-41d72ae0440d /mediadrive     ext3    relatime        0       2
# /dev/sda2
UUID=d9503515-5f4f-41d7-815e-98e323971399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.0GB: boot/grub/menu.lst
   4.1GB: boot/grub/stage2
   4.0GB: boot/initrd.img-2.6.24-23-generic
   4.0GB: boot/initrd.img-2.6.24-23-generic.bak
   4.1GB: boot/initrd.img-2.6.24-24-generic
   4.0GB: boot/initrd.img-2.6.24-24-generic.bak
   4.1GB: boot/vmlinuz-2.6.24-23-generic
   4.1GB: boot/vmlinuz-2.6.24-24-generic
   4.1GB: initrd.img
   4.0GB: initrd.img.old
   4.1GB: vmlinuz
   4.1GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=40f69a3e-9ce9-4e11-a2e4-4121cd845973

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
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc2 during installation
UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda1 during installation
UUID=53E3-EBFA  /data           vfat    utf8,umask=007,gid=46 0       1
# /mediadrive was on /dev/sdb3 during installation
UUID=5c1925bf-71f5-4218-a99b-41d72ae0440d /mediadrive     ext3    relatime        0       2
# swap was on /dev/sdb2 during installation
UUID=d9503515-5f4f-41d7-815e-98e323971399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc2: Location of files loaded by Grub: ===================


 149.1GB: boot/grub/menu.lst
 149.1GB: boot/grub/stage2
 149.2GB: boot/initrd.img-2.6.28-11-generic
 149.2GB: boot/vmlinuz-2.6.28-11-generic
 149.2GB: initrd.img
 149.2GB: vmlinuz
```

---

### Post by oldfred on 2009-09-14
I thinke I gave you the wrong partition. After looking again at your result.txt in the other post (one more reason for one post so all info is handy). 

title Microsoft Win XP Black
rootnoverify (hd0,[COLOR=Red]0[/COLOR])
savedefault
chainloader +1

The only other choice is similar to your original post:
title Microsoft Win XP Black
 rootnoverify (hd2,0[COLOR=Red][/COLOR])
 savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
 chainloader +1

If you use the root command you also need the makeactive line. with rootnoverify you do not need the makeactive if the partition is flagged as active which yours is.

---

### Post by jdstunner on 2009-09-14
why would i use hd(0,0)?

---

### Post by jdstunner on 2009-09-14
Ok... here we go...

I got to thinking... both Grub and WinXP want to selfishly hold onto the MBR. If I install grub to sdc, it overwrites xp and then we cant boot windows. fixmbr only makes so we cant boot ubuntu.

So I have 3 drives... why not install grub to another MBR?

I booted to my backup OS, Ubuntu 8.04. Grub is installed on sdb here.

I added the following lines to the menu.lst

```
title Microsoft Win XP Black
 rootnoverify (hd2,0)
 savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
 chainloader +1

```
Awesome... I can now boot ubuntu 8.04 and XP.

Now I have to map an entry to the 9.04 installation.

```
title        Ubuntu 9.04 - MAIN OS
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

Hopefully this works... I'll reboot before i hit submit on this post! ;)

Nope... error 15: File not found

So now I have...

Grub on sdb
booting to:
xp - sdc1 (works)
9.04 - sdc2 (doesn't work)
8.04 - sdb1 (works)

---

### Post by oldfred on 2009-09-14
I have never understood the difference between BIOS and Grub on drive order. That is why some of the other more experience members here have better answers. Mine is more trial & error, often it works but sometimes not.

Your windows is on the first partition and in grub that is zero. The question I have does grub see the drive as zero or 2? If it is first I would expect it to be sda and (hd0,0) and you would not need the map commands. If it is the third drive  sdc (hd2,0) you need the map commands to convert windows to drive 0. But if sdc is first I am not sure and that is why I suggested two choices, with and without the map commands.

I still think update-grub may automatically write the correct entries as seen from your boot order.

---

### Post by jdstunner on 2009-09-14
presence1960 posted a reply to [http://ubuntuforums.org/showthread.php?t=1265928](http://ubuntuforums.org/showthread.php?t=1265928)

He explains the BIOS/grub difference:
> 
When using (hdx,y) it is the disk boot order in BIOS that determines the x(device) setting because that is the actual order of how the disks load. Since sdc is set to boot first it is actually (hd0). You only need map commands when windows is not on the first disk which boots. So you don't need them here.

Now hopefully both of us understand! With hd(x,y), the x is the BIOS boot order number counting from 0. The y is the partition number from fdisk -l. 

So I think I may heed his instruction here.

---

### Post by jdstunner on 2009-09-14
Post solved at [http://ubuntuforums.org/showthread.php?p=7948625#post7948625](http://ubuntuforums.org/showthread.php?p=7948625#post7948625)

Thank you to all who helped!

---

