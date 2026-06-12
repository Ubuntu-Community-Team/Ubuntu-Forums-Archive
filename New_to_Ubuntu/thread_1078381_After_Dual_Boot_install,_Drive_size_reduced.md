---
title: "After Dual Boot install, Drive size reduced"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by jbcollins on 2009-02-23
Hi, noobie question:

I just finished building my own budget system with GIGABYTE GA-MA74GM-S2 motherboard and AMD Athlon 64 X2 5200 Brisbane 2.7GHz processor with 4 GB Ram, and 2 Hard drives.

1. Drive #1 SATA 500 GB.
2. Drive #2 IDE 300 GB, jumper set to Master.

After reading the suggestions of many on this forum, I installed WinXP first on Drive 1 (SATA). Everything worked fine. (Am keeping XP only because I run some propriatary software which is only available in XP, I tried Wine, didn't like it much, perhaps because I don't know how to use it well.) 

Next, I installed the 2nd drive (IDE) and then installed Ubuntu 8.10 on it. The install went according to plan. I am a total noob when it comes to Linux (and Ubuntu in particular), but GRUB loaded fine and I was able to load both operating systems just fine with GRUB.

My problem is :

1. When I load WinXP, which is on the SATA 500 GB drive, the size of the drive shows only 127 GB instead of 500 GB. However, checking the BIOS, both the drives show up with correct drive sizes.

2. From WinXP, the IDE drive is invisible - what I mean is, I can see the C: drive, but not the 300 GB drive as an installed drive. Is this normal?

And finally, (and a bit unrelated to the above 2 questions)

3. I am a very proactive person, so I am scared to run Ubuntu without a firewall or a virus protection and connect it to the Internet.  I did read the super-excellent thread @ [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) and I will confess I have a Windows mindeset, I guess what I am looking for is reassurance.

Thanks much, and best regards. (sorry for the many questions).

---

### Post by Jeroen Vernooij on 2009-02-23
Hi,
1) This is a very [common problem]("http://www.google.com/search?hl=en&q=windows+xp+127gb+limit"), I think you need Service pack 1.

2) In order to see the Ubuntu partition on your IDE drive, you need a windows driver which you can download at [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by jbcollins on 2009-02-23
@ Jeroen Vernooij,

Thanks very much for the quick reply - very helpful links. Yes, I did not install SP1 on my XP, only 2 and 3. I will try your suggestions tonight and report back. Thanks again. Much appreciated.

---

### Post by Jeroen Vernooij on 2009-02-23
If you already have SP2 & 3 installed, I wouldn't recommend installing SP1 on top of that. 
If I recall correctly, back in my Windows days I used [Maxtor big drive enabler]("http://www.google.com/search?hl=en&q=maxtor+big+drive+enabler") (works also on non-Maxtor drives)
but please note that you are asking Windows questions on a Linux forum which may result in misinformed info.

---

### Post by jbcollins on 2009-02-23
Sure, and thanks. 

No, I wasn't planning on loading the full SP1 - the link you provided lead me to MS KB 331958 which has a Q331958_WXP_SP2_x86_ENU.exe hotfix. I was planning on installing that to see if that would take care of the problem.

And as far as this being a Windows question - I don't mean to dispute, but before loading Ubuntu, XP Home by itself did recognize the 500 GB SATA drive; which is making me wonder if its my older HDD (IDE) which is causing the problem or if its an Ubuntu issue. 

The Maxtor big drive enabler seems more like a better alternative. thanks again for your help.

---

### Post by jbcollins on 2009-02-23
Just to give you an Update:

Maxtor big drive enabler pretty much did nothing and Q331958_WXP_SP2_x86_ENU.exe hotfix won't load since I have SP2 & SP3. 

I updated BIOS (which was 2 releases behind). That ran successfully but upon restart, won't go past POST (won't load GRUB) :( I guess I will have to play more with BIOS.

Thanks again for your help.

---

### Post by caljohnsmith on 2009-02-23
I think it would help to get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by jbcollins on 2009-02-23
@caljohnsmith,

Thanks much, for offering to help. As soon as I can get past POST, I will do what you said and update status.

---

### Post by jbcollins on 2009-02-23
@caljohnsmith,

Got the GRUB to work, and here's the result file as per your direction.

Thanks very much

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95429542

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d531b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   566,323,379   566,323,317  83 Linux
/dev/sdb2         566,323,380   586,067,264    19,743,885   5 Extended
/dev/sdb5         566,323,443   586,067,264    19,743,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="26E8C3B9E8C38611" TYPE="ntfs" 
/dev/sdb1: UUID="581a2379-9123-482f-b98e-502c86d44452" TYPE="ext3" 
/dev/sdb5: UUID="019011b0-d1dd-4ac7-8753-279f9e398e36" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/j/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=j)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn /usepmtimer


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
# kopt=root=UUID=581a2379-9123-482f-b98e-502c86d44452 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=581a2379-9123-482f-b98e-502c86d44452

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		581a2379-9123-482f-b98e-502c86d44452
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=581a2379-9123-482f-b98e-502c86d44452 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		581a2379-9123-482f-b98e-502c86d44452
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=581a2379-9123-482f-b98e-502c86d44452 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		581a2379-9123-482f-b98e-502c86d44452
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=581a2379-9123-482f-b98e-502c86d44452 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=019011b0-d1dd-4ac7-8753-279f9e398e36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  94.0GB: boot/grub/menu.lst
  94.1GB: boot/grub/stage2
  94.1GB: boot/initrd.img-2.6.27-7-generic
  94.1GB: boot/vmlinuz-2.6.27-7-generic
  94.1GB: initrd.img
  94.1GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-02-23
> **jbcollins said:**
> ```

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="Blue"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95429542

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   [COLOR="Blue"]268,413,957[/COLOR]   7 HPFS/NTFS

```
I think the above results explain your problem of why Windows is only seeing its partition as being 127 GB; notice the total size of the Windows sda1 partition is 268,413,957 sectors, or:
```
268,413,957 sectors * 512 bytes/sector = 137,427,945,984 bytes = ~128 GB
```
Note the total size of your drive is 976773168 sectors, or ~466 GB. That's of course less than the advertised 500 GB since manufacturers use the decimal definition of GB, i.e. 1*10^9 bytes, instead of the binary GB definition used by computers, which is 2^30 bytes. So the bottom line is that you simply need to resize your Windows partition to use the full space on the HDD. You can resize sda1 with gparted on the Live CD (System > Admin > Partition Editor) if you want. Anyway, good luck and let me know how it goes. :)

---

### Post by jbcollins on 2009-02-23
I feel like an idiot right now :oops:! Sorry to put you both through this - yes it worked. Thanks very much. I just created a new partition for the unused space. Thanks again.

---

### Post by caljohnsmith on 2009-02-23
> **jbcollins said:**
> I feel like an idiot right now :oops:! Sorry to put you both through this - yes it worked. Thanks very much. I just created a new partition for the unused space. Thanks again.
Not a problem at all, I'm glad that the solution turned out to be simple. Cheers and enjoy Ubuntu and Windows. :)

---

