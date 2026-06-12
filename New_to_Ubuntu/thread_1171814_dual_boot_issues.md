---
title: "dual boot issues"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by mmriley159 on 2009-05-27
New Guy Here,
I am attempting to use Ubuntu in a dual boot with Windows XP. After I divided the hard drive and installed, I could not find Ubuntu. I then looked on a site that recommended that I use Grub, which I did by going through the sudo grub, etc. I then was able to open Ubuntu 8.10, which then upgraded to 9.04, along with 301 patches. Then I could not find XP, even though it showed up on the boot list. It said NTLDR is missing. After some research, I was able to fix by using the fixmbr command from my install XP disk. Now Ubuntu is gone missing. What do I need to do?

---

### Post by NHArticleTen on 2009-05-27
[http://ubuntuforums.org/showthread.php?t=984955](http://ubuntuforums.org/showthread.php?t=984955)

---

### Post by presence1960 on 2009-05-27
> **mmriley159 said:**
> New Guy Here,
I am attempting to use Ubuntu in a dual boot with Windows XP. After I divided the hard drive and installed, I could not find Ubuntu. I then looked on a site that recommended that I use Grub, which I did by going through the sudo grub, etc. I then was able to open Ubuntu 8.10, which then upgraded to 9.04, along with 301 patches. Then I could not find XP, even though it showed up on the boot list. It said NTLDR is missing. After some research, I was able to fix by using the fixmbr command from my install XP disk. Now Ubuntu is gone missing. What do I need to do?

When you ran fixmbr you overwrote GRUB. Now to restore GRUB do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

At #6 I would do > setup (hd0) to place GRUB in MBR, provided Ubuntu & Windows are on the first hard disk or if you only have one hard disk. 

see if this brings up the GRUB menu when you boot. If your windows option does not boot or there is no windows option in the menu it should just be a simple matter of editing one file to fix. But we'll cross that bridge if we get to it.

---

### Post by mmriley159 on 2009-05-28
OK, I tried the fix listed, first using the setup (hd0,4), which said something like fail, but not fatal, but then the computer would not shut down. I then tried the setup (hd0), which got me back to where I was before, I can see the boot menu under grub, but when I try to select windows xp, I get the NTLDR is missing message. Ubuntu loads fine.

---

### Post by presence1960 on 2009-05-28
> **mmriley159 said:**
> OK, I tried the fix listed, first using the setup (hd0,4), which said something like fail, but not fatal, but then the computer would not shut down. I then tried the setup (hd0), which got me back to where I was before, I can see the boot menu under grub, but when I try to select windows xp, I get the NTLDR is missing message. Ubuntu loads fine.

To get a better picture of your setup download the Boot Info Script to your Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Open a terminal and run > sudo bash ~/Desktop/boot_info_script*.sh  This will create a RESULTS.txt file on your desktop. Paste the contents of that file here. Highlight all the text after pasting here and click the # button on the toolbar to place Code tags around the text. I am going to bed but some one here will be glad to take a look at that info and help you out. That's another advantage here, the forum never closes.

---

### Post by mmriley159 on 2009-05-28
I was able to reinstall the MBR using the windows disk, but now can't get into 9.04. Can I do what you said from the install cd using a terminal window?

---

### Post by presence1960 on 2009-05-28
> **mmriley159 said:**
> I was able to reinstall the MBR using the windows disk, but now can't get into 9.04. Can I do what you said from the install cd using a terminal window?

mmriley, i was just going to go to bed and decided to check my email. I am subscribed to this thread so I got your post in my email. 

yes you can do that from the Ubuntu Live CD.

---

### Post by mmriley159 on 2009-05-30
I will confess that I decided to remove Ubuntu from the dual boot on my computer, but I did install it on my wife's Vaio laptop, removing vista and running it solo. So far it has been working fine on all fronts. So this is where I will leave it and play with it as I learn.
I can't afford to lose windows as I write a newsletter in publisher and run other applications for various organizations. Oh well. Thanks for the help. This is a great forum.

---

### Post by m3tropolis on 2009-06-11
Hi! (especially *presence1960*)

I hope it isn't too rude to hijack this thread, but my situation is exactly the same as the OP before he gave up. 

I haven't yet gone the fixmbr route, because I can see (via Ubuntu) my boot.ini file and ntldr. Somehow the wrong drive is trying to boot? Isn't there an easier way?

Many, many thanks for helping another Linux noooob get back into Windows to finish some work!!! :D

So this is what Boot Info Script came up with:  

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd

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

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0dacbbbd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,384,364    61,384,302   7 HPFS/NTFS
/dev/sda2          61,384,365   156,296,384    94,912,020   f W95 Ext d (LBA)
/dev/sda5          61,384,428   115,378,829    53,994,402   7 HPFS/NTFS
/dev/sda6         115,378,893   156,296,384    40,917,492   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x964003df

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16c716c6

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdc2         204,796,620   586,099,394   381,302,775   f W95 Ext d (LBA)
/dev/sdc5         204,796,683   490,030,694   285,234,012   7 HPFS/NTFS
/dev/sdc6         490,030,758   582,083,144    92,052,387  83 Linux
/dev/sdc7         582,083,208   586,099,394     4,016,187  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x475e475e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="ECA89EB1A89E79B2" LABEL="Web" TYPE="ntfs" 
/dev/sda5: UUID="11C7A499738F26E1" LABEL="goodies2" TYPE="ntfs" 
/dev/sda6: UUID="BC4C55F84C55ADC0" LABEL="Projects" TYPE="ntfs" 
/dev/sdb1: UUID="ECA080DBA080ADA0" LABEL="Azweepey" TYPE="ntfs" 
/dev/sdc1: UUID="ECACA7D9ACA79C98" LABEL="OS" TYPE="ntfs" 
/dev/sdc5: UUID="38742DE4742DA61A" LABEL="Music" TYPE="ntfs" 
/dev/sdc6: UUID="f457e9e2-f32b-4570-9cf6-6582c698eaa5" TYPE="ext3" 
/dev/sdc7: UUID="3e51da6b-63ea-4ed0-b7e6-72c8968ad2f1" TYPE="swap" 
/dev/sdd1: UUID="43181B94E451C044" LABEL="Goodies" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdc6 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda1 on /media/Web type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
/dev/sdc1 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc6/boot/grub/menu.lst: ===========================

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
default        4

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
# kopt=root=UUID=f457e9e2-f32b-4570-9cf6-6582c698eaa5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f457e9e2-f32b-4570-9cf6-6582c698eaa5

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
uuid        f457e9e2-f32b-4570-9cf6-6582c698eaa5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f457e9e2-f32b-4570-9cf6-6582c698eaa5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f457e9e2-f32b-4570-9cf6-6582c698eaa5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f457e9e2-f32b-4570-9cf6-6582c698eaa5 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f457e9e2-f32b-4570-9cf6-6582c698eaa5
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc6 :
UUID=f457e9e2-f32b-4570-9cf6-6582c698eaa5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdc7 :
UUID=3e51da6b-63ea-4ed0-b7e6-72c8968ad2f1 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/Web ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sdc5 /media/Music ntfs-3g defaults,locale=en_CA.UTF-8 0 0

=================== sdc6: Location of files loaded by Grub: ===================


 272.4GB: boot/grub/menu.lst
 272.3GB: boot/grub/stage2
 272.3GB: boot/initrd.img-2.6.28-11-generic
 272.4GB: boot/vmlinuz-2.6.28-11-generic
 272.3GB: initrd.img
 272.4GB: vmlinuz
```

---

### Post by mmriley159 on 2009-06-11
Once I gave up on the dual boot, I had to find a free partition program to remove and restore the hard drive on my windows machine. But I have been having great fun using Ubuntu on the laptop. It sounds crazy, but it reminds me of my first CPM machine that I got from my father in law, when I have to go into the terminal window to enter command lines. Of course, in those days, there was no internet to pose my questions to.

---

### Post by m3tropolis on 2009-06-11
Yes, I am liking Ubuntu very much; without the internet, maybe not! I'd be reinstalling windows at this point if it wasn't for all the tips I've found.

I know my machine is really close to actually dual-booting! I can smell it! I just...need...one...last...tip! ;)

I hope.

Thanks *mmriley159*

---

### Post by m3tropolis on 2009-06-11
> **presence1960 said:**
> To get a better picture of your setup download the Boot Info Script to your Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Open a terminal and run   This will create a RESULTS.txt file on your desktop. Paste the contents of that file here. Highlight all the text after pasting here and click the # button on the toolbar to place Code tags around the text. I am going to bed but some one here will be glad to take a look at that info and help you out. That's another advantage here, the forum never closes.

Hi *presence1960*,

I thought I'd revive this thread, since I'm basically at the same point as mmriley159 was, but not having done the fixmbr thing. I posted the output of Boot Info Script as a starting point.

Many thanks in advance!
chris.

---

### Post by presence1960 on 2009-06-12
> **m3tropolis said:**
> Hi *presence1960*,

I thought I'd revive this thread, since I'm basically at the same point as mmriley159 was, but not having done the fixmbr thing. I posted the output of Boot Info Script as a starting point.

Many thanks in advance!
chris.

If you're getting a message such as NTLDR is missing you are going to have to run fixmbr from the XP install CD: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) , then restore GRUB from the Ubuntu live CD. If you are not getting a NTLDR is missing or windows bootloader is missing message then...

Your menu.lst looks like it is ok. Why don't you go into BIOS and report back the boot order of your hard disks. I am thinking this may be the problem as sometimes BIOS and GRUB read the disks differently. Example my machine take a look at sudo fdisk -l:
```

raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2   *       16478       18389    15358140   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
/dev/sdb4           14520       16477    15727635   83  Linux
```

sda1 is XP, sdb2 is Jaunty, sdb4 is Hardy, sda3 is Jaunty /home.

But now take a look at my windows entry on menu.lst :
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

Now think this through here: Windows is on sda1 so why does my menu.lst entry for windows have rootnoverify (hd1,0)?...

Because in BIOS my boot order is the 160 GB drive (sdb) is first, then my 250 GB drive (sda) is second. Why sudo fdisk -l is reporting it the other way I don't know. But the fix was easy. Since windows is on the first partition of the second drive in my boot order I just changed it to (hd1,0)

Check your boot order in BIOS and note the order of your hard disks boot. If the drive that has windows (sdc) is not the third position in the boot order in BIOS change your Windows entry in menu.lst to correspond to it's boot order in BIOS. Remember the counting starts at 0, so if it is the first disk in the boot order your entry will be (hd0,0), the second disk will be (hd1,0) etc. Change your map lines accordingly also. They need to correspond to your Windows drive and your linux drive numbers.

---

### Post by m3tropolis on 2009-06-12
> **presence1960 said:**
> 
Check your boot order in BIOS and note the order of your hard disks boot. If the drive that has windows (sdc) is not the third position in the boot order in BIOS change your Windows entry in menu.lst to correspond to it's boot order in BIOS. Remember the counting starts at 0, so if it is the first disk in the boot order your entry will be (hd0,0), the second disk will be (hd1,0) etc. Change your map lines accordingly also. They need to correspond to your Windows drive and your linux drive numbers.
:D:D:D:D:D
THANK YOU!! That explanation finally made sense of this mess, and yes, as soon as I set the windows drive as hd(0,0), thar she went. Whew. I knew it was close. What bites my ***, is that grub is f*cking up the volume choice; I mean, hasn't it been around awhile, and installed on many systems with multiple drives???

*presence1960* - many many thanks for your time and help with this. I can easily see how I might be still banging my head, thinking that everything "looked" right. I hope this thread can help many other people I saw posting about this problem. From as far back as 2002!! (well, it won't help **them** anymore)

chris.

---

### Post by presence1960 on 2009-06-12
I don't think it is GRUB, because if you look at the results in your RESULTS.txt file under the command ```
sudo fdisk -l
```
you will see your disks are listed that way. That is not GRUB. I am not sure why, but when one has multiple hard disks sometimes the order in BIOS is not recognized by Ubuntu the same way resulting in the problem you just experienced. Looking at the results of sudo fdisk -l everything seems to be ok. But it isn't so you will be ready to bang your head against the wall. My suggestion is systems with multiple disks that have a GRUB error always compare your fdisk results with the boot order in BIOS.

Glad you got it working. Enjoy!

---

