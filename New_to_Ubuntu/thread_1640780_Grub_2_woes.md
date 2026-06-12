---
title: "Grub 2 woes"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2010-12-08
In short: I need to reinstall GRUB 2. On startup I get a black screen.

Background: Used to have 3 partitions excluding swap - Ubuntu on sda2, Windows 7 on sda3 and "Stuff" (a mutual file storage partition formatted to NTFS) on sda1. 

Got rid on Windows 7, installed "MeeGo" instead (just to try it out, I'm trying Jolicloud next and then maybe UNR). After install I got an option to use MeeGo's boot loader or the currently installed one. I pressed currently installed. Restarted, no GRUB, straight into MeeGo. Booted from a LiveCD, gave the boot flag to Ubuntu instead to see if that had any effect - it gave me "No bootable partition found". Back into LiveCD, reinstalled GRUB using the following: 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd91ac89e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7343       19326    96261480    7  HPFS/NTFS
/dev/sda2   *           1        1958    15727603+  83  Linux
/dev/sda3            1959        7342    43246980   83  Linux
/dev/sda4           19327       19457     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031274496 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d913c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1015     1006849    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

Now upon booting I get a black screen, nothing else. Possibly a blinking _ cursor for a fraction of a second. 

After writing this I'll try giving MeeGo the boot flag again and seeing what happens (I remember Windows 7 had it previously, but it shouldn't matter because GRUB is installed to the MBR right? Not completely sure how it works), then I'll try installing GRUB 2 in the MeeGo partition. 

MeeGo could use grub-legacy, but seeing as I chose the use current boot loader I have no idea why it would change. "grub-install -v" gives me 1.98 anyway so GRUB 2 is installed.

Help would be much appreciated, I'll let you know how it goes.

---

### Post by sikander3786 on 2010-12-08
It would be better to post the output of bootinfoscript as per instructinons here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better advise your setup and thus advise efficiently ;-)

> ubuntu@ubuntu:~$ sudo update-grub

This commands needs to be run from the Ubuntu install not from the Live CD.

---

### Post by drs305 on 2010-12-08
You can try to completely purge and reinstall Grub 2 using this guide:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

This will remove and reinstall the grub-common and grub-pc packages. grub-install will write to the MBR and regenerate core.img, but the above will completely replace any missing or corrupted grub files.

---

### Post by Jakey_TheSnake on 2010-12-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  MeeGo release 1.1 (MeeGo) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         117,949,230   310,472,189   192,522,960   7 HPFS/NTFS
/dev/sda2    *             63    31,455,269    31,455,207  83 Linux
/dev/sda3          31,455,270   117,949,229    86,493,960  83 Linux
/dev/sda4         310,472,190   312,576,704     2,104,515  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031274496 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2014208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     2,013,759     2,013,698   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3085C79157C2FF5D                       ntfs       Stuff                         
/dev/sda2        3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d   ext4                                     
/dev/sda3        99fb5c6c-63aa-4731-bab3-ed53b58c3b1c   ext3       netbook-ia32-x86              
/dev/sda4        b48a3be8-4171-4b0c-8052-749671f5eba6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        596E-4AD2                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /mnt                     ext4       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2548b97f02cbdf48
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda2 :
UUID=3fdc6c21-69e4-4fe9-b92d-0da4ca9b268d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=3085C79157C2FF5D	/media/Stuff	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=78D6D8317F15A3A3	/media/WD1TB	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.utf8	0	0
#Entry for /dev/sda3 :
UUID=2548B97F02CBDF48	/media/Win7	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda4 :
UUID=b48a3be8-4171-4b0c-8052-749671f5eba6	none	swap	sw	0	0



=================== sda2: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
  11.2GB: boot/grub/grub.cfg
  15.6GB: boot/initrd.img-2.6.32-24-generic
   8.1GB: boot/initrd.img-2.6.35-22-generic
   5.2GB: boot/vmlinuz-2.6.32-24-generic
   8.9GB: boot/vmlinuz-2.6.35-22-generic
   8.1GB: initrd.img
  15.6GB: initrd.img.old
   8.9GB: vmlinuz
   5.2GB: vmlinuz.old

=============================== sda3/etc/fstab: ===============================


#
# /etc/fstab
# Created by installer on Wed Dec  8 10:08:31 2010
#
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/sda3               /                       ext3    defaults        1 1
/dev/sda4               swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda3: Location of files loaded by Grub: ===================


  16.8GB: boot/vmlinuz-2.6.35.3-10.3-netbook
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 00 00 00  |.X.SYSLINUX.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  08 cb 27 05 00 00 00 00  00 00 00 00 00 00 00 00  |..'.............|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 fa fc 31 c9 8e d1  |............1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 00 80 7b 00  66 ba 00 00 00 00 bb 00  |}.f...{.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e bd 19 9b 72 75 71 ea  |~...f.>$~...ruq.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 26 66 52 66 50 06  53 6a 01 6a 10 89 e6 b4  |..&fRfP.Sj.j....|
00000140  42 e8 7c 00 8d 64 10 72  01 c3 66 60 31 c0 cd 13  |B.|..d.r..f`1...|
00000150  66 61 e2 df c6 06 32 7d  26 66 60 66 0f b7 36 18  |fa....2}&f`f..6.|
00000160  7c 66 0f b7 3e 1a 7c 66  f7 f6 31 c9 87 ca 66 f7  ||f..>.|f..1...f.|
00000170  f7 66 3d ff 03 00 00 77  17 c0 e4 06 41 08 e1 88  |.f=....w....A...|
00000180  c5 88 d6 b8 01 02 e8 37  00 66 61 72 01 c3 e2 c9  |.......7.far....|
00000190  31 f6 8e d6 bc 6c 7b 8e  de 66 8f 06 78 00 be cb  |1....l{..f..x...|
000001a0  7d e8 09 00 31 c0 cd 16  cd 19 f4 eb fd 66 60 ac  |}...1........f`.|
000001b0  20 c0 74 09 b4 0e bb 07  00 cd 10 eb f2 66 61 c3  | .t..........fa.|
000001c0  8a 16 74 7b 66 60 cd 13  66 61 c3 42 6f 6f 74 20  |..t{f`..fa.Boot |
000001d0  65 72 72 6f 72 0d 0a 00  00 00 00 00 00 00 00 00  |error...........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2010-12-08
Jakey_TheSnake,

**Added:** See *sikander3786*'s suggestion first.


I don't know what MeeGo is so I can't comment on that. Your Windows partition has no boot files in it. If you have a valid Windows OS on sda1 you will need to run the Windows repair CD and restore your Windows boot files (fixmbr, fixboot, etc).
See *oldfred's* Post #7 at this link for Windows repair links:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

As far as Grub2 goes, I don't see problems so if it's not working and you haven't tried the purge/reinstall solution that is what I'd try.

I can't comment on MeeGo...

---

### Post by sikander3786 on 2010-12-08
I think sda1 is not your Windows partition any more and you've just formatted it NTFS for data etc. Right?

Grub seems pretty ok to me. That blinking cursor problem might be being caused by your graphics card.

Try to press and hold down Shift key from Bios screen until Grub menu pops up. Highlighting the first entry, press 'e' to edit it. Navigate to words "quiet and splash", delete them and type "nomodeset" instead. Press Ctrl + X to continue booting. Lets see how far that goes.

And please list your graphics card in your next post ;-)

---

### Post by drs305 on 2010-12-08
> **sikander3786 said:**
> Grub seems pretty ok to me. That blinking cursor problem might be being caused by your graphics card.

And please list your graphics card in your next post ;-)

Yes, I'd agree with this. If you can call up your Grub menu by holding down the SHIFT key and select an item, and then it continues to a flashing single cursor the problem is not with Grub2.

If you have an nvidia card the 'nomodeset' advice given by *sikander3786* will probably get you to the Desktop and allow you to install the nvidia driver.

---

### Post by Jakey_TheSnake on 2010-12-08
Error configuring grub-pc/common:

```
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 216 not upgraded.
After this operation, 5,804kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 137864 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 216 not upgraded.
Need to get 0B/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 137585 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/# dpkg-reconfigure grub-pc
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
root@ubuntu:/# ls
bin    dev   initrd.img      lost+found  opt   sbin	sys  var
boot   etc   initrd.img.old  media	 proc  selinux	tmp  vmlinuz
cdrom  home  lib	     mnt	 root  srv	usr  vmlinuz.old

```

There is no problem outside of GRUB as I haven't changed any hardware or my Ubuntu partition since before it hasn't worked, i.e. it's always worked before. Also the "Windows 7" partition has no OS on it, it's just NTFS file storage. I ls'd to prove it's mounted. Attached is an image of one of the screens I get when trying to install/reconfigure GRUB - odd because legacy has never been installed on this partition and should have just been purged?

I have sometimes encountered this error too, no idea when:```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

I don't get a GRUB menu, that's the problem. Nothing. 

Gfx card: 

```
root@ubuntu:/# lspci | grep VGA
pcilib: Cannot open /proc/bus/pci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

```

---

### Post by Quackers on 2010-12-08
Hi, can you tell me please which of these commands did you run?
```
sudo mkdir /mnt/temp /mnt/temp/boot
sudo mount /dev/sdXY /mnt/temp  # Example:  sudo mount/dev/sda5  /mnt/temp
sudo mount /dev/sdXZ /mnt/temp/boot # Only if you have a separate /boot partition. Example:  sudo mount /dev/sda6 /mnt/temp/boot
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

---

### Post by Jakey_TheSnake on 2010-12-08
Only the ones I was supposed to *shrug*

```
sudo mkdir /mnt/temp /mnt/temp/boot
sudo mount /dev/sda2 /mnt/temp
sudo chroot /mnt/temp
```

All returned no errors; I was able to get the root@ubuntu prompt. I didn't bother with the network one as mine is working fine, hence this very post. 

Thanks.

---

### Post by Quackers on 2010-12-08
Not quite I'm afraid.
The commands should have been```
sudo mkdir /mnt/temp 
sudo mount /dev/sda2 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  
sudo chroot /mnt/temp
```
I will message drs305 and ask him if the first line is correct or not but I think the first line I have given you above is what you need.
You also seem to have missed the third line completely. I understand why, as it seems like a strangely formatted line, but that is correct. It mounts certain directories needed to do what you want to.
The fourth line probably isn't needed - but it could be.

---

### Post by Jakey_TheSnake on 2010-12-08
> **Quackers said:**
> Not quite I'm afraid.
The commands should have been```
sudo mkdir /mnt/temp 
sudo mount /dev/sda2 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  
sudo chroot /mnt/temp
```
I will message drs305 and ask him if the first line is correct or not but I think the first line I have given you above is what you need.
You also seem to have missed the third line completely. I understand why, as it seems like a strangely formatted line, but that is correct. It mounts certain directories needed to do what you want to.
The fourth line probably isn't needed - but it could be.

Ah, that's perfectly correct and all is in working order now. 

I didn't realise "for" was a command, so I just read it as a continuation of the commented out part of the line above, thus ignored it. I forgot that in [code] tags the text doesn't automatically continue on the next line but instead adds a sideways scroll bar. 

A foolish error, but an easily avoidable one. Maybe a small comment could be inserted into the howto, but I have no idea who would have sufficient privileges to do that. 

Thread marked as solved nonetheless.

---

### Post by Quackers on 2010-12-08
I made the same mistake when the guide was first changed :-) We live and learn!
Glad you're all fixed up now - nice one!

---

### Post by sikander3786 on 2010-12-09
So, the error was with Grub and not with the graphics card or so. Never mind.

Glad to know that it has been fixed. **drs305** have covered nearly every single aspect of Grub2 and **Quackers** were experienced enough to guide you with that.

Most of the time, it takes many of us to figure out the problem ;-)

Happy Ubuntu-ing!

---

### Post by drs305 on 2010-12-09
Making a "/mnt/boot" mountpoint doesn't hurt anything and saves a step but I can see how it might add to the confusion and have reformatted the steps and added a note about who needs to run it.

Regarding the "for i in ..." command, it had never occurred to me that it could be regarded in the way it was - but it re-emphasizes how we see can things differently. I'll have to figure out how I'm going to prevent that from happening again. There is a much longer way of writing the commands out but this is just too efficient to give up. I guess I'll add a note.

Thanks for the feedback.

---

### Post by QLee on 2010-12-09
[QUOTE=drs305]...
Regarding the "for i in ..." command, it had never occurred to me that it could be regarded in the way it was - but it re-emphasizes how we see can things differently. I'll have to figure out how I'm going to prevent that from happening again. There is a much longer way of writing the commands out but this is just too efficient to give up. I guess I'll add a note.[/QUOTE]

That efficiency is effective for the audience who just cut-and-paste commands from a trusted source as yourself. However, the long form is somewhat more clear for users who are trying to understand what is going on and who aren't coders. Maybe a brief mention of why the chroot needs access to the devices on the system could be added for clarity. And/or simple explanation of what the code does. I know there is always a trade off between keeping it simple and giving opportunities to learn, your guides are always good in terms of content.

---

### Post by Quackers on 2010-12-09
The "for" command saves a serious amount of typing (or copy/pasting) it's a great line. It just looks weird to the more inexperienced, like me :-)
Using as little as 3 lines instead of 7 is definitely preferrable, even when copy/pasting.

---

### Post by drs305 on 2010-12-09
I've added a section at the bottom of the post showing what the "for i" command does. :-)

---

