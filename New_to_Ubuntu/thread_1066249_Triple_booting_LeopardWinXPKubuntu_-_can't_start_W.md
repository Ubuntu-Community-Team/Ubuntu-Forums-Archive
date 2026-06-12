---
title: "Triple booting Leopard/WinXP/Kubuntu - can't start Windows"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by rogueofmv on 2009-02-10
OK, so:

I just started using Linux yesterday (literally).
I had heard there were certain procedures to go through when triple-booting on a MacBook, including setting up Linux on a partition preceding that of Windows, which I did.

I'm using rEFIt to boot up. It works fine.

BUT, here's where the problem comes in: Windows is listed as an option under GRUB. And whenever I try to boot to it, it gets to the Windows splash, then flickers a BSOD for a split second and instantly reboots.

If it helps any, my HDD is split into 5 partitions:
[LIST]
[*]dev/sda1 - free space (FAT32)
[*]dev/sda2 - Mac OS X
[*]dev/sda3 - Kubuntu
[*]dev/sda4 - WinXP
[*]dev/sda5 - swap for Kubuntu
[/LIST]

I had already installed WinXP before I installed Kubuntu.
HELP! I really need to be able to use Windows again... :(

Oh, yes. I should also make it clear that I'm running Kubuntu 8.10, if that helps.

---

### Post by drumfire420 on 2009-02-10
First off, welcome to Linux, I hope you enjoy it.


Windows is really picky about how it needs to be started, I don't know about the macbook aspect, but this is what I had to do to get my desktop to boot windows.
(my entry in /boot/grub/menu.lst  for windows)  

```

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


The "make active" "map"s and "chainloader" lines are all necessary, and the grub website can explain it much better than I can.  You could probably copy the above, change the root   (hd1,0) line to match your partition scheme and be ok.

  As with everything, you can make things ALOT worse playing around with this, so read the documentation and be careful.

(and keeping a good live cd on hand can go a long way towards making it easy to get things back when you mess up)

[_Grub's documentation page on multi booting with windows_]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows")

---

### Post by rogueofmv on 2009-02-11
> **drumfire420 said:**
> First off, welcome to Linux, I hope you enjoy it.


Windows is really picky about how it needs to be started, I don't know about the macbook aspect, but this is what I had to do to get my desktop to boot windows.
(my entry in /boot/grub/menu.lst  for windows)  

```

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


The "make active" "map"s and "chainloader" lines are all necessary, and the grub website can explain it much better than I can.  You could probably copy the above, change the root   (hd1,0) line to match your partition scheme and be ok.

  As with everything, you can make things ALOT worse playing around with this, so read the documentation and be careful.

(and keeping a good live cd on hand can go a long way towards making it easy to get things back when you mess up)

[_Grub's documentation page on multi booting with windows_]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows")

After reading the documentation, it appears to me that this applies only to systems with multiple hard drives.
All my OSs are on the same HDD.

---

### Post by cjv8888 on 2009-02-11
Have you tried booting with a Windows recovery CD and do a 

```
fixmbr
```?

---

### Post by rogueofmv on 2009-02-11
> **cjv8888 said:**
> Have you tried booting with a Windows recovery CD and do a 

```
fixmbr
```?

Sadly, I've lost my Windows CD since I installed it. :(

---

### Post by KuroYoma on 2009-02-11
Did you move the windows partition with Gparted then install or did you shrink MacOS X to install kubuntu?

---

### Post by rogueofmv on 2009-02-11
> **KuroYoma said:**
> Did you move the windows partition with Gparted then install or did you shrink MacOS X to install kubuntu?

I shrank Mac OS.

---

### Post by KuroYoma on 2009-02-11
The thing I am wondering then is if when you select windoze if windoze is still looking at the partition right after osX.  If so then it would explain the quick crashing.  If you could I would boot into a linux live distro and go to your windows boot.ini and make sure it is pointing to the proper partition.  beyond that you may want to try Grub but I am not sure how well it works with Mac, never used Mac before.  Beyond that I would suggest download and iso file of your version of windoze and burn it to a disk so you can try the fixmbr command thing.

hope this helps

if you do decide to try grub I would suggest downloading the Super Grub CD before you do so that you have the tool you need to fix grub.

---

### Post by rogueofmv on 2009-02-11
> **KuroYoma said:**
> The thing I am wondering then is if when you select windoze if windoze is still looking at the partition right after osX.  If so then it would explain the quick crashing.  If you could I would boot into a linux live distro and go to your windows boot.ini and make sure it is pointing to the proper partition.  beyond that you may want to try Grub but I am not sure how well it works with Mac, never used Mac before.  Beyond that I would suggest download and iso file of your version of windoze and burn it to a disk so you can try the fixmbr command thing.

hope this helps

if you do decide to try grub I would suggest downloading the Super Grub CD before you do so that you have the tool you need to fix grub.

Funny you should mention fiddling with the boot.ini.

I actually already tried that; at first, I was getting a "corrupt hal.dll" error upon booting, and when I opened the boot.ini in Linux, I noticed that it WAS, in fact, pointing to the wrong partition (partition 3).

So I changed it to the correct one (partition 4), and that's how I ended up in this boat. Windows is completely there, but it's bluescreening now.

---

### Post by lynnevan on 2009-02-11
Like others before me, I don't know anything about Mac, but I understand Mac OS X is based on Unix and Unix partitioning can get pretting strange in it's nomenclature.  Maybe what you have partitioned is fine, but in windoz & linux, no way could you have a primary partition on sda4 and still have a sda5 partition.  For example, here is a copy of the partitioning of my second hard drive.  Make believe it is the first hard drive.  Look at sdb4.
Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+   2676    2677-  21502971   83  Linux
/dev/sdb2       2677    5353    2677   21503002+  83  Linux
/dev/sdb3       5354    8030    2677   21503002+  83  Linux
/dev/sdb4       8031   19456   11426   91779345    5  Extended
/dev/sdb5       8031+   8161     131-   1052226   82  Linux swap / Solaris
/dev/sdb6       8162+  19456   11295-  90727056    7  HPFS/NTFS

If that was my 1st hard drive, I'd put windoz first and the rest would just fall in naturally.  An operating system on an extended partition is impossible.  If sdb4 (or sda4) is a primary partition, you can't have any sdb5 (sda5).

What's the output of sfdisk -l or fdisk -l ??  Also, give us the output of df -h .

You might try running gparted (just to look) and see what you get.  Download the CD if you have to.

luck,

lynn

---

### Post by cjv8888 on 2009-02-11
> **rogueofmv said:**
> Sadly, I've lost my Windows CD since I installed it. :(

you can download a boot CD to repair the MBR from [here]("http://www.ultimatebootcd.com/").

---

### Post by louieb on 2009-02-11
[LEFT]As lynnevan points out the partition layout in post #1 does not look right. If windows is in a **logical partition** - it won't boot unless there is another install of windows in a primary partition. - Windows is strange that way. 
Did you have another windows install that got replaced by Kubuntu?

Need more info. Look at this post [http://ubuntuforums.org/showpost.php?p=6606431&postcount=6](http://ubuntuforums.org/showpost.php?p=6606431&postcount=6)  Follow the instructions and post the results.txt file back here. 
 [/LEFT]

---

### Post by rogueofmv on 2009-02-14
> **louieb said:**
> [LEFT]As lynnevan points out the partition layout in post #1 does not look right. If windows is in a **logical partition** - it won't boot unless there is another install of windows in a primary partition. - Windows is strange that way. 
Did you have another windows install that got replaced by Kubuntu?

Need more info. Look at this post [http://ubuntuforums.org/showpost.php?p=6606431&postcount=6](http://ubuntuforums.org/showpost.php?p=6606431&postcount=6)  Follow the instructions and post the results.txt file back here. 
 [/LEFT]

Got it. Here's my results.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 350526712 
    of the same hard drive for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #3 for /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcba4cba4

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   348,560,631   348,150,992 HFS+
/dev/sda3     348,822,776   397,418,479    48,595,704 Linux (usually)
/dev/sda4     403,062,824   488,397,127    85,334,304 Linux (usually)
/dev/sda5     397,418,480   401,418,480     4,000,001 Linux Swap

/dev/sda4 ends after the last cylinder of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="EFI" UUID="2860-11F4" TYPE="vfat" 
/dev/sda2: UUID="A2A57C84364FC0ED" LABEL="Macintosh HD" TYPE="hfsplus" 
/dev/sda3: UUID="b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d" TYPE="ext3" 
/dev/sda4: UUID="723C5AA03C5A5F63" TYPE="ntfs" 
/dev/sda5: UUID="60834ca2-610f-49e7-9a77-104793715116" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d

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
uuid		b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Professional
root		(hd0,3)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b1734bb9-c242-4ee4-aebe-a2dfcb9fe77d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=60834ca2-610f-49e7-9a77-104793715116 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 179.4GB: boot/grub/menu.lst
 179.4GB: boot/grub/stage2
 179.4GB: boot/initrd.img-2.6.27-11-generic
 179.4GB: boot/initrd.img-2.6.27-7-generic
 179.5GB: boot/vmlinuz-2.6.27-11-generic
 179.5GB: boot/vmlinuz-2.6.27-7-generic
 179.4GB: initrd.img
 179.4GB: initrd.img.old
 179.5GB: vmlinuz
 179.5GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=============================== StdErr Messages: ===============================

sed: can't read sda2/etc/issue: No such file or directory
```

And no Windows install was overwritten by Kubuntu; I created a new partition for that.

Windows was always able to boot just fine before I installed Kubuntu.

Also, here's the sfdisk -l output:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  30401-  30402- 244198583+  ee  GPT
                start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4   *      0       -       0          0    0  Empty

```

And the df -h output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              23G  2.9G   19G  13% /
tmpfs                 995M     0  995M   0% /lib/init/rw
varrun                995M  108K  995M   1% /var/run
varlock               995M     0  995M   0% /var/lock
udev                  995M  2.9M  993M   1% /dev
tmpfs                 995M     0  995M   0% /dev/shm
lrm                   995M  2.0M  993M   1% /lib/modules/2.6.27-11-generic/volatile

```

---

### Post by louieb on 2009-02-14
Most PCs use the MBR partition structure. Yours uses a **GPT (GUID Partition Table) **thats why the partitioning looked strange to me. Other that boundary warning   for sda4 I guess the table looks fine.

May want to report this thread and get it moved to the Apple section of the forum. 
I guess you could reinstall / use** rEFIt  **as your boot loader / manager.

Another thing you might try is to comment out the makactive statement in the windows entry in /boot/grub/menu.lst. Can't hurt and in some cases its a fix that works.

```
title        Microsoft Windows XP Professional
root        (hd0,3)
savedefault
[COLOR=Sienna]#makeactive[/COLOR]
chainloader    +1
```

---

### Post by Mahogan on 2009-02-16
I have a very similar problem.  I also have OSX, XP and Kubuntu.  But cannot boot OSX.  I first made 3 partitions loaded OSX on the first (it works), then XP on the second (it works) and Kubuntu with an extended swap on the third (it works).  I expected after loading Kubuntu that OSX would show up on the grub menu, but just Kubuntu and XP.  Any advice how to get OSX to be in the menu?

Well, I guess I answered my own question by altering the code that louieb posted above to my menu.lst:  

title        Mac OSX
root        (hd0,0)
savedefault
#makeactive
chainloader    +1

It works perfect for my setup!  Now I can triple boot OSX, XP and Kubuntu with no problems!

---

### Post by rogueofmv on 2009-02-17
> **louieb said:**
> Most PCs use the MBR partition structure. Yours uses a **GPT (GUID Partition Table) **thats why the partitioning looked strange to me. Other that boundary warning   for sda4 I guess the table looks fine.

May want to report this thread and get it moved to the Apple section of the forum. 
I guess you could reinstall / use** rEFIt  **as your boot loader / manager.

Another thing you might try is to comment out the makactive statement in the windows entry in /boot/grub/menu.lst. Can't hurt and in some cases its a fix that works.

```
title        Microsoft Windows XP Professional
root        (hd0,3)
savedefault
[COLOR=Sienna]#makeactive[/COLOR]
chainloader    +1
```

Gave that a try; didn't work. So I examined a bit further. It turned out my BOOT.INI was directing to the wrong partition. So I changed it to the correct one. Then I got a missing HAL.DLL error. So I ran the rEFIt partitioning tool to get the Linux partition table in order. Now it's bluescreening again. Same problem; new form. :(

I'll get this moved to the Apple section.

---

