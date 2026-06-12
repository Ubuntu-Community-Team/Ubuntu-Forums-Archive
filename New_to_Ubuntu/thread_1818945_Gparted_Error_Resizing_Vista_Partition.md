---
title: "Gparted Error Resizing Vista Partition"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by JDude1025 on 2011-08-05
I'm Having Trouble Resizing my windows partition (i want to resize it from 221 GB to 161 GB and allow for 60GB for Linux on dual boot). wWhenever i try to resize the partition (I'm using gparted from live on my flash drive) i get an error and when i check the detail report page it says this:

GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
    **Shrink /dev/sda1 from 221.74 GiB to 161.74 GiB**  00:01:49    ( ERROR )             calibrate /dev/sda1  00:00:01    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 465020927
size: 465020865 (221.74 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:15    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 238090682880 bytes (238091 MB)
Current device size: 238090682880 bytes (238091 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use       : 158881 MB (66.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    185830 MB             0
Multi-Record       :    238066 MB         13271
$MFTMirr           :    119151 MB             1
Compressed         :    148430 MB         83122
Sparse             :    182286 MB         20360
Ordinary           :    238087 MB        462384
You might resize at 158880890880 bytes or 158881 MB (freeing 79210 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:01:16    ( ERROR )             run simulation  00:01:16    ( ERROR )             ***ntfsresize -P --force /dev/sda1 -s 173667222015 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 238090682880 bytes (238091 MB)
Current device size: 238090682880 bytes (238091 MB)
New volume size    : 173667217920 bytes (173668 MB)
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use       : 158881 MB (66.7%)
Collecting resizing constraints ...
Needed relocations : 6618291 (27109 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1792 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sda1 for errors and (if possible) fix them  00:00:16    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 238090682880 bytes (238091 MB)
Current device size: 238090682880 bytes (238091 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use       : 158881 MB (66.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    185830 MB             0
Multi-Record       :    238066 MB         13271
$MFTMirr           :    119151 MB             1
Compressed         :    148430 MB         83122
Sparse             :    182286 MB         20360
Ordinary           :    238087 MB        462384
You might resize at 158880890880 bytes or 158881 MB (freeing 79210 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:01    ( SUCCESS )             run simulation  00:00:00    ( SUCCESS )             ***ntfsresize -P --force /dev/sda1 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 238090682880 bytes (238091 MB)
Current device size: 238090682880 bytes (238091 MB)
New volume size    : 238090678784 bytes (238091 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:01    ( SUCCESS )             ***ntfsresize -P --force /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 238090682880 bytes (238091 MB)
Current device size: 238090682880 bytes (238091 MB)
New volume size    : 238090678784 bytes (238091 MB)
Nothing to do: NTFS volume size is already OK.[/I]before doing this i already ran defrag.exe on vista (a long time ago but that was before i installed Linux through Wubi. it mentioned to try shrinking less space but i have 70GB free on the windows Partition (+ 30 more GB after i get Linux using Wubi off that partition). i ran CHKDSK before i tried using Gparted and i also ran the hard drive diagnostics test and it passed the SMART test (and didnt find any bad sectors). So what do i need to do now?

---

### Post by Basher101 on 2011-08-05
Why do you not shrink it from within windows? it has some built in options to resize partitions - even its own. Normally you access it by Start-> right click on Computer, choose Manage. After a window opens, click on Disk utility (or sth similar to that) in the upper left of the windows. After that it will load for a few secs, then below you will see the partitions. Try to resize it from there. Tell me when it worked

Regards

---

### Post by JDude1025 on 2011-08-05
I tried that but it only allows me to shrink it by 3503 MB and that was after i disabled the pagefile and shut off the restore points. i redid disk check and did defragmentation using auslogics boostspeed (trial) and it said my drive was badly fragmented (33% compared to the mere 6 percent defrag.exe said it was) i defragmented it and all but it still isnt letting me resize (to a usable amount).

---

### Post by JDude1025 on 2011-08-06
i just tried gparted again to see what would happen and i guess the defrag and disc cleanup made it possible to shrink the partition and i got it running, thanks for your help

---

