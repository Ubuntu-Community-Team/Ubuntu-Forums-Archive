---
title: "Grub error 15 after fresh 8.04 install"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by BlakeWolf on 2009-06-29
Hi!

I'm a first-time linux user trying hard to switch from windows (XP) to Ubuntu. At first I installed Jaunty, which worked to some extent. However, I ran in to quite a bit of trouble with my ATI graphics card and after extensive reading here at the forums I decided to go for Hardy to avoid complications.

Once I had completed the installation, using the same setup of partitions but reformatting them, I got a grub error 17. I spent a week trying to figure out a solution by reading on this forum and some others, but failed. Yesterday I wiped the Ubuntu install and reinstalled XP for an evening (in order to have music while some friends were over). Today I wiped the XP install and installed Hardy again. Having figured out that I probably had an error in my MBR I was kind of hoping that XP would have bulldozed it (as Windows tends to do with most things) and that the clean Ubuntu install would work. Instead I got a grub error 15. And this is where I stand - writing from the Live CD.

Here is the result of sudo fdisk -l :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x23303d00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      581463   293057320+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ea84ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  83  Linux
/dev/sdb2            3163       24791   173734942+   f  W95 Ext'd (LBA)
/dev/sdb3             123        2554    19535040   83  Linux
/dev/sdb4            2555        3162     4883760   82  Linux swap / Solaris
/dev/sdb5            6375       24791   147934521    7  HPFS/NTFS
/dev/sdb6            3163        6374    25800327   83  Linux

Partition table entries are not in disk order


If I can't fix this then I'll be forced to go back to Windows against my will - I simply can't figure this out myself simply by reading other threads related to my problem.

Please let me know if more info is needed to diagnose the problem. Any and all help is very much appreciated!

---

### Post by jerrrys on 2009-06-29
sorry to hear your having so many problems.  installing 804 should be painless.  your ending up with too many partitions.  makes me think your not using the "use entire disk option" when trying to install.  i would suggest using the "guided install" and the "use entire disk" option...

---

### Post by raymondh on 2009-06-29
2 great links from Herman involving ERROR 15 ..... The second link has good info starting at post # 36

[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)
[http://ubuntuforums.org/showthread.php?t=948327&highlight=grub+error+15&page=2](http://ubuntuforums.org/showthread.php?t=948327&highlight=grub+error+15&page=2)

Good luck.

---

### Post by BlakeWolf on 2009-06-29
You're right - I'm using the manual option (might be over my head, as you say) as I need to keep the NTFS partitions on both drives. I don't have any more storage, and these partitions contain files, movies, music, etc. that I really don't want to loose. I didn't think I could use the guided option without loosing these partitions, is it possible?

I chose to put Ubuntu on the second drive because it is a SATA drive, whereas the first is an old PATA (the installer first opts to put Ubuntu on the first drive). Does it complicate things that the first drive isn't the boot drive?

---

### Post by BlakeWolf on 2009-06-29
raymond:

Thanks for the links, the first is a nice handbook. It got me to make a super grub disc so far - which is nice, but hasn't quite solved the issues.

jerrys:

I erased all of the partitions except the ntfs partition on sdb, and then used the guided install with the option "largest continuous free space" (or some such), which installed ubuntu where I wanted it. Unfortunately all it did was switch me back to error 17 in grub. I've tried fixing the install with the grub super disc, but without result.

---

### Post by BlakeWolf on 2009-06-29
From what I've read, I'm pretty sure that something is wrong in my MBR (especially since I even got the grub error 17 when attempting to boot windows and there was no linux distro at all on my computer). 

How would I go about confirming, and then fixing such a problem? Anyone?

---

### Post by jerrrys on 2009-06-29
here's something to ponder while i investigate further

 [http://www.mepis.org/node/9283](http://www.mepis.org/node/9283)

---

### Post by oldfred on 2009-06-29
When I installed 9.04 on my 3rd drive it found all three additional boot drives and correctly configured them. They have improved the finding of drives in 9.04. 

See the supergrub site for much more info than I can provide here. [http://www.supergrubdisk.org/w/index.php5?title=Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/w/index.php5?title=Howto_Boot_Windows_without_problems)

On my system the windows boot in menu.lst is:
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Since your windows is A and the partition is 1, your menu.lst for windows should be the same. 

For Ubuntu my old mother board did not allow selecting boot order and sometimes the Sata drives came up first and sometimes the Pata drive. So the boot order would be different and the system would give Grub errors. My solution was the change from the root (hd1,0) notation to the UUID xxxx notation in menu.lst.

If you cannot tell what to edit in your menu.lst, we need your latest fdisk -l and menu.lst. All the lines in menu.lst with # are comments and are not important, usually just the last lines after all the comments.

---

### Post by BlakeWolf on 2009-06-30
jerrys:

Are you suggesting that I edit my partitioning and leave the first cylinder blank?

oldfred:

I think you've misunderstood my desired outcome - I've been using Windows and want to rid myself of it completely. Any attempts I may make at dual-booting, etc. are well into the future! I only want Ubuntu to run stable on my system right now.

---

### Post by cjv8888 on 2009-06-30
To get a better picture of your booting problem, please  download the Boot Info Script to your liveCD desktop from the following link (curtesy of caljohnsmith & meierfra)

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by BlakeWolf on 2009-06-30
Ok, here is the RESULTS.txt content:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb5 sdb5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb5 sdb5 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb5 sdb5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb5 sdb5 ntfs-3g force 0 0

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23303d00

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,114,703   586,114,641   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ea84ea7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    98,125,019    98,124,957  83 Linux
/dev/sdb2          98,125,020   398,267,414   300,142,395   f W95 Ext d (LBA)
/dev/sdb5         102,398,373   398,267,414   295,869,042   7 HPFS/NTFS
/dev/sdb6          98,125,146   102,398,309     4,273,164  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="2AD0596BD0593E6F" LABEL="PATA 300" TYPE="ntfs" 
/dev/sdb1: UUID="1f730e55-13c7-43a8-a720-63db78df0984" TYPE="ext3" 
/dev/sdb5: UUID="7EACD308ACD2B9BB" LABEL="SATA 150" TYPE="ntfs" 
/dev/sdb6: TYPE="swap" UUID="fb04764c-a211-4885-a8c1-39ea1168461a" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/blake/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=blake)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=blake)


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
# kopt=root=UUID=1f730e55-13c7-43a8-a720-63db78df0984 ro

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1f730e55-13c7-43a8-a720-63db78df0984 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=fb04764c-a211-4885-a8c1-39ea1168461a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  32.9GB: boot/grub/menu.lst
  32.9GB: boot/grub/stage2
  32.8GB: boot/initrd.img-2.6.24-23-generic
  32.9GB: boot/vmlinuz-2.6.24-23-generic
  32.8GB: initrd.img
  32.9GB: vmlinuz
```

In case it matters - I am no longer booting from the LiveCD. I am using my super grub disc to access my Hardy installation.
 
For good measure, here is the latest result of fdisk -l:

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x23303d00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      581463   293057320+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ea84ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6108    49062478+  83  Linux
/dev/sdb2            6109       24791   150071197+   f  W95 Ext'd (LBA)
/dev/sdb5            6375       24791   147934521    7  HPFS/NTFS
/dev/sdb6            6109        6374     2136582   82  Linux swap / Solaris

Partition table entries are not in disk order
```

And my menu.lst:

```
## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root



```

---

### Post by unutbu on 2009-06-30
BlakeWolf,

If you can boot Hardy using SuperGrub Disk, open a terminal and run
```

gksu gedit /boot/grub/menu.lst
```

Go about 2/3 of the way down to where you see boot stanzas. Add this entry:

```
title        TEST
root         (hd0,0)
kernel       /boot/vmlinuz-2.6.24-23-generic root=/dev/sdb1 ro quiet splash
initrd       /boot/initrd.img-2.6.24-23-generic
quiet
```

Save and exit gedit. Reboot. Go to the GRUB menu and see if you can boot TEST.

---

### Post by BlakeWolf on 2009-06-30
unutbu:

Are you sure of this? As far as I understand hd0 is my first hard drive, which only contains some scrap remains of an old XP install... I have Hardy on hd1, I believe.

---

### Post by BlakeWolf on 2009-06-30
I tried your suggestion in any case - the result was another grub error 17.

---

### Post by unutbu on 2009-06-30
BlakeWolf, I am never 100% sure of anything I suggest regarding GRUB. LOL :)
However, what I suggest is harmless -- if it doesn't work, you are no worse off.
To revert the change, you merely remove the lines from menu.lst.

The reason why I suggested the above boot stanza is this:

When you use GRUB from within Linux, GRUB uses Linux to list the order of the drives.
When you boot the computer, GRUB uses the BIOS to list the order of the drives.
Usually the two lists match and there is no problem.
Occassionally there is a mismatch in the ordering. 

So although we believe hd1 to mean sdb while working within Linux,
GRUB may interpret hd1 to mean sda when we boot the computer.

Also, I believe BIOSes have a tendency (or may always?) call the boot drive the first drive. If I am right about this, then since you are booting sdb, GRUB would call sdb (hd0).

---

### Post by BlakeWolf on 2009-06-30
Ok, I see what you mean. So what did the newfound error tell us? Since it didn't work ... does that mean that GRUB is pointing to the correct hard drive?

I definitely think you might be on to something with the hard drive order. sda is identified by my BIOS as residing on channel 0, whereas sdb is on channel 2. I have listed the hard drive boot order as ch2, then ch0, but maybe there is some confusion anyway.

---

### Post by cjv8888 on 2009-06-30
I think you try using the uuid instead of the /dev/sdb1 in you menu

So edit the entry to 

```
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=1f730e55-13c7-43a8-a720-63db78df0984 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

```

I am using Hardy as well and this is what I have on the menu.lst

---

### Post by unutbu on 2009-06-30
I am puzzled that you got Error 17 (Cannot mount selected partition) when using

```
root (hd0,0)
```

and

```
root (hd1,0)
```

I would have thought that GRUB could mount at least one of these.
(Your sda1 partition has been shutdown uncleanly, so I'm not surprised GRUB had problems mounting that drive. That might be why you were getting Error 15 (File not found) at some points.)

Although I can't confidently tell you how to fix your problem, here are two things which may help a little:

[list]
[*] If you can use SuperGRUB Disk to boot Windows, do so and then shutdown cleanly.
This should restore Linux (and GRUB's) ability to mount sda1. If you can't boot Windows, tell us and we can tell you a different way to get sda1 mounting again.
[*] Boot the computer and get to the GRUB menu. Press 'c' to get to the GRUB command line.
Type ```


geometry (hd0)
geometry (hd1)
```

These commands will yield output which looks something like this:
```

grub> geometry **(hd0)**
drive 0x80: C/H/S = 243/255/63, The number of sectors = 3915776, **/dev/sdb**
   Partition num: 0,  Filesystem type unknown, partition type 0x7

```
Notice at the end of the first line of output, GRUB tells you what device it associates with (hd0).
This will settle once and for all what we should use on the root line in the menu.lst boot stanza.
[/list]

---

### Post by BlakeWolf on 2009-06-30
cjv8888:

I had the partitions specified with UUID's from the start, but changed to the /dev/sdb1 notation in an attempt to follow another thread. I've changed it back now.

unutbu:

Its been a long time since sda had an OS on it - in order to do as you suggest I would have to reinstall XP on that drive, shut it down and erase it. Do you think that would fix the issue? Incidentally - Jaunty could read and mount it just fine.

Here is the output of my drive geometries in GRUB:

```
grub> geometry (hd0)
geometry (hd0)

Error 21: Selected disk does not exist

grub> geometry (hd1)
geometry (hd1)

Error 21: Selected disk does not exist
```This worries me more than a little, and seems to confirm my suspicion that GRUB can't really detect my drives at all... What do you think? And of course - how to fix it?

I've checked BIOS, and the hard drives are both detected just fine there.

---

### Post by unutbu on 2009-06-30
What options does your BIOS provide? Are there any options related to hard drive detection? modes?

If you have a way to take screenshots of the BIOS menu, posting them may be useful.

---

### Post by cjv8888 on 2009-06-30
Also have you tried changing the order of booting of the HDs in the BIOS ?

I have to go to bed now because I have a virus. ( a physical one)

Hope Unutbu can continue to help you to solve this.  I will check back in again tomorrow.

---

### Post by BlakeWolf on 2009-06-30
I'm not quite sure how to get a screen capture from my BIOS, but I've copied the hard drive menus down:

My BIOS version: AwardBIOS W7100NMS v3.0

_Primary slave_ (PATA)

IDE HDD Auto-Detection (no options)

IDE Primary Slave (options: None, Auto, Manual)
Access Mode (options: CHS, LBA, Large, Auto)

Both options are set to "Auto"

_Third Master (SATA)_

IDE Auto-Detection (no options, but note that it does not read IDE HDD like the first drive)

Extended IDE Drive (options: None, Auto)
Access Mode (options: Large, Auto)

Both options are set to "Auto".


After these menus some non-interactive lines follow with info on size, no. of cylinders etc.

---

### Post by BlakeWolf on 2009-06-30
cjv8888:

No, I haven't tried that, but do I really want the drive without the OS first in the boot menu in BIOS?

Hope you get better soon, and thanks for the help so far!

---

### Post by unutbu on 2009-06-30
BlakeWolf, under the "Third Master (SATA)" section, try setting "Extended IDE Drive" to "None" instead of "Auto". 

If that does not work, it would not hurt to cycle through each of the options, changing each one at a time. 

There are 3 "IDE Primary Slave" options, (PATA)
          4 "Access Mode" options (PATA)
          2 "Extended IDE Drive" options (SATA)
          2 "Access Mode"  options (SATA)

so in total there are 48 combinations. I know this sounds like a lot of rebooting, and rather stupid advice.

But I'd rather get you boot using stupid advice than leave you unbooting because I was ashamed to suggest something stupid. 

I know the Access Mode should probably be LBA (or Auto) for the PATA,
and I suspect no change need be made to the PATA to get Ubuntu (on SATA) booting.
That should narrow down the number of combinations (to 4) that you should try first.

However, like I said before, I am continually surprised by the way GRUB behaves and the solutions which fix boot problems. So rather than assume I know that some combination need not be tried, I'd rather suggest that you try all options.

cjv8888, thanks for your help on this. Hope you feel better soon.

---

### Post by BlakeWolf on 2009-06-30
Haha, now we're talking :) You're right though, better safe than sorry. I'll post back once I've tried the 4 first combos.

---

### Post by BlakeWolf on 2009-06-30
For the SATA drive:

Holding the "Extended IDE Drive" options at "Auto" and varying the "Acces Mode" options changes nothing - both result in a grub error 17.

Switching the "Extended IDE Drive" mode from "Auto" to "None" effectively makes the drive invisible to BIOS and the "Acces Mode" options are greyed out. No varying is possible here. Attempting to boot "without" this drive gave a grub error 21 , which makes sense since the boot files are located on this drive.

While I was at it I also tried the geometry commands you suggested earlier, but from the actual GRUB command line this time (instead of via the Ubuntu terminal). This gave the kind of results you were expecting:

```
grub> geometry (hd0)
drive 0x80: C/H/S=1023/16/63, The number of sectors=586114704, LBA
Partition num: 0, Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S=1023/255/63, The number of sectors=398299088, LBA
Partition num: 0, Filesystem type ext2fs, partition type 0x83
Partition num: 4, Filesystem type unknown, partition type 0x7
Partition num: 5, No BSD/Solaris sub-partition found, partition type 0x82
```This at least proves that GRUB sees the drives and numbers them the way we expect, right?

Should I continue to vary the BIOS settings for the PATA disc?

---

### Post by unutbu on 2009-06-30
The GRUB output of the geometry commands looks fine. It looks like 
```

root (hd1,0) 
```

was correct.

Now I am of the opinion that no change need be made in the BIOS menu. (Ask me again in an hour... :) )

---

### Post by BlakeWolf on 2009-06-30
Lol, opinions are functions of time as far as I'm concerned - I'll be mucking around in BIOS before long again :)

So now what, are we out of leads?

---

### Post by unutbu on 2009-06-30
Every time you try to boot, are you trying the normal 

"Ubuntu 8.04.2, kernel 2.6.24-23-generic"

boot option and the 

"TEST"

boot option?

Do they both always yield Error 17?

---

### Post by BlakeWolf on 2009-06-30
No, I've only been trying the first option, not the "TEST" option. Which settings would you like me to try with the "TEST" option?

---

### Post by unutbu on 2009-06-30
I'm afraid I'm just taking potshots in the dark at this point BlakeWolf.
It seems like we have all the ducks lined up in a row, and yet GRUB keeps falling to pieces. (How do like them mixed metaphors?) 

But seriously, I am curious what would happen if you use the BIOS menu to set the "IDE Primary Slave" (PATA) to None. I think this makes the BIOS ignore this drive during boot.
If I'm right about that, then perhaps GRUB would list sdb (Ubuntu) as (hd0).
Then the TEST boot stanza might actually work. Furthermore, I believe once the Linux kernel takes over, it polls for devices on its own and should then detect the PATA drive. 
So, if things go as planned (ha!) you would be able to boot and access both drives normally.

---

### Post by BlakeWolf on 2009-06-30
unutbu - you've made my system boot on it's own for the first time in days! The PATA drive is working fine, but my large NTFS partition with data on the SATA drive cannot be mounted.

What now? What should I do with my menu.lst file? 

We're making good progress now! :)

---

### Post by unutbu on 2009-06-30
I'm shocked one of my ideas worked! Woohoo!

Time to press my luck:

Try
```

sudo mount -t ntfs-3g /dev/sdb5 /mnt -o force
```

This may mount the NTFS partition on the SATA drive at /mnt.
If it works, then do 
```

sudo umount /mnt              # unmount sdb5 cleanly
sudo mount /dev/sdb5 /mnt     # Check that you can now mount it normally
```

If this does not work, then try
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda5
sudo mount -t ntfs-3g /dev/sdb5 /mnt -o force
```

---

### Post by BlakeWolf on 2009-06-30
I actually beat you to it :P Which, of course, may not be a good thing...

I did the following, as recommended by Ubuntu when mounting failed:

```
 mount -t ntfs-3g /dev/sdb5 sdb5 -o force
```This gave a respons that mounting had failed, yet 30 seconds later I could access the partition. It is now mounted at /media together with the one partition on sda and my optical devices. Is this where it should be?

I have to admit, I'm a little confused now - am I somehow in the clear....? Sounds unlikely to me, lol!

---

### Post by unutbu on 2009-06-30
Try shutting down, and the rebooting. 
Does everything work right "off the bat" now?

PS. 
Since your current menu.lst works, save a backup copy of it. Then edit /boot/grub/menu.lst: do a find and search for
(hd1,0) and change it to (hd0,0). Then you can delete the TEST boot stanza.

---

### Post by BlakeWolf on 2009-06-30
Ok, it works beautifully now! I changed the boot stanzas for the regular Ubuntu kernels to (hd0,0), and everything boots "off the bat" :)

My only remaining question is how I rid sda of grub and the windows boot files. In case I change the setup of my system I don't want all this coming back to bite me!

---

### Post by unutbu on 2009-06-30
Congratulations. I'm glad to hear things are better now. :p

To get rid sda of GRUB, you could boot the XP CD, and run fixboot. (See
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221))

Regarding windows boot files I am truly clueless.

---

### Post by BlakeWolf on 2009-06-30
Ok, but what do you think will happen if I simply delete the files?

---

### Post by unutbu on 2009-06-30
Before I tell you its okay to delete some files, I better confess I don't know exactly what you are referring to. Are these windows boot files on sda1? If so, then yes -- you should be able to delete anything in sda1 and not affect your machine's ability to boot.

---

### Post by BlakeWolf on 2009-06-30
Yes, all of the files are on sda1. The files I'm referring to are boot.ini, ntldr and ntdetect.com

---

### Post by unutbu on 2009-06-30
Yes. It is perfectly fine to delete them. 
If fact, you can repartition/reformat sda any way you wish -- nothing you do there will affect your ability to boot one iota.

sda is invisible to the BIOS (unless you undo the change in the BIOS menu). So the BIOS hands off to GRUB on sdb, which reads the menu.lst and boots sdb1. Nowhere does it use sda.

---

### Post by BlakeWolf on 2009-06-30
I ran fixmbr and fixboot from an XP cd, which temporarily screwed everything up again. I then ran the SuperGrub Disc and fixed my Ubuntu boot, which got me back. Unfortunately GRUB was not removed from sda. This round gave me a real scare after having my system running, so I think I'll leave this timebomb for later, lol :) As for the Windows boot files, I deleted them without any issues.

All and all - I consider my problems solved now. Thanks to you unutbu! I can't tell you how grateful I am!

---

### Post by unutbu on 2009-06-30
Glad I could do more good than harm today :)
Enjoy Ubuntuing...

---

### Post by BlakeWolf on 2009-06-30
You saved my day, no my week, to tell the truth :) Now I'm definitely going to enjoy Ubuntuing!

---

