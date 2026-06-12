---
title: "Real problem here"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Justbill on 2011-04-10
I have installed Ubuntu side by side (dual boot) successfully many times in the past. Ubuntu always "sees" that windows is installed and gives me my partitioning options.
I currently have a HP Pavilion (about 5 year old computer) with windows xp installed (using "destructive system recovery), and when I attempt to install 10.10 from my live cd, Ubuntu tells me there is _no_ operating system installed and wants to use the entire disk. Windows IS installed and running. Everything else seems to be normal, live cd boots normally, gives me the install or try options, just will not see windows on the hard drive. 

Can anyone help?
Thanks in advance!
Bill

---

### Post by Jerry N on 2011-04-10
I would create the partition(s) for Ubuntu using gparted before trying to do the Ubuntu install.  With my 5 year old Pavillion I cloned the old 80gb hard drive to a new 320gb hard drive using Clonezilla.  This left me with a lot of unused space in which I created an extended partition.  I created logical partitions in the extended partition for Ubuntu 10.04 and a big NTFS data partition.  I did all the partitioning and formatting before trying to install Ubuntu.

Being an older computer, Windows and HP only used 3 of the 4 permissible partitions so I wasn't faced with a decision about what existing partition to remove.

Jerry

---

### Post by seawolf167 on 2011-04-10
First of all - back up your entire hdd with [Clonezilla]("http://www.clonezilla.org").

Once you do that, boot into Windows and resize Windows partitions if you need too. After you have your Windows partition sized as you like, boot off the LiveCD to start the install process. When you get to the disk partitioning, select the manual partitioning option. Here you can create your own partitions in the unallocated free space (maybe /, /home & swap partitions for simplicity). Then continue the install process, and install GRUB on that disk.

---

### Post by Hedgehog1 on 2011-04-10
Please be aware the many HP computers already have all 4 primary partitions defined, and you may need to remove one to make from for Ubuntu (all of the Ubuntu partitions can fit in a single 'extended' partition.

Here is an example of what we often find on HP systems.

**BEFORE:**

[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]

**AFTER:**

[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]


***The Hedge***

:KS

---

### Post by Justbill on 2011-04-10
I appreciate all the replies so far! When I run "gparted" all it says is 
"unallocated (then a little triangular warning symbol) unallocated (again) and then 149.05 GB"

This is a 160 GB hard drive. Windows XP is running, and the "system restore" is present and working.

So "gparted" is NOT showing the fat32 or NTFS file systems that are already present. This is the same problem I had trying to install, the partitioning tool is not "seeing" the existing partitions. It believes there is "no operating system installed".

As a side note, I use Ubuntu exclusively. I have win xp on one of my boxes, and myself or the rest of my family NEVER uses xp. I'm trying to set this system up for a friend to introduce them to Ubuntu, while they still have the option to use something they are familiar with (xp).

---

### Post by Quackers on 2011-04-10
How many NTFS/FAT32 file systems are present on the disc?

---

### Post by Justbill on 2011-04-10
Also, I don't know if this is pertinent, this is the "Media Center Edition".

---

### Post by Justbill on 2011-04-10
> **Quackers said:**
> How many NTFS/FAT32 file systems are present on the disc?

That I know of 1 FAT32 (system recovery) and 1 NTFS

---

### Post by Quackers on 2011-04-10
Hmm, if you only have 2 primary partitions and gparted cannot see them, there is a chance that something is wrong with the partition table. Has any partitioning been done lately?

---

### Post by Justbill on 2011-04-10
> **Quackers said:**
> Hmm, if you only have 2 primary partitions and gparted cannot see them, there is a chance that something is wrong with the partition table. Has any partitioning been done lately?

On my first attempt to install Ubuntu 10.10, the partitioning tool did see the NTFS partition, and gave a suggested size for the NTFS partition and for the ext4 partition. I resized the NTFS partition down a little, and began the install. Shortly after that the installer "crashed". I tried again, to no avail. Having thought of that (that there may be a problem with the fact that a partition resizing may be part of the problem), I did a "destructive" system restore of XP, to bring it back to a factory fresh install.

---

### Post by Quackers on 2011-04-10
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Justbill on 2011-04-10
In an attempt to get more information, I just installed Norton Partition Magic on Win XP. When I launched partition magic (after install) I got this error.

Init failed:  Error 117.
Partitions drive letter cannot be identified


Don't know if that will help

Thanks in advance
Bill

---

### Post by Justbill on 2011-04-10
OK here it is

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,219,039    11,218,977   b W95 FAT32
/dev/sda2    *     11,219,040   128,610,719   117,391,680   7 HPFS/NTFS
/dev/sda3         128,598,014   312,575,759   183,977,746   5 Extended
/dev/sda5         128,598,016   305,006,591   176,408,576  83 Linux
/dev/sda6         305,008,640   312,580,095     7,571,456  82 Linux swap / Solaris

/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda5
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        414C-2DCF                              vfat       HP_RECOVERY                   
/dev/sda2        9EE4F051E4F02CE1                       ntfs       HP_PAVILION                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        18fc6047-1715-46a5-8a8c-de2c5a64b6ca   ext4                                     
/dev/sda6        e432ce1b-d4f5-4f9a-9e35-631dcf766bf9   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional Edition" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=18fc6047-1715-46a5-8a8c-de2c5a64b6ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e432ce1b-d4f5-4f9a-9e35-631dcf766bf9 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f7 d8 eb 02 33 c0 c2 04  00 8b 44 24 04 f6 40 14  |....3.....D$..@.|
00000010  80 74 06 f6 40 78 01 74  09 8b 40 74 66 a9 20 0c  |.t..@x.t..@tf. .|
00000020  74 04 33 c0 eb 06 c1 e8  09 83 e0 01 c2 04 00 55  |t.3............U|
00000030  8b ec 83 ec 2c ff 75 10  8d 45 d4 50 ff 75 0c ff  |....,.u..E.P.u..|
00000040  75 08 e8 05 00 00 00 83  c4 10 c9 c3 55 8b ec 83  |u...........U...|
00000050  ec 44 53 56 8b 75 08 57  6a 00 8b 46 04 8d 8e 11  |.DSV.u.Wj..F....|
00000060  01 00 00 51 ff 10 8b d8  83 fb ff 89 5d 08 0f 84  |...Q........]...|
00000070  40 01 00 00 8b 46 04 68  5f 01 00 00 ff 50 44 8b  |@....F.h_....PD.|
00000080  f8 8b 46 04 85 ff 89 7d  fc 74 29 6a 00 68 80 00  |..F....}.t)j.h..|
00000090  00 00 53 ff 50 10 8b 46  04 8d 4d bc 6a 40 51 53  |..S.P..F..M.j@QS|
000000a0  ff 50 08 66 83 7d bc 00  74 10 8b 46 04 57 ff 50  |.P.f.}..t..F.W.P|
000000b0  48 8b 46 04 53 e9 f7 00  00 00 8b 45 0c 66 3b 45  |H.F.S......E.f;E|
000000c0  be 76 02 33 c0 0f bf 55  c6 0f b7 c0 0f af c2 8b  |.v.3...U........|
000000d0  4e 04 6a 01 50 53 ff 51  10 0f bf 4d c6 8b 46 04  |N.j.PS.Q...M..F.|
000000e0  51 57 53 ff 50 08 66 83  7d c6 04 75 04 8b 07 eb  |QWS.P.f.}..u....|
000000f0  03 0f b7 07 0f bf 55 c4  0f af c2 03 45 c0 8b 4e  |......U.....E..N|
00000100  04 6a 00 50 53 ff 51 10  8b 46 04 68 57 01 00 00  |.j.PS.Q..F.hW...|
00000110  57 53 ff 50 08 8b 1d 0c  f1 49 00 57 ff d3 83 f8  |WS.P.....I.W....|
00000120  28 77 75 57 ff 75 10 ff  15 34 f1 49 00 57 ff d3  |(wuW.u...4.I.W..|
00000130  8d 7c 38 01 57 ff d3 3d  2d 01 00 00 77 4c 8a 07  |.|8.W..=-...wL..|
00000140  8b 5d 14 84 c0 74 29 50  e8 25 0e 07 00 85 c0 8a  |.]...t)P.%......|
00000150  07 74 09 88 03 8a 47 01  43 47 eb 09 3c 26 75 05  |.t....G.CG..<&u.|
00000160  38 47 01 74 03 88 03 43  8a 47 01 47 84 c0 75 d7  |8G.t...C.G.G..u.|
00000170  80 23 00 8b 46 04 ff 75  fc ff 50 48 8b 46 04 ff  |.#..F..u..PH.F..|
00000180  75 08 ff 50 04 6a 01 58  eb 2c 8b 45 14 ff 75 fc  |u..P.j.X.,.E..u.|
00000190  80 20 00 8b 46 04 eb 10  8b 45 10 57 80 20 00 8b  |. ..F....E.W. ..|
000001a0  45 14 80 20 00 8b 46 04  ff 50 48 8b 46 04 ff 75  |E.. ..F..PH.F..u|
000001b0  08 ff 50 04 33 c0 5f 5e  5b c9 c3 55 8b ec 00 ef  |..P.3._^[..U....|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 c8 83 0a 00 ef  |................|
000001d0  ff ff 05 ef ff ff 02 c8  83 0a 00 90 73 00 00 00  |............s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Quackers on 2011-04-10
Wow. Well that's the problem then. Look at the bits in red. You have severe partition problems on this disc.
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    11,219,039    11,218,977   b W95 FAT32
/dev/sda2    *     11,219,040   128,610,719   117,391,680   7 HPFS/NTFS
/dev/sda3         128,598,014   312,575,759   183,977,746   5 Extended
/dev/sda5         128,598,016   305,006,591   176,408,576  83 Linux
/dev/sda6         305,008,640   312,580,095     7,571,456  82 Linux swap / Solaris

[COLOR="Red"]/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda5
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3[/COLOR]
```

---

### Post by Justbill on 2011-04-10
So, is there a way to fix it? Would I be better off wiping the drive, and if so is there a way to copy windows and re-install after the wipe drive?

---

### Post by Quackers on 2011-04-10
In the Ubuntu live desktop if you go to the Places menu, is there an entry for the Windows partition in there? If so, can you view it?

---

### Post by Justbill on 2011-04-10
I can go to places, and then either computer or HP_PAVILION and I see a bunch of folders, one of them says Windows.

---

### Post by Quackers on 2011-04-10
If you can see any of the files that you would want to backup I would suggest backing them up.
I would also suggest looking at the possibility of making an image backup of sda1 and sda2, using clonezilla. Details below.
It may then be possible to wipe the hard drive, then restore the image of sda1 and sda2 (just those 2) to the clean disc. That might work.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Justbill on 2011-04-10
I don't have anything to put the clone on tonight (need to get a bigger usb drive). Thanks for all the help, really appreciate it!

Bill

---

### Post by Miljet on 2011-04-10
Look closely at the start and end numbers. There doesn't appear to be any problem with sda1 and sda2. The problems start with sda3.

I would just try deleting sda3 through sda6 and recreating them. That is assuming that you have no valuable data saved. And you did state that you had already performed a destructive restore so the XP should be pristine.

---

### Post by Justbill on 2011-04-11
> **Miljet said:**
> Look closely at the start and end numbers. There doesn't appear to be any problem with sda1 and sda2. The problems start with sda3.

I would just try deleting sda3 through sda6 and recreating them. That is assuming that you have no valuable data saved. And you did state that you had already performed a destructive restore so the XP should be pristine.

The problem is that I have no idea how to access sda3 thru sda6. None of the partitioning tools I have are seeing the partitions, they see the drive as unallocated space

---

### Post by Justbill on 2011-04-11
After some lengthy research, I found that sfdisk would access my drive and show me the partition table. Using this tutorial [http://ubuntuforums.org/archive/index.php/t-1192598.html]("http://ubuntuforums.org/archive/index.php/t-1192598.html") I was able to delete sda3 through sda6, at which point the partitioning tools were able to "see" the partition table, and not just show "unallocated space". From that point on it was really just a simple install, put 10.04.2 on the free space, and can boot either system from grub........like normal.

Thanks to everyone for your help! And thanks to ALL those that contribute to these forums!

Bill

---

### Post by Miljet on 2011-04-11
Good deal! Glad to hear that you got it working.

---

### Post by AndyM2612 on 2011-04-12
Cool thanks for the link to this thread JustBill, for my 2c I know that you at least Partition Magic version 8.5 or above to work with SATA drives. I was able to format mine with PM8.5 but got the same sorts of errors about not being able to read or define partitions with version 8 and 6.5. But I like the idea of potentially installing the OS to a 20GB drive by its self then ghosting that hard drive to the partition on the multiple partition drive. With that, you'd probably need to use Norton Ghost Version 8.5 or above

---

### Post by Justbill on 2011-04-12
> **AndyM2612 said:**
> Cool thanks for the link to this thread JustBill, for my 2c I know that you at least Partition Magic version 8.5 or above to work with SATA drives. I was able to format mine with PM8.5 but got the same sorts of errors about not being able to read or define partitions with version 8 and 6.5. But I like the idea of potentially installing the OS to a 20GB drive by its self then ghosting that hard drive to the partition on the multiple partition drive. With that, you'd probably need to use Norton Ghost Version 8.5 or above

I ended up using "Parted Magic", here is a link [http://partedmagic.com/doku.php?id=start]("http://partedmagic.com/doku.php?id=start") . I REALLY liked this much better! Haven't used everything in it yet, but it contains a lot of good stuff (gparted, clonezilla, etc.)! Good luck too you!

---

