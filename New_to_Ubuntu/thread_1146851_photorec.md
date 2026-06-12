---
title: "photorec"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by sekani on 2009-05-03
i have downloaded testdisk/photorec 6.11.2 from CG security but am unable to open it,i get this message....."/home/dean/testdisk-6.11.2/linux/l/linux".could not display.there is no application installed for this device...what am i doing wrong?. i am using ubuntu 8.10...thanks

---

### Post by logos34 on 2009-05-03
no, all you do is

> sudo apt-get install testdisk\

(make sure **universe** repo is enabled)

PhotoRec is included

apt-cache show testdisk

man photorec

good luck

---

### Post by sekani on 2009-05-03
thanks for the reply,i entered the command as you suggested and got this message.... dean@dean-desktop:~$ sudo apt-get install testdisk 
[sudo] password for dean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  testdisk
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1225kB of archives.
After this operation, 1155kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid/universe testdisk 6.9-1.1 [1225kB]
Fetched 1225kB in 12s (102kB/s)                                                
(Reading database ... 117127 files and directories currently installed.)
Preparing to replace testdisk 6.8-1 (using .../testdisk_6.9-1.1_i386.deb) ...
Unpacking replacement testdisk ...
Processing triggers for man-db ...
Setting up testdisk (6.9-1.1) ...
dean@dean-desktop:~$ apt-cache show testdisk
Package: testdisk
Priority: optional
Section: universe/admin
Installed-Size: 3768
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Jean-Michel Kelbert <kelbert@debian.org>
Architecture: i386
Version: 6.9-1.1
Depends: e2fslibs, libc6 (>= 2.4), libcomerr2 (>= 1.33-3), libjpeg62, libncursesw5 (>= 5.6+20071006-3), libntfs10 (>= 2.0.0), libuuid1
Filename: pool/universe/t/testdisk/testdisk_6.9-1.1_i386.deb
Size: 1224820
MD5sum: e4234b672ecd7cd5832c03d2dd219562
SHA1: 6bd14d78f15c2fe3106c25a55f7012a35affb79d
SHA256: e6372b942eade674b1c44b57c9fccfba44fc04eea2fbb3cee3e59e8e5db8042c
Description: Partition scanner and disk recovery tool
  TestDisk checks the partition and boot sectors of your disks.
  It is very useful in recovering lost partitions.
  It works with :
  * DOS/Windows FAT12, FAT16 and FAT32
  * NTFS ( Windows NT/2K/XP )
  * Linux Ext2 and Ext3
  * BeFS ( BeOS )
  * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
  * CramFS (Compressed File System)
  * HFS and HFS+, Hierarchical File System
  * JFS, IBM's Journaled File System
  * Linux Raid
  * Linux Swap (versions 1 and 2)
  * LVM and LVM2, Linux Logical Volume Manager
  * Netware NSS
  * ReiserFS 3.5 and 3.6
  * Sun Solaris i386 disklabel
  * UFS and UFS2 (Sun/BSD/...)
  * XFS, SGI's Journaled File System
  .
  PhotoRec is file data recovery software designed to recover
  lost pictures from digital camera memory or even Hard Disks.
  It has been extended to search also for non audio/video headers.
  It searchs for
  * Sun/NeXT audio data (.au)
  * RIFF audio/video (.avi/.wav)
  * BMP bitmap (.bmp)
  * bzip2 compressed data (.bz2)
  * Source code written in C (.c)
  * Canon Raw picture (.crw)
  * Canon catalog (.ctg)
  * FAT subdirectory
  * Microsoft Office Document (.doc)
  * Nikon dsc (.dsc)
  * HTML page (.html)
  * JPEG picture (.jpg)
  * MOV video (.mov)
  * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
  * Moving Picture Experts Group video (.mpg)
  * Minolta Raw picture (.mrw)
  * Olympus Raw Format picture (.orf)
  * Portable Document Format (.pdf)
  * Perl script (.pl)
  * Portable Network Graphics (.png)
  * Raw Fujifilm picture (.raf)
  * Contax picture (.raw)
  * Rollei picture (.rdc)
  * Rich Text Format (.rtf)
  * Shell script (.sh)
  * Tar archive (.tar )
  * Tag Image File Format (.tiff)
  * Microsoft ASF (.wma)
  * Sigma/Foveon X3 raw picture (.x3f)
  * zip archive (.zip)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

so i assume photorec is installed,how can i open the programme? do i need to select the programme or will it happen automatically? what is universe and how do i open?...thanks for your help

---

### Post by bumanie on 2009-05-03
To use testdisk>  sudo testdisk to use photorec > sudo photorecin terminal

---

### Post by sekani on 2009-05-04
thanks bumanie for the reply, i now have photorec working but i have another problem...on the opening page under 'select a media' it is not showing my cd-rom drive,i only have disk/dev/sda 250gb drive showing!  i do have the cd-rw with the lost photos on that i am trying to recover in the drive. the cd drive desk top icon is saying that a blank cd-rw disc is in the drive.

---

