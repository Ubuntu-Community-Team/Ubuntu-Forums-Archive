---
title: "no such partition grub rescue"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by fmr16 on 2011-06-26
Hi I am new to ubuntu
I recently installed ubuntu 11.04 on my asus eeepc along with windows xp.
Both were working fine for last couple of weeks, until this morning when i tried to boot
I get this error
"no such partition 
grub rescue"
 and then nothing happens
so i searched around a  bit and then did boot into live ubunt using usb
and ran the boot info script.
I am copy pasting here the results.txt, 
kindly help as this file is different from other results.txt i have seen on ubuntu foum that are having the same problem. I dont know what to do next
Thanks
```

```                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
`    Boot sector info:   Syslinux looks at sector 8396256 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   173,385,293   173,385,231   7 NTFS / exFAT / HPFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         173,385,726   302,245,887   128,860,162  15 Unknown


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,633,407    15,633,376   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E21CE9DA1CE9A9AD                       ntfs       
/dev/sda2        CCED-990E                              vfat       PE
/dev/sdb1        B802-5CB2                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  7f c4 80 0e 56 89 bc 20  e5 d8 51 5b cc e7 fa f9  |....V.. ..Q[....|
00000010  27 19 e0 e9 29 46 a7 70  af e2 87 f8 cd 2b 53 aa  |'...)F.p.....+S.|
00000020  5d 5f 95 1e 95 ea 88 1e  85 8f 43 3d c7 aa b7 9b  |]_........C=....|
00000030  e8 43 c0 83 1d 5a 43 35  b5 14 29 73 bf cc 86 58  |.C...ZC5..)s...X|
00000040  88 6c 8e e3 44 89 bd bc  7b 93 e3 e8 b8 01 22 6c  |.l..D...{....."l|
00000050  07 8e 1a 04 90 62 db c4  1e 3d 0d ea b9 b2 f9 6b  |.....b...=.....k|
00000060  24 4e 8e b4 85 cc 81 59  e5 3d 54 c2 c4 4f 66 d9  |$N.....Y.=T..Of.|
00000070  a5 5c 09 c1 a9 b2 90 83  10 c5 51 b8 de 43 d1 42  |.\........Q..C.B|
00000080  4e 64 b7 f8 79 0b ed 4f  e7 f7 b3 1e 09 f6 9d 38  |Nd..y..O.......8|
00000090  e1 0d b2 22 7f b7 7e cd  ab 07 14 3e 4a d6 2c 40  |..."..~....>J.,@|
000000a0  24 0a 28 0c 42 a8 29 07  9e 1c 22 66 a9 52 e6 eb  |$.(.B.)..."f.R..|
000000b0  d9 04 33 82 3e ca cc 06  08 63 79 df 23 d5 2c c4  |..3.>....cy.#.,.|
000000c0  c6 a3 fd 53 f8 05 4c d8  2b 08 bf f9 c0 c9 64 54  |...S..L.+.....dT|
000000d0  af 9b aa 45 fa 4c 91 8d  49 39 9a fc 84 99 ef 2c  |...E.L..I9.....,|
000000e0  59 93 5f 29 c2 84 7d 29  ab 23 b0 32 76 b3 34 d2  |Y._)..}).#.2v.4.|
000000f0  85 38 3b cb d8 9c f4 c0  94 ec 9f f0 92 84 95 d7  |.8;.............|
00000100  f9 33 65 f1 be 7f da 56  43 c7 0d 76 e1 77 7a c8  |.3e....VC..v.wz.|
00000110  77 37 01 6f f9 1e 13 ff  01 db a0 1a 68 f7 43 2c  |w7.o........h.C,|
00000120  c5 e7 35 0c 0a 5e 84 c1  11 57 fc 24 27 71 53 8e  |..5..^...W.$'qS.|
00000130  a7 f7 21 95 79 2a 0e ac  b5 65 c4 df 25 51 0f 84  |..!.y*...e..%Q..|
00000140  e0 0f ee d8 c9 76 96 cb  34 32 9a 9c 6a 03 dd 8c  |.....v..42..j...|
00000150  34 dc bb 9d 7c 29 06 27  cf ea 26 a0 ee f3 23 3f  |4...|).'..&...#?|
00000160  67 0b ad b5 1a 30 3a d1  cb b9 09 3a c3 8c 3e 22  |g....0:....:..>"|
00000170  3f 46 e9 e9 24 78 16 cf  70 cb e8 b8 e4 3a 96 c0  |?F..$x..p....:..|
00000180  7d 39 94 03 1a ec 83 31  fb 4e 65 66 56 6d 90 a9  |}9.....1.NefVm..|
00000190  ea 94 d0 d2 89 77 64 05  b5 66 2a 8c 1d 8b 8f 68  |.....wd..f*....h|
000001a0  41 f9 c2 21 ed 05 9a 54  e1 4a d2 74 42 04 f8 88  |A..!...T.J.tB...|
000001b0  50 20 8b be d0 80 0e 29  c2 1f 0c 74 c5 42 00 fe  |P .....)...t.B..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 8e 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  8e 07 00 a8 1f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by oldfred on 2011-06-26
Script could not mount your sda3 FAT efi partition and sda4 which fdisk has as type 15 unknown.

Did you have an abnormal shutdown that corrupted file system.

If you know for sure that sda4 was a Linux partition you need to change it back to Linux. Since script cannot mount it I am not sure if from liveCD gparted or Disk Utility will let you change the type to 83 from 15, but do not format.

Do this first, just to have a backup copy:
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

If you get it changed to type 83 then run e2fsck. I do not think it will work unless type is 83 and it sees it as a extx format partition. 
#From liveCD so everything is unmounted,swap off if necessary, change sda4 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda4
#if errors:
sudo e2fsck -f -y -v /dev/sda4

---

