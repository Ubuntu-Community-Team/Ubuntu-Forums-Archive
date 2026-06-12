---
title: "Installed Ubuntu now Windows returns Unmountable Boot Volume"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by wiseheart on 2009-02-18
First of all, I have searched on this question, and found two threads, both of which didn't have answers, and several others that didn't seem to apply. 

I installed Feisty Fawn Ubuntu from a live Cd onto a refurbished IBM T41 with Windows XP installed on it. Used live cd partition manager to set up a partition for Ubuntu. Installation went fine. 

However, when I tried to boot back into XP, I received a blue screen of death with the error "Unmountable Boot Volume" as described here: [http://support.microsoft.com/kb/555302](http://support.microsoft.com/kb/555302)

I tried asking on #ubuntu IRC channel and was told this was a Windows problem, not an Ubuntu problem. That was very discouraging, because XP ran fine until I installed Ubuntu. I was told this was a problem related to fragmentation of the drive, however this was a clean drive, so that doesn't make much sense.

So, I tried the M$ instructions to fix, boot into recovery console, chkdsk, that didn't work, so then fixboot. 

This gave me a NETLDR is missing error and also disabled grub or kept me from booting into Ubuntu. I used the live cd to boot Ubuntu, and tried some of the grub fixes listed in the forums. These returned File not found errors. I tried looking at the partitions and there were a lot of ??? marks. 

Fortunately, IntuitiveNipple helped me rebuild my partition tables and now I am running on Ubuntu again. However, I still get Unmountable Boot Volume error for XP. 

Could anyone suggest a thread, instructions, or some other help for how to be able to dual-boot into XP. (I also read a few other mentions of this from other IBM Thinkpad owners, so perhaps this is model specific?)

Thanks for any help.

---

### Post by sydbat on 2009-02-18
Could be that XP didn't like being partitioned and is now corrupted (at least for booting purposes). If you have anything important on the XP partition, use the Live CD to access it (if possible) put it into the Ubuntu partition then reformat the XP partition with the XP install disk.

Other than that, I have no idea. I do know Windows does not like other OS's messing with partitioning schemes.

If anything, this will bump your post!

---

### Post by LastWho on 2009-02-18
> Could anyone suggest a thread, instructions, or some other help for how to be able to dual-boot into XP.
i m not sure that will help:
[&#8220;How to&#8221; Dual boot Ubuntu and Windows 7 (Ubuntu installed first) ]("http://ubuntuforums.org/showthread.php?t=1035999")

good luck

---

### Post by caljohnsmith on 2009-02-18
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by wiseheart on 2009-02-20
Thanks Caljohnsmith. I did this from my Ubuntu install instead of loading up the Live CD, as it seemed that it would produce the same reults. They are pasted below: 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 55443288 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69737369

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    49,994,279    49,994,217   7 HPFS/NTFS
/dev/sda2          49,994,280    76,854,959    26,860,680  83 Linux
/dev/sda3          76,855,023    78,140,159     1,285,137  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4648BF6248BF4F83" LABEL="IBM_PRELOAD" TYPE="ntfs" 
/dev/sda2: UUID="02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="0199a7ea-dd62-434b-9593-d8d5556e0940" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/d/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=d)(rw,nosuid,nodev,max_read=65536,user=d)


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.2, kernel 2.6.20-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=02dac94c-2bb4-4ae9-8955-9a6f0f0b0de1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0199a7ea-dd62-434b-9593-d8d5556e0940 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda2: Location of files loaded by Grub: ===================


  28.3GB: boot/grub/menu.lst
  28.3GB: boot/grub/stage2
  28.3GB: boot/initrd.img-2.6.20-17-generic
  28.4GB: boot/initrd.img-2.6.22-15-generic
  28.3GB: boot/initrd.img-2.6.22-15-generic.bak
  28.3GB: boot/initrd.img-2.6.24-21-generic
  28.7GB: boot/initrd.img-2.6.24-21-generic.bak
  28.3GB: boot/initrd.img-2.6.24-22-generic
  28.3GB: boot/initrd.img-2.6.24-22-generic.bak
  27.7GB: boot/initrd.img-2.6.24-23-generic
  27.7GB: boot/initrd.img-2.6.24-23-generic.bak
  28.2GB: boot/vmlinuz-2.6.20-17-generic
  28.4GB: boot/vmlinuz-2.6.22-15-generic
  28.4GB: boot/vmlinuz-2.6.24-21-generic
  28.3GB: boot/vmlinuz-2.6.24-22-generic
  27.7GB: boot/vmlinuz-2.6.24-23-generic
  27.7GB: initrd.img
  28.3GB: initrd.img.old
  27.7GB: vmlinuz
  28.3GB: vmlinuz.old
```

---

### Post by emshains on 2009-02-20
Looks like a dead disk to me.

---

### Post by caljohnsmith on 2009-02-20
The script was able to mount and read your sda1 Windows partition just fine, so I'm confused about what you said in your first post:
[QUOTE=wiseheart]However, I still get Unmountable Boot Volume error for XP. [/QUOTE]
So do you get that error when you try to mount the sda1 XP partition in Ubuntu, or when you boot XP? At this point it does look like you have a Windows problem and not a Grub problem, because everything seems to be in order to boot Windows just fine from Grub. So what exactly happens now when you boot Windows from Grub? Is that when you get the "unmountable boot volume" error?

---

### Post by wiseheart on 2009-02-20
> **caljohnsmith said:**
> The script was able to mount and read your sda1 Windows partition just fine, so I'm confused about what you said in your first post:

So do you get that error when you try to mount the sda1 XP partition in Ubuntu, or when you boot XP? At this point it does look like you have a Windows problem and not a Grub problem, because everything seems to be in order to boot Windows just fine from Grub. So what exactly happens now when you boot Windows from Grub? Is that when you get the "unmountable boot volume" error?

Yes, I select the Windows partition in Grub, then Windows begins to load, then a blue screen of death appears with the Unmountable boot volume error. 

If this is a problem with Windows, why did it only happen after installing Ubuntu?

And if this is a problem I can't fix from Ubuntu, is it safe to re-install Windows to that partition? I don't want to do anything that can destroy my partition tables again or otherwise prevent me from booting into Ubuntu.

---

### Post by caljohnsmith on 2009-02-20
Before you do a complete reinstall of Windows, I would instead recommend trying to do a "Windows Repair" from the Windows Install CD. You can do that by selecting the install Windows option from the Windows CD main menu, and then after that you will be offered the chance to do a Windows Repair instead of doing a full reinstall. Let me know how that goes if you try it.

---

### Post by p007pramod on 2009-03-01
> **caljohnsmith said:**
> Before you do a complete reinstall of Windows, I would instead recommend trying to do a "Windows Repair" from the Windows Install CD. You can do that by selecting the install Windows option from the Windows CD main menu, and then after that you will be offered the chance to do a Windows Repair instead of doing a full reinstall. Let me know how that goes if you try it.

Hi,
I have been facing the same problem with my T60 for the last 2 night & days.

I have a 320Gb Hitachi brand-new HDD
Here is the sequence that I followed:
1. Installed windows on 15Gb primary partition
2. Installed Ubuntu 8.10 (Intrepid) on 18 Gb logical partition
3. a separate 500Mb partition for /boot
4. after the ubuntu installation finished, I was no longer able to go back to XP
5. Everytime choosing WinXP from GRUB screen will take me to "UNMOUNTABLE_BOOT_VOLUME" blue screen.
6. the script that has been mentioned above seems to give all perfect results as ubuntu would like to see.

But definitely something in the MBR got corrupted when I installed GRUB (via Ubuntu live CD)

I have tried the recovery console CD for Xp and also tried "fixmbr" command but, it didnt help at all. Instead it created a new problem for me. 

After running fixmbr, windows xp CD detects only 130 Gb from a 320 Gb HDD. I dont know what happened to the other 190 Gb. 

I tried Gparted live CD as well. It shows me 298Gb HDD but does not let me create any logical partitions (only primary & extended partitions). 

Now I am completely messed up with three issues....
1. How to get back WinXP running on my machine
2. How to get the socalled dualboot up and running with ubuntu 8.10 and winxp pro
3. how to recover the 190Gb which now windows setup can't even recognize (even if it is not in /ext3 format)

I am dying to see any suggestions on any of the above mentioned issues' resolution..

Thanks in advance
Pramod

---

### Post by caljohnsmith on 2009-03-01
Pramod, how about posting the results of the boot info script so we can get a better idea of your setup.

---

### Post by p007pramod on 2009-03-02
Attaching the script output..

One point worth mentioning:
> while trying to boot with QParted live cd, it **showed warning flag for my /dev/sda1** (ntfs partition of 50 Gb)
> also when I tried running the recover CD for win xp pro, 
 **chkdisk /p & /r** reported that "The drive conatins unrecoverable data"

So does that mean the whole partition has been screwed and I will have to reinstall windows??

Thanks,Pramod

---

### Post by caljohnsmith on 2009-03-02
> **p007pramod said:**
> 
So does that mean the whole partition has been screwed and I will have to reinstall windows??

Yes, I think reinstalling Windows is probably your best bet. Good luck and let me know how it goes.

---

### Post by TJCIB on 2009-03-02
I just was messing around with the same error, although it wasn't even a dual boot, it was on a friend's machine.  That Unbootable message can be caused by a number of things, even from the power going out or doing an improper reboot.

After trying the Windows repair option, I ended up reformatting and reinstalling Windows.  God Bless separate partitions for storing documents!

---

### Post by wiseheart on 2009-03-03
> **emshains said:**
> Looks like a dead disk to me.

This is not helpful at all, if you have something against Windows, then by all means take it somewhere else. The disk is obviously not dead, because I am running Ubuntu on it. If you had taken time to read the thread you would see that.

---

### Post by wiseheart on 2009-03-03
> **p007pramod said:**
> Hi,
I have been facing the same problem with my T60 for the last 2 night & days.

I have a 320Gb Hitachi brand-new HDD
Here is the sequence that I followed:
1. Installed windows on 15Gb primary partition
2. Installed Ubuntu 8.10 (Intrepid) on 18 Gb logical partition
3. a separate 500Mb partition for /boot
4. after the ubuntu installation finished, I was no longer able to go back to XP
5. Everytime choosing WinXP from GRUB screen will take me to "UNMOUNTABLE_BOOT_VOLUME" blue screen.
6. the script that has been mentioned above seems to give all perfect results as ubuntu would like to see.

But definitely something in the MBR got corrupted when I installed GRUB (via Ubuntu live CD)

I have tried the recovery console CD for Xp and also tried "fixmbr" command but, it didnt help at all. Instead it created a new problem for me. 

After running fixmbr, windows xp CD detects only 130 Gb from a 320 Gb HDD. I dont know what happened to the other 190 Gb. 

I tried Gparted live CD as well. It shows me 298Gb HDD but does not let me create any logical partitions (only primary & extended partitions). 

Now I am completely messed up with three issues....
1. How to get back WinXP running on my machine
2. How to get the socalled dualboot up and running with ubuntu 8.10 and winxp pro
3. how to recover the 190Gb which now windows setup can't even recognize (even if it is not in /ext3 format)

I am dying to see any suggestions on any of the above mentioned issues' resolution..

Thanks in advance
Pramod

Pramod, 

There are a lot of people on here who would like to throw darts at a dartboard all day, and they will try to tell you oh this could be a million things, but it's not. This is a reproducible error from installing Ubuntu via a Live CD on a Txx laptop. I have successfully reproduced this on a T43 after my T41 problem mentioned above. Also if you google for T** laptop ubuntu xp you will find two other forum results from different forums mentioning this same problem. 

What I can tell you is that this problem is fixable if you know how to manually edit your partition table. Unfortunately, this is not a skill many of us possess, but there was one extremely helpful British fellow in #ubuntu IRC channel IntuitiveNipple who helped me edit the partition table using the 'dd' command and got the partitions back to normal. I wouldn't recommend doing it without expert help though.

Thanks to Caljohnsmith though for giving some reasonable help.

---

