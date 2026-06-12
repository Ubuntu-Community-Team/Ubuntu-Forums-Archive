---
title: "Unable to mount disk on ubuntu plz help"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by vijitk on 2011-05-09
HI guys can any one help.

my win 7 acer laptop crashed few days back.
wen i try to install win 7 it asks to locate drivers.

but i want to take backup so wen trying to run unbuntu live cd so i tried to mount my disk but am unable to do it .
please help.

i list the partition using #sudo fdisk -l

wat i see is 
/dev/sda1
/dev/sda2*
/dev/sda3

the system info it shows is neither ntfs nor fat32
it shows sfs


plz help guys..

---

### Post by Hedgehog1 on 2011-05-09
We need to get a look at what shape your system is in to try to help.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by user1397 on 2011-05-09
might be as simple as just seeing if your other partitions show up on nautilus.

when you boot into the livecd, go to places > my computer and see if there are any partitions there which look like it might be the one you want (they're usually separated by GB size).  Then just double click it to mount it.

---

### Post by vijitk on 2011-05-11
the thing is my windows 7 laptop crashed and i want to take backup from my disk so i ran ubuntu live cd
after that it showed 2 partition in fdisk cmd, somehow i format /dev/sda1 but i wasnt even able to access /dev/sda3
plz help guys it has been days since my laptop crashed.

thanks hedgehog, i ran the script ,this is wat i got

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   151,091,324   151,091,262   7 HPFS/NTFS
/dev/sda3         151,093,248   312,579,759   161,486,512  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A7512272F97E9DC                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  02 b0 30 04 60 c0 35 83  00 47 01 80 21 06 00 34  |..0.`.5..G..!..4|
00000010  bc 18 06 58 0c 04 e8 30  13 a0 c0 4d 83 00 da 10  |...X...0...M....|
00000020  c1 80 14 06 00 38 21 03  00 e4 0c 02 b0 21 03 00  |.....8!......!..|
00000030  1c ac 03 81 80 6e 06 03  1d 58 f8 18 06 40 0f c0  |.....n...X...@..|
00000040  60 28 80 ff c1 80 0d 07  00 11 41 80 8b 06 03 b4  |`(........A.....|
00000050  18 09 c0 60 08 fe 10 41  80 1e 12 47 a0 c0 7a 50  |...`...A...G..zP|
00000060  60 1c 01 a0 07 d6 06 01  bc 18 05 00 60 1a 81 80  |`...........`...|
00000070  6c 04 01 2c 18 00 e0 82  01 80 c0 14 97 09 42 48  |l..,..........BH|
00000080  1e 1e ab 06 00 44 18 03  80 60 0d 41 80 18 04 18  |.....D...`.A....|
00000090  07 87 ea 84 bf 02 80 18  06 f0 60 05 81 80 20 06  |..........`... .|
000000a0  00 34 18 07 00 85 bf 2e  90 bc 18 08 80 82 5c 08  |.4............\.|
000000b0  63 e1 e8 90 3f 1e 89 45  e5 e5 c1 9f 5f 5c 0c 0d  |c...?..E...._\..|
000000c0  34 c7 e1 04 21 00 78 30  07 c0 c0 08 02 07 82 18  |4...!.x0........|
000000d0  94 5c 01 a0 c0 0e 03 00  a2 0c 03 40 41 12 40 38  |.\.........@A.@8|
000000e0  7e 3f 55 e0 86 01 a1 08  18 05 60 60 06 41 80 1c  |~?U.......``.A..|
000000f0  1f 00 70 43 06 00 40 48  97 e5 e2 48 94 0c 00 89  |..pC..@H...H....|
00000100  78 30 06 40 82 5c 0c 03  40 ff fe 1f 2a 00 c5 60  |x0.@.\..@...*..`|
00000110  c0 36 03 00 39 e2 ea 10  fe 0c 03 98 fe 03 40 15  |.6..9.........@.|
00000120  70 0c 03 48 30 0a 20 c0  16 03 00 e2 a8 18 05 e1  |p..H0. .........|
00000130  f7 81 80 6a 06 01 44 21  97 00 78 38 00 96 0c 01  |...j..D!..x8....|
00000140  70 30 06 e0 c0 0e 97 02  08 30 03 e0 c0 09 79 50  |p0.......0....yP|
00000150  07 04 30 60 09 42 18 30  04 40 82 3f 8a fd 01 80  |..0`.B.0.@.?....|
00000160  50 00 ff 03 00 20 0c 00  a0 30 0e 40 1a 0c 01 41  |P.... ...0.@...A|
00000170  70 07 83 02 19 00 3d 58  f8 21 83 00 ba 0c 03 68  |p.....=X.!.....h|
00000180  93 f0 0c 1f 97 83 00 25  3e 0d 03 2f 5f 5c 0c 0d  |.......%>../_\..|
00000190  30 81 80 63 06 01 58 18  02 30 0d 56 0c 02 30 30  |0..c..X..0.V..00|
000001a0  0d 20 c0 08 97 83 00 ca  3f 06 01 a4 1c 07 be 05  |. ......?.......|
000001b0  08 30 1e 40 c0 0a 03 00  e6 0c 00 a0 30 01 c0 80  |.0.@........0...|
000001c0  0c 00 88 30 03 e0 c0 79  03 00 aa 0c 00 a8 30 0a  |...0...y......0.|
000001d0  21 04 18 08 b0 60 19 c4  80 60 19 01 80 71 08 20  |!....`...`...q. |
000001e0  c0 32 03 01 14 10 41 80  17 54 0c 00 a8 90 0a 10  |.2....A..T......|
000001f0  60 07 01 80 1c 06 03 d4  48 08 3f 06 01 b4 bc 18  |`.......H.?.....|
00000200

---

