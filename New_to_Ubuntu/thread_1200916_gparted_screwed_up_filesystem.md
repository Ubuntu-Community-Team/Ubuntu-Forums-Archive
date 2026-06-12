---
title: "gparted screwed up filesystem"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by djbushido on 2009-06-30
I was trying to move my filesystem when my computer crashed. Now it can't recognize the partition. Is there any way to restore the partition without formatting? And if not, can I get my files off of it? Thanks for the help!

---

### Post by jimsheep on 2009-06-30
try booting to your live-cd and at least backing up the data you need.

---

### Post by djbushido on 2009-06-30
Bit late for that. Besides, didn't have the space.
What has happened is that the partition is corrupted, and I need to try and get what data off that I can.

---

### Post by drs305 on 2009-06-30
There is a pretty good chance TestDisk can sort things out. Try not to do anything that will write to the disk until you recover things. If TestDisk can't sort out the table it also includes Photorec, which helps recover files.

There have been many posts on these forums about using testdisk and any search should turn them up. One of the frequent posters, caljohnsmith, was an early proponent of testdisk and has authored some of the really good posts.

---

### Post by djbushido on 2009-06-30
Thanks. Will search. Also, fdisk recognizes the partition as ext3, just can't mount it. "dmesg | tail" outputs: VFS: Can't find ext3 filesystem on dev sdc3.

---

### Post by starcraft.man on 2009-06-30
Gparted didn't screw up your filesystem, your computer crashing messed up the file system/partition. Gparted doesn't cause crashes to my knowledge it's been very stable any time I used it. Regardless, no partitioner is perfect and it is always recommended to back up all your important data before doing any such operations.

As for trying to save the data, I assume when you've booted back into gparted it doesn't detect the partitions correctly. You can try test disk (see my post [here]("http://tiny.cc/eFHlt")) to search for partitions and recreate the table with the tool. If it can't work after that, it would be troubling. I don't know if it can be saved in that case.

---

### Post by djbushido on 2009-06-30
/*HUZZAH FOR TESTDISK!!!!!
OMG IT SAVED MY LIFE!!!
Well, not really, but the partitions are back safe and sound.
I can work from here.
Lesson learned - Don't panic.*/

Nope, partitions are still weird.
I can boot to my ubuntu machine. Which is part of the weirdness. I will try to explain the best I can, but there is some crazy stuff going down.

Fdisk and gparted recognize 4 partitions - /dev/sda1 is my Fedora machine.
- /dev/sda2 is a small partition
- /dev/sda3 is what my machine should be running off of
- /dev/sda4 is swap

Those are the partitions. Now the weird stuff.

When I log in, checking free disk space shows that I have a partition of 140 Gb. This is /dev/sda3. However, when booting, I grub says I am booting (hd0,1) which is a small partition that really shouldn't exist. Also, /dev/sda2 has the uuid of the disk, which is what ubuntu boots from.

So the final madness is that I should by all rights be booting off of /dev/sda2, but my machine somehow loads /dev/sda3. Any help? I don't want to leave my computer in this messed up state.

---

### Post by djbushido on 2009-07-03
Double post, sorry.

---

### Post by drs305 on 2009-07-03
> **djbushido said:**
> /*HUZZAH FOR TESTDISK!!!!!
OMG IT SAVED MY LIFE!!!
Well, not really, but the partitions are back safe and sound.
I can work from here.
Lesson learned - Don't panic.*/

Nope, partitions are still weird.
I can boot to my ubuntu machine. Which is part of the weirdness. I will try to explain the best I can, but there is some crazy stuff going down.

Fdisk and gparted recognize 4 partitions - /dev/sda1 is my Fedora machine.
- /dev/sda2 is a small partition
- /dev/sda3 is what my machine should be running off of
- /dev/sda4 is swap

Those are the partitions. Now the weird stuff.

When I log in, checking free disk space shows that I have a partition of 140 Gb. This is /dev/sda3. However, when booting, I grub says I am booting (hd0,1) which is a small partition that really shouldn't exist. Also, /dev/sda2 has the uuid of the disk, which is what ubuntu boots from.

So the final madness is that I should by all rights be booting off of /dev/sda2, but my machine somehow loads /dev/sda3. Any help? I don't want to leave my computer in this messed up state.

If your question is still are unanswered:

The way grub looks at things, if it says hd0,1 that is really sda2. Grub (legacy) starts counting devices and partitions at 0. So the first partition on the first device is (hd0,0).

The other part of the puzzle is that grub doesn't have to be installed on the same partition as your OS. It puts part in the mbr and the rest may have been installed on sda2, where another distro, /boot or another release may have been. 

The bottom line is that there is a good possibility that if you eliminate sda2 you will probably delete grub and not be able to get into sda3 at all. You should be able to use the "grub" or "grub-install" command to get grub on the sda3 partition instead of sda2.

---

### Post by djbushido on 2009-07-03
The problem is that my Fedora menu is linked to chainload sda3 (hd0,2). The UUID is stuck on sda2 (I can fix this later) so that it boots (hd0,1), which is /dev/sda2. Grub specifically says that it is booting (hd0,1), and gives a UUID. The UUID then checks out with "ls /dev/disk/by-uuid -lha" as /dev/sda2. Then the system actually loads /dev/sda3, given by my free space is way bigger than the sda2 partition. My question is if this table is actually correct, because grub says that I am booting /dev/sda2 (hd0,1), while ubuntu apparently is loading /dev/sda3 (hd0,2). Also, if this table is incorrect, as I suspect that it is, how would I go about fixing it? I just used testdisk to restore the table, and would prefer not to use it again unless I have to.

Also, both fdisk -l and gparted give me the same table - 3 partitions and 1 swap. If anybody needs more info in trying to figure this out, I am happy to provide it.

---

### Post by louieb on 2009-07-03
[Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  - good script - will tell you a lot about how the PC boots. Put the content in your next post. (please wrap it in CODE tags)

---

### Post by djbushido on 2009-07-04
Results of Boot info:
```
============================= Boot Info Summary: 
==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 10 (Cambridge) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 72745063 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 200076190 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/grub.conf.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d82b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    52,436,159    52,436,097  83 Linux
/dev/sda2    *    126,158,445   182,193,164    56,034,720  83 Linux
/dev/sda3         184,265,550   484,199,099   299,933,550  83 Linux
/dev/sda4         484,199,100   488,392,064     4,192,965  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="Fedora" UUID="739b010c-b317-4395-b94d-c52511417dc6" TYPE="ext3" 
/dev/sda2: UUID="7b48155a-17c4-4df0-9dcb-431fa86dfa41" TYPE="ext3" 
/dev/sda3: LABEL="Xubuntu" UUID="7b48155a-17c4-4df0-9dcb-431fa86dfa41" TYPE="ext3" 
/dev/sda4: UUID="98e1986d-f6f0-4d07-ba04-ef264ecb68a3" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw)
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
gvfs-fuse-daemon on /home/brad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brad)
/dev/sda3 on /media/Xubuntu type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


========================== sda1/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,0)
#          kernel /boot/vmlinuz-version ro root=/dev/sda1
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=3
timeout=5
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.21-170.2.56.fc10.i686)
	root=(hd0,0)
	kernel /boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686 ro root=UUID=739b010c-b317-4395-b94d-c52511417dc6 rhgb quiet
	initrd /boot/initrd-2.6.27.21-170.2.56.fc10.i686.img
title Fedora (2.6.27.19-170.2.35.fc10.i686)
	root=(hd0,0)
	kernel /boot/vmlinuz-2.6.27.19-170.2.35.fc10.i686 ro root=UUID=739b010c-b317-4395-b94d-c52511417dc6 rhgb quiet
	initrd /boot/initrd-2.6.27.19-170.2.35.fc10.i686.img
title Fedora (2.6.27.9-159.fc10.i686)
	root=(hd0,0)
	kernel /boot/vmlinuz-2.6.27.9-159.fc10.i686 ro root=UUID=739b010c-b317-4395-b94d-c52511417dc6 rhgb quiet
	initrd /boot/initrd-2.6.27.9-159.fc10.i686.img
title Ubuntu Grub Menu
	root (hd0,2)
	chainloader +1

=============================== sda1/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Tue Dec 30 19:54:19 2008
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=739b010c-b317-4395-b94d-c52511417dc6 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
UUID=98e1986d-f6f0-4d07-ba04-ef264ecb68a3 swap                    swap    
defaults        0 0

=================== sda1: Location of files loaded by Grub: ===================


  24.2GB: boot/grub/grub.conf
  24.2GB: boot/grub/menu.lst
  24.2GB: boot/grub/stage2
  24.1GB: boot/initrd-2.6.27.19-170.2.35.fc10.i686.img
  24.2GB: boot/initrd-2.6.27.21-170.2.56.fc10.i686.img
  24.2GB: boot/initrd-2.6.27.9-159.fc10.i686.img
  24.2GB: boot/vmlinuz-2.6.27.19-170.2.35.fc10.i686
  24.2GB: boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686
  24.2GB: boot/vmlinuz-2.6.27.9-159.fc10.i686

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b48155a-17c4-4df0-9dcb-431fa86dfa41

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
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7b48155a-17c4-4df0-9dcb-431fa86dfa41 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7b48155a-17c4-4df0-9dcb-431fa86dfa41
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Gentoo Base System release 1.12.11.1 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda1 
initrd		/boot/initramfs-genkernel-x86-2.6.24-gentoo-r5
savedefault
boot
##ADDED BY DJBUSHIDO:THIS IS DEPRECATED

========================== sda2/boot/grub/grub.conf: ==========================

```

EDIT: Also, when I booted up my computer, the network-manager daemon didn't run. When I tried to start the services menu, it wouldn't let me access it, even running it with sudo from terminal. Any help on this?

---

### Post by louieb on 2009-07-04
> **djbushido said:**
> Grub specifically says that it is booting (hd0,1), and gives a UUID. The UUID then checks out with "ls /dev/disk/by-uuid -lha" as /dev/sda2. Then the system actually loads /dev/sda3, given by my free space is way bigger than the sda2 partition. My question is if this table is actually correct, because grub says that I am booting /dev/sda2 (hd0,1), while ubuntu apparently is loading /dev/sda3 (hd0,2)

You have duplicate UUID's for sda2 and sda3.   GParted will do that when you copy a partition to free space. (other ways to it too). Probably causing great confusion.

```
/dev/sda2: UUID="7b48155a-17c4-4df0-9dcb-431fa86dfa41" TYPE="ext3" 
/dev/sda3: LABEL="Xubuntu" UUID="7b48155a-17c4-4df0-9dcb-431fa86dfa41" TYPE="ext3"
```TO give one of the partitions a new UUID  use tune2fs

```
sudo tune2fs -U random /dev/sda#
```Thats a capital -U - lowercase -u does something else. see **man tune2fs **

---

### Post by djbushido on 2009-07-04
Ready for madness???

Trying to unmount /dev/sda2 to reset the uuid indicates that it is mounted at /. Meaning /dev/sda2 is actually being booted. 
So why then does my system apparently think that it has 140 Gb of space? Gparted indicates that the partition is only ~25Gb in size.
Partitions screwed up?
And thanks for the tip on generating uuid's, but I'm going to hold off of doing that until the partition weirdness gets fixed. Unless you think that this is the problem. My guess is that both gparted and fdisk aren't recognizing my table correctly. Maybe another run through with testdisk?

---

### Post by djbushido on 2009-07-04
Okay, reset the uuid on /dev/sda2 with "tune2fs -U random /dev/sda2" from the alt recovery cd. Then moved the original onto /dev/sda3, again with tune2fs. As far as I can tell, I should be able to delete the partition, but I'm not so sure that I'm going to do that just yet.

---

### Post by louieb on 2009-07-04
> **djbushido said:**
> ...My guess is that both gparted and fdisk aren't recognizing my table correctly. 

fdisk -l just prints the content of the partition table - pretty straight forward - doesn't care if the entries are valid - its just printing what is there. 

With your power going off in the middle of moving a partition its really amazing that the partition is readable at all. 

BTW: from the results.txt file looks like the PC loads Fedora's grub 
and the Ubuntu entry in Fedora's grub.conf is chainloading sda3 (hd0,2)  when you select Ubuntu.

---

### Post by djbushido on 2009-07-05
The partition table wasn't readable for a while. That's where the first testdisk run came in. I know exactly what grub is doing, I set that up. Fedora chainloads to ubuntu, as the fedora bootloader has graphics. Looks nicer. Anyway, my question is if it is safe to delete the partition that gparted created to move the partition to - if gparted did a copy or cut operation - meaning did it just copy the files, or did it delete them as it went?

---

