---
title: "error, wubi???"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Ivaylo Nedqlkow on 2011-02-02
can you tell me what caused this. ubunto install with wubi. after the start ubunto, starts loading and displays this error:
[http://alfa.kachi-snimka.info/images/rgh1296649656w.JPG](http://alfa.kachi-snimka.info/images/rgh1296649656w.JPG)

---

### Post by Mark Phelps on 2011-02-02
IT could be that your filesystem has been corrupted.

Boot into Windows and run chkdsk on the volume containing the Ubuntu file.

---

### Post by Ivaylo Nedqlkow on 2011-02-02
I checked with chkdsk, no errors. What can I do. I want both operating system. Now I have windows 7. I want to use wubi. I can not figure out what wrong?????:(

---

### Post by steveneddy on 2011-02-02
In my experience I believe that you would be much happier trying to run Ubuntu in Virtual Box instead of Wubi.

Wubi is a troublesome little bit if software that is made for only short trial period only.

VB will give you an experience very close to a native install of Ubuntu.

---

### Post by Rubi1200 on 2011-02-02
Hi,
this is what I suggest:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Ivaylo Nedqlkow on 2011-02-03
```
      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 14. According to the info in the 
                       boot sector, sda1 has 204799 sectors, but according to 
                       the info from fdisk, it has 206833 sectors.
    Mounting failed:
Failed to read last sector (204799): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (204799): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 105064448. But according to the info from 
                       fdisk, sda3 starts at sector 105062400. The info in 
                       boot sector on the starting sector of the MFT is 
                       wrong. According to the info in the boot sector, sda3 
                       has 204799 sectors, but according to the info from 
                       fdisk, it has 2047 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 105269248. But according to the info from 
                       fdisk, sda4 starts at sector 105064448. The info in 
                       boot sector on the starting sector of the MFT is 
                       wrong. According to the info in the boot sector, sda4 
                       has 209715199 sectors, but according to the info from 
                       fdisk, it has 204799 sectors.
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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  14       206,847       206,834  42 SFS
/dev/sda2             206,848   105,062,399   104,855,552  42 SFS
/dev/sda3         105,062,400   105,064,447         2,048  42 SFS
/dev/sda4    *    105,064,448   105,269,247       204,800  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C8C4B6C5C4B6B4D2                       ntfs                                     
/dev/sda2        DA38E81938E7F285                       ntfs                                     
/dev/sda3        2C7691E47691AED8                       ntfs                                     
/dev/sda4        F8F696D2F696908C                       ntfs       Filmi i igri                  
/dev/sda5        5C929B65929B4286                       ntfs                                     
/dev/sda6        A6467C84467C56D1                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1CE0-375B                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/DA38E81938E7F285  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/2C7691E47691AED8  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/Filmi i igri      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda3

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  02 00 e3 81 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  f9 aa 8f 91 d5 ab cb 01  f9 aa 8f 91 d5 ab cb 01  |................|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  f9 aa 8f 91 d5 ab cb 01  |................|
000000c0  f9 aa 8f 91 d5 ab cb 01  f9 aa 8f 91 d5 ab cb 01  |................|
000000d0  f9 aa 8f 91 d5 ab cb 01  00 40 00 00 00 00 00 00  |.........@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 21 00 01 90 91  b0 00 00 00 50 00 00 00  |!@U!........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 21 21 01 fe fd  |........!.T!!...|
00000190  00 00 01 00 00 a0 e3 81  ff ff ff ff 00 00 00 00  |................|
000001a0  00 00 04 00 00 00 00 00  21 40 55 21 00 01 90 91  |........!@U!....|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 21 21 01 fe fd  00 00 01 00 00 a0 02 00  |!.T!!...........|
00000200
MFT Sector of sda4

00000000  46 49 4c 45 30 00 03 00  89 23 5f 02 00 00 00 00  |FILE0....#_.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  16 00 f1 81 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  46 ad 40 95 d5 ab cb 01  46 ad 40 95 d5 ab cb 01  |F.@.....F.@.....|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  46 ad 40 95 d5 ab cb 01  |........F.@.....|
000000c0  46 ad 40 95 d5 ab cb 01  46 ad 40 95 d5 ab cb 01  |F.@.....F.@.....|
000000d0  46 ad 40 95 d5 ab cb 01  00 40 00 00 00 00 00 00  |F.@......@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 0a 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 a4 00 00 00 00 00  |@...............|
00000130  00 00 a4 00 00 00 00 00  00 00 a4 00 00 00 00 00  |................|
00000140  32 40 0a 00 00 0c 00 8c  b0 00 00 00 50 00 00 00  |2@..........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  31 01 ff ff 0b 11 01 ff  |........1.......|
00000190  00 00 01 00 00 e0 f1 81  ff ff ff ff 00 00 00 00  |................|
000001a0  00 00 04 00 00 00 00 00  31 40 00 00 0c 00 8c 91  |........1@......|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 e0 16 00  |1...............|
00000200
Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 60 77 00 ca 1d 00 00  00 00 00 00 02 00 00 00  |.`w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5b 37 e0 1c 4e  4f 20 4e 41 4d 45 20 20  |..)[7..NO NAME  |
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
00000100  7d 00 66 b8 bc 3b 00 00  66 ba 00 00 00 00 bb 00  |}.f..;..f.......|
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


```

---

### Post by Rubi1200 on 2011-02-03
Hi,
not sure what went wrong here, but there seem to be seem serious issues.

I am going to ask some others to look at this and offer some ideas.

Hang in there please.

Thanks.

---

### Post by Rubi1200 on 2011-02-03
> **Ivaylo Nedqlkow said:**
> can you tell me what caused this. ubunto install with wubi. after the start ubunto, starts loading and displays this error:
[http://alfa.kachi-snimka.info/images/rgh1296649656w.JPG](http://alfa.kachi-snimka.info/images/rgh1296649656w.JPG)
I hope the moderators will forgive me for double-posting, but this is pretty important.

Okay, here is what I would like you to do please.

Boot a LiveCD and run this command:

```
sudo dmraid -E -r /dev/sda
```
run this and remove as instructed.

If your disk was/is not part of a RAID array, this will only remove the metadata on it and nothing else.

**If you are supposed to have a RAID setup, then do not run the command. **

The other problem is that your disk appears to be dynamic not the standard basic type (indicated by the SFS tag next to the partitions).

I don't know if it was always like this, can you tell us more please?

This is probably one of the reasons Wubi failed to install.

---

### Post by srs5694 on 2011-02-03
I wouldn't recommend following Rubi1200's advice****. If your Windows installation is working, I wouldn't do anything to touch low-level disk structures, since what you've got there is a Windows installation using "dynamic disks" (aka SFS or LDM), which is Windows' equivalent of Linux's Logical Volume Manager (LVM). Such a configuration complicates dual-boot installations and makes use of Linux low-level disk tools inadvisable.

If you've just tried to install Ubuntu using WUBI, I agree with steveneddy: Delete the WUBI files from Windows and use VirtualBox. I don't know how WUBI interacts with SFS/LDM/dynamic disks, but from your experience it looks bad -- and perhaps even risky.

If your WUBI install used to work but now doesn't, and if you need to recover data from it, then I'm not sure what to suggest, since I'm not very familiar with either WUBI or SFS/LDM/dynamic disks.

If you want a true dual-boot configuration, then your best bet is to buy a new hard disk for use by Linux, install it in the computer, and install Linux to the new disk so as to avoid the SFS/LDM/dynamic disk setup from Linux. If that's not practical, you could look into [Partition Wizard,](http://www.partitionwizard.com/) which is supposed to be able to convert SFS/LDM/dynamic disks into conventional MBR disks, which Linux can use. I've never used this program, though, much less done this conversion. As a general rule, conversions on this level are always a bit risky -- a bug could write invalid data to the disk, causing you to lose everything. Thus, I recommend backing up everything important from your Windows installation before proceeding if you go this route.

---

### Post by Rubi1200 on 2011-02-04
As per instructions from srs5694, ignore my post asking you to remove RAID metadata.

From what I know of Wubi, I think it is unlikely that you can install it with your current configuration.

Therefore, the best thing to do would be to either use VirtualBox as steveneddy suggested or buy another disk and use that as srs5694 recommended.

Thanks to srs5694 too for offering his insight about this and I hope you manage to get something sorted out so you can try Ubuntu.

If you need more help, just ask.

---

