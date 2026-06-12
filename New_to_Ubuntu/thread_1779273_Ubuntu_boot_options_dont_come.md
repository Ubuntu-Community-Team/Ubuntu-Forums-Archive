---
title: "Ubuntu boot options dont come"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by noobda on 2011-06-10
I Had Installed Ubuntu And It Was Working Fine Until,
I Have Tried To Format Ma Logical Partition To Create Partition Using XP SP2 Boot CD..
And I Have Deleted One Of Ma Logical Drive And Canceled Xp sp2 Setup.
Just To Create Partition FAT32 And When I Restart Ma Computer
Its Not Giving Boot Options To Boot Ubuntu..

I Had Installed Ubuntu 11.04 Its Not Giving Boot Options To Start Ubuntu..
What Do I Do Now?

Install Ubuntu Again Or Is There Ny Other Option To Get It Back??

Thanks In Advance..

---

### Post by ajgreeny on 2011-06-10
Run a live CD of ubuntu, and from that use the **Boot-info-script** link in my signature.

Follow the instruction on the site, and then copy the RESULTS.txt file back here in code tags, the # at top right of the reply entry box.

---

### Post by noobda on 2011-06-10
```

#
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    31,455,269    31,455,207   7 NTFS / exFAT / HPFS
/dev/sda2          31,455,331   976,751,999   945,296,669   f W95 Extended (LBA)
/dev/sda5          31,455,333   346,554,179   315,098,847   7 NTFS / exFAT / HPFS
/dev/sda6         346,554,243   649,090,259   302,536,017   4 FAT16 <32M
/dev/sda7         649,101,312   655,372,287     6,270,976  82 Linux swap / Solaris
/dev/sda8         655,382,528   661,651,455     6,268,928  82 Linux swap / Solaris
/dev/sda9         661,653,153   976,751,999   315,098,847   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        D62804CF2804B113                       ntfs       
/dev/sda5        A8D0F2E6D0F2B9A0                       ntfs       S o f t w a r e z
/dev/sda7        a237534f-5c2d-4382-bb4d-f36038dc8bb3   swap       
/dev/sda8        8607bfa7-9e3f-492f-8b50-6ca24a9dea33   swap       
/dev/sda9        B844F99044F9519C                       ntfs       M o v i e s
/dev/sdb1        D6DC3729DC3702F3                       ntfs       Stash

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------


```

---

### Post by noobda on 2011-06-10
Anyone Can Help Me With This?
I Need To Fix It Soon :(
Im Using Ubuntu LIve Cd.
I Guess My Problem Is Common But Still NO Answer :(

---

### Post by ajgreeny on 2011-06-10
OK, thanks a lot for that, but it is not as helpful as I had hoped as you only have windows partitions on the disks, apart from two swap partitions on sda.  How did they get there; have you already tried to install Ubuntu twice, or are they a relic of your successful Ubuntu system?

Whatever the answer to that, you do not have a Ubuntu system on disk at the moment, nor grub, so I can only assume that whatever you did with your attempt to:-
> I Had Installed Ubuntu And It Was Working Fine Until,
I Have Tried To Format Ma Logical Partition To Create Partition Using XP SP2 Boot CD..
And I Have Deleted One Of Ma Logical Drive And Canceled Xp sp2 Setup.
Just To Create Partition FAT32 And When I Restart Ma Computer
Its Not Giving Boot Options To Boot Ubuntu..totally messed things up for you.

So, can you run System->Administration->gparted from the live CD and post a screenshot of the gparted window, mainly for sda, but also perhaps from sdb, which you have labeled **stash**, so I presume is just for storage.

This will give a much better indication of the partition sizes, layout and %age used, because at the moment I am finding it difficult to know what is what on your partition table.

---

### Post by oldfred on 2011-06-10
The sda6 FAT16 partition is a little unusual and it is just before a swap partition which would be where a Linux partition might be. Was that your Ubuntu install?

I might try looking at the partition with testdisk, but if you started to install or copy something to the partition then it will not be bootable. You may get it back enough to copy some data if you do not have good backups.

From Ubuntu liveCD:
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

