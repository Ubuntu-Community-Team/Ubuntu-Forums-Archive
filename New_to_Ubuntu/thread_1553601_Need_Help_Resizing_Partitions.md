---
title: "Need Help Resizing Partitions"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2010-08-15
Got some Problems resizing my Partitions. MY situation:

Ubuntu 10.04 LTS
Ubuntu 9.04
Windows 7
Windows XP

Now I want to shrink the windows partition and than resize my Ubuntu Partition (10.04). I am using Gparted, I am first trying to shrink Windows Partition but I still get errors while shrinking .... I am using the Ubuntu Live version (via USB).

There are 2 Files attached, one is a screenshot of my partitions and one is the error file of gparted.

Hope to get some help.

Thank you!

---

### Post by Elfy on 2010-08-15
Did you try to do what it said - > Please try to free less space.

Possibly it is because sda3 is as full as it is that is causing the issue - though I am not sure that is the case.

Gparted details to save others downloading it 
```

GParted 0.5.1

Libparted 2.2
Shrink /dev/sda3 from 263.66 GiB to 166.02 GiB  00:01:35    ( ERROR )
     	
calibrate /dev/sda3  00:00:00    ( SUCCESS )
     	
path: /dev/sda3
start: 31744440
end: 584685674
size: 552941235 (263.66 GiB)
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:12    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 283105907200 bytes (283106 MB)
Current device size: 283105912320 bytes (283106 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 169567 MB (59.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 164903 MB 0
Multi-Record : 279317 MB 97513
$MFTMirr : 150570 MB 1
Compressed : 266346 MB 11835
Ordinary : 282556 MB 366484
You might resize at 169566498816 bytes or 169567 MB (freeing 113539 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:01:11    ( ERROR )
     	
run simulation  00:01:11    ( ERROR )
     	
ntfsresize -P --force /dev/sda3 -s 178258268159 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 283105907200 bytes (283106 MB)
Current device size: 283105912320 bytes (283106 MB)
New volume size : 178258260480 bytes (178259 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 169567 MB (59.9%)
Collecting resizing constraints ...
Needed relocations : 9627168 (39433 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1792 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda3 for errors and (if possible) fix them  00:00:11    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 283105907200 bytes (283106 MB)
Current device size: 283105912320 bytes (283106 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 169567 MB (59.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 164903 MB 0
Multi-Record : 279317 MB 97513
$MFTMirr : 150570 MB 1
Compressed : 266346 MB 11835
Ordinary : 282556 MB 366484
You might resize at 169566498816 bytes or 169567 MB (freeing 113539 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:01    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda3 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 283105907200 bytes (283106 MB)
Current device size: 283105912320 bytes (283106 MB)
New volume size : 283105907200 bytes (283106 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:01    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 283105907200 bytes (283106 MB)
Current device size: 283105912320 bytes (283106 MB)
New volume size : 283105907200 bytes (283106 MB)
Nothing to do: NTFS volume size is already OK.
```

---

### Post by HermanAB on 2010-08-15
Hmm, bear in mind that resizing partitions *always* results in lost data.

The only exception is when you waste 3 days making backups first, then the resizing goes perfectly smoothly of course...

---

### Post by Krabby.Linux on 2010-08-15
Thanks for the respones.

What would you do if you need more space? I am not using windows anymore but want to keep it. Another thing is : I want to DELETE/Format the Ubuntu 9.04 Partition and transfer the space to the 10.04 disk? Is that possible ?

---

### Post by Elfy on 2010-08-15
Yes it is - if you're not sure which partition is which - boot 10.04 then see which one is mounted.

Once you know - then you can move space about as you want in the livecd. 

Backup and then backup the backups.

---

### Post by Krabby.Linux on 2010-08-16
What happens if i format the ubuntu 9.04 drive (ext3) to ext4? does it than automatically belong to lucid?

I need space .... What would you suggest if you want to move the space from windows to lucid? How can i Backup Lucid? Usually if you resize a partition (make it bigger) no data is lost or am i wrong?

---

### Post by Krabby.Linux on 2010-08-16
Ok, I found out that it does not automatically belong to my ubuntu 10.04 Partition. I guess I am trying to delete the 9.10 and than resize my 10.04. Hope that nothing goes bad :-).

---

