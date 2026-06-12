---
title: "GRUB: No such disk"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Baelfael on 2009-11-30
I'm so ******* pissed off.

Alright, so I have a Maxtor OneTouch II xHD, and I decided I'd install Ubuntu 9.10 on it. Alright, cool, it installs no problem, I choose to just erase everything on the xHD for Ubuntu because nothing was there anyway.

I reboot, and what do I get?

GRUB Loading...
error: no such disk
grub rescue >_

So I figure maybe, "Oh well I guess the xHD is messed up, lets just boot back into Windows on my internal HD..." so I turn off the xHD, and boot up my Internal HD.

SAME MESSAGE.

I am completely clueless as to what to do right now. I'm really pissed off that this is happening and I need help FAST. I have no idea what to do. I hardly know anything about hard drive ****, much less about GRUB. Ugh.

Someone please help me out, all I REALLY want to do at this point is boot back into Windows XP so I don't lose everything on my computer.

---

### Post by Kobin on 2009-11-30
Did you install from USB or CD?

Could you post /boot/grub/grub.cfg and /boot/grub/device.map here?

---

### Post by Baelfael on 2009-11-30
I installed from a CD.

I don't know how to do that.

---

### Post by wirate on 2009-11-30
If you just want XP to run, boot from your XP installation cd and in the repair or recovery mode whatever its called, run fixmbr.
 
you could otherwise boot from a ubuntu livecd, open files /boot/grub/grub.cfg and /boot/grub/device.map in gedit and post the outputs here to get further help

---

### Post by presence1960 on 2009-11-30
Try to calm down, you won't lose XP, it is still there. I need to see more about your setup & boot process. Do this please:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by gackt on 2009-12-01
I went trough similar problem, i have installed ubuntu and windows afterward and after changing some grub setting i cannot get into any partition with error no such disk ( basically i think that the computer just cant find the record where boot is kept) and this post solved my problem:

[http://ubuntuforums.org/showthread.php?t=1306900](http://ubuntuforums.org/showthread.php?t=1306900)

---

### Post by chumchum on 2009-12-19
Right, I've exactly the same problem so...

Here are the results; 
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=98b90bd8-f774-4d6a-8ecf-4fe399edbd8d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM /wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xace22e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    12,582,974    12,582,912   b W95 FAT32
/dev/sda2          12,582,990   312,560,639   299,977,650   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,784,725,109 1,784,725,047   c W95 FAT32 (LBA)
/dev/sdb2       1,784,725,110 1,953,520,064   168,794,955   5 Extended
/dev/sdb5       1,784,725,173 1,946,563,919   161,838,747  83 Linux
/dev/sdb6       1,946,563,983 1,953,520,064     6,956,082  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1b811b80

Partition  Boot         Start           End          Size  Id System

/dev/sde1                 243     2,012,159     2,011,917   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="BACKUP" UUID="F089-8808" TYPE="vfat" 
/dev/sda2: UUID="7CD849E9D849A26E" LABEL="HDD" TYPE="ntfs" 
/dev/sdb1: LABEL="Elements" UUID="56CA-E3AA" TYPE="vfat" 
/dev/sdb5: UUID="98b90bd8-f774-4d6a-8ecf-4fe399edbd8d" TYPE="ext4" 
/dev/sdb6: UUID="d4a30562-b712-4ab1-a9df-5935d5d74a29" TYPE="swap" 
/dev/sde1: SEC_TYPE="msdos" UUID="3372-D369" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/HDD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5 on /media/98b90bd8-f774-4d6a-8ecf-4fe399edbd8d type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons

C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..."


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons

C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..."


================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

C:\wubildr.mbr = "Ubuntu"


================================== sdb1 Wubi: ==================================

/ubuntu/disk/root.disk was found, but could not be mounted

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 98b90bd8-f774-4d6a-8ecf-4fe399edbd8d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 98b90bd8-f774-4d6a-8ecf-4fe399edbd8d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98b90bd8-f774-4d6a-8ecf-4fe399edbd8d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 98b90bd8-f774-4d6a-8ecf-4fe399edbd8d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=98b90bd8-f774-4d6a-8ecf-4fe399edbd8d ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f089-8808
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 7cd849e9d849a26e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=98b90bd8-f774-4d6a-8ecf-4fe399edbd8d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=d4a30562-b712-4ab1-a9df-5935d5d74a29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 913.7GB: boot/grub/grub.cfg
 913.7GB: boot/initrd.img-2.6.31-14-generic
 913.7GB: boot/vmlinuz-2.6.31-14-generic
 913.7GB: initrd.img
 913.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sdf 
=============================== StdErr Messages: ===============================

mount: you must specify the filesystem type
```

---

### Post by presence1960 on 2009-12-19
chumchum,

You have wubi installed on sdb1. Once you get Ubuntu & windows booting I would go into windows and remove wubi from Control Panel > Add/Remove Programs.

You put GRUB onto the MBR of sda (160 GB) disk. I would put it on MBR of sdb (1 TB) disk. Here is how:

Boot the Ubuntu 9.10 Live CD/USB. Choose "Try ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo mount /dev/sdb5 /mnt
```
This will mount your 9.10 root partition.

Next from terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
This will put GRUB on MBR of sdb (1TB) disk. Reboot. Go into BIOS and set the sdb (1 TB) disk as first hard disk to boot in the hard disk boot order. This will bring up GRUB when you boot. Save changes to CMOS and continue booting. Choose Ubuntu and open a terminal and run ```
sudo update-grub
```
This will refresh your GRUB menu. If you watch the terminal output you will see what is being detected and added to GRUB menu. If you miss it you will see the options on the menu next time you reboot.

Then I would suggest you boot into windows and remove wubi.

P.S. here is a [link]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for restoring GRUB2 from a 9.10 Live CD/USB for your reference.

---

### Post by chumchum on 2009-12-20
Right, so I've followed all your advice up to changing the boot order, and now my PC starts booting from the external hard disk, but returns a similar error, "no such partition"
Is there any way for me to boot directly into an OS past grub?
I wouldn't mind getting rid of Ubuntu all together if it let's me use my computer again, all I want to preserve is Windows, data on it's partition and what's on the external hard disk.

---

### Post by chumchum on 2009-12-20
*BUMP*

Sorry for being so pushy, but my PC's pretty much dead and I'd like to get it working again :3
Am worried to see this on page 6, have been hammering "refresh" all day in the hope to get this running again D:

---

### Post by drs305 on 2009-12-20
If you are getting a Grub 2 menu but can't get past that, see if this helps:
[Grub2#Command Line & Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by chumchum on 2009-12-20
No menu, just something along the lines of
"Loading grub
error: no such partition
rescue>   "
and I'm expected to type something...

---

### Post by drs305 on 2009-12-20
> **chumchum said:**
> No menu, just something along the lines of
"Loading grub
error: no such partition
rescue>   "
and I'm expected to type something...

Ok. What you are supposed to type is detailed in the Rescue Mode section of the link I provided.

---

### Post by presence1960 on 2009-12-20
> **chumchum said:**
> Right, so I've followed all your advice up to changing the boot order, and now my PC starts booting from the external hard disk, but returns a similar error, "no such partition"
Is there any way for me to boot directly into an OS past grub?
I wouldn't mind getting rid of Ubuntu all together if it let's me use my computer again, all I want to preserve is Windows, data on it's partition and what's on the external hard disk.

Unfortunately you made no mention of an external disk. I assume it is sdb. If that is so you must set your BIOS to boot USB/Removable before hard disk in the boot order. Then GRUB2 on the external will boot when the external is plugged in at boot. You can then restore windows to MBR of sda (with external unplugged) with a windows XP install disk and follow the instructions for XP [here]("http://ubuntuforums.org/showthread.php?t=1014708"). Or you can try testdisk. It will be easier if you have an xp install CD. let me know.

Once windows is restored to MBR of sda if you boot without the external it will go right to windows.

---

### Post by chumchum on 2009-12-20
Sorry I didn't mention it

Regardless of what device I boot from, I can't get into an OS (except ubuntu live CD)
Whether I select the normal Hard Disk or the WD storage (name of the externel hard disk) or "Generic USB" etc
I always end up with something unhelpful (such as a blank screen) or grub which keeps returning the damned "no such partition error"
I then try drs305's advice, but none of the commands work, even "help" is an "unknown command"

Also, I don't have a windows rescue CD (I have windows XP by the way)

---

### Post by steveneddy on 2009-12-20
nvm

---

### Post by drs305 on 2009-12-20
> **chumchum said:**
> 
I then try drs305's advice, but none of the commands work, even "help" is an "unknown command"


When you were running the commands in the Rescue section, did you use the "set prefix" command? Often times when G2 seems completely lost it's because it has lost all track of where things are. Until it's told, it doesn't know where to look, including where to find the help information.

---

### Post by chumchum on 2009-12-21
Right, so I entered
```
set root=(hd2,5)
```
In the hope that this would tell grub what the correct partition is, but then it doesn't return anything, just expects another command, I assumed it saved the change and would know to look for root in that partition so I reboot (forcibly since "reboot" is an unknown command, but I get the same "no such partition" error.

Is there any way to be rid of Linux and grub altogether from the Ubuntu live CD?
I'm starting to lose hope and just want to return to Windows now and keep my data, thought I don't have a windows rescue disk

---

### Post by drs305 on 2009-12-21
> **chumchum said:**
> Right, so I entered
```
set root=(hd2,5)
```
In the hope that this would tell grub what the correct partition is, but then it doesn't return anything, just expects another command, I assumed it saved the change and would know to look for root in that partition so I reboot (forcibly since "reboot" is an unknown command, but I get the same "no such partition" error.

Is there any way to be rid of Linux and grub altogether from the Ubuntu live CD?
I'm starting to lose hope and just want to return to Windows now and keep my data, thought I don't have a windows rescue disk

The "set root" and "set prefix..." are two distinct commands. When G2 takes you to the rescue prompt, you use variations of the "set" command to either view or change environmental settings (non-geek translation - to change things). When you issue a "set" command, you won't see anything happen but the change is made (unless you do see something, which would probably be an error message).

So you have to run the "set prefix" command in addition to the "root" command. If you follow each step in the Rescue Mode section of the GRUB2 community doc you may have success. But you have to accomplish each step or it will fail. It may fail anyway, but following the steps precisely is the only wah to give it a chance.

In answer to your question, the easiest way to get rid of Ubuntu from the LiveCD would be to open Gparted/Partition Editor (System, Administration, Gparted/Partition Editor) and reformat the Ubuntu and swap partitions (you have to unmount the swap partition before it can be deleted with by highlighting the swap partition, then Partition, Swapoff).

**However, you would need a Windows CD so you can restore the Windows bootloader** or  you won't be able to boot into Windows. Here is a link on how to do that **with a Winodws CD**:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Since you say you don't have the CD, what system do you plan on using if you remove Ubuntu and Grub?

---

### Post by CaptainMark on 2009-12-21
do you have the windows cd, boot from it and run the fixmbr option, then if you wanted to install ubuntu on an ex hdd then use the ubuntu cd again to install but at the last stage you need to go to advanced settings and install grub to the ex hdd.

Then in your bios boot menu put the ex hdd above your normal hdd and when you boot if your ex hdd is plugged in it will boot ubuntu, if it isnt it will boot windows

---

### Post by CaptainMark on 2009-12-21
Sorry i see you dont have the windows recovery disk, perhaps ask your friends if someone you know has a windows recovery disk, alot of people keep all the cds that come with their pc, otherwise i believe it is legal to download a windows cd via torrents and burn your own, because you are downloading software you already own and you have paid for your registration key legitimatley, (dont take that for truth, it depends on where you live, but im sure that the case where i live, can anyone verify), 

If you manage it and run fixmbr, it will repairs windows boot record onto your internal hdd to detect. Whats happened is when you install  ubuntu from cd onto an external hdd the default behaviour is to install grub onto the first available hdd, in your case your internal hdd by doing this its has over written windows mbr (master boot record)

---

### Post by drs305 on 2009-12-21
You can also use SuperGrubDisk to boot to Windows, and I believe it may have the capability of running *fixmbr* to restore your Windows boot permanently.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")


**Added:**

I haven't used it, but this may allow you to fix the MBR from within Linux. 
[URL="http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/"]
How to fix your Windows MBR with an Ubuntu liveCD[/URL]

In either case, let us know of your success/failure.

---

### Post by chumchum on 2009-12-21
Ah, I missread the ls as Is, so tried following all the steps of grub rescue.
Well upon entering ls it lists (hd0) (hd0,1) (hd1) (hd2) (fd0)
Which is not at all what I expected, so I tried setting root and prefix for all of them, then trying ls /boot for each setting  to which all disks return "unknown filesystem" except when I use(fd0) which throws out "biodisk read error"


I think I now have some understanding of the problem, correct me if I'm wrong;
I installed Ubuntu on a partition of the external hard disk, but grub was installed on the main, internal HDD, overwriting window's boot record. The grub on the main HDD looks for ubuntu, but can't find it, since it's on another disk.
Using ms-sys to install the windows MBR on the HDD would overwrite grub there, and allow me to boot into windows again when booting from that disk. I would then need to install grub on the external hard disk so that when I chose to boot from there it will load linux?

So, I tried installing the second utility which drs305 kindly provided; I wasn't sure what they meant by 
"Once Ubuntu starts up, go to System -> Administration -> Software Sources and enable (by checking it off) the Universal repository."
so I just ticked "Community-maintained Open Source software (universe)"
and "Software restricted by copyright or legal issues (multiverse)"
And refreshed to download all the latest information.
When I wanted to install the tool by typing 
```
sudo apt-get install ms-sys
```
into the console, it wasn't able to install, returning this,
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
```

---

### Post by CaptainMark on 2009-12-21
it seems ms-sys is an old package that was taken away a while ago, that site must be old. [http://packages.debian.org/etch/i386/ms-sys/download](http://packages.debian.org/etch/i386/ms-sys/download) this is the .deb package, dont know if it will still work being quite old though. download it and execute like you would a .exe in windows

---

### Post by drs305 on 2009-12-21
> **chumchum said:**
> 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
```


I checked and it appears that ms-sys is no longer in the repositories. But you can get the .deb package from here for 32-bit systems:
[http://packages.debian.org/etch/i386/ms-sys/download]("http://packages.debian.org/etch/i386/ms-sys/download")

It will download to your Desktop - double-click to install it on 32-bit machines.

Here is the link for 64-bit machines:
[http://packages.debian.org/etch/amd64/ms-sys/download]("http://packages.debian.org/etch/amd64/ms-sys/download")

---

### Post by chumchum on 2009-12-21
OK, thanks for the link, so I followed the instructions and;
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6291456    b  W95 FAT32
/dev/sda2             784       19456   149988825    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      111094   892362523+   c  W95 FAT32 (LBA)
/dev/sdb2          111095      121601    84397477+   5  Extended
/dev/sdb5          111095      121168    80919373+  83  Linux
/dev/sdb6          121169      121601     3478041   82  Linux swap / Solaris

Disk /dev/sde: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Disk identifier: 0x1b811b80

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              21      167680     1005958+   6  FAT16
ubuntu@ubuntu:~$     sudo ms-sys -m /dev/sda2
/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record

```

I saw the NTFS filesystem, so I assumed sda2 hosts the windows partition, and entered the second command, though the program seems to have some doubts "/dev/sda2 seems to be a disk partition device,
use the switch -f to force writing of a master boot record"  

I've now become paranoid over changing anything in my PC so I just wanted to know if this was the right partition and whether or not I should force the writing there.

---

### Post by drs305 on 2009-12-21
> **chumchum said:**
> 
I've now become paranoid over changing anything in my PC so I just wanted to know if this was the right partition and whether or not I should force the writing there.

The device should be "sda" and not "sda2". You want it written to the MBR of sda, not to the partition sda2.

Check the instructions in the link to be sure, but I would expect you don't put the partition number into the command.

---

### Post by chumchum on 2009-12-21
Ah brilliant!
I can now boot into Windows again when the external disk isn't plugged in!
Thank you very much for all your help.
*Stupid crap was here*

---

### Post by CaptainMark on 2009-12-21
it shouldnt work because grub was written to your main drive and you just had to delete that, i would do a fresh install onto the ex hdd but make sure you install grub onto the right drive, then just set your bios to look for usb devices before your hdd when booting, simples

---

### Post by chumchum on 2009-12-21
No means of just installing grub on the external disk without installing Ubuntu all over again?

---

### Post by nishant.singh28 on 2009-12-21
If you haven't done a lot of customisation in Ubuntu, it's barely a 10 minute job...... :D

---

### Post by CaptainMark on 2009-12-21
its probaly not difficult to make your own grub entry and reinstall grub from a live cd but it would be even less difficult to reinstall, its never come up for me so ive never had to do it but perhaps someone can talk you through it if you need to do it that way, heres somewhere to start [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

EDIT: on karmic grub 2 is default see drs305 post below

---

### Post by drs305 on 2009-12-21
For Grub2, this is the ubuntu community doc. There is a section on reinstalling Grub 2:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by chumchum on 2009-12-21
Well reinstalling grub didn't help so I'll try a fresh install...eehhh, not sure what to do now, any help please?
[IMG]http://img694.imageshack.us/img694/4483/screenshotinstall.png[/IMG]

---

### Post by drs305 on 2009-12-21
> **chumchum said:**
> Well reinstalling grub didn't help so I'll try a fresh install...eehhh, not sure what to do now, any help please?
[IMG]http://img694.imageshack.us/img694/4483/screenshotinstall.png[/IMG]

If you don't have anything on the current Ubuntu install you want to save, I'd delete the partition and the swap partition with Gparted from the LiveCD (to delete the swap partition, you need to turn off swap. Select the swap partition, then Partition, Swapoff).

Afterward, you will have sdb1 and unallocated space. Then you can install and tell it to use the unallocated space. This way you won't end up with two Ubuntu installs on your system.

If you have *anything* on the current Ubuntu partition you want to save, copy it elsewhere before doing this, of course.

---

### Post by kansasnoob on 2009-12-21
> **drs305 said:**
> I checked and it appears that ms-sys is no longer in the repositories. But you can get the .deb package from here for 32-bit systems:
[http://packages.debian.org/etch/i386/ms-sys/download]("http://packages.debian.org/etch/i386/ms-sys/download")

It will download to your Desktop - double-click to install it on 32-bit machines.

Here is the link for 64-bit machines:
[http://packages.debian.org/etch/amd64/ms-sys/download]("http://packages.debian.org/etch/amd64/ms-sys/download")

The new package is mbr!

So you'd:

```
sudo apt-get install mbr
```

I think prior to Jaunty (possibly Karmic) you have to enable the universe or multiverse repo. Then:

```
sudo install-mbr /dev/sdX
```

Where X is the proper destination.

---

