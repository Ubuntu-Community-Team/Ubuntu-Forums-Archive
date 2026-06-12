---
title: "Installation problem"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-06-11
Having given up with 11.04 (wouldn't open or shut down properly) I thought I'd go for 10.10 64 bit which worked fine from the CD.

Nearly reached the end of the installation then came up with an error message;-
"*An error occurred not possible to install boot loader*"
Tried other options in the box then install without bootloader but then everything had frozen.

What should I have done at that stage?

My setup is below except I have a 1.85 gig partition at hte end designated as swap.

Disk /dev/sda: 200.0 GB, 200049647616 bytes  
 255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x8a45b80b  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1              63    83955689    41977813+  1c  Hidden W95 FAT32 (LBA)  
 /dev/sda2   *    83955690   167493689    41769000    c  W95 FAT32 (LBA)  
 /dev/sda3       167493690   237135464    34820887+   c  W95 FAT32 (LBA)  
 /dev/sda4       237135465   390716864    76790700    f  W95 Ext'd (LBA)  
 /dev/sda5       237135528   286278299    24571386    b  W95 FAT32  
 /dev/sda6       286278363   390716864    52219251    7  HPFS/NTFS

---

### Post by VOT Productions on 2011-06-11
Do you get GRUB already if you startup your computer? If so, don't install the bootloader.

---

### Post by wildmanne39 on 2011-06-11
> **Mccfuzz said:**
> Having given up with 11.04 (wouldn't open or shut down properly) I thought I'd go for 10.10 64 bit which worked fine from the CD.

Nearly reached the end of the installation then came up with an error message;-
"*An error occurred not possible to install boot loader*"
Tried other options in the box then install without bootloader but then everything had frozen.

What should I have done at that stage?

My setup is below except I have a 1.85 gig partition at hte end designated as swap.

Disk /dev/sda: 200.0 GB, 200049647616 bytes  
 255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Disk identifier: 0x8a45b80b  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1              63    83955689    41977813+  1c  Hidden W95 FAT32 (LBA)  
 /dev/sda2   *    83955690   167493689    41769000    c  W95 FAT32 (LBA)  
 /dev/sda3       167493690   237135464    34820887+   c  W95 FAT32 (LBA)  
 /dev/sda4       237135465   390716864    76790700    f  W95 Ext'd (LBA)  
 /dev/sda5       237135528   286278299    24571386    b  W95 FAT32  
 /dev/sda6       286278363   390716864    52219251    7  HPFS/NTFS
Hi, well all your patitions are window partitions, you did not create any for ubuntu which should have been ext4. Aslo you may have to many primary partitions already.
Boot with the livecd and post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Mccfuzz on 2011-06-11
> **wildmanne39 said:**
> Hi, well all your patitions are window partitions, you did not create any for ubuntu which should have been ext4. Aslo you may have to many primary partitions already.
Boot with the livecd and post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Hi thanks for the replies.

I should have explained better.  The list I gave was how my computer was partitioned prior to trying Ubuntu 10.04 which was functioning perfectly on SDA2.
I was then lured into trying 11.04 AMD 64 bit which sort of worked but with shutdown problems so I then tried to install 10.10 64 bit with which I've hit the above problem.

In the mean time I'll look into'bootinfo script.

Thanks...Mccfuzz

---

### Post by Mccfuzz on 2011-06-11
Hi Again

I think this is what you requested.
Some of the info there also relates to a second hard drive and maybe also a USB stick.

The info:-
============================ Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb5 starts at sector 240220008. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *         16,065    80,292,869    80,276,805   f W95 Extended (LBA)
Empty Partition.
/dev/sda5              32,193    80,292,869    80,260,677   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    84,983,849    84,983,787  1c Hidden W95 FAT32 (LBA)
/dev/sdb2          84,983,850   169,550,009    84,566,160  83 Linux
/dev/sdb3    *    169,550,010   240,219,944    70,669,935   c W95 FAT32 (LBA)
/dev/sdb4         240,220,006   390,716,864   150,496,859   f W95 Extended (LBA)
/dev/sdb5         240,220,008   285,266,204    45,046,197   b W95 FAT32
/dev/sdb6         285,266,268   387,793,034   102,526,767   7 NTFS / exFAT / HPFS
/dev/sdb7         387,793,098   390,716,864     2,923,767  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.4 GB, 15352725504 bytes
61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,064    29,985,791    29,977,728   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        FAB1-2002                              vfat       DRIVE TWO
/dev/sdb1        2940-DBAB                              vfat       INTERNET
/dev/sdb2        28ae00a4-2fec-47e0-827d-f4ced4433c9d   ext4       
/dev/sdb3        1966-DD90                              vfat       EBAY P2P
/dev/sdb5        4565-77FD                              vfat       BACKUP DRIV
/dev/sdb6        42DC5149DC51387D                       ntfs       Shared Docs
/dev/sdb7        1bdb7a63-b579-4d6e-be10-304962df81f4   swap       
/dev/sdc1        418A-3271                              vfat       USB2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/USB2              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.838509560 = 45.997499392   boot/grub/core.img                             1
  41.312417030 = 44.358870016   boot/initrd.img-2.6.35-22-generic              1
  42.804066658 = 45.960516608   boot/vmlinuz-2.6.35-22-generic                 1
  41.312417030 = 44.358870016   initrd.img                                     1
  42.804066658 = 45.960516608   vmlinuz                                        1

================================ sdb3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  cb 3b d7 fa ab d1 93 b0  de 75 4d 63 56 6b b6 4e  |.;.......uMcVk.N|
00000010  8b 7b be d2 2d 0e ab 88  5d dd 95 0b 78 1d 03 28  |.{..-...]...x..(|
00000020  e1 f7 ec dd 28 14 af 6d  32 89 82 68 94 01 c9 2a  |....(..m2..h...*|
00000030  1e 25 f1 98 b3 17 37 7e  e8 e4 07 a1 99 ff 98 ee  |.%....7~........|
00000040  fc 53 94 1f 4b 83 09 68  20 7a f8 eb 32 2b 8a 13  |.S..K..h z..2+..|
00000050  f7 99 3b 9c ff f4 34 73  cd 95 de 3f e9 2e e7 91  |..;...4s...?....|
00000060  fc 9b e1 a0 2f 4d 1a b5  b8 db cd e6 a5 b4 36 19  |..../M........6.|
00000070  3d 57 3c 7c ed e9 67 d4  1c ed ae 2b 00 58 2d 53  |=W<|..g....+.X-S|
00000080  ed e7 04 ba 20 a6 fe c1  0d 7d 5b 8c ae 04 0d b3  |.... ....}[.....|
00000090  66 85 52 90 d6 28 62 87  24 f6 9c cc e5 a0 8e 51  |f.R..(b.$......Q|
000000a0  a5 2c 33 14 3e ba 57 8a  aa 3c a8 46 72 55 4f 4b  |.,3.>.W..<.FrUOK|
000000b0  90 e4 d2 b7 2c 81 ed 02  f7 66 1c 02 47 40 62 60  |....,....f..G@b`|
000000c0  f5 5c 4e 14 b2 a9 64 87  bc 00 06 97 98 66 0d 7e  |.\N...d......f.~|
000000d0  79 55 57 82 86 f1 ff ee  5c bf 4f 25 e6 6e 3b 9c  |yUW.....\.O%.n;.|
000000e0  67 b0 df a7 ee ed bb 44  cb 3d 85 73 c9 b3 60 5e  |g......D.=.s..`^|
000000f0  d7 f9 1c 5e 9b 3d 0b c0  b9 38 51 5f 19 94 b3 7b  |...^.=...8Q_...{|
00000100  16 50 b1 01 ad 47 7b 95  b5 10 2f d5 39 60 d2 63  |.P...G{.../.9`.c|
00000110  2e 58 de 1d 0d cc 17 e0  99 71 74 cc 5c 87 e7 bd  |.X.......qt.\...|
00000120  99 96 48 7b 8e 85 c9 8c  a7 fe ba 03 d0 59 fc 23  |..H{.........Y.#|
00000130  d9 0c 22 33 7e ad 6f 34  3d 2d 31 68 df d9 ea 0f  |.."3~.o4=-1h....|
00000140  b1 84 10 8f 51 72 f0 7d  4c 09 a9 bd 82 ce 62 e9  |....Qr.}L.....b.|
00000150  3f 44 fe a4 a3 5f 36 b3  c3 e5 8d a3 4d 7e bb 01  |?D..._6.....M~..|
00000160  5f 6b 27 4a f0 29 57 4c  97 bb 4b b6 c5 be c5 e7  |_k'J.)WL..K.....|
00000170  ee 18 2c 2a 46 67 28 89  db 3a fd 7f 93 ac 2b 89  |..,*Fg(..:....+.|
00000180  ef 54 ea 83 97 22 8c f1  34 14 4f fe 53 61 7d 7a  |.T..."..4.O.Sa}z|
00000190  be e7 31 64 38 0c 43 58  81 fc d6 61 29 73 5e 0e  |..1d8.CX...a)s^.|
000001a0  92 33 42 ae 2c 67 74 09  ce e6 99 98 6b 71 2d 47  |.3B.,gt.....kq-G|
000001b0  d9 9d 5e 59 c7 7b ba 39  44 b7 e6 f6 dd 8c 00 01  |..^Y.{.9D.......|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 b5 59 af 02 00 fe  |...........Y....|
000001d0  ff ff 05 fe ff ff b7 59  af 02 6e 6f 1c 06 00 00  |.......Y..no....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Message```

```

---

### Post by wildmanne39 on 2011-06-11
> **Mccfuzz said:**
> Hi Again

I think this is what you requested.
Some of the info there also relates to a second hard drive and maybe also a USB stick.

The info:-
============================ Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb5 starts at sector 240220008. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *         16,065    80,292,869    80,276,805   f W95 Extended (LBA)
Empty Partition.
/dev/sda5              32,193    80,292,869    80,260,677   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    84,983,849    84,983,787  1c Hidden W95 FAT32 (LBA)
/dev/sdb2          84,983,850   169,550,009    84,566,160  83 Linux
/dev/sdb3    *    169,550,010   240,219,944    70,669,935   c W95 FAT32 (LBA)
/dev/sdb4         240,220,006   390,716,864   150,496,859   f W95 Extended (LBA)
/dev/sdb5         240,220,008   285,266,204    45,046,197   b W95 FAT32
/dev/sdb6         285,266,268   387,793,034   102,526,767   7 NTFS / exFAT / HPFS
/dev/sdb7         387,793,098   390,716,864     2,923,767  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.4 GB, 15352725504 bytes
61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,064    29,985,791    29,977,728   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        FAB1-2002                              vfat       DRIVE TWO
/dev/sdb1        2940-DBAB                              vfat       INTERNET
/dev/sdb2        28ae00a4-2fec-47e0-827d-f4ced4433c9d   ext4       
/dev/sdb3        1966-DD90                              vfat       EBAY P2P
/dev/sdb5        4565-77FD                              vfat       BACKUP DRIV
/dev/sdb6        42DC5149DC51387D                       ntfs       Shared Docs
/dev/sdb7        1bdb7a63-b579-4d6e-be10-304962df81f4   swap       
/dev/sdc1        418A-3271                              vfat       USB2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/USB2              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.838509560 = 45.997499392   boot/grub/core.img                             1
  41.312417030 = 44.358870016   boot/initrd.img-2.6.35-22-generic              1
  42.804066658 = 45.960516608   boot/vmlinuz-2.6.35-22-generic                 1
  41.312417030 = 44.358870016   initrd.img                                     1
  42.804066658 = 45.960516608   vmlinuz                                        1

================================ sdb3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  cb 3b d7 fa ab d1 93 b0  de 75 4d 63 56 6b b6 4e  |.;.......uMcVk.N|
00000010  8b 7b be d2 2d 0e ab 88  5d dd 95 0b 78 1d 03 28  |.{..-...]...x..(|
00000020  e1 f7 ec dd 28 14 af 6d  32 89 82 68 94 01 c9 2a  |....(..m2..h...*|
00000030  1e 25 f1 98 b3 17 37 7e  e8 e4 07 a1 99 ff 98 ee  |.%....7~........|
00000040  fc 53 94 1f 4b 83 09 68  20 7a f8 eb 32 2b 8a 13  |.S..K..h z..2+..|
00000050  f7 99 3b 9c ff f4 34 73  cd 95 de 3f e9 2e e7 91  |..;...4s...?....|
00000060  fc 9b e1 a0 2f 4d 1a b5  b8 db cd e6 a5 b4 36 19  |..../M........6.|
00000070  3d 57 3c 7c ed e9 67 d4  1c ed ae 2b 00 58 2d 53  |=W<|..g....+.X-S|
00000080  ed e7 04 ba 20 a6 fe c1  0d 7d 5b 8c ae 04 0d b3  |.... ....}[.....|
00000090  66 85 52 90 d6 28 62 87  24 f6 9c cc e5 a0 8e 51  |f.R..(b.$......Q|
000000a0  a5 2c 33 14 3e ba 57 8a  aa 3c a8 46 72 55 4f 4b  |.,3.>.W..<.FrUOK|
000000b0  90 e4 d2 b7 2c 81 ed 02  f7 66 1c 02 47 40 62 60  |....,....f..G@b`|
000000c0  f5 5c 4e 14 b2 a9 64 87  bc 00 06 97 98 66 0d 7e  |.\N...d......f.~|
000000d0  79 55 57 82 86 f1 ff ee  5c bf 4f 25 e6 6e 3b 9c  |yUW.....\.O%.n;.|
000000e0  67 b0 df a7 ee ed bb 44  cb 3d 85 73 c9 b3 60 5e  |g......D.=.s..`^|
000000f0  d7 f9 1c 5e 9b 3d 0b c0  b9 38 51 5f 19 94 b3 7b  |...^.=...8Q_...{|
00000100  16 50 b1 01 ad 47 7b 95  b5 10 2f d5 39 60 d2 63  |.P...G{.../.9`.c|
00000110  2e 58 de 1d 0d cc 17 e0  99 71 74 cc 5c 87 e7 bd  |.X.......qt.\...|
00000120  99 96 48 7b 8e 85 c9 8c  a7 fe ba 03 d0 59 fc 23  |..H{.........Y.#|
00000130  d9 0c 22 33 7e ad 6f 34  3d 2d 31 68 df d9 ea 0f  |.."3~.o4=-1h....|
00000140  b1 84 10 8f 51 72 f0 7d  4c 09 a9 bd 82 ce 62 e9  |....Qr.}L.....b.|
00000150  3f 44 fe a4 a3 5f 36 b3  c3 e5 8d a3 4d 7e bb 01  |?D..._6.....M~..|
00000160  5f 6b 27 4a f0 29 57 4c  97 bb 4b b6 c5 be c5 e7  |_k'J.)WL..K.....|
00000170  ee 18 2c 2a 46 67 28 89  db 3a fd 7f 93 ac 2b 89  |..,*Fg(..:....+.|
00000180  ef 54 ea 83 97 22 8c f1  34 14 4f fe 53 61 7d 7a  |.T..."..4.O.Sa}z|
00000190  be e7 31 64 38 0c 43 58  81 fc d6 61 29 73 5e 0e  |..1d8.CX...a)s^.|
000001a0  92 33 42 ae 2c 67 74 09  ce e6 99 98 6b 71 2d 47  |.3B.,gt.....kq-G|
000001b0  d9 9d 5e 59 c7 7b ba 39  44 b7 e6 f6 dd 8c 00 01  |..^Y.{.9D.......|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 b5 59 af 02 00 fe  |...........Y....|
000001d0  ff ff 05 fe ff ff b7 59  af 02 6e 6f 1c 06 00 00  |.......Y..no....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Message```

```Hi, I have asked a friend to come and look at your boot script information, he is really good with these issues, and I do not want to make your problem worse, please be patient so he can help you, I am not sure if he is on here right now, but it is better to wait.

---

### Post by Mccfuzz on 2011-06-12
Hi there,

Ok thanks for your efforts

---

### Post by oldfred on 2011-06-12
You have grub2's bootloader installed to the MBR of sda & sdb. The one in sda does not look complete and both are grub 1.99 which is from Natty. If you are using 10.10 Maverick you should have 1.98, so the correct grub never installed. You also are missing grub.cfg so just reinstalling grub2 v1.98's boot loader will not be enough.

You should chroot into your install and reinstall grub2 putting the boot loader into sdb if you BIOS lets you choose which drive to boot. If your system is older (win2000?) is the BIOS new enough to let you choose drives to boot. If you cannot choose drive then you have to install grub2's boot loader to sda.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

The other alternative is to reinstall 10.10 and see if it works correctly on a reinstall.

---

### Post by wildmanne39 on 2011-06-12
> **oldfred said:**
> You have grub2's bootloader installed to the MBR of sda & sdb. The one in sda does not look complete and both are grub 1.99 which is from Natty. If you are using 10.10 Maverick you should have 1.98, so the correct grub never installed. You also are missing grub.cfg so just reinstalling grub2 v1.98's boot loader will not be enough.

You should chroot into your install and reinstall grub2 putting the boot loader into sdb if you BIOS lets you choose which drive to boot. If your system is older (win2000?) is the BIOS new enough to let you choose drives to boot. If you cannot choose drive then you have to install grub2's boot loader to sda.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

The other alternative is to reinstall 10.10 and see if it works correctly on a reinstall.
Hi, thank you for helping out it is much appreciated.

---

### Post by apollothethird on 2011-06-12
> **Mccfuzz said:**
> Hi Again

I think this is what you requested.
Some of the info there also relates to a second hard drive and maybe also a USB stick.

The info:-
```
============================ Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb5 starts at sector 240220008. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *         16,065    80,292,869    80,276,805   f W95 Extended (LBA)
Empty Partition.
/dev/sda5              32,193    80,292,869    80,260,677   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    84,983,849    84,983,787  1c Hidden W95 FAT32 (LBA)
/dev/sdb2          84,983,850   169,550,009    84,566,160  83 Linux
/dev/sdb3    *    169,550,010   240,219,944    70,669,935   c W95 FAT32 (LBA)
/dev/sdb4         240,220,006   390,716,864   150,496,859   f W95 Extended (LBA)
/dev/sdb5         240,220,008   285,266,204    45,046,197   b W95 FAT32
/dev/sdb6         285,266,268   387,793,034   102,526,767   7 NTFS / exFAT / HPFS
/dev/sdb7         387,793,098   390,716,864     2,923,767  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.4 GB, 15352725504 bytes
61 heads, 61 sectors/track, 8058 cylinders, total 29985792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,064    29,985,791    29,977,728   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        FAB1-2002                              vfat       DRIVE TWO
/dev/sdb1        2940-DBAB                              vfat       INTERNET
/dev/sdb2        28ae00a4-2fec-47e0-827d-f4ced4433c9d   ext4       
/dev/sdb3        1966-DD90                              vfat       EBAY P2P
/dev/sdb5        4565-77FD                              vfat       BACKUP DRIV
/dev/sdb6        42DC5149DC51387D                       ntfs       Shared Docs
/dev/sdb7        1bdb7a63-b579-4d6e-be10-304962df81f4   swap       
/dev/sdc1        418A-3271                              vfat       USB2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/USB2              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.838509560 = 45.997499392   boot/grub/core.img                             1
  41.312417030 = 44.358870016   boot/initrd.img-2.6.35-22-generic              1
  42.804066658 = 45.960516608   boot/vmlinuz-2.6.35-22-generic                 1
  41.312417030 = 44.358870016   initrd.img                                     1
  42.804066658 = 45.960516608   vmlinuz                                        1

================================ sdb3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  cb 3b d7 fa ab d1 93 b0  de 75 4d 63 56 6b b6 4e  |.;.......uMcVk.N|
00000010  8b 7b be d2 2d 0e ab 88  5d dd 95 0b 78 1d 03 28  |.{..-...]...x..(|
00000020  e1 f7 ec dd 28 14 af 6d  32 89 82 68 94 01 c9 2a  |....(..m2..h...*|
00000030  1e 25 f1 98 b3 17 37 7e  e8 e4 07 a1 99 ff 98 ee  |.%....7~........|
00000040  fc 53 94 1f 4b 83 09 68  20 7a f8 eb 32 2b 8a 13  |.S..K..h z..2+..|
00000050  f7 99 3b 9c ff f4 34 73  cd 95 de 3f e9 2e e7 91  |..;...4s...?....|
00000060  fc 9b e1 a0 2f 4d 1a b5  b8 db cd e6 a5 b4 36 19  |..../M........6.|
00000070  3d 57 3c 7c ed e9 67 d4  1c ed ae 2b 00 58 2d 53  |=W<|..g....+.X-S|
00000080  ed e7 04 ba 20 a6 fe c1  0d 7d 5b 8c ae 04 0d b3  |.... ....}[.....|
00000090  66 85 52 90 d6 28 62 87  24 f6 9c cc e5 a0 8e 51  |f.R..(b.$......Q|
000000a0  a5 2c 33 14 3e ba 57 8a  aa 3c a8 46 72 55 4f 4b  |.,3.>.W..<.FrUOK|
000000b0  90 e4 d2 b7 2c 81 ed 02  f7 66 1c 02 47 40 62 60  |....,....f..G@b`|
000000c0  f5 5c 4e 14 b2 a9 64 87  bc 00 06 97 98 66 0d 7e  |.\N...d......f.~|
000000d0  79 55 57 82 86 f1 ff ee  5c bf 4f 25 e6 6e 3b 9c  |yUW.....\.O%.n;.|
000000e0  67 b0 df a7 ee ed bb 44  cb 3d 85 73 c9 b3 60 5e  |g......D.=.s..`^|
000000f0  d7 f9 1c 5e 9b 3d 0b c0  b9 38 51 5f 19 94 b3 7b  |...^.=...8Q_...{|
00000100  16 50 b1 01 ad 47 7b 95  b5 10 2f d5 39 60 d2 63  |.P...G{.../.9`.c|
00000110  2e 58 de 1d 0d cc 17 e0  99 71 74 cc 5c 87 e7 bd  |.X.......qt.\...|
00000120  99 96 48 7b 8e 85 c9 8c  a7 fe ba 03 d0 59 fc 23  |..H{.........Y.#|
00000130  d9 0c 22 33 7e ad 6f 34  3d 2d 31 68 df d9 ea 0f  |.."3~.o4=-1h....|
00000140  b1 84 10 8f 51 72 f0 7d  4c 09 a9 bd 82 ce 62 e9  |....Qr.}L.....b.|
00000150  3f 44 fe a4 a3 5f 36 b3  c3 e5 8d a3 4d 7e bb 01  |?D..._6.....M~..|
00000160  5f 6b 27 4a f0 29 57 4c  97 bb 4b b6 c5 be c5 e7  |_k'J.)WL..K.....|
00000170  ee 18 2c 2a 46 67 28 89  db 3a fd 7f 93 ac 2b 89  |..,*Fg(..:....+.|
00000180  ef 54 ea 83 97 22 8c f1  34 14 4f fe 53 61 7d 7a  |.T..."..4.O.Sa}z|
00000190  be e7 31 64 38 0c 43 58  81 fc d6 61 29 73 5e 0e  |..1d8.CX...a)s^.|
000001a0  92 33 42 ae 2c 67 74 09  ce e6 99 98 6b 71 2d 47  |.3B.,gt.....kq-G|
000001b0  d9 9d 5e 59 c7 7b ba 39  44 b7 e6 f6 dd 8c 00 01  |..^Y.{.9D.......|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 b5 59 af 02 00 fe  |...........Y....|
000001d0  ff ff 05 fe ff ff b7 59  af 02 6e 6f 1c 06 00 00  |.......Y..no....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


===============================
``` StdErr Message

Hi, Mccfuzz.  Please... the next time you past output paste it between code tags:

[ code ]  [ /code ]

As above without the spaces.  It'll make your messages easier to read.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Mccfuzz on 2011-06-13
Hi there,

Eventually got the problem sorted.
I had another go at installing today and then I noticed that despite working on the designated partition on my main Sata drive there was a box underneath that had defaulted to my second drive.
I changed this to the SATA drive and it all installed properly this time.

Apologies for time wasting but it's all new to me.

However, I've a new problem now so if research fails I'll be posting again soon.
If you're interested the problem is with the 2nd drive.
I can load files from it but for some unknown reason I can't write to it.
It tells me it's a read only file system.

Once again many thanks.
Mccfuzz :(

---

### Post by Alien74 on 2011-06-13
Can anyone help me out????????????
I'm running BT5 as on my entire HD, but now I want to use Ubuntu with 75% and BT5 with 25%. But when I boot my system it won't read the cd/dvd to install Ubuntu 11.04. Is there a way to install it? thanks a lot an my apologizes for using your thread to post mine.

---

### Post by apollothethird on 2011-06-13
> **Mccfuzz said:**
> Hi there,

Eventually got the problem sorted.
I had another go at installing today and then I noticed that despite working on the designated partition on my main Sata drive there was a box underneath that had defaulted to my second drive.
I changed this to the SATA drive and it all installed properly this time.

Apologies for time wasting but it's all new to me.

However, I've a new problem now so if research fails I'll be posting again soon.
If you're interested the problem is with the 2nd drive.
I can load files from it but for some unknown reason I can't write to it.
It tells me it's a read only file system.

Once again many thanks.
Mccfuzz :(

Hi, Mccfuzz.  Once you have a problem resolved please consider giving back to the forum by marking it solved.  Unless your new problem is directly related to this issue that you said is resolved start a new topic with the new issue with a description that suggests the content.  This way others with similar problems with find it easier to find the resolution.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by nzjethro on 2011-06-13
> **Alien74 said:**
> Can anyone help me out????????????
I'm running BT5 as on my entire HD, but now I want to use Ubuntu with 75% and BT5 with 25%. But when I boot my system it won't read the cd/dvd to install Ubuntu 11.04. Is there a way to install it? thanks a lot an my apologizes for using your thread to post mine.

Why not post a new thread, instead of hijacking others'? You'll get more help that way. I'd recommend changing your boot order in your BIOS menu (hit F2, or esc, or whatever when the BIOS starts up). But post this question in a new thread, you'll get more info, and it helps the community if other people run into the same problem. To start a new thread, go to the Ubuntu Forums home, click on your category (probably Unstall & Upgrades) then click New Thread.

---

### Post by wildmanne39 on 2011-06-13
> **Mccfuzz said:**
> Hi there,

Eventually got the problem sorted.
I had another go at installing today and then I noticed that despite working on the designated partition on my main Sata drive there was a box underneath that had defaulted to my second drive.
I changed this to the SATA drive and it all installed properly this time.

Apologies for time wasting but it's all new to me.

However, I've a new problem now so if research fails I'll be posting again soon.
If you're interested the problem is with the 2nd drive.
I can load files from it but for some unknown reason I can't write to it.
It tells me it's a read only file system.

Once again many thanks.
Mccfuzz :(
Hi, you will need to change permissions to allow you to write to that drive, here is how I changed mine.
```
 sudo chown -R username:username /media/music

```your /media/music will be /media/whatever your file is called on that disk, that should give you access. If you need more help go ahead and start another thread and mark this one solved by using thread tools at the top of the page.

---

### Post by oldfred on 2011-06-13
wildmanne39's instructions are good if you partition is a Linux format as that supports permissions & ownership. But if it is one of the NTFS partition you only set permissions and ownship at time of mounting. If part of internal drive best to modify fstab and permanently mount. I also noticed you are mounting root with a device (/dev/sdb2) not by UUID. It is usually best to use UUID as that almost never changes.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Mccfuzz on 2011-06-14
Hi 

Thanks for letting me know about the 'solved' option. Done!

Also thanks for the links 'Oldfred' I'll take a look at those.
At the moment though being a Newbie fstab and UUID are a little meaningless to me.
I'm beginning to see Ubuntu is as much of a hobby as an OS!  LOL!

---

### Post by apollothethird on 2011-06-14
> **Mccfuzz said:**
> I'm beginning to see Ubuntu is as much of a hobby as an OS!  LOL!

Actually some people look at all the OS' about the same way.  There are some people that are always tweaking their system. and some that will just do a chore and don't worry about tweaks.  I'm kind of in the middle.  At times I spend a lot of time with my computer chores, then there are other times where I get caught up in spending many hours tweaking and upgrading both software and hardware.

I always spent more time tweaking (or using) Windows as like a hobby than Linux.  For about the first 15 years of using Linux as a stabled OS and went many months and sometimes as much as a year without rebooting.  But lately (in the past 6 or 8 months) I've been spending a lot of time playing with the OS... making lots of my chores fun and interesting, especially since the release of Ubuntu 11.04 which I've been playing with the many Unity effects.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Mccfuzz on 2011-06-14
Hi  Appollo,

I doubt I'll ever  be up to your level with regards to 'Tweaking'  etc  but I will endeaver to acquaint my self with the basics.
FSTAB and UUID seems a good place to start.

I myself was keen  on 11.04  but I had problem with shutting down.  There was a suggestion that it didn't like my graphics card.
I was especially keen on 11.04 I could access my Nationwide Bank Account.
Just won't bring up the website at all on 10.04 or 10.10.  ??????

---

