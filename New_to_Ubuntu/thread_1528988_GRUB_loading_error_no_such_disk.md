---
title: "GRUB loading error: no such disk"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-11
I'm trying to install 9.10 on a second internal HD. I thought everything was working this time (which is about the 5th try), but when the computer restarted, I got the following error message:

GRUB loading error
No such disk
GRUB rescue>

I'm now on the live CD and here's what's going on:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051    7  HPFS/NTFS
/dev/sda2            9542        9726     1486012+   5  Extended
/dev/sda5            9542        9726     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x206e7510

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9541    76638051   83  Linux
/dev/sdb2            9542        9726     1486012+   5  Extended
/dev/sdb5            9542        9726     1485981   82  Linux swap / Solaris
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

The machine is a Dell Dimension 2400 with winXP on the main HD. I've looked through all the other threads on this topic and I still can't figure out what I'm supposed to do to fix this. Any help would be greatly appreciated.

---

### Post by oldfred on 2010-07-11
Did you try booting the other drive. This script will tell where everything is installed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Also this link may have info:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by Chris1274 on 2010-07-11
I was just about to post the boot script when the CD locked up on me. Now I can't get a GUI when I reboot from it. I'm going to burn another CD and (hopefully) post the script for you soon.

---

### Post by Chris1274 on 2010-07-11
.

---

### Post by Chris1274 on 2010-07-11
OK, here's the boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=a6fff40c-0e71-47c0-a700-521606f5cf4b)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,276,164   153,276,102   7 HPFS/NTFS
/dev/sda2         153,276,165   156,248,189     2,972,025   5 Extended
/dev/sda5         153,276,228   156,248,189     2,971,962  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x206e7510

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   153,276,164   153,276,102  83 Linux
/dev/sdb2         153,276,165   156,248,189     2,972,025   5 Extended
/dev/sdb5         153,276,228   156,248,189     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        D22C9F9E2C9F7C63                       ntfs                                     
/dev/sda5        d6b897c5-f7e7-4c5d-a1f1-cc1dfc5b7652   swap                                     
/dev/sdb1        a6fff40c-0e71-47c0-a700-521606f5cf4b   ext4                                     
/dev/sdb5        72f81a74-ab49-4807-8b7a-c35cf67fbb6f   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set a6fff40c-0e71-47c0-a700-521606f5cf4b
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set a6fff40c-0e71-47c0-a700-521606f5cf4b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a6fff40c-0e71-47c0-a700-521606f5cf4b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set a6fff40c-0e71-47c0-a700-521606f5cf4b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a6fff40c-0e71-47c0-a700-521606f5cf4b ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d22c9f9e2c9f7c63
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a6fff40c-0e71-47c0-a700-521606f5cf4b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=72f81a74-ab49-4807-8b7a-c35cf67fbb6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .2GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: initrd.img
    .2GB: vmlinuz

```

---

### Post by Chris1274 on 2010-07-11
I'm unable to boot from the second HD. It doesn't give me that option in the boot menu.

---

### Post by wilee-nilee on 2010-07-11
Just install grub2 to sdb=MBR of the second HD, use this link to do this from a live CD of karmic or later.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Then put sdb 1st to be read in bios, run the update-grub when you get in. If you want to put the MS bootloader back in the mbr=sda you just need a xp install disc and a command line of fixmbr
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Grub2 should install and show you xp and Ubuntu at grub.

You also have a extended and swap in sda that you probably don't need.

Always check the advanced button on a install, last gui for where grub is pointed, should be at the mbr of the HD your installing to.

[COLOR="Red"]Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=a6fff40c-0e71-47c0-a700-521606f5cf4b)/boot/grub.[/COLOR]

This is reading the correct uuid but on the wrong HD,

---

### Post by oldfred on 2010-07-11
+1 for wilee-nilee's suggestions

Karmic 9.10 had bigger issues with grub2 not on the same drive as the install. I prefer to have grub on the same drive anyway as then you do not have to have both drives working just to boot.

---

### Post by Chris1274 on 2010-07-11
The problem remains. Here's what I did so far.

```
sudo mount /dev/sdb1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sdb
```

When I restarted I got the same error message.

When I try to reconfigure the setup to read sdb first, I'm unable to do so. The boot sequence options consist only of the CD-ROM device and the C: drive. Is the BIOS just not seeing the second HD or something?

---

### Post by oldfred on 2010-07-11
Does the BIOS show both drives. It just about has to or you could not install grub to sdb.

BIOS usually has two settings. One is HD, CD, Floppy etc. Most seem to then have a separate setting for which HD is first in the HD choice. Also you may have another single boot choice, my system it is f12 and if I choose HD then it opens another window on which HD.

---

### Post by Chris1274 on 2010-07-11
Here's what my bios setup tells me ...

Under boot sequence, I have:

1. IDE CD-ROM Device
2. Hard-Disk Drive C:
3. Floppy device

Under drive configuration, I have:

Diskette Drive A: ... 3.5 inch, 1.44 MB
Primary Master Drive ... Hard Drive
Primary Slave Drive ... OFF
Secondary Master Drive ... CD-ROM Device
Secondary Slave Drive ... OFF
IDE Drive UDMA ... ON

For the primary slave drive, I can toggle between 'off' and 'auto', which I tried on a previous installation and it really messed things up. I thought I destroyed the computer. Anyway, I'm unable to see anything that corresponds to sdb. Am I missing something?

---

### Post by oldfred on 2010-07-11
That is saying you only have one drive.

Do you have three color connectors (80 wire) cables to your drives or the 40 conductor cables. With the 80 conductors you set drive jumpers on hard drive to cable select. With 40 conductor you have to set the jumpers to master or slave. Some drives also have jumper for master with slave. Either label or vendors site should give you details on settings. Then in BIOS it should work. (SATA is a lot easier).

[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://www.kitchentablecomputers.com/hdrive3.php](http://www.kitchentablecomputers.com/hdrive3.php)

---

### Post by Chris1274 on 2010-07-11
I have the 40 conductor cables. They were arranged in an odd way (my brother installed the second HD initially). There was one cable from the main HD to the primary IDE plug in the motherboard, then a second cable from the secondary IDE plug went to the optical drive (as drive 0) and then to the second HD (as drive 1). I tried taking that second cable and plugging it into the primary IDE mount and making the main HD drive 0 and the second HD drive 1, setting the jumpers as "master" and "slave" respectively. That didn't work, the BIOS still didn't see the second drive. I gave up after that and just did "fixmbr" on the main HD so I can at least start up winXP.

---

### Post by Chris1274 on 2010-07-12
The problem turned out to be one with the IDE cables and not with Ubuntu after all. Once I got the cables arranged in the correct way, I reinstalled 9.1 on the slave HD and everything worked perfectly. No need to tweak the GRUB loader or anything.

---

