---
title: "Cannot install Wubi"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by mrtn474 on 2011-05-03
I've been using wubi for about two months. A few days ago, I did the upgrade to 11.04 from 10.10. I looked around it to see the changes, and then I finally did some looking at the compiz settings. That finally messed up everything. 

You can skip this paragraph:

First, the launcher disappeared. I tried to fix it through compiz (I thought it would come back if I undid the changes). Then, the title bar and the menu bars of all windows totally disappeared! And finally, the main panel. I was left with nothing but the desktop when I tried to restart. So  I uninstalled it.

Now, I'm trying to reinstall ubuntu 11.04 on my hp mini (do I HAVE to install the netbook edition?). at the very end, it asks me that there's an error, and to look at the log file. I went to look at it, and it said that permissions were denied.

Please keep your responses simple, since I'm a total noob :)

Thank you all in advance.

---

### Post by wilee-nilee on 2011-05-03
So what is keeping you, since you have tried Ubuntu from just dual booting. Basically that is what wubi is for, trying it out, although I understand that people need it for various other reasons.

---

### Post by mrtn474 on 2011-05-03
I'm still trying to install it using wubi. I wish I could create a new partition and do a fresh install, but my hp netbook already came with four partitions. From everything I read, to delete "HP Tools" partition is an uncertain decision.

---

### Post by wilee-nilee on 2011-05-03
> **mrtn474 said:**
> I'm still trying to install it using wubi. I wish I could create a new partition and do a fresh install, but my hp netbook already came with four partitions. From everything I read, to delete "HP Tools" partition is an uncertain decision.

You might check the the md5sum, since you have installed before I presume your in the admin doing all this, and that the old wubi is clean gone including any remnants. If your using a disc make sure it is burned at the slowest speed. 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Good thing is that there are a couple of regulars who are knowledgeable in this area in general, so your thread header could not be any better really; straight to the point.;)

I will say though that most computers can be cleaned of the extra partitions so keep that in mind and let us help you do it or somebody who knows. You can clone the windows setup and have a backup that is just slid back in at any time needed. Its actually quite easy once you know how.

---

### Post by mrtn474 on 2011-05-03
I already know how to delete, and then shrink my partitions. I simply don't have the guts to risk breaking my computer.

I uninstalled wubi through the uninstall or change program window in the control panel of windows. So I hope wubi has been cleanly wiped. Would it be alright to message you, if I ever decide to do a full install?

---

### Post by beew on 2011-05-03
Forget about Wubi and do a real install, Wubi is only a try and see and you have tried for a few months already. :)

---

### Post by Frogs Hair on 2011-05-03
I have let three people install Via Wubi on Win 7 from my 11.04 ISO and it's worked well for everyone . If you can , download the ISO and you will have all the boot options.

---

### Post by wilee-nilee on 2011-05-03
> **mrtn474 said:**
> I already know how to delete, and then shrink my partitions. I simply don't have the guts to risk breaking my computer.

I uninstalled wubi through the uninstall or change program window in the control panel of windows. So I hope wubi has been cleanly wiped. Would it be alright to message you, if I ever decide to do a full install?

Certainly, I would probably have others look at it just to be sure, we all to some extent in this area work together, to make sure we are on the right track. Personally I would suggest you clone the whole disc to start with, or the partitions you can't loose...etc, it is easy to do. That is the best insurance you can have basically.

I understand your concerns though, been there.

---

### Post by 5149.5 on 2011-05-03
I am curious how you would go about cloning the disk. What method would be used for that?

---

### Post by wilee-nilee on 2011-05-03
> **5149.5 said:**
> I am curious how you would go about cloning the disk. What method would be used for that?

You have at the least a one time backup that will save the windows as an image, I assume that is usual here. You also have a recovery partition that will overwrite the C=main OS to where it was brand new. 

When you dual boot and start removing partitions that is what usually can't be used again, the recovery. Although on my acer aspire one netbook, the recovery booted with no problems with the Ubuntu grub2 bootloader stranger things have happened I was shocked. Many people come to the forums with the grub2 bootloader showing the Windows main and recovery choice in the boot menu, I don't recall anybody using the recovery they are looking for just general help usually.

Sorry for the long preamble I use clonezilla, you download a cd and boot from it to save the HD, or individual partitions to another media, I use a external HD. Fairly easy to use, and just copies bit for bit what you want along with the bootloader in the mbr.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by mrtn474 on 2011-05-04
> **wilee-nilee said:**
> ... 

When you dual boot and start removing partitions that is what usually can't be used again, the recovery. Although on my acer aspire one netbook, the recovery booted with no problems with the Ubuntu grub2 bootloader stranger things have happened I was shocked. Many people come to the forums with the grub2 bootloader showing the Windows main and recovery choice in the boot menu, I don't recall anybody using the recovery they are looking for just general help usually.

Sorry for the long preamble I use clonezilla, you download a cd and boot from it to save the HD, or individual partitions to another media, I use a external HD. Fairly easy to use, and just copies bit for bit what you want along with the bootloader in the mbr.
[http://clonezilla.org/](http://clonezilla.org/)

okay, I've decided to make the full install on my netbook alongside windows 7.

I have four partitions with their capacity: the C drive (133.48GB), HP tools (99MB), Recovery (15.28GB), and System (199MB).

So I'm planning on creating a recovery media on my friend's external HD, then i'll use his computer to burn it into DVDs. After that, I think I should delete the HP tools partition and shrink the C drive to make space for the Ubuntu partition.

Does that sound about right? Or am I about to screw everything up? lol.

---

### Post by mrtn474 on 2011-05-04
wilee-nilee, you could also message me if you'd like since this thread has gone out of topic.

---

### Post by wilee-nilee on 2011-05-04
> **mrtn474 said:**
> okay, I've decided to make the full install on my netbook alongside windows 7.

I have four partitions with their capacity: the C drive (133.48GB), HP tools (99MB), Recovery (15.28GB), and System (199MB).

So I'm planning on creating a recovery media on my friend's external HD, then i'll use his computer to burn it into DVDs. After that, I think I should delete the HP tools partition and shrink the C drive to make space for the Ubuntu partition.

Does that sound about right? Or am I about to screw everything up? lol.

Lets have you run the bootscript it is an excellent tool for saving pertinent information, but also just telling us what is where. This will make things much easier, so click on the bootscript in my signature. Download it drag it to the desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

The link has another click to get the scrip[t.

The thread is fine as far as subject matter and we actually want this on the forums we want the others who do this covering our backs. It is always good to know that others that you know are skilled at this as well are there to help.

Yeah do the recovery media make sure it is not just the disc to initiate recovery but that your saving the whole operating system.

The bootscript will really help in this especially teasing out where the boot files are, as that partition you want to wipe may be part of the boot, but that can be dealt with.

---

### Post by mrtn474 on 2011-05-04
the bootscript link you gave me says to run that in any linux operating system I no longer have ubuntu on my computer. Is there any way to do the same thing on windows? 

And actually, I stupidly realized that I can't run the recovery disks on my netbook.. duh! so if I ever need to recover, can I just paste those files into a flash drive and do it from there? The recovery media manager says that it needs a little bit more than 13GB to burn the recovery media into a device. Will that contain a copy of the entire OS?

---

### Post by wilee-nilee on 2011-05-04
> **mrtn474 said:**
> the bootscript link you gave me says to run that in any linux operating system I no longer have ubuntu on my computer. Is there any way to do the same thing on windows? 

You will need a live cd or a usb thumb to install you would use that for the script

> **mrtn474 said:**
> And actually, I stupidly realized that I can't run the recovery disks on my netbook.. duh! so if I ever need to recover, can I just paste those files into a flash drive and do it from there? The recovery media manager says that it needs a little bit more than 13GB to burn the recovery media into a device. Will that contain a copy of the entire OS?

The way recovery works is it is all saved to one place, and needs to be loaded from that place with a windows recovery disc. Pretty straight forward once you know how.

13 gigs I don't know what is on the computer. In that recovery gui you can customise the save so just look. I will reboot to my W7 set up if you want more specific info, I don't know which Windows you have. 

It is also 10:30 pm here so I don't think this will happen tonight, but after class tomorrow I will be back around 2:00 pm LA pacific time. There are others though generally on line that I know from the forum so if you want to get it done I can see if they are on.

---

### Post by mrtn474 on 2011-05-04
> 13 gigs I don't know what is on the computer. In that recovery gui you can customise the save so just look. I will reboot to my W7 set up if you want more specific info, I don't know which Windows you have.

Yup, I have W7

Edit: I will use a live flash drive to do what you said.

---

### Post by wilee-nilee on 2011-05-04
> **mrtn474 said:**
> Yup, I have W7

Edit: I will use a live flash drive to do what you said.

Cool I have the pro version, and it is a adjustable back up scheme I can use it repeatedly, generally the version on a purchased computer is a one backup.

So I'm not sure if it is any different, as far as more backup choices with a version less then pro. Back up choices meaning the docs, music...etc user saved extras.

---

### Post by mrtn474 on 2011-05-04
> **wilee-nilee said:**
> Cool I have the pro version, and it is a adjustable back up scheme I can use it repeatedly, generally the version on a purchased computer is a one backup.

So I'm not sure if it is any different, as far as more backup choices with a version less then pro. Back up choices meaning the docs, music...etc user saved extras.

I'm using a netbook, and microsoft saw it fit to only provide windows7 starter on all netbooks -.- 

I ran the bootscript, and here's what it spit out:

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   280,334,335   279,924,736   7 HPFS/NTFS
/dev/sda3         280,334,336   312,369,151    32,034,816   7 HPFS/NTFS
/dev/sda4         312,369,152   312,579,759       210,608   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4159 MB, 4159700992 bytes
64 heads, 32 sectors/track, 3967 cylinders, total 8124416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     8,122,367     8,122,336   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B422AEE822AEAEB4                       ntfs       SYSTEM                        
/dev/sda2        E4C27674C2764AB6                       ntfs                                     
/dev/sda3        EAFC6493FC645C37                       ntfs       RECOVERY                      
/dev/sda4        5245-3157                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        15FB-3107                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 ef 7b 00 bb 3d 00 00  00 00 00 00 02 00 00 00  |..{..=..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 07 31 fb 15 4e  4f 20 4e 41 4d 45 20 20  |..).1..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 9a  7b 00 00 66 ba 00 00 00  |..E}.f..{..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by wilee-nilee on 2011-05-04
I'm going to repost your script in code tags so it is easier to read, at this time, if you can wrap the original with the instruction in my signature with ```
 tags, that would be helpful.

So are you backed up now? If you are how did you do it? just making sure we are set here.

[CODE]Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Windows is installed in the MBR of /dev/sda
=> Syslinux is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr /Boot/BCD

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /boot/BCD /Windows/System32/winload.exe
/ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr /boot/bcd

sda4: __________________________________________________ _______________________

File system: vfat
Boot sector type: Vista: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 2,048 409,599 407,552 7 HPFS/NTFS
/dev/sda2 409,600 280,334,335 279,924,736 7 HPFS/NTFS
/dev/sda3 280,334,336 312,369,151 32,034,816 7 HPFS/NTFS
/dev/sda4 312,369,152 312,579,759 210,608 c W95 FAT32 (LBA)


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 4159 MB, 4159700992 bytes
64 heads, 32 sectors/track, 3967 cylinders, total 8124416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 * 32 8,122,367 8,122,336 c W95 FAT32 (LBA)


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 B422AEE822AEAEB4 ntfs SYSTEM
/dev/sda2 E4C27674C2764AB6 ntfs
/dev/sda3 EAFC6493FC645C37 ntfs RECOVERY
/dev/sda4 5245-3157 vfat HP_TOOLS
/dev/sda: PTTYPE="dos"
/dev/sdb1 15FB-3107 vfat PENDRIVE
/dev/sdb: PTTYPE="dos"
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sdb1 /cdrom vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437, iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 /rofs squashfs (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sdb1

00000000 eb 58 90 53 59 53 4c 49 4e 55 58 00 02 04 20 00 |.X.SYSLINUX... .|
00000010 02 00 00 00 00 f8 00 00 3f 00 ff 00 20 00 00 00 |........?... ...|
00000020 e0 ef 7b 00 bb 3d 00 00 00 00 00 00 02 00 00 00 |..{..=..........|
00000030 01 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000040 80 00 29 07 31 fb 15 4e 4f 20 4e 41 4d 45 20 20 |..).1..NO NAME |
00000050 20 20 46 41 54 33 32 20 20 20 fa fc 31 c9 8e d1 | FAT32 ..1...|
00000060 bc 76 7b 52 06 57 1e 56 8e c1 b1 26 bf 78 7b f3 |.v{R.W.V...&.x{.|
00000070 a5 8e d9 bb 78 00 0f b4 37 0f a0 56 20 d2 78 1b |....x...7..V .x.|
00000080 31 c0 b1 06 89 3f 89 47 02 f3 64 a5 8a 0e 18 7c |1....?.G..d....||
00000090 88 4d bc 50 50 50 50 cd 13 eb 5c 8b 55 aa 8b 75 |.M.PPPP...\.U..u|
000000a0 a8 c1 ee 04 01 f2 81 fa b7 07 73 2b f6 45 b4 7f |..........s+.E..|
000000b0 75 25 38 4d b8 74 20 66 3d 21 47 50 54 75 10 80 |u%8M.t f=!GPTu..|
000000c0 7d b8 ed 75 0a 66 ff 75 ec 66 ff 75 e8 eb 0f 51 |}..u.f.u.f.u...Q|
000000d0 51 66 ff 75 bc eb 07 51 51 66 ff 36 1c 7c b4 08 |Qf.u...QQf.6.|..|
000000e0 cd 13 72 13 20 e4 75 0f c1 ea 08 42 89 16 1a 7c |..r. .u....B...||
000000f0 83 e1 3f 89 0e 18 7c fb bb aa 55 b4 41 8a 16 74 |..?...|...U.A..t|
00000100 7b cd 13 72 10 81 fb 55 aa 75 0a f6 c1 01 74 05 |{..r...U.u....t.|
00000110 c6 06 45 7d 00 66 b8 9a 7b 00 00 66 ba 00 00 00 |..E}.f..{..f....|
00000120 00 bb 00 7e e8 10 00 66 81 3e 24 7e d4 ff 73 72 |...~...f.>$~..sr|
00000130 75 76 ea 38 7e 00 00 66 03 06 60 7b 66 13 16 64 |uv.8~..f..`{f..d|
00000140 7b b9 10 00 eb 2b 66 52 66 50 06 53 6a 01 6a 10 |{....+fRfP.Sj.j.|
00000150 89 e6 66 60 b4 42 e8 7f 00 66 61 8d 64 10 72 01 |..f`.B...fa.d.r.|
00000160 c3 66 60 31 c0 e8 70 00 66 61 e2 da c6 06 45 7d |.f`1..p.fa....E}|
00000170 2b 66 60 66 0f b7 36 18 7c 66 0f b7 3e 1a 7c 66 |+f`f..6.|f..>.|f|
00000180 f7 f6 31 c9 87 ca 66 f7 f7 66 3d ff 03 00 00 77 |..1...f..f=....w|
00000190 17 c0 e4 06 41 08 e1 88 c5 88 d6 b8 01 02 e8 37 |....A..........7|
000001a0 00 66 61 72 01 c3 e2 c9 31 f6 8e d6 bc 68 7b 8e |.far....1....h{.|
000001b0 de 66 8f 06 78 00 be df 7d e8 09 00 31 c0 cd 16 |.f..x...}...1...|
000001c0 cd 19 f4 eb fd 66 60 ac 20 c0 74 09 b4 0e bb 07 |.....f`. .t.....|
000001d0 00 cd 10 eb f2 66 61 c3 8a 16 74 7b cd 13 c3 42 |.....fa...t{...B|
000001e0 6f 6f 74 20 65 72 72 6f 72 0d 0a 00 00 00 00 00 |oot error.......|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by bcbc on 2011-05-04
> **mrtn474 said:**
> I've been using wubi for about two months. A few days ago, I did the upgrade to 11.04 from 10.10. I looked around it to see the changes, and then I finally did some looking at the compiz settings. That finally messed up everything. 

You can skip this paragraph:

First, the launcher disappeared. I tried to fix it through compiz (I thought it would come back if I undid the changes). Then, the title bar and the menu bars of all windows totally disappeared! And finally, the main panel. I was left with nothing but the desktop when I tried to restart. So  I uninstalled it.

Now, I'm trying to reinstall ubuntu 11.04 on my hp mini (do I HAVE to install the netbook edition?). at the very end, it asks me that there's an error, and to look at the log file. I went to look at it, and it said that permissions were denied.

Please keep your responses simple, since I'm a total noob :)

Thank you all in advance.
Just fyi, wubi.exe still offers Ubuntu-netbook (but there is no more Netbook edition, as regular Ubuntu desktop has the Unity interface). They forgot to remove Ubuntu-netbook from wubi.exe (it only appears when run standalone) - and that's probably why you got that error.

I know you don't need this anymore, but that's the reason if anyone else is looking.

---

### Post by wilee-nilee on 2011-05-04
> **bcbc said:**
> Just fyi, wubi.exe still offers Ubuntu-netbook (but there is no more Netbook edition, as regular Ubuntu desktop has the Unity interface). They forgot to remove Ubuntu-netbook from wubi.exe (it only appears when run standalone) - and that's probably why you got that error.

I know you don't need this anymore, but that's the reason if anyone else is looking.

Thanks bcbc that is very helpful to know for sure.;)

I installed a Natty to wubi from a regular download just to make sure it was working, we want everybody to get the full experience if possible I think. Slipped right in no problem, and was all gone with no file remnants when removed.

---

### Post by mrtn474 on 2011-05-05
> Originally Posted by wilee-nilee
So are you backed up now? If you are how did you do it? just making sure we are set here.

I wasn't able to get my hands on an external disk drive :\ and I do not have the money for one. I think the full install is going to have to wait a while. Or is there a way to it through a desktop? Like connect my netbook to a desktop and burn the disks there?


> 
Originally Posted by bcbc
Just fyi, wubi.exe still offers Ubuntu-netbook (but there is no more Netbook edition, as regular Ubuntu desktop has the Unity interface). They forgot to remove Ubuntu-netbook from wubi.exe (it only appears when run standalone) - and that's probably why you got that error.

I know you don't need this anymore, but that's the reason if anyone else is looking.

I didn't try to install the netbook edition. It wasn't even available. i downloaded it straight from the ubuntu website. The error said it did not get permissions.

---

### Post by bcbc on 2011-05-05
> **mrtn474 said:**
> I didn't try to install the netbook edition. It wasn't even available. i downloaded it straight from the ubuntu website. The error said it did not get permissions.
Did you download ubuntu-11.04-desktop-i386.iso and burn it to CD or are you referring to wubi.exe? (If the latter, it does still have that option).

If you want help with the log file, open up windows explorer, enter **%temp%** in the address bar, open wubi-11.04-rev211.log and paste the contents here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

---

### Post by wilee-nilee on 2011-05-05
> **bcbc said:**
> Did you download ubuntu-11.04-desktop-i386.iso and burn it to CD or are you referring to wubi.exe? (If the latter, it does still have that option).

If you want help with the log file, open up windows explorer, enter **%temp%** in the address bar, open wubi-11.04-rev211.log and paste the contents here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

OP this is a forum member among a few others that for wubi especially is good to have on your side.

Thanks for posting bcbc......carry on .;)

---

### Post by mrtn474 on 2011-05-05
Thanks for your time, wilee-nilee. I really appreciate it :)

> **bcbc said:**
> Did you download ubuntu-11.04-desktop-i386.iso and burn it to CD or are you referring to wubi.exe? (If the latter, it does still have that option).

If you want help with the log file, open up windows explorer, enter **%temp%** in the address bar, open wubi-11.04-rev211.log and paste the contents here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

Note: I'm using a netbook.

I had recently done a clean up on on my computer recently so the log file was gone. I tried installing it again just to get the error again. However, surprisingly, the installer flew through the process without a problem! It took less than two minutes, compared to the three+ hours I had to previously wait last time. I swear I did the same thing, except that I left it at the default 17gb that it would use. i wanted 25, but I wasn't expecting it to succeed.

The problem now, is that 11.04 does not allow me to connect to the wi-fi router. I had no problem with that with 10.10 (not that I intend to go back).

Also, as a sort of unrelated question: once I'm able to connect to the internet, if I get compiz again, will that mess up ubuntu like it did when I first messed it up? (tittle bars and window menus disappeared, along with the launcher and panel).

---

### Post by mrtn474 on 2011-05-05
here's the new log file, by the way. If it's of any use anymore:

```
05-04 14:39 INFO   root: === wubi 11.04 rev211 ===
05-04 14:39 DEBUG  root: Logfile is c:\users\mrtn\appdata\local\temp\wubi-11.04-rev211.log
05-04 14:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-04 14:39 DEBUG  CommonBackend: data_dir=C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\data
05-04 14:39 DEBUG  WindowsBackend: 7z=C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\bin\7z.exe
05-04 14:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-04 14:39 DEBUG  CommonBackend: Fetching basic info...
05-04 14:39 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-04 14:39 DEBUG  CommonBackend: platform=win32
05-04 14:39 DEBUG  CommonBackend: osname=nt
05-04 14:39 DEBUG  CommonBackend: language=en_US
05-04 14:39 DEBUG  CommonBackend: encoding=cp1252
05-04 14:39 DEBUG  WindowsBackend: arch=amd64
05-04 14:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\data\isolist.ini
05-04 14:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-04 14:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-04 14:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-04 14:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-04 14:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-04 14:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-04 14:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-04 14:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-04 14:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-04 14:39 DEBUG  WindowsBackend: Fetching host info...
05-04 14:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-04 14:39 DEBUG  WindowsBackend: windows version=vista
05-04 14:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-04 14:39 DEBUG  WindowsBackend: windows_sp=None
05-04 14:39 DEBUG  WindowsBackend: windows_build=7600
05-04 14:39 DEBUG  WindowsBackend: gmt=-8
05-04 14:39 DEBUG  WindowsBackend: country=US
05-04 14:39 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-04 14:39 DEBUG  WindowsBackend: windows_username=mrtn
05-04 14:39 DEBUG  WindowsBackend: user_full_name=mrtn
05-04 14:39 DEBUG  WindowsBackend: user_directory=C:\Users\mrtn
05-04 14:39 DEBUG  WindowsBackend: windows_language_code=1033
05-04 14:39 DEBUG  WindowsBackend: windows_language=English
05-04 14:39 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-04 14:39 DEBUG  WindowsBackend: bootloader=vista
05-04 14:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95525.5117188 mb free ntfs)
05-04 14:39 DEBUG  WindowsBackend: drive=Drive(C: hd 95525.5117188 mb free ntfs)
05-04 14:39 DEBUG  WindowsBackend: drive=Drive(D: hd 2251.6796875 mb free ntfs)
05-04 14:39 DEBUG  WindowsBackend: drive=Drive(E: hd 89.6650390625 mb free fat32)
05-04 14:39 DEBUG  WindowsBackend: drive=Drive(F: removable 3265.609375 mb free fat32)
05-04 14:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-04 14:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-04 14:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-04 14:39 DEBUG  WindowsBackend: keyboard_id=67699721
05-04 14:39 DEBUG  WindowsBackend: keyboard_layout=us
05-04 14:39 DEBUG  WindowsBackend: keyboard_variant=
05-04 14:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-04 14:39 DEBUG  CommonBackend: locale=en_US.UTF-8
05-04 14:39 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-04 14:39 DEBUG  CommonBackend: Searching ISOs on USB devices
05-04 14:39 DEBUG  CommonBackend: Searching for local CDs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Ubuntu Netbook CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Kubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Kubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Xubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Xubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Mythbuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp is a valid Mythbuntu CD
05-04 14:39 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-04 14:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-04 14:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-04 14:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-04 14:39 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-04 14:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-04 14:39 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-04 14:39 INFO   root: Running the CD menu...
05-04 14:39 DEBUG  WindowsFrontend: __init__...
05-04 14:39 DEBUG  WindowsFrontend: on_init...
05-04 14:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\translations, languages=['en_US', 'en']
05-04 14:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylDB34.tmp\translations, languages=['en_US', 'en']
05-04 14:40 INFO   WindowsFrontend: Operation cancelled
05-04 14:40 DEBUG  WindowsFrontend: frontend.quit
05-04 14:40 DEBUG  WindowsFrontend: frontend.on_quit
05-04 14:40 DEBUG  root: application.on_quit
05-04 14:40 INFO   root: sys.exit
05-05 00:20 INFO   root: === wubi 11.04 rev211 ===
05-05 00:20 DEBUG  root: Logfile is c:\users\mrtn\appdata\local\temp\wubi-11.04-rev211.log
05-05 00:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\mrtn\\Downloads\\wubi.exe"']
05-05 00:20 DEBUG  CommonBackend: data_dir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\data
05-05 00:20 DEBUG  WindowsBackend: 7z=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\bin\7z.exe
05-05 00:20 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-05 00:20 DEBUG  CommonBackend: Fetching basic info...
05-05 00:20 DEBUG  CommonBackend: original_exe=C:\Users\mrtn\Downloads\wubi.exe
05-05 00:20 DEBUG  CommonBackend: platform=win32
05-05 00:20 DEBUG  CommonBackend: osname=nt
05-05 00:20 DEBUG  CommonBackend: language=en_US
05-05 00:20 DEBUG  CommonBackend: encoding=cp1252
05-05 00:20 DEBUG  WindowsBackend: arch=amd64
05-05 00:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\data\isolist.ini
05-05 00:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-05 00:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-05 00:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-05 00:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-05 00:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-05 00:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-05 00:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-05 00:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-05 00:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-05 00:20 DEBUG  WindowsBackend: Fetching host info...
05-05 00:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-05 00:20 DEBUG  WindowsBackend: windows version=vista
05-05 00:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-05 00:20 DEBUG  WindowsBackend: windows_sp=None
05-05 00:20 DEBUG  WindowsBackend: windows_build=7600
05-05 00:20 DEBUG  WindowsBackend: gmt=-8
05-05 00:20 DEBUG  WindowsBackend: country=US
05-05 00:20 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-05 00:20 DEBUG  WindowsBackend: windows_username=mrtn
05-05 00:20 DEBUG  WindowsBackend: user_full_name=mrtn
05-05 00:20 DEBUG  WindowsBackend: user_directory=C:\Users\mrtn
05-05 00:20 DEBUG  WindowsBackend: windows_language_code=1033
05-05 00:20 DEBUG  WindowsBackend: windows_language=English
05-05 00:20 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-05 00:20 DEBUG  WindowsBackend: bootloader=vista
05-05 00:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95507.3359375 mb free ntfs)
05-05 00:20 DEBUG  WindowsBackend: drive=Drive(C: hd 95507.3359375 mb free ntfs)
05-05 00:20 DEBUG  WindowsBackend: drive=Drive(D: hd 2251.6796875 mb free ntfs)
05-05 00:20 DEBUG  WindowsBackend: drive=Drive(E: hd 89.6650390625 mb free fat32)
05-05 00:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-05 00:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-05 00:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-05 00:20 DEBUG  WindowsBackend: keyboard_id=67699721
05-05 00:20 DEBUG  WindowsBackend: keyboard_layout=us
05-05 00:20 DEBUG  WindowsBackend: keyboard_variant=
05-05 00:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-05 00:20 DEBUG  CommonBackend: locale=en_US.UTF-8
05-05 00:20 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-05 00:20 DEBUG  CommonBackend: Searching ISOs on USB devices
05-05 00:20 DEBUG  CommonBackend: Searching for local CDs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu Netbook CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Kubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Kubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Xubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Xubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Mythbuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Mythbuntu CD
05-05 00:20 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-05 00:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-05 00:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:20 INFO   root: Already installed, running the uninstaller...
05-05 00:20 INFO   root: Running the uninstaller...
05-05 00:20 INFO   CommonBackend: This is the uninstaller running
05-05 00:20 DEBUG  WindowsFrontend: __init__...
05-05 00:20 DEBUG  WindowsFrontend: on_init...
05-05 00:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\translations, languages=['en_US', 'en']
05-05 00:22 INFO   root: Received settings
05-05 00:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\translations, languages=['en_US', 'en']
05-05 00:22 DEBUG  TaskList: # Running tasklist...
05-05 00:22 DEBUG  TaskList: ## Running Backup ISO...
05-05 00:22 DEBUG  TaskList: ## Finished Backup ISO
05-05 00:22 DEBUG  TaskList: ## Running Remove bootloader entry...
05-05 00:22 DEBUG  WindowsBackend: Could not find bcd id
05-05 00:22 DEBUG  WindowsBackend: undo_bootini C:
05-05 00:22 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 95507.3359375 mb free ntfs)
05-05 00:22 DEBUG  WindowsBackend: undo_bootini D:
05-05 00:22 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2251.6796875 mb free ntfs)
05-05 00:22 DEBUG  WindowsBackend: undo_bootini E:
05-05 00:22 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 89.6650390625 mb free fat32)
05-05 00:22 DEBUG  TaskList: ## Finished Remove bootloader entry
05-05 00:22 DEBUG  TaskList: ## Running Remove target dir...
05-05 00:22 DEBUG  CommonBackend: Deleting C:\ubuntu
05-05 00:22 DEBUG  TaskList: ## Finished Remove target dir
05-05 00:22 DEBUG  TaskList: ## Running Remove registry key...
05-05 00:22 DEBUG  TaskList: ## Finished Remove registry key
05-05 00:22 DEBUG  TaskList: # Finished tasklist
05-05 00:22 INFO   root: Almost finished uninstalling
05-05 00:22 INFO   root: Finished uninstallation
05-05 00:22 DEBUG  CommonBackend: Fetching basic info...
05-05 00:22 DEBUG  CommonBackend: original_exe=C:\Users\mrtn\Downloads\wubi.exe
05-05 00:22 DEBUG  CommonBackend: platform=win32
05-05 00:22 DEBUG  CommonBackend: osname=nt
05-05 00:22 DEBUG  WindowsBackend: arch=amd64
05-05 00:22 DEBUG  CommonBackend: Parsing isolist=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\data\isolist.ini
05-05 00:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-05 00:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-05 00:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-05 00:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-05 00:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-05 00:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-05 00:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-05 00:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-05 00:22 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-05 00:22 DEBUG  WindowsBackend: Fetching host info...
05-05 00:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-05 00:22 DEBUG  WindowsBackend: windows version=vista
05-05 00:22 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
05-05 00:22 DEBUG  WindowsBackend: windows_sp=None
05-05 00:22 DEBUG  WindowsBackend: windows_build=7600
05-05 00:22 DEBUG  WindowsBackend: gmt=-8
05-05 00:22 DEBUG  WindowsBackend: country=US
05-05 00:22 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-05 00:22 DEBUG  WindowsBackend: windows_username=mrtn
05-05 00:22 DEBUG  WindowsBackend: user_full_name=mrtn
05-05 00:22 DEBUG  WindowsBackend: user_directory=C:\Users\mrtn
05-05 00:22 DEBUG  WindowsBackend: windows_language_code=1033
05-05 00:22 DEBUG  WindowsBackend: windows_language=English
05-05 00:22 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
05-05 00:22 DEBUG  WindowsBackend: bootloader=vista
05-05 00:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95932.1132813 mb free ntfs)
05-05 00:22 DEBUG  WindowsBackend: drive=Drive(C: hd 95932.1132813 mb free ntfs)
05-05 00:22 DEBUG  WindowsBackend: drive=Drive(D: hd 2251.6796875 mb free ntfs)
05-05 00:22 DEBUG  WindowsBackend: drive=Drive(E: hd 89.6650390625 mb free fat32)
05-05 00:22 DEBUG  WindowsBackend: uninstaller_path=None
05-05 00:22 DEBUG  WindowsBackend: previous_target_dir=None
05-05 00:22 DEBUG  WindowsBackend: previous_distro_name=None
05-05 00:22 DEBUG  WindowsBackend: keyboard_id=67699721
05-05 00:22 DEBUG  WindowsBackend: keyboard_layout=us
05-05 00:22 DEBUG  WindowsBackend: keyboard_variant=
05-05 00:22 DEBUG  WindowsBackend: total_memory_mb=1011.8984375
05-05 00:22 DEBUG  CommonBackend: Searching ISOs on USB devices
05-05 00:22 DEBUG  CommonBackend: Searching for local CDs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu Netbook CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Kubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Kubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Xubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Xubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Mythbuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Mythbuntu CD
05-05 00:22 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-05 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-05 00:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:22 INFO   root: Running the installer...
05-05 00:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\translations, languages=['en_US', 'en']
05-05 00:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\translations, languages=['en_US', 'en']
05-05 00:23 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=martin
05-05 00:23 INFO   root: Received settings
05-05 00:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\translations, languages=['en_US', 'en']
05-05 00:23 DEBUG  TaskList: # Running tasklist...
05-05 00:23 DEBUG  TaskList: ## Running select_target_dir...
05-05 00:23 INFO   WindowsBackend: Installing into C:\ubuntu
05-05 00:23 DEBUG  TaskList: ## Finished select_target_dir
05-05 00:23 DEBUG  TaskList: ## Running create_dir_structure...
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-05 00:23 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-05 00:23 DEBUG  TaskList: ## Finished create_dir_structure
05-05 00:23 DEBUG  TaskList: ## Running uncompress_target_dir...
05-05 00:23 DEBUG  TaskList: ## Finished uncompress_target_dir
05-05 00:23 DEBUG  TaskList: ## Running create_uninstaller...
05-05 00:23 DEBUG  WindowsBackend: Copying uninstaller C:\Users\mrtn\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-05 00:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-05 00:23 DEBUG  TaskList: ## Finished create_uninstaller
05-05 00:23 DEBUG  TaskList: ## Running copy_installation_files...
05-05 00:23 DEBUG  WindowsBackend: Copying C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-05 00:23 DEBUG  WindowsBackend: Copying C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\winboot -> C:\ubuntu\winboot
05-05 00:23 DEBUG  WindowsBackend: Copying C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-05 00:23 DEBUG  TaskList: ## Finished copy_installation_files
05-05 00:23 DEBUG  TaskList: ## Running get_iso...
05-05 00:23 DEBUG  CommonBackend: Searching for local CD
05-05 00:23 DEBUG  Distro:   checking whether C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp is a valid Ubuntu CD
05-05 00:23 DEBUG  Distro:     does not contain C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\casper\filesystem.squashfs
05-05 00:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-05 00:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-05 00:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-05 00:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-05 00:23 DEBUG  CommonBackend: Searching for local ISO
05-05 00:23 DEBUG  Distro:   checking Ubuntu ISO C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-05 00:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-05 00:23 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 DEBUG  CommonBackend: Trying to use ISO C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 DEBUG  TaskList: New task check_iso
05-05 00:23 DEBUG  TaskList: ### Running check_iso...
05-05 00:23 DEBUG  CommonBackend: Checking C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 DEBUG  Distro:   checking Ubuntu ISO C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso
05-05 00:23 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
05-05 00:23 DEBUG  TaskList: New task get_metalink
05-05 00:23 DEBUG  TaskList: #### Running get_metalink...
05-05 00:23 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink > C:\ubuntu\install
05-05 00:23 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-05 00:23 DEBUG  downloader: download finished (read 28158 bytes)
05-05 00:23 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-05 00:23 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-05 00:23 DEBUG  downloader: download finished (read 874 bytes)
05-05 00:23 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-05 00:23 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-05 00:23 DEBUG  downloader: download finished (read 198 bytes)
05-05 00:23 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-05 00:23 INFO   saplog: Checking block bindings..
05-05 00:23 INFO   saplog: Key verified successfully.
05-05 00:23 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-05 00:23 DEBUG  TaskList: #### Finished get_metalink
05-05 00:23 DEBUG  TaskList: New task get_file_md5
05-05 00:23 DEBUG  TaskList: #### Running get_file_md5...
05-05 00:23 DEBUG  TaskList: #### Finished get_file_md5
05-05 00:23 DEBUG  TaskList: ### Finished check_iso
05-05 00:23 DEBUG  TaskList: New task copy_file
05-05 00:23 DEBUG  CommonBackend: Copying C:\Users\mrtn\Downloads\ubuntu-11.04-desktop-i386.iso > C:\ubuntu\install\installation.iso
05-05 00:23 DEBUG  TaskList: ### Running copy_file...
05-05 00:24 DEBUG  TaskList: ### Finished copy_file
05-05 00:24 DEBUG  TaskList: ## Finished get_iso
05-05 00:24 DEBUG  TaskList: ## Running extract_kernel...
05-05 00:24 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
05-05 00:24 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
05-05 00:24 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
05-05 00:25 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
05-05 00:25 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-05 00:25 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-05 00:25 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
05-05 00:25 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-05 00:25 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
05-05 00:25 DEBUG  TaskList: ## Finished extract_kernel
05-05 00:25 DEBUG  TaskList: ## Running choose_disk_sizes...
05-05 00:25 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-05 00:25 DEBUG  TaskList: ## Finished choose_disk_sizes
05-05 00:25 DEBUG  TaskList: ## Running create_preseed...
05-05 00:25 DEBUG  TaskList: ## Finished create_preseed
05-05 00:25 DEBUG  TaskList: ## Running modify_bootloader...
05-05 00:25 DEBUG  TaskList: New task modify_bcd
05-05 00:25 DEBUG  TaskList: ### Running modify_bcd...
05-05 00:25 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 95932.1132813 mb free ntfs)
05-05 00:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {ed8235ca-8127-11df-80a4-aac7ae5d4c48}
05-05 00:25 DEBUG  TaskList: ### Finished modify_bcd
05-05 00:25 DEBUG  TaskList: New task modify_bcd
05-05 00:25 DEBUG  TaskList: ### Running modify_bcd...
05-05 00:25 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2251.6796875 mb free ntfs)
05-05 00:25 DEBUG  WindowsBackend: BCD has already been modified
05-05 00:25 DEBUG  TaskList: ### Finished modify_bcd
05-05 00:25 DEBUG  TaskList: New task modify_bcd
05-05 00:25 DEBUG  TaskList: ### Running modify_bcd...
05-05 00:25 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 89.6650390625 mb free fat32)
05-05 00:25 DEBUG  WindowsBackend: BCD has already been modified
05-05 00:25 DEBUG  TaskList: ### Finished modify_bcd
05-05 00:25 DEBUG  TaskList: ## Finished modify_bootloader
05-05 00:25 DEBUG  TaskList: ## Running modify_grub_configuration...
05-05 00:25 DEBUG  TaskList: ## Finished modify_grub_configuration
05-05 00:25 DEBUG  TaskList: ## Running create_virtual_disks...
05-05 00:25 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
05-05 00:25 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
05-05 00:25 DEBUG  TaskList: ## Finished create_virtual_disks
05-05 00:25 DEBUG  TaskList: ## Running uncompress_files...
05-05 00:25 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-05 00:25 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-05 00:25 DEBUG  TaskList: ## Finished uncompress_files
05-05 00:25 DEBUG  TaskList: ## Running eject_cd...
05-05 00:25 DEBUG  TaskList: ## Finished eject_cd
05-05 00:25 DEBUG  TaskList: # Finished tasklist
05-05 00:25 INFO   root: Almost finished installing
05-05 00:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\mrtn\AppData\Local\Temp\pylA880.tmp\translations, languages=['en_US', 'en']
05-05 00:26 INFO   root: Finished installation
05-05 00:26 DEBUG  root: application.quit
05-05 00:26 DEBUG  WindowsFrontend: frontend.quit
05-05 00:26 DEBUG  WindowsFrontend: frontend.on_quit
05-05 00:26 DEBUG  root: application.on_quit
05-05 00:26 INFO   root: sys.exit

```

---

### Post by bcbc on 2011-05-05
> **mrtn474 said:**
> Thanks for your time, wilee-nilee. I really appreciate it :)



Note: I'm using a netbook.

I had recently done a clean up on on my computer recently so the log file was gone. I tried installing it again just to get the error again. However, surprisingly, the installer flew through the process without a problem! It took less than two minutes, compared to the three+ hours I had to previously wait last time. I swear I did the same thing, except that I left it at the default 17gb that it would use. i wanted 25, but I wasn't expecting it to succeed.

The problem now, is that 11.04 does not allow me to connect to the wi-fi router. I had no problem with that with 10.10 (not that I intend to go back).

Also, as a sort of unrelated question: once I'm able to connect to the internet, if I get compiz again, will that mess up ubuntu like it did when I first messed it up? (tittle bars and window menus disappeared, along with the launcher and panel).
As you pointed out the log file doesn't show much except a canceled first attempt, and then the successful install. 

I have no idea why your wireless card should be affected by 11.04, but it's best to specify which card it is - or go through the networking & wireless subforum as they have stickies related to troubleshooting these.

11.04 has compiz installed - are you referring to the compiz config settings manager? Or enabling the advanced effects. I don't know a lot about it, but perhaps your graphics card doesn't support these. If you are using Wubi, backup your root.disk, experiment - and if you break it, just copy over the backup.

---

### Post by mrtn474 on 2011-05-05
> **bcbc said:**
> As you pointed out the log file doesn't show much except a canceled first attempt, and then the successful install. 

I have no idea why your wireless card should be affected by 11.04, but it's best to specify which card it is - or go through the networking & wireless subforum as they have stickies related to troubleshooting these.

11.04 has compiz installed - are you referring to the compiz config settings manager? Or enabling the advanced effects. I don't know a lot about it, but perhaps your graphics card doesn't support these. If you are using Wubi, backup your root.disk, experiment - and if you break it, just copy over the backup.

I restarted my computer to get on Ubuntu to enter that code from the troubleshooting guide from a sticky only to discover that the wireless connection is working flawlessly! is this a sign that there is worst trouble to come?

Another problem that has persisted since the beginning is that banshee won't play mp3. It'll play for about three seconds, and then stop. I also changed the source folder, and my library won't fill up with the songs. Should I post a new thread, since this is a different issue?

It's very unsettling that there's problems that are suddenly not there :\ It has also frozen every time I shut it down. I try using the magic sysreq key, but that doesn't work, so I turn it off manually.


Update: Now the mp3's are working -.-

---

### Post by bcbc on 2011-05-05
The freezing isn't good. Does it only happen on shutdown? You can run chkdsk from windows just to make sure ntfs is clean. Or look in your logs - but that sort of hard freeze usually isn't logged. You might have some hardware that is being difficult. Try the Suspend function and see if you have similar issues on suspend, or waking up.

---

### Post by mrtn474 on 2011-05-05
> **bcbc said:**
> The freezing isn't good. Does it only happen on shutdown? You can run chkdsk from windows just to make sure ntfs is clean. Or look in your logs - but that sort of hard freeze usually isn't logged. You might have some hardware that is being difficult. Try the Suspend function and see if you have similar issues on suspend, or waking up.

I did not have issues after waking up on suspend. and now it's been shutting off just fine. Faster than 10.10, actually. Although, with 10.10, it did freeze some times.

The wireless connectivity connection is acting up again. The difference now is that it DOES connect. However, webpages take forever to connect. The Ubuntu forums will load only the top part (loogo, name, search bar, login boxes), and that's it. facebook loads faster, google apps load faster too. but still too long. once on those other websites, it is very hard to go to another page within it.

---

