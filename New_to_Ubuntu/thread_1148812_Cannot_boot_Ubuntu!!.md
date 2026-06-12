---
title: "Cannot boot Ubuntu!!"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by xreaper on 2009-05-04
Hello all. 
 
I am using Ubuntu 9.04 with latest updates and drivers. Recently I was playing a Fullscreen game and tried minimizing, then after several failed attempts I did a hard restart and now all I can seem to get is either a blank screen while I'm waiting for ubuntu to boot (which it won't) or when I boot in recovery mode, it hangs on:
 
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)
[6.097425] Dumping ftrace buffer:
[6.097477] (ftrace buffer empty)
 
Please help.

---

### Post by robindog on 2009-05-04
You need to be more specific.
Are you booting from CD or hard drive.
Do you have dual booting or is ubuntu your only o/s:guitar:

---

### Post by xreaper on 2009-05-04
Dual booting windows xp with ubuntu 9.04, I am booting from a hard drive (well trying to anyway =\) and this is the first time that its ever happened to me.

---

### Post by kansasnoob on 2009-05-04
Does this happen to be a Wubi install?

---

### Post by xreaper on 2009-05-04
Uhh... I installed Ubuntu onto my hard drive after resizing my windows partition to make room for it, and it has been working perfectly fine except for after I did a hard restart on it.

---

### Post by warren94 on 2009-05-04
do you have the cd, or a usb of it
if so plug that in and boot from that, on the main menu (after language select) you can choose rescue a broken system i believe.

hope i helped.

---

### Post by xreaper on 2009-05-04
Yes I have a cd, but so far no avail with the rescue broken system =[ it just puts me in one of those full screen terminal "shells" and I get lost.

---

### Post by warren94 on 2009-05-04
well, i have never used that, so i suppose you should try googling it
good luck.

---

### Post by kansasnoob on 2009-05-04
Did the installation look like this:

[http://wubi-installer.org/screenshots.php](http://wubi-installer.org/screenshots.php)

Or more like this:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

If you can boot the Ubuntu live Cd and post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L. It would be helpful.

---

### Post by xreaper on 2009-05-04
Its more like the second one, I booted/installed from the ubuntu cd.
I'll use an old 8.04 live cd to get the output of that command in a sec.

---

### Post by cholericfun on 2009-05-04
can you access your ubuntu partition from the LiveCD?
if not so then gparted should be your friend

when youre on your LiveCD go to System -> Admin. -> gparted and click on your ubuntu partition, theres an option to "fix" the partiton.

---

### Post by xreaper on 2009-05-04
Hmm.. its booting into the live cd now. Would it be able to detect an ext4 partion on 8.04 I wonder?

---

### Post by cholericfun on 2009-05-04
thats an interesting question...
might need to go through synaptic and install a newer version of gparted
have a read in the web. no idea myself

---

### Post by xreaper on 2009-05-04
Well, its come up as ext3, but it won't let me check/fix it

---

### Post by cholericfun on 2009-05-04
well, i had the problem once that gparted didnt even recognise my HD unless it was the first thing that i opened after booting from LiveCD

so either try that or look for a gparted version that supports ext4 (if exists)
actually a quick search seems to say there was some bug about ext4 beeing falsly detected as ext3 and that it has been fixed so try an update of gparted

---

### Post by xreaper on 2009-05-04
Can't seem to find any versions that support ext4 :S

---

### Post by kansasnoob on 2009-05-04
What happens in you go to terminal (from the live CD) and run:

```
sudo fdisk -l
```

Again that's a lower case L at the end.

---

### Post by xreaper on 2009-05-04
Oh! sorry! I forgot about that.. here:

Disk /dev/sda: 13.6 GB, 13611982336 bytes
255 heads, 63 sectors/track, 1654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3dd93047

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         827     6642846    7  HPFS/NTFS
/dev/sda2             828        1654     6642877+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17021   136721151    7  HPFS/NTFS
/dev/sdb2           18238       19457     9799650   83  Linux
/dev/sdb3           17022       18237     9767520    5  Extended
/dev/sdb5           17022       18237     9767488+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by kansasnoob on 2009-05-04
> **xreaper said:**
> Oh! sorry! I forgot about that.. here:

Disk /dev/sda: 13.6 GB, 13611982336 bytes
255 heads, 63 sectors/track, 1654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3dd93047

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         827     6642846    7  HPFS/NTFS
/dev/sda2             828        1654     6642877+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17021   136721151    7  HPFS/NTFS
/dev/sdb2           18238       19457     9799650   83  Linux
/dev/sdb3           17022       18237     9767520    5  Extended
/dev/sdb5           17022       18237     9767488+  82  Linux swap / Solaris

Partition table entries are not in disk order

OK, I see you have two hard drives.

Beyond that I'm puzzled:confused:

I've already messaged one guru, I'll message another. Unless he's blocked me:)

---

### Post by xreaper on 2009-05-04
Heh, thank you all for your help. I'll just sit here patiently and get whooped on gnuchess =]

---

### Post by cholericfun on 2009-05-04
ok, just had a quick look at what the word is bout gparted and ext4
seems like a mild headache,
c.f. this forum entry

[http://ubuntuforums.org/archive/index.php/t-1076479.html](http://ubuntuforums.org/archive/index.php/t-1076479.html)

the tip with downloading that tar.gz and doing a make/install might seem unsatisfactorily -especially if it doesnt actually help you get back to your system...
on the other hand i cant really think of anything smarter than some "click-on-the-fix-all-buttom" solution.
can you access files and read them properly from the LiveCD then?
cause if you can your problem is prob. somewhere else...

---

### Post by xreaper on 2009-05-04
I can't access files on my ubuntu 9.04 partion, it just politely tells me that it is ext4 and unsupported  :D

---

### Post by cholericfun on 2009-05-04
well, that is very polite... 

ok well my last "smart" suggestion for today will be:
somehow get a copy of jaunty (the desktop version includes the liveCD facility) and use that gparted there... (if that doesnt work i dunno what!)

from there you can see if you can at least access your files (and maybe save them somewhere)


or else make a gparted install from the source.
see that link i send before (and prob much much quicker option)

---

### Post by xreaper on 2009-05-04
Downloading desktop cd now :P Thanks for the help, I'll talk back here once its done in an hour :S

---

### Post by kansasnoob on 2009-05-04
Hopefully either caljohnsmith or meierfra will respond. They know this stuff like the back of their hands.

I'm sure others do too!

---

### Post by xreaper on 2009-05-04
Okay,thank you. :D

---

### Post by xreaper on 2009-05-04
BUMP !!! o.O

---

### Post by xreaper on 2009-05-04
Okay, I've tried using the partition manager to check/fix the ubuntu partition, and it still hangs on the same error during boot. Any more ideas?

---

### Post by xreaper on 2009-05-04
Is it possible that theres a backup of some boot files somewhere..?

---

### Post by meierfra. on 2009-05-04
> 
BUMP !!! o.O 

Please wait for 24 hours before bumping a thread

> Can't seem to find any versions that support ext4 :S
??? The newest version of gparted (4.4.1) definitely supports ext4.
Anyway, since you got the Ubuntu 9.04 CD, no more need to get the gparted LiveCD.

> Okay, I've tried using the partition manager to check/fix the ubuntu partition, and it still hangs on the same error during boot


Did gparted fix any errors?
Try running a filsystem check in the terminal:

```
sudo umount /dev/sdb2
sudo e2fsck -yfv /dev/sdb2
```
(I"m guessing that Ubuntu is on /dev/sdb2. If not, use /dev/sda2 in place of /dev/sdb2. )

Post the output of the "e2fsck" command.
If  "e2fsck" fixed some  errors,  you might run "e2fsck" a second time.

Are you able to access your Ubuntu partition from the 9.04 CD?

---

### Post by ymra on 2009-05-04
Did you try booting into recovey mode.  It should be an option in the boot loader (grub)

---

### Post by xreaper on 2009-05-04
[INDENT]> Try running a filsystem check in the terminal:
Code:sudo umount /dev/sdb2
sudo e2fsck -yfv /dev/sdb2(I"m guessing that Ubuntu is on /dev/sdb2. If not, use /dev/sda2 in place of /dev/sdb2. )
Post the output of the "e2fsck" command.
If  "e2fsck" fixed some  errors,  you might run "e2fsck" a second time.
Are you able to access your Ubuntu partition from the 9.04 CD?

Heres the output that I got:
ubuntu@ubuntu:~$ sudo e2fsck -yfv /dev/sdb2
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb2: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  122793 inodes used (20.02%)
     610 non-contiguous files (0.5%)
      92 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 108733/30
 1728411 blocks used (70.55%)
       0 bad blocks
       1 large file

   93911 regular files
   13860 directories
      69 character device files
      26 block device files
       3 fifos
     505 links
   14879 symbolic links (13886 fast symbolic links)
      36 sockets
--------
  123289 files

And yes I can access my Ubuntu partion from the live cd. 
[/INDENT]

---

### Post by xreaper on 2009-05-04
Yes I have tried booting in recovery mode, thats how I found out the error.

---

### Post by meierfra. on 2009-05-04
Seems your file system is fine.  Let's have a closer look at your system:

Boot from the 9.04 CD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by xreaper on 2009-05-04
Sorry about the delay... here are the results:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 13.6 GB, 13611982336 bytes
255 heads, 63 sectors/track, 1654 cylinders, total 26585903 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3dd93047

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    13,285,754    13,285,692   7 HPFS/NTFS
/dev/sda2          13,285,755    26,571,509    13,285,755  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a3e9e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   273,442,364   273,442,302   7 HPFS/NTFS
/dev/sdb2         292,977,405   312,576,704    19,599,300  83 Linux
/dev/sdb3         273,442,365   292,977,404    19,535,040   5 Extended
/dev/sdb5         273,442,428   292,977,404    19,534,977  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A2F4B4E3F4B4BB3D" TYPE="ntfs" 
/dev/sda2: UUID="d0c535f9-2f85-4f0e-8d05-b447dbb6a742" TYPE="ext4" 
/dev/sdb1: UUID="D4AC1768AC174480" TYPE="ntfs" 
/dev/sdb2: UUID="021df460-cd0f-47df-80f5-1b8c9fec8a6c" TYPE="ext4" 
/dev/sdb5: TYPE="swap" UUID="eb56f86e-706c-4999-b1b4-f0c94291c6b8" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

============================= sda2/grub/menu.lst: =============================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=021df460-cd0f-47df-80f5-1b8c9fec8a6c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d0c535f9-2f85-4f0e-8d05-b447dbb6a742

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
# defoptions=splash vga=795

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
# howmany=1

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
uuid        d0c535f9-2f85-4f0e-8d05-b447dbb6a742
kernel        /vmlinuz-2.6.28-11-generic root=UUID=021df460-cd0f-47df-80f5-1b8c9fec8a6c ro splash vga=795 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d0c535f9-2f85-4f0e-8d05-b447dbb6a742
kernel        /vmlinuz-2.6.28-11-generic root=UUID=021df460-cd0f-47df-80f5-1b8c9fec8a6c ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d0c535f9-2f85-4f0e-8d05-b447dbb6a742
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sda2: Location of files loaded by Grub: ===================


   6.8GB: grub/menu.lst
   6.8GB: grub/stage2
   6.8GB: initrd.img-2.6.28-11-generic
   6.8GB: vmlinuz-2.6.28-11-generic

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=021df460-cd0f-47df-80f5-1b8c9fec8a6c /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=d0c535f9-2f85-4f0e-8d05-b447dbb6a742 /boot           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=eb56f86e-706c-4999-b1b4-f0c94291c6b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by meierfra. on 2009-05-04
Grub is configured correctly.  


Did you run a file system check on your boot partition? If not, do 

```
sudo umount /dev/sda2
sudo e2fsck -yfv /dev/sda2
```

and post the output.

---

### Post by xreaper on 2009-05-04
> **meierfra. said:**
> Grub is configured correctly.  


Did you run a file system check on your boot partition? If not, do 

```
sudo umount /dev/sda2
sudo e2fsck -yfv /dev/sda2
```and post the output.

I'm pretty sure I have, but heres the output anyways:
```

ubuntu@ubuntu:~$ sudo umount /dev/sda2
umount: /dev/sda2: not mounted
ubuntu@ubuntu:~$ sudo e2fsck -yfv /dev/sda2
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      34 inodes used (0.01%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 24
   63954 blocks used (3.85%)
       0 bad blocks
       1 large file

      21 regular files
       4 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
      25 files
```

---

### Post by meierfra. on 2009-05-04
I'm starting to run out of ideas, but let's see what happens if you reinstall the kernel

```
sudo mount /dev/sdb2  /mnt
cd /mnt      
sudo cp /etc/resolv.conf etc  
sudo mount --bind {/,}proc 
sudo mount --bind {/,}dev
sudo mount --bind {/,}sys
sudo chroot /mnt  
```



and at the new prompt
```

mount /dev/sda2 /boot
apt-get update
apt-get purge linux-image-2.6.28-11-generic
apt-get install linux-image-2.6.28-11-generic linux-restricted-modules linux-restricted-modules-2.6.28-11-generic linux-restricted-modules-generic
```

---

### Post by thingy87654321 on 2009-05-04
wouldnt it be quicker to just do a reinstall, like if u used wubi, unintall ubuntu from add/remove on windows or if you used the other method, just reinstall? im just saying, thats what i would do.....

---

### Post by xreaper on 2009-05-04
:o Is that safe to do inside the live cd?

---

### Post by xreaper on 2009-05-04
Yeah.. It would be. But I spent half a day and most of my bandwith setting it up so.. :D

---

### Post by meierfra. on 2009-05-04
I accidentally left out all the "sudo"'s in the first bunch of commands. It's fixed now.

---

### Post by thingy87654321 on 2009-05-04
yeah i know the feeling, i was setting up a computer for a friend, i put tons of stuff on it, customized it, it took 3 days, then it got a virus that messed up a lot of things on it and i had to reinstall the next day, so 3 day setup, reinstall, now another 3 days setup, thats about 6 to 7 days

---

### Post by xreaper on 2009-05-04
Oh. I was root when I did it so would it matter if I left them out? Heres the output:

```
root@ubuntu:/home/ubuntu# mount /dev/sdb2  /mnt
root@ubuntu:/home/ubuntu# cd /mnt 
root@ubuntu:/mnt# cp /etc/resolv.conf etc 
root@ubuntu:/mnt# mount  --bind {/,}proc
root@ubuntu:/mnt# mount --bind {/,}dev
root@ubuntu:/mnt# mount --bind {/,}sys
root@ubuntu:/mnt# chroot /mnt
root@ubuntu:/# mount /dev/sda2 /boot
root@ubuntu:/# apt-get update
Hit http://nz.archive.ubuntu.com jaunty Release.gpg                        
Ign http://nz.archive.ubuntu.com jaunty/main Translation-en_US             
Ign http://nz.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty/multiverse Translation-en_US
Get:1 http://nz.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://nz.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://nz.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://nz.archive.ubuntu.com jaunty Release
Get:2 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Get:3 http://nz.archive.ubuntu.com jaunty-updates Release [49.6kB]  
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:4 http://security.ubuntu.com jaunty-security Release [49.6kB]
Hit http://nz.archive.ubuntu.com jaunty/main Packages     
Hit http://nz.archive.ubuntu.com jaunty/restricted Packages
Hit http://nz.archive.ubuntu.com jaunty/main Sources  
Hit http://nz.archive.ubuntu.com jaunty/restricted Sources
Hit http://nz.archive.ubuntu.com jaunty/universe Packages
Hit http://nz.archive.ubuntu.com jaunty/universe Sources
Hit http://nz.archive.ubuntu.com jaunty/multiverse Packages
Hit http://nz.archive.ubuntu.com jaunty/multiverse Sources
Get:5 http://nz.archive.ubuntu.com jaunty-updates/main Packages [29.6kB]
Get:6 http://nz.archive.ubuntu.com jaunty-updates/restricted Packages [14B]
Get:7 http://nz.archive.ubuntu.com jaunty-updates/main Sources [10.4kB]
Get:8 http://nz.archive.ubuntu.com jaunty-updates/restricted Sources [14B]     
Get:9 http://nz.archive.ubuntu.com jaunty-updates/universe Packages [11.0kB]   
Get:10 http://nz.archive.ubuntu.com jaunty-updates/universe Sources [1787B]    
Get:11 http://nz.archive.ubuntu.com jaunty-updates/multiverse Packages [675B]  
Get:12 http://nz.archive.ubuntu.com jaunty-updates/multiverse Sources [639B]   
Get:13 http://security.ubuntu.com jaunty-security/main Packages [16.4kB]       
Get:14 http://security.ubuntu.com jaunty-security/restricted Packages [14B]
Get:15 http://security.ubuntu.com jaunty-security/main Sources [4512B]
Get:16 http://security.ubuntu.com jaunty-security/restricted Sources [14B]
Get:17 http://security.ubuntu.com jaunty-security/universe Packages [4925B]
Get:18 http://security.ubuntu.com jaunty-security/universe Sources [14B]
Get:19 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]
Get:20 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]
Fetched 180kB in 4s (43.0kB/s)
Reading package lists... Done
root@ubuntu:/# apt-get purge linux-image-2.6.28-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms* linux-generic* linux-image-2.6.28-11-generic* linux-image-generic*
  linux-restricted-modules-2.6.28-11-generic*
  linux-restricted-modules-generic* nvidia-180-kernel-source* nvidia-glx-180*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 134MB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 106900 files and directories currently installed.)
Removing nvidia-glx-180 ...
Purging configuration files for nvidia-glx-180 ...
dpkg - warning: while removing nvidia-glx-180, directory `/usr/lib/tls' not empty so not removed.
Removing nvidia-180-kernel-source ...
Removing all DKMS Modules
Done.
Removing dkms ...
Purging configuration files for dkms ...
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.28-11-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Purging configuration files for linux-restricted-modules-2.6.28-11-generic ...
Removing linux-image-generic ...
Removing linux-image-2.6.28-11-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.28-11-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@ubuntu:/# apt-get install linux-image-2.6.28-11-generic linux-restricted-modules linux-restricted-modules-2.6.28-11-generic linux-restricted-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot nvidia-settings patch nvidia-180-libvdpau
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed:
  linux-image-2.6.28-11-generic linux-restricted-modules
  linux-restricted-modules-2.6.28-11-generic linux-restricted-modules-generic
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.5MB of archives.
After this operation, 98.4MB of additional disk space will be used.
Get:1 http://nz.archive.ubuntu.com jaunty/main linux-image-2.6.28-11-generic 2.6.28-11.42 [24.6MB]
Get:2 http://nz.archive.ubuntu.com jaunty/restricted linux-restricted-modules-2.6.28-11-generic 2.6.28-11.15 [883kB]
Get:3 http://nz.archive.ubuntu.com jaunty/restricted linux-restricted-modules-generic 2.6.28.11.15 [3406B]
Get:4 http://nz.archive.ubuntu.com jaunty/restricted linux-restricted-modules 2.6.28.11.15 [3396B]
Fetched 25.5MB in 1min 2s (411kB/s)                                            
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package linux-image-2.6.28-11-generic.
(Reading database ... 103890 files and directories currently installed.)
Unpacking linux-image-2.6.28-11-generic (from .../linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb) ...
Done.
Selecting previously deselected package linux-restricted-modules-2.6.28-11-generic.
Unpacking linux-restricted-modules-2.6.28-11-generic (from .../linux-restricted-modules-2.6.28-11-generic_2.6.28-11.15_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-generic.
Unpacking linux-restricted-modules-generic (from .../linux-restricted-modules-generic_2.6.28.11.15_i386.deb) ...
Selecting previously deselected package linux-restricted-modules.
Unpacking linux-restricted-modules (from .../linux-restricted-modules_2.6.28.11.15_i386.deb) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-restricted-modules-2.6.28-11-generic (2.6.28-11.15) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

Setting up linux-restricted-modules-generic (2.6.28.11.15) ...
Setting up linux-restricted-modules (2.6.28.11.15) ...
root@ubuntu:/# 
```

---

### Post by meierfra. on 2009-05-04
> that safe to do inside the live cd?
 

Yes. The first bunch of code logs you into the file system on your Ubuntu partition.

---

### Post by meierfra. on 2009-05-04
Looks good. See what happens when you reboot.

---

### Post by xreaper on 2009-05-04
Wow! It worked!!! Thanks heaps! Really, wow... I don't know how I could ever repay you! :D!!!!!!!!

---

### Post by meierfra. on 2009-05-04
> Wow! It worked!!!
Reinstalling the kernel just was a shot in the dark. So I'm really glad it worked.

I'm not sure that your  booting problems was caused by your crash.
Did you install anything just before you crashed?  Changed some configuration?


I just noticed that purging the kernel, remove some ndvia files:

> nvidia-180-kernel-source* nvidia-glx-180*
 
So you might have to reinstall those:

```

sudo apt-get install nvidia-180-kernel-source nvidia-glx-180
```

---

### Post by xreaper on 2009-05-04
Yeah, Reinstalling the restricted drivers now. Thanks heaps, really. I think I was playing around a bit with start up manager before I went onto Regnum Online.. Then came the hard restart and yeah...

---

