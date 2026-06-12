---
title: "Grub/Partition Problem After Crash"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Wungle on 2010-08-26
My netbook crashed after trying to save an open office document as an old word format... After forced reboot, I was faced with the Grub Rescue prompt. 

I tried going through the actions recommended by Ubuntu Documentation - specifically what to do in Grub Rescue Mode - but kept getting "Unknown filesystem" response.  After running Boot Info Scripts, I can see why.  

However, as a complete noob, I have no idea how to change this.  Any hints or help on this would be greatly appreciated.  Also, if anyone has an idea why this happened, and what can be done to prevent it happening again, that would also be much appreciated.

Results of Boot Info Scripts:
                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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

/dev/sda1    *          2,048   306,620,415   306,618,368  83 Linux
/dev/sda2         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sda5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8118 MB, 8118075392 bytes
250 heads, 62 sectors/track, 1022 cylinders, total 15855616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,840,999    15,840,938   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ddb10d2b-9693-4092-a11d-72d7f09297a1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E392-ADBB                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  03 00 2e 00 0c 00 01 02  2e 00 00 00 8d 12 2c 00  |..............,.|
00000010  0c 00 02 02 2e 2e 00 00  05 00 2e 00 34 00 08 01  |............4...|
00000020  4d 61 6b 65 66 69 6c 65  64 70 6b 67 2d 6e 65 77  |Makefiledpkg-new|
00000030  05 00 2e 00 1c 00 11 01  4d 61 6b 65 66 69 6c 65  |........Makefile|
00000040  2e 64 70 6b 67 2d 6e 65  77 00 00 00 0a 00 2e 00  |.dpkg-new.......|
00000050  18 00 0a 02 66 75 6c 6f  6f 6e 67 2d 32 65 67 2d  |....fuloong-2eg-|
00000060  6e 65 77 00 06 00 2e 00  10 00 06 02 63 6f 6d 6d  |new.........comm|
00000070  6f 6e 00 00 04 00 2e 00  1c 00 07 01 4b 63 6f 6e  |on..........Kcon|
00000080  66 69 67 32 66 2e 64 70  6b 67 2d 6e 65 77 77 00  |fig2f.dpkg-neww.|
00000090  0c 00 2e 00 70 0f 09 02  6c 65 6d 6f 74 65 2d 32  |....p...lemote-2|
000000a0  66 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |f...............|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
```

---

### Post by Mrandersonjr on 2010-08-26
Do you shutdown your computer properly? If not then your hard drive is probably corrupt. Get a gparted live cd and boot up from it. Once it boots up just click on sda1 and click check/repair this filesystem and click apply. Also, it sounds like your MBR might be corrupt or your hard drive is about to go.

---

