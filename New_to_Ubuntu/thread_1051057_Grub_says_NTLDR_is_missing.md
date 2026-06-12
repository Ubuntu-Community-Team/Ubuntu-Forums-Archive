---
title: "Grub says NTLDR is missing"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by LarZman on 2009-01-26
Mythbuntu noob here, had 8.1 briefly installed for testing & learning, then cleared due to adding hard drives/changing config. Reinstalled Mythbuntu 8.10, now Grub says NTLDR is missing when I choose to boot into WinXP. Mythbuntu boots fine from Grub menu. If I boot from CD with Supergrub on it, it will load WinXP without a problem. Any solutions in mind?  Mythbuntu will not boot from Super Grub menu.

Also, I want to change the default Grub boot menu, to have XP be first. This is due to the fact that Mythbuntu (or Grub) does not see my wireless kb/mouse so I cannot select any O/S except default w/timer. Right now, I'm trying to sort the first problem, the menu issue is secondary, but will be required when I move this pc back to connection with plasma tv & stereo. I'll be using this multi-boot pc as an htpc. Having XP allows me to use it immediately while I iron out issues with Mythbuntu, which is what I eventually want to use as the only O/S for the htpc.


Hardware setup (direct copy from my personal log, sorry if too much info). No drives are partitioned (unless Mythbuntu did it by default on installation)

Drive 1		Western Digital
01TB SATAII
usage 2009-01: Archive 02 - Movies in High Def., Custom DVD, or ISO


Drive 2 	Western Digital
01TB SATAII
usage 2009-01: Archive 01 - Movies in Standard Def.

Drive 3		Western Digital
500GB SATA
usage 2009-01: Video Recordings (from PVR)


Drive 4		Western Digital
320GB IDE 5400RPM
usage 2009-01: Mythbuntu 8.1 O/S drive

Drive 5		IBM 
60GB IDE 7200RPM
usage 2009-01: WinXP Pro O/S drive

---

### Post by Sjeti on 2009-01-26
It sounds like you have a mapping problem in your grub menu.

Do a 'sudo fdisk -l' and find out where your linux and windows partitions are at.

When you have figured out where it is at, '/dev/sdb1' etc, and see if you have a device map.

```
sudo gedit /boot/grub/device.map 
```

Then check your menu.lst (keep both open.

```
sudo gedit /boot/grub/menu.lst 
```

Go in and make sure your OS's are trying to boot from the proper partitions.  You might also want 'rootnoverify' in your windows menu.lst entry.

Hope this helps.

---

### Post by LarZman on 2009-01-26
device.map
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc
(hd3) /dev/sdd
(hd4) /dev/sde

menu.1st
nothing (blank)

---

### Post by caljohnsmith on 2009-01-26
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by LarZman on 2009-01-26
errrrrr, damn thing won't let me enter a password for me, green square cursor

[sudo] password for larry:


and I can't enter anything in the Terminal window. Elsewhere, the keyboard responds normally


people wonder why there is alot of apprehension about switching to Linux, this is another reason. I'm very fluent in XP, but Mythbuntu is driving me crazy. about to say f*** it, clean my Linux drive and stay with XP.

---

### Post by xc1024 on 2009-01-26
it seems to be issue with your windows install. google for "ntdlr restore xp".

---

### Post by dragos_iliescu_2005 on 2009-01-26
There must to be a file named NTLDR on your root partition (c:/ ussualy). It seems that this file is missing. Look on the Windows install CD for this file or (better) run a repair.

With repair option, the boot option in Grub will be lost. SO you have to back-up and restore. See partimage program for details.

---

### Post by LarZman on 2009-01-26
I don't want to run a "Restore" or "Repair" from Windows, as Windows works flawlessly the way it is now. Only problem is that the boot loader, Grub 1.5 is not finding the NTLDR file. I know it's present, as when booting from the SuperGrub Disc (CD), windows loads without a problem. Unfortunately, I don't know how to permanently install SuperGrub Disc, where it provides the pre-boot menu, where it offers to select an O/S to boot into. Also, Mythbuntu does not like SuperGrub, as it fails to load when booting from SuperGrub.

---

### Post by meierfra. on 2009-01-26
> 
[sudo] password for larry:

and I can't enter anything in the Terminal window. 


It only seems  that way.  For security reason the terminal shows no reaction while you type your password.  So  just type your password and press "enter".

---

### Post by LarZman on 2009-01-26
thanks meierfra. damn, somehow knew it would be something simple for experienced Linux users. I'll try it in a few. Hope I can then proceed with caljohn's earlier suggestion.

---

### Post by Sjeti on 2009-01-26
You typed in menu.1st instead of menu.lst

You have to have a menu.lst to boot.


I'm guessing your device map might be a little messed up, I had a similar problem.  It more than likely is not a problem with windows, but with grub trying to boot the wrong partition.  The first thing it looks for is ntldr and if it isn't there you get that error.

---

### Post by Vantrax on 2009-01-26
Windows can also say NTLDR is missing if you have a floppy disk (or USB key if your systems boots of USB) inserted. Windows XP for some reason will default to trying to boot off that and not get past it.

Other than that, follow the advice given. You seem to be in good hands.

As people have already said, your bug is a windows bug, not a Linux bug, Grub doesn't touch windows any more than to identify that its there and set up an option to boot to it. If you are getting to the NTLDR is missing bit it likely means that Grub has done its job and passed you off to Windows, and Windows has a problem.

---

### Post by LarZman on 2009-01-26
Thanks for the opinions all.

Ok, I'm feeling put in my place, although a bit biased by the company on this forum.

I'm surprised by those who are quick to say it's another Windows problem, of which there are many. BUT, it seems to be more of a bootloader problem, as evidenced by the fact that I can boot cleanly/completely into either O/S, depending on which bootloader I'm using. Me experience with bootloaders is on par with Linux experience, next to none!

This is the reason I'm asking questions in a pro-Linux forum, as y'all have much more experience with bootloaders and command lines. I would appreciate any constructive assistance that can be performed with relative ease. Yes, I'm certainly learning alot as I go, but some things that experienced people take for granted are not that simple to a noob.

---

### Post by LarZman on 2009-01-26
Ok, finally got things back going a little. As requested earllieer, my results.txt file shows the following

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520002 sectors.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520002 sectors.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

How do I change bootloader to point correctly to XP?

---

### Post by LarZman on 2009-01-26
Menu.lst looks like this:
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by meierfra. on 2009-01-26
Since you have so many hard drives it will be easiest to just try out the various possibilities:

Add this to the end of your menu.lst (Just use copy and paste)


title Microsoft Windows XP Professional (hd0)
rootnoverify (hd0,0)
chainloader +1 


title Microsoft Windows XP Professional (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

title Microsoft Windows XP Professional (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 

title Microsoft Windows XP Professional (hd3)
rootnoverify (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1 

title Microsoft Windows XP Professional (hd4)
rootnoverify (hd4,0)
map (hd0) (hd4)
map (hd4) (hd0)
chainloader +1 


Reboot and  try all the entries. Hopefully one of them will work.

If not, could you post the whole content of "RESULTS.txt"?  In particular the very beginning of the file would be helpful.

---

### Post by LarZman on 2009-01-26
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520002 sectors.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1953519615 sectors, but according to the info from 
                       fdisk, it has 1953520002 sectors.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e6f21a2

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            631,953,520,0641,953,520,002  42 SFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x379a122e

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 631,953,520,0641,953,520,002  42 SFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd26f9f45

Partition  Boot        Start          End         Size  Id System

/dev/sdc1    *            63  120,085,874  120,085,812   7 HPFS/NTFS


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b28d99b

Partition  Boot        Start          End         Size  Id System

/dev/sdd1                 63   23,438,834   23,438,772  83 Linux
/dev/sdd2         23,438,835  625,137,344  601,698,510   5 Extended
/dev/sdd5         23,438,898   25,430,894    1,991,997  82 Linux swap / Solaris
/dev/sdd6         25,430,958  625,137,344  599,706,387  83 Linux


Drive sde: _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc63acd12

Partition  Boot        Start          End         Size  Id System

/dev/sde1    *            63  976,768,064  976,768,002  42 SFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="303804243803E7A4" LABEL="SATA2-1TBb" TYPE="ntfs" 
/dev/sdb1: UUID="98D42F74D42F53B2" LABEL="SATA-1TB" TYPE="ntfs" 
/dev/sdc1: UUID="B298F4F498F4B845" LABEL="SATA-60GB" TYPE="ntfs" 
/dev/sdd1: UUID="d7ce7503-f921-48cc-b25b-70715beff09e" TYPE="ext3" 
/dev/sdd5: UUID="847ea431-efa8-4b14-8daf-9b8f8c7df593" TYPE="swap" 
/dev/sdd6: UUID="e27e9256-c5ca-4dfb-8a94-813fe5048b6e" TYPE="xfs" 
/dev/sde1: UUID="2890156190153732" LABEL="SATA500" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdd6 on /var/lib type xfs (rw)
/dev/sde1 on /media/SATA500 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/SATA-1TB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/SATA2-1TBb type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7ce7503-f921-48cc-b25b-70715beff09e

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7ce7503-f921-48cc-b25b-70715beff09e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d7ce7503-f921-48cc-b25b-70715beff09e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdd1 :
UUID=d7ce7503-f921-48cc-b25b-70715beff09e / ext3 errors=remount-ro 0 1
# Entry for /dev/sdd6 :
UUID=e27e9256-c5ca-4dfb-8a94-813fe5048b6e /var/lib xfs defaults 0 2
# Entry for /dev/sdd5 :
UUID=847ea431-efa8-4b14-8daf-9b8f8c7df593 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sde1 /media/SATA500 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/SATA-1TB ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/SATA2-1TBb ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdd1: Location  of files loaded by Grub: ===================


   1.4GB: boot/grub/menu.lst
   1.4GB: boot/grub/stage2
   1.4GB: boot/initrd.img-2.6.27-7-generic
   1.4GB: boot/initrd.img-2.6.27-9-generic
   1.4GB: boot/vmlinuz-2.6.27-7-generic
   1.4GB: boot/vmlinuz-2.6.27-9-generic
   1.4GB: initrd.img
   1.4GB: initrd.img.old
   1.4GB: vmlinuz
   1.4GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by meierfra. on 2009-01-27
RESULTS.txt looks fine, so one of the five entries I suggested in my last post should work. Did you try them all? If none of them works, please  report  the error messages you got for each of the tries.

---

### Post by LarZman on 2009-01-27
didn't try 'em all yet. ran outta time, wife was calling :-). I'll try 'em when I get home tonight. Thanks

---

### Post by dragos_iliescu_2005 on 2009-01-27
If NTLDR is missing just copy and past onto your hdd. Look for this particular file on the i386 folder from your Win install CD.

---

### Post by LarZman on 2009-01-27
title Microsoft Windows XP Professional (hd0)
rootnoverify (hd0,0)
chainloader +1 

Works like a champ. Thanks so much meierfra :-)

Now can I just relocate it up to the top of the menu so Windows will ve the default O/S? My problem with it being last is that I have to use a wired (USB or nromal KBD cable) rather than my DiNovo wireless keyboard/mouse, because Mythbuntu does not load the drivers (?) before the boot menu screen, so I have no way of scrolling down and selecting Windows unless I have a wired keyvoard plugged in. 

Granted, I will start using Mythbuntu as the primary O/S when I have everything set up properly to record TV, watch movies, etc. I'm getting very close on that regard, but wife is getting impatient. Until then (hope it's not long), I neeed to get the htpc installed and running well enough to do movies, which XP does very well. This little(!) htpc project started when she wanted a DVR, but I told her it would be better to build one and not pay DirectTV or Comcast a monthly fee for their DVR box.

---

### Post by Vantrax on 2009-01-27
> **LarZman said:**
> 
Now can I just relocate it up to the top of the menu so Windows will ve the default O/S?

You can, but if its inside the auto generated list it will be automatically removed (this is bad). Either set it above the auto generated list, or change the 'default' entry from 0 (the first option in the list) to which ever number entry is your windows one (just count em up and subtract 1 as the first entry is 0 not 1).

---

### Post by meierfra. on 2009-01-27
> Now can I just relocate it up to the top of the menu so Windows will ve the default O/S? 

Yes, but make sure you put it  before the line

### BEGIN AUTOMAGIC KERNELS LIST

Otherwise your Windows item will be deleted during the next kernel upgrade.

Have fun with Ubuntu and XP.

---

### Post by LarZman on 2009-01-27
thanks Vantrax & Meierfra for the help. 

Maybe I'll be a Linux guru someday so I can help others break from the Windows chain :-) I already do encourage people to explore Linux, but without the skills to assist, it's hard to support them when problems inevitably arise.

---

