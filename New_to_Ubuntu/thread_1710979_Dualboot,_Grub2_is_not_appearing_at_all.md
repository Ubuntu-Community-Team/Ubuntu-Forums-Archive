---
title: "Dualboot, Grub2 is not appearing at all"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by FlyingFishSalad on 2011-03-20
-----------------------------------------------------------------------
**SOLVED:**
Installed EasyBCD build 137, Added a Linux-GRUB2 boot option.
-----------------------------------------------------------------------

after following the instructions on how to make a dualboot system [here]("http://lifehacker.com/#%215403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

With
[LIST=1]
[*]Win7 x64
[*]Ubuntu x32
[/LIST]

[LIST]
[*]On Asus EEE PC 1001px
[*]Using USB flashdrives
[/LIST]

Grub2 menu is not appearing, windows is trying to load itself, tries to activate recovery. If you skip recovery - it boots for a while and then goes into BSOD.

NOTE:
[LIST=1]
[*]I have reached this situation twice, starting from scratch.
[*]When I did the same on my PC it worked perfectly.
[*]I would really like to solve this quickly and without having to format/reinstall Windows or modifying/deleting Windows or Storage partitions, if possible. I am fine with formatting the ubuntu partition though.
[*]Again, if possible, I really need a quick solution, I don't have much time to try to fix this.
[*]**Additional information**: Deleting Ubuntu partition in gparted, then replacing it with a same-sized empty(no filesystem) partition lets windows 7 boot normally for some reason. Oh, and after completing this task gparted crashes, and it crashes if I try to launch it again (until a complete clean of the hdd is done).
[/LIST]
Results from boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    81,919,999    81,713,152   7 HPFS/NTFS
/dev/sda3          81,920,000   163,839,999    81,920,000  83 Linux
/dev/sda4         163,840,000   312,580,095   148,740,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2055 MB, 2055208448 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4014079 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,011,647     4,011,586   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1042A4A142A48CD2                       ntfs       &#1047;&#1072;&#1088;&#1077;&#1079;&#1077;&#1088;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1086;&#1081;
/dev/sda2        24A2AD0FA2ACE690                       ntfs                                     
/dev/sda4        17554255718E3091                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        39CD-3D5E                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....|
00000020  42 36 3d 00 48 0f 00 00  00 00 00 00 02 00 00 00  |B6=.H...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 5e 3d cd 39 20  20 20 20 20 20 20 20 20  |..)^=.9         |
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
00000100  7d 00 66 b8 90 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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


```

e2fsck results
```

sudo e2fsck -C0 -p -f -v /dev/sda3
                                                                               
  131645 inodes used (5.13%)
      21 non-contiguous files (0.0%)
      87 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 106526/2
  694577 blocks used (6.78%)
       0 bad blocks
       1 large file

   86465 regular files
   14531 directories
      59 character device files
      26 block device files
       0 fifos
       0 links
   30555 symbolic links (25022 fast symbolic links)
       0 sockets
--------
  131636 files

```


If you need any other info on the problem, please tell me what should be listed.
Thanks in advance!

---

### Post by TexasRussian on 2011-03-20
ok, if you are able to boot into windows, there is a program called EasyBCD, it's a free program and with it you can create a grub like menu when you start your computer so you may choose Ubuntu or Windows. Hope that helps! :D

---

### Post by Hedgehog1 on 2011-03-20
We need to get a look at what shape your partitons are in.

Please boot off the LiveCD/LiveUSB, select try, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

With any luck, we can also figure out why the original install failed.


***The Hedge***

:KS

---

### Post by wilee-nilee on 2011-03-20
> **Hedgehog1 said:**
> We need to get a look at what shape your partitons are in.

Please boot off the LiveCD/LiveUSB, select try, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

With any luck, we can also figure out why the original install failed.


***The Hedge***

:KS

+1 for the bootscript

---

### Post by FlyingFishSalad on 2011-03-21
Will do ASAP, probably within the next 6 hours.
DONE, results added here and in header.

EDIT:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    81,919,999    81,713,152   7 HPFS/NTFS
/dev/sda3          81,920,000   163,839,999    81,920,000  83 Linux
/dev/sda4         163,840,000   312,580,095   148,740,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2055 MB, 2055208448 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4014079 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,011,647     4,011,586   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1042A4A142A48CD2                       ntfs       &#1047;&#1072;&#1088;&#1077;&#1079;&#1077;&#1088;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1086;&#1081;
/dev/sda2        24A2AD0FA2ACE690                       ntfs                                     
/dev/sda4        17554255718E3091                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        39CD-3D5E                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....|
00000020  42 36 3d 00 48 0f 00 00  00 00 00 00 02 00 00 00  |B6=.H...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 5e 3d cd 39 20  20 20 20 20 20 20 20 20  |..)^=.9         |
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
00000100  7d 00 66 b8 90 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

```
> **TexasRussian said:**
> if you are able to boot into windows
It either goes into recovery mode(I did not have the time to let it finish, so I don't know where that road leads), or it keeps booting for about 1/2 or 2/3 of the usual time and then - BSOD. Probably does not count as "booting into" :)

---

### Post by FlyingFishSalad on 2011-03-21
Should I paste anything else?
PS I'll try BCD in a little while, as soon as I won't _NEEEED_ to have a working system 12/7:)

---

### Post by oldfred on 2011-03-21
Not sure why windows does not boot, sda1 is normal (hidden) windows boot partition and sda2 is your main install or c:. MBR says it is booting and boot flag is on sda1.

Did you use windows to resize windows partition or gparted. If you used gparted windows needs to run chkdsk on your windows partition or it may need to do that anyway.

The sda3 is shown as linux in one place and not mountable in another. That may cause lots of problems. 

From liveCD I might try this, if it will let you.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by FlyingFishSalad on 2011-03-21
> **oldfred said:**
> Not sure why windows does not boot, sda1 is normal (hidden) windows boot partition and sda2 is your main install or c:. MBR says it is booting and boot flag is on sda1.
Yeah, that's what's bothering me too. I did the same thing with my PC, and frankly, I was more prepared for my PC to be more of a problem than the NB... Oh boy was I wrong :). I feel it necessary to repeat, though, that grubs2 does NOT appear at all, it goes straight to WIN7.

> **oldfred said:**
> Did you use windows to resize windows partition or gparted. If you used gparted windows needs to run chkdsk on your windows partition or it may need to do that anyway.
I completely erased the disk prior to installation, this is the second time I've tried this way.

> **oldfred said:**
> The sda3 is shown as linux in one place and not mountable in another. That may cause lots of problems.
That might be because of the whole situatione with it being clean at first, then having Ubuntu installed on it, then being deleted once again by gparted(which, as said before, crashes right after formatting the leftover space into the same type of partition that is described prior to the installation of Ubuntu. 


> **oldfred said:**
> From liveCD I might try this, if it will let you.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1
Thanks, I will post the results.


Results:

sudo e2fsck -C0 -p -f -v /dev/sdb1
/dev/sdb1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes

e2fsck: Bad magic number in super-block while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by FlyingFishSalad on 2011-03-24
> **TexasRussian said:**
> ok, if you are able to boot into windows, there is a program called EasyBCD, it's a free program and with it you can create a grub like menu when you start your computer so you may choose Ubuntu or Windows. Hope that helps! :D

I'm trying to use EasyBCD now, buuut... It does not see the ubuntu partition, so I can't set it to boot U, only W7. :(
EDIT: And I tried setting up grub, but I can't seem to make sense of any of the tutorials that I've seen (No clue what most of the variables mean), and I've also tried to find out how to chainboot, but to no avail, couldn't grasp it today.

---

### Post by oldfred on 2011-03-24
You ran the e2fsck on your external drive. My posting was an example with change to your partition. Which I think is sda3.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda3
if errors:
sudo e2fsck -f -y -v /dev/sda3

---

### Post by FlyingFishSalad on 2011-03-24
It was pretty much the same(and it was unmounted.), when I did it with /sda3 right now I'm at a different point... I've installed EasyBCD, and then installed Ubuntu. So the new efsck results will be from running it on an ext4 ubuntu drive.

//Now W loads, but again, no grub/grub2 menu(though I could get the EBCD grub to work I could not make it load anything/chainload grub2.

Thank you all for the patient and helpful treatment :)

---

### Post by oldfred on 2011-03-24
I thought the new version of ECBD did not need to chainload grub but worked more like grub2 does in finding other systems and directly booting them.

To chainload you have to install grub to the partition. Grub2 does not like to install to a partition as it is not enough space and it has to use blocklists. With block lists the address on the hard drive of the next boot file is hard coded. Then if for any reason (grub updates, fscks, other) then grub will fail. You then have to use a liveCD and reinstall grub2 to the partition.

---

### Post by FlyingFishSalad on 2011-03-25
After using a different usb to load it worked.... Ill try installing from this one.


sudo e2fsck -C0 -p -f -v /dev/sda3
                                                                               
  131645 inodes used (5.13%)
      21 non-contiguous files (0.0%)
      87 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 106526/2
  694577 blocks used (6.78%)
       0 bad blocks
       1 large file

   86465 regular files
   14531 directories
      59 character device files
      26 block device files
       0 fifos
       0 links
   30555 symbolic links (25022 fast symbolic links)
       0 sockets
--------
  131636 files

EDIT:
PS
You may be completely right, but for me EBCD did not notice the ubuntu partition at all(I installed ubuntu after installing EBCD, fearing that I'd be back at square 0 with the BSOD otherwise. When I tried to manually adjust the settings it did not even see the partition at all.

---

### Post by FlyingFishSalad on 2011-03-29
So-o-o-o... Is there anything I can try or do? I´m really puzzled by this whole thing.

---

### Post by oldfred on 2011-03-29
What works or does nothing?

Has the error the boot script showed on sda3 been resolved?

Rerun boot script so we can see where you are at.

---

### Post by FlyingFishSalad on 2011-03-31
sudo e2fsck -C0 -p -f -v /dev/sda3
                                                                               
  134778 inodes used (5.26%)
      26 non-contiguous files (0.0%)
      91 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 109056/3
  813298 blocks used (7.94%)
       0 bad blocks
       1 large file

   88718 regular files
   14779 directories
      59 character device files
      26 block device files
       0 fifos
     377 links
   31187 symbolic links (25624 fast symbolic links)
       0 sockets
--------
  135146 files


Booting still does not work correctly: no BSOD, but no Ubuntu either. 
Ubuntu is installed on sda3, I'm booting with EBCD, but to no effect (it does not recognise the linux partition and I have no idea how to make it notice it at all.).


INSTALLING EBCD beta build 137 and making a linux boot option with GRUB2 in it solved the problem.

---

### Post by FlyingFishSalad on 2011-03-31
Thank you all for being understanding and helpful! Without you I would not be able to do this :)

---

