---
title: "Grub 17"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by choochoo22 on 2009-05-07
After learning WAY more than I wanted to, and not nearly enough, I still can't get past Grub error 17 on booting.  The disks look like this: (much trial and error with Grub and the partitioner has led to this point)

sda1 NTFS  41GB WinXP trashed and re-installed
sda5 swap   8mb
 
sdb1 NTFS 220GB Aux storage for videos, now empty
sdb3 EXT3  30GB Jaunty install, I think, won't boot
sdb5 swap 500mb

System is an older board with 1.2G AMD CPU, 256mb memory.  The two hard drives are both on IDE channel 1 with a CD drive on channel 2.  There is also an onboard RAID controller with no disks installed but apparantly can't be disabled.  the system seems to boot from hd0, no matter what I set in the BIOS boot order, as if it can find no other choice.

---

### Post by raymondh on 2009-05-07
choochoo ....

This is just "food for thought" as you/we ponder your dilemna.  I distinctly remember that on older boards and older BIOS', there is a limit where the bootloader just can't get through.  The bootloader has to find a OS within that limit.  I think it's 1024 cyclinders.  (Cannot remember the website but googling for 1024 cyclinder limit and grub 17 error should help).  Basically, this happens when we add a newer and bigger HDD.  Arrgggh, I can't remember the specifics right now (sorry, am typing fast to get back to work).  IN fact, on old borads, the limit was closer to 8GB.

I had that dilemna on a gOS install (a derivative of hardy) which was solved by installing the distro within the first 100GB of the HD ... the closer to the front of the drive, the better.... as well as enabling LBA on the BIOS.

Hope this helps.

---

### Post by Altay_H on 2009-05-07
If you're just trying to get Grub working again, I'd suggest you give [SuperGrub]("http://www.supergrubdisk.org/index.php?pid=5") a try. It's incredibly useful for fixing Grub.

---

### Post by SaaTeeVaaGreen on 2009-05-07
this could be caused by a number of things (as i found out when i had the same error!). if you can still get into ubuntu (by booting from a cd for example) you could try this:

first open a terminal and type ```
sudo grub
``` which will open a grub shell.
next type ```
find /boot/grub/stage1
``` which will tell you where grub is. next, quit the grub shell (just type quit), and then type into the terminal ```
sudo fdisk -l
``` comparing the output of these 2 commands as well as the contents of menu.lst should tell if grub is looking at the correct partitions at boot, which was my problem.
alternatively post the output of the commands and contents of menu.lst here and i'll see if it looks right. (cant promise anything tho, this is still quite new to me too!)

---

### Post by 73ckn797 on 2009-05-07
Post the boot info from your /boot/grub/menu.lst

How is the Ubuntu drive listed? Based on what you provided it would be "root (hd1,2)" in the grub, if it is listed at all. The 9.04 does not list this anymore but it can be inserted into the grub menu.lst.

---

### Post by choochoo22 on 2009-05-07
I had already stumbled my way through some of the steps suggested but I am confused by some differences in nomenclature.  Grub refers to disks like (hd1,1) while the partitioner and fdisk refer to disks like sda1, sdb3, etc.  I don't understand how to translate one to the other.  

In any case; Grub> find /boot/grub/stage1 yields (hd1,1) and fdisk lists:

     boot
sda1    * NTFS
sda2      extended
sda5      swap

sdb1      NTFS
sdb2      Linux
sdb3      extended
sdb5      swap

I don't know how to post a file to display this to you directly.  One complication is that I have thus far been unable to get Ubuntu to connect to the network.  I figure I will put off fixing that and printer setup until I can boot to a permanent installation.

Raymond mentioned earlier that there may be a problem with trying to to boot from too far from the beginning of the disk.  Since I will have to reconstruct everything anyway, I am going to try installing ubuntu in sdb1 and see if that boots.

---

### Post by SaaTeeVaaGreen on 2009-05-07
if you open your menu.lst file, located in /boot/grub (type ```
gnome-open /boot/grub/menu.lst
``` in a terminal)
and scoll towards the end of the file, beneath where it says ## end default options ## you should find here the boot options. the first line will be title with release and kernel details, the second line will be root. is this also (hd1,1)? you could copy and paste these boot options to a new post if unsure

---

### Post by choochoo22 on 2009-05-07
> **SaaTeeVaaGreen said:**
> if you open your menu.lst file, located in /boot/grub (type ```
gnome-open /boot/grub/menu.lst
``` in a terminal)


"No such file or directory"

PS: I can't cut and paste anything since I don't have an internet connection from Ubuntu.  I am communicating with this forum using a seperate Vista system.

---

### Post by presence1960 on 2009-05-07
run the following commands in terminal one at a time. Paste the output here. ```
sudo fdisk -l
``` Note that is a lowercase L & ```
cat /boot/grub/menu.lst
```

This will help sort out things.

I have to watch a movie with my little girl now, but if you post the output of those 2 commands someone will be able to help you. If not I'll be back in about 2 hours.

P.S. Did you reinstall Windows after Ubuntu was installed. If you did you need to restore GRUB. If this is the case follow this:
> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

I would install GRUB to the MBR.

---

### Post by caljohnsmith on 2009-05-07
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by 73ckn797 on 2009-05-07
> **choochoo22 said:**
> "No such file or directory"

PS: I can't cut and paste anything since I don't have an internet connection from Ubuntu.  I am communicating with this forum using a seperate Vista system.

If you can view the Ubuntu directories from Windows Explorer look for "boot/grub/menu.lst". If you can read the directory then open "menu.lst" into  Word Pad or Notepad and you can then just copy the last section that lists the operating systems. 

An example would look like this:

```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a6ad6af7-c6f3-40de-b7da-4de6e4a4f851 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd2,0) 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a6ad6af7-c6f3-40de-b7da-4de6e4a4f851 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

title        Ubuntu 9.04, memtest86+ 
kernel        /boot/memtest86+.bin  
savedefault
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Ubuntu 9.04 ext4, kernel 2.6.28-11-generic
root        (hd1,0)
uuid        48a2f031-c9ae-4d1c-94bc-e35781b3f6f9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=48a2f031-c9ae-4d1c-94bc-e35781b3f6f9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,0)
uuid        48a2f031-c9ae-4d1c-94bc-e35781b3f6f9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=48a2f031-c9ae-4d1c-94bc-e35781b3f6f9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        48a2f031-c9ae-4d1c-94bc-e35781b3f6f9
kernel        /boot/memtest86+.bin
quiet


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
chainloader    +1
```

---

### Post by choochoo22 on 2009-05-07
The live CD boots OK but, as stated twice now, the networking is not working so downloading, or posting, or cut & paste anything seems unworkable.  All I can do is try your suggestions (appreciated) and report the results.

gnome-open /boot/grub/menu.lst
cat /boot/grub/menu.lst

both result in file-not-found messages

I tried the suggestion of installing Ubuntu at the beginning of sdb, this seemed promissing but still results in Grub 17.  This did, of course, change the partition structure.  The current structure is:

Grub> find /boot/grub/stage1
results: (hd1,0)

fdisk -l reports the following:

sda1 * NTFS
sda2   extended
sda5   Linux swap

sdb1   Linux
sdb2   extended
sdb5   Linux swap

---

### Post by Sarai the Geek on 2009-05-07
I don't have a solution to your problem, but if you have any sort of external storage device: a thumb/jump drive, external hard drive, sd card, heck even an iPod or maybe your phone, you could paste the outputs into text files and transfer them to the networked computer. Just a thought- :)

---

### Post by choochoo22 on 2009-05-07
Well I tried the same thing I had done before and now the networking is working in the live CD!  Miracles I guess. Anyway, here is the output from fdisk.  The info_script downloaded OK but I can't seem to run it, "can't find file".  I will continue to work on getting more info.

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf310f310

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5004    40194598+   7  HPFS/NTFS
/dev/sda2            5005        5005        8032+   5  Extended
/dev/sda5            5005        5005        8001   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80c2dfa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3647    29294496   83  Linux
/dev/sdb2            3648        3738      730957+   5  Extended
/dev/sdb5            3648        3738      730926   82  Linux swap / Solaris
```

---

### Post by choochoo22 on 2009-05-07
Here is menu.lst

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e7e5f211-21ba-46db-b8e7-6bf6fc556382
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e7e5f211-21ba-46db-b8e7-6bf6fc556382 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e7e5f211-21ba-46db-b8e7-6bf6fc556382
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e7e5f211-21ba-46db-b8e7-6bf6fc556382 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e7e5f211-21ba-46db-b8e7-6bf6fc556382
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by choochoo22 on 2009-05-07
Info script results:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf310f310

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,389,259    80,389,197   7 HPFS/NTFS
/dev/sda2          80,389,260    80,405,324        16,065   5 Extended
/dev/sda5          80,389,323    80,405,324        16,002  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80c2dfa4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    58,589,054    58,588,992  83 Linux
/dev/sdb2          58,589,055    60,050,969     1,461,915   5 Extended
/dev/sdb5          58,589,118    60,050,969     1,461,852  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="46A4050CA404FFE3" LABEL="Main" TYPE="ntfs" 
/dev/sda5: UUID="81508280-b851-4113-8e30-c7079cca5aee" TYPE="swap" 
/dev/sdb1: UUID="e7e5f211-21ba-46db-b8e7-6bf6fc556382" TYPE="ext3" 
/dev/sdb5: UUID="5548f2e0-3147-4c92-b7c8-180797e9cdcb" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin


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
# kopt=root=UUID=e7e5f211-21ba-46db-b8e7-6bf6fc556382 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e7e5f211-21ba-46db-b8e7-6bf6fc556382

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
uuid		e7e5f211-21ba-46db-b8e7-6bf6fc556382
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e7e5f211-21ba-46db-b8e7-6bf6fc556382 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e7e5f211-21ba-46db-b8e7-6bf6fc556382
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e7e5f211-21ba-46db-b8e7-6bf6fc556382 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e7e5f211-21ba-46db-b8e7-6bf6fc556382
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e7e5f211-21ba-46db-b8e7-6bf6fc556382 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=81508280-b851-4113-8e30-c7079cca5aee none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=5548f2e0-3147-4c92-b7c8-180797e9cdcb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   9.2GB: boot/grub/menu.lst
   9.1GB: boot/grub/stage2
   9.1GB: boot/initrd.img-2.6.28-11-generic
   9.2GB: boot/vmlinuz-2.6.28-11-generic
   9.1GB: initrd.img
   9.2GB: vmlinuz
```

---

### Post by presence1960 on 2009-05-07
why don't you run this command in terminal  ```
sudo blkid -c /dev/null
``` and compare the UUID of your Ubuntu partition from the output to the UUID of your Ubuntu entries in menu.lst.

---

### Post by presence1960 on 2009-05-08
sorry didnt see you finally ran the script which contains that info. I gotta get some shuteye- have work in the morning. Someone will surely help you here. My eyes are like lead weights right now.

---

### Post by choochoo22 on 2009-05-08
I don't understand what this is but here are the results:

```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="46A4050CA404FFE3" LABEL="Main" TYPE="ntfs" 
/dev/sda5: UUID="81508280-b851-4113-8e30-c7079cca5aee" TYPE="swap" 
/dev/sdb1: UUID="e7e5f211-21ba-46db-b8e7-6bf6fc556382" TYPE="ext3" 
/dev/sdb5: UUID="5548f2e0-3147-4c92-b7c8-180797e9cdcb" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
ubuntu@ubuntu:~$ 
```

---

### Post by cjv8888 on 2009-05-08
Try the following:

```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```

---

### Post by choochoo22 on 2009-05-08
It looks like Raymond may have nailed the problem in the very first reply.  The Linux boot sector on hd1 was too far from the beginning of the disk.

When I re-partioned and installed Ubuntu in the first partion on hd1 it still generated grub 17.  Later, however, I remembered I had changed the boot disk to hd1 in an earlier experiment.  When I changed the boot disk back to hd0, bingo, grub gives me a boot menu and no errors!  I re-installed XP on hd0, fixed the boot block, and it still works. :)

Now if I can fix the pesky network problem I should be on the road to Ubuntu land.  DHCP is disabled in my router and each local computer has its own IP address.  Ubuntu defaults to DHCP so the network is initially unavailable.  It's a fairly easy correction to edit the network connection and set the IP address but USUALLY Ubunto blocks me from applying the change.  The "apply" button simply greys out.  For some reason it did permit me to fix it in the live CD once but not now that the system is installed to hd1.  It feels like a permissions problem.  Any suggestions?

---

### Post by raymondh on 2009-05-08
choochoo ....

Am glad that worked for you.  I had boot problems with a pentium 2 computer until a forum member told me about the "cylinder" limit. It happens when we put in a BIG hard drive. In fact, mine was a 8GB limit.  Oh well, took out windows in that computer :)

It'll help other members if you could close/mark the GRUB17 thread solved.  Go to your first post > edit > advanced > type SOLVED in the beginning of the title > save

Time to search the forum and/or give your best google-fu on the network/DHCP problem ...... post/start a new thread if needed :)

---

