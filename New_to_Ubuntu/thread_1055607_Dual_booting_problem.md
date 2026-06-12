---
title: "Dual booting problem"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Vittra on 2009-01-30
I just installed linux for the first time so bear with me..

I've got 3 SATA hard drives, XP is on one, Linux and the other is just data.

Computer boots fine and just loads into XP so it doesn't look like Grub even gets noticed.  Doesn't prompt me for an OS to boot into

Here's what menu.lst says:

```

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3507dc38-efaf-4268-8364-4db130c16ee9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3507dc38-efaf-4268-8364-4db130c16ee9 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

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
# on /dev/sdc1
title		Windows XP Media Center Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

I think when I installed Ubuntu, it select (hd0,0) as the boot loader device but I'm not sure of that...  Any ideas?

Thank you

---

### Post by Synt4xError on 2009-01-30
Hey where is the menu.lst located? I forgot :(

---

### Post by caljohnsmith on 2009-01-30
How about going into your BIOS and change the boot order; whichever of your two other drives are not being booted first on start up, how about booting them first and see what happens. If you still have problems, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Vittra on 2009-01-30
Thanks for the response!

I changed the boot order of the drives and I got a Grub error 17.



Here are the results from the script file:


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
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 164.6 GB, 164696555520 bytes
16 heads, 63 sectors/track, 319120 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a052a05

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   321,670,943   321,670,881   7 HPFS/NTFS
/dev/sda2         321,670,944   321,672,959         2,016   f W95 Ext'd (LBA)
Empty Partition

/dev/sda1 ends after the last cylinder of /dev/sda
/dev/sda2 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83d4e691

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    19,535,039    19,534,977  83 Linux
/dev/sdb2         102,398,310   156,296,384    53,898,075   7 HPFS/NTFS
/dev/sdb3          19,535,040   102,398,309    82,863,270   5 Extended
/dev/sdb5          19,535,103    29,302,559     9,767,457  82 Linux swap / Solaris
/dev/sdb6          29,302,623   102,398,309    73,095,687  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc5988a95

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   321,653,429   321,653,367   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D8184C6D184C4CA6" TYPE="ntfs" 
/dev/sdb1: UUID="3507dc38-efaf-4268-8364-4db130c16ee9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="F696E07096E03333" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="873fd1d4-7d1a-4b1f-8db3-480bd401db51" 
/dev/sdb6: UUID="595f2130-d30c-4921-835b-06639344525f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="A8E03B2FE03B035C" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

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
# kopt=root=UUID=3507dc38-efaf-4268-8364-4db130c16ee9 ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3507dc38-efaf-4268-8364-4db130c16ee9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3507dc38-efaf-4268-8364-4db130c16ee9 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

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
# on /dev/sdc1
title		Windows XP Media Center Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3507dc38-efaf-4268-8364-4db130c16ee9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=595f2130-d30c-4921-835b-06639344525f /home           ext3    relatime        0       2
# /dev/sdb5
UUID=873fd1d4-7d1a-4b1f-8db3-480bd401db51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location  of files loaded by Grub: ===================


   6.1GB: boot/grub/menu.lst
   6.1GB: boot/grub/stage2
   6.2GB: boot/initrd.img-2.6.24-23-generic
   6.1GB: boot/vmlinuz-2.6.24-23-generic
   6.2GB: initrd.img
   6.1GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer


```

Thank you!

---

### Post by Vittra on 2009-01-31
So I did some looking around and made a Super grub disk.  First I tried to boot MBR from the drive with Grub on it and it just spammed the word grub repeatedly forever.  

Then I tried the restore MBR with gnu/linux option, and it loaded up Grub and gave me options to boot into XP now.  I choose XP and it gives me Error 13, something about invalid boot or whatever.

I'm pretty sure the problem is with grub being loaded on another hard drive that's not the #1 main windows one, I dont really know what to do about that except try and change the MBR of the first drive?  or see if I can use windows boot loader instead

---

### Post by spd214 on 2009-01-31
Since you are running on seperate drives, have you checked the jumper settings on both drives to insure they are set to cable select.  Assuming they are IED drives, that is.  Hope this helps.

---

### Post by caljohnsmith on 2009-01-31
Unfortunately the issue is that you have Ubuntu installed to your sdb drive, yet Grub is installed to the MBR (Master Boot Record) of your sda Windows drive. For your setup to work the way it is right now, your sda drive would need to be first in the BIOS boot order, and the sdb drive would need to be 2nd. But even if you were to do that, the problem with that is your sda and sdb drives would be dependent on each other for booting. Since you can change the BIOS boot order, it is much more ideal if you can just install Grub to the sdb drive, or the drive that Ubuntu is on, so then your drives will be completely independent of each other when it comes to booting. That means if anything happens to either the Windows or Ubuntu drive, you should be able to boot the other drive OK. If that sounds good, how about from your Live CD doing:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
sudo mount /dev/sdb1 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all your Ubuntu entries to use (hd0,0) instead of (hd1,0) similar to:
```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3507dc38-efaf-4268-8364-4db130c16ee9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet
```
Also change the "# groot=(hd1,0)" line to:
```
# groot=[COLOR="Blue"](hd0,0)
[/COLOR]
```
Also, in addition to the Windows entry you all ready have in the menu.lst, add this one as well:
```
title		Windows XP (hd1)
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
And lastly, to restore a Windows MBR to your Windows drive, how about doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then reboot, set your sdb Ubuntu drive to boot first, and let me know how far you get about booting Ubuntu and Windows from your Grub menu. We can work from there if necessary.

---

### Post by Vittra on 2009-01-31
Thanks again for helping, I'll try those things and let you know how it goes.

I've got one question which hopefully should be an easy answer,

Could I theoretically just reformat my linux drive and do a wubi installation if this fails?  That should still give me dual booting options if I read correctly

---

### Post by ChristopherDante on 2009-01-31
From what I read in the first post, grub is installed in the /boot sector of your linux distro, not in the MBR - why would Windows start up otherwise?

If I am correct, then you have to let Win bootloader know that there is another OS.

Open a terminal and go to /boot/grub (this is also where menu.lst is located) and type ```
"dd if=/dev/sdb* of=bootgrub.bin bs=512 count=1"
``` to create a bootgrub.bin file. Replace * with the correct location of your /boot location. (I'm not sure if it is on 1 or 6)

Now copy bootgrub.bin to a USB stick or shared drive that Win can read.
Boot into Windows, make a backup of your boot.ini file (in case something goes wrong), copy the bootgrub.bin file into C:\ and add the following line to C:\boot.ini:
```
"C:\bootgrub.bin="Ubuntu"
```
You can change the default timeout of 30 sec. to something that suits you better.
Also change the default OS to your liking.

---

### Post by Rhyader on 2009-01-31
If windows is starting and GRUB gets ignored when you boot, then GRUB was not installed to your master boot record (MBR) of the boot drive. In that  case it's rather irrelevant what menu.lst says. If you switched the boot order of the drives betwixt installing things, then your Ubuntu and GRUB  may be confuddled with the wrong settings. 

It's hard to tell what's going on here.  Please forgive me if I just preach at you from my experience, since this is what I have been working on the past week. First, if you install linux with the boot order one way, and then change it, linux and grub will be confused and probably not work. The  first thing is to decide how you WANT to boot your computer. How do you WANT to boot your computer? Do you want to use the BIOS for "firmware  control", and change the drive boot order to select which drive you want to boot? Or do you want to NOT do this, and install a boot manager into  your MBR of the first drive and use that to control booting? If so, WHAT boot manager? Grub? Windows boot manager? 

If you are new to linux I'd recommend giving windows first priority. This means keep your bios settings to boot the first windows drive first. With  it set like that, boot from the ubuntu CD and install Ubuntu on the second hard drive. That way Ubuntu will expect to be on the "second" hard drive. Let it format the partition it will use. Since you say you just installed it, you should have nothing to lose from wiping out your Ubuntu and  installing it all over again. When it gets to the install GRUB part, select the advanced options. If you want to use GRUB to control booting,  install GRUB to the default location which should be the MBR of the first drive. If you would rather have windows handle it (which I HIGHLY  RECOMMEND) then tell ubuntu to install GRUB to the drive it is booting from, NOT the MBR of drive one. This will be some weird hd 1,0, /dev/sdb1, or something like that. As long as the the cryptic codes mean "*the partition of the drive where Ubuntu is, and not the MBR of the boot drive*".

Once it is all done, your Ubuntu is installed, and you can NOT boot it. Your computer will ignore GRUB and boot into windows. This is highly  desirable, in my opinion. Boot Windows. Download and install "EasyBCD", which is recommended by Microsoft for this. EasyBCD is a front end program  that will configure the Microsoft Windows bootloader for you. Configure it. Now reboot. When your computer reboots you should get the windows boot  selector, with entries for Microsoft Windows and whatever entry you made for linux, which must point to the place where Ubuntu lives (like /dev/sdb1  or /dev/sdc5 or wherever). The default will be Windows. If it worked, selecting the linux entry with the arrow key and enter will get you the  GRUB menu, which will then let you boot Ubuntu.

If you want GRUB in your MBR instead, then don't select the "advanced" option for installing GRUB and just let Ubuntu put GRUB where it wants to.  Then your computer should boot up into GRUB and let you load windows or linux. But I like it better my way.

This sounds like a round-about way to do things. But if you scan these forums, you will see many posts from people upset because they have updated 
Ubuntu and their GRUB is now screwed up. This seems to be a common problem and can result in you not being to boot anything at all. My solution is  to let Windows bootloader have the MBR, not GRUB. Then if GRUB screws up, as it so often does, you will at least still be able to run windows and  log into these Ubuntu forums to look for a solution. 

Good luck in your endeavors.

PS: Look here:
[http://ubuntuforums.org/showthread.php?t=1037689](http://ubuntuforums.org/showthread.php?t=1037689)

---

