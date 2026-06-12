---
title: "boot parameters"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by marves on 2011-01-28
I tried to install ubuntu 10.10(dell studio 1555) but it couldnt pass the installation screen. I think that it may be fixed by changing boot parameters. Which parameters should I use?

 ============================ Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920   195,414,015   195,332,096   7 HPFS/NTFS
/dev/sda3         195,414,016   625,137,663   429,723,648   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        32D80878D8083D1B                       ntfs                                     
/dev/sda3        D2D6A48BD6A47201                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        87CE-8CA7                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 30 00  |.X.SYSLINUX.. 0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 80 1f 00 00  |........?.......|
00000020  80 50 77 00 78 07 00 00  00 00 00 00 02 00 00 00  |.Pw.x...........|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 a7 8c ce 87 54  4f 53 48 49 42 41 20 20  |..)....TOSHIBA  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
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
00000100  7d 00 66 b8 40 0f 00 00  66 ba 00 00 00 00 bb 00  |}.f.@...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2011-01-29
Hi and welcome to the forums :-)

What graphics card do you have installed and how much RAM is available?

Also, how much space do you have free to install Ubuntu/want to dedicate to it?

You will need to create a partition where Ubuntu can be installed.

But first post the information I requested before we move ahead.

Thanks.

---

### Post by mikewhatever on 2011-01-29
The installation screen? Which one? Did you get any errors?
As a side note, the bootinfo script has nothing to do with installation problems or boot parameters.

---

### Post by marves on 2011-01-29
I thought that boot info would be  helpful. Apparently it isnt
First, I used wubi to install but fans were too noisy and the laptop overheated and uninstalled it. I upgraded BIOS (from A06 to A08. Then I tried to install by booting from CD but it gave error, something like "can not mount".
Then I tried to install with USB. During this installation first a black screen appeared with the following choices: install on harddisk, run ubuntu from USB (i dont remember exactly). If I choose install on hard disk again it gives error. I tried to run from USB and from opened ubuntu desktop I clicked on install. It stuck on preparing to install process. I saw this in help ubuntu   [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)


graphic card is ATI mobility radeon hd 4570 gddr3.
for ubuntu free space to install 10 gb. or 20 gb much better?

---

### Post by supererki on 2011-01-29
Do you have SATA or PATA disks ? 

You can always try the graphical installer. It helps in some mystic cases.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by marves on 2011-01-29
SATA disks.
Also, during installation it gives error:
**cannot mount /dev/lop0 (/cdrom/casper/filesystem. squashfs**

---

### Post by marves on 2011-02-10
I could install ubuntu!  The problem was I hadnt burned the CD in an  appropriate way. I checked with m5ds, it seemed that nothing's wrong with iso files. Probably I burned the CD at max. speed. Anyway problem is solved now.

---

