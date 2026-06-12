---
title: "External hard drive shows up as &quot;unallocated&quot; in GParted"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by walawa on 2010-11-13
I'm about to make a clean install of my dual-booting Ubuntu and Windows 7 system, so I made some backups to an external hard drive which has two partitions, one hfs+(journaled) and one hfs+. I would use the non-journaled one for ubuntu. Both were made using disk utility on a mac. 

I was able to make my backups a few days ago, but now when I plug in the hard drive, Ubuntu doesn't recognize it and GParted lists it as entirely unallocated space. However, when I plug it into the Mac, both partitions show up just fine. Windows also shows the drive as unallocated.

This is the output for "sudo parted /dev/sdb print"
```
Model: Hitachi HDP725050GLA360 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags
```

"sudo fdisk -l"
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000a6cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6527    52428096    b  W95 FAT32
/dev/sda2   *        6528        9791    26218080    7  HPFS/NTFS
/dev/sda3            9792       29761   160409025   83  Linux
/dev/sda4           29762       30401     5140800    5  Extended
/dev/sda5           29762       30401     5140768+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4842f440

   Device Boot      Start         End      Blocks   Id  System
```

What can I do to regain acces to this drive?

---

### Post by psusi on 2010-11-13
See what the mac partition tool thinks the partition type is.  You probably used the old mac partition table.  If so you will need to reformat the disk and use either msdos or gpt partition tables.

---

### Post by walawa on 2010-11-13
Disk utility lists them both as hfs+, one journaled and one not. Would I really need to reformat the drive? I was able to read and write to it previously with Ubuntu. Also the output of "parted /dev/sdb print" says the parition table is in fact msdos.

---

### Post by psusi on 2010-11-13
Those are the types of the partitions.  What is the type of the PARTITION TABLE.

---

### Post by srs5694 on 2010-11-13
Please download and install the latest version of [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) from its [Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) and post the output of typing "sudo gdisk -l /dev/sdb". The result should look something like this:

```

$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 0.6.13

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sdc: 31576064 sectors, 15.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 98902377-B4BC-4F63-AE17-3E1B7309141F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31576030
Partitions will be aligned on 2048-sector boundaries
Total free space is 1560509 sectors (762.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        19531775   9.3 GiB     0700  Linux/Windows data
   2        19900416        24094719   2.0 GiB     0700  Linux/Windows data
   3        24639488        30930943   3.0 GiB     0700  Linux/Windows data

```

I'm particularly interested in the "partition table scan" lines, since those will reveal what type of partition tables are present (of the four that the program can detect). My suspicion is that the disk either has an old Apple Partition Map (APM) partition table or that it's got a new GUID Partition Table (GPT), but that it or its protective MBR has been damaged in some way. Precisely how to recover from the problem depends on what's happened, of course.

---

### Post by walawa on 2010-11-13
"sudo gdisk -l /dev/sdb" :
```
gdisk: /lib/libuuid.so.1: no version information available (required by gdisk)
GPT fdisk (gdisk) version 0.6.13

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 087350FE-FAB9-46CF-BDEC-4B7D16C735BD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 976773101 sectors (465.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
```

---

### Post by walawa on 2010-11-13
According to "parted /dev/sdb print" the partition table is msdos, but it was created using disk utility and hfs+. Does that make sense?

---

### Post by srs5694 on 2010-11-13
According to gdisk, the disk is a standard MBR disk with no partitions defined. This is consistent with what parted is saying, but both of these tools disagree with what OS X is saying. In OS X, could you please run the following command from an OS X Terminal and post the results back?

```

sudo diskutil list

```

This might give some clue about why OS X is reporting the presence of partitions where Linux can't seem to find them.

---

### Post by walawa on 2010-11-13
"sudo diskutil list" :
```
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *111.8 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            111.5 Gi   disk0s2
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *465.8 Gi   disk2
   1:        Apple_partition_map                         31.5 Ki    disk2s1
   2:             Apple_Driver43                         28.0 Ki    disk2s2
   3:             Apple_Driver43                         28.0 Ki    disk2s3
   4:           Apple_Driver_ATA                         28.0 Ki    disk2s4
   5:           Apple_Driver_ATA                         28.0 Ki    disk2s5
   6:             Apple_FWDriver                         256.0 Ki   disk2s6
   7:         Apple_Driver_IOKit                         256.0 Ki   disk2s7
   8:              Apple_Patches                         256.0 Ki   disk2s8
   9:                  Apple_HFS Disque externe          400.0 Gi   disk2s10
  10:                  Apple_HFS Tristan                 65.5 Gi    disk2s12
```

---

### Post by walawa on 2010-11-14
I ran testdisk on this drive and it managed to identify both lost partitions and their start and end sectors. Only it couldn't write the partitions and gave this message : "Function write_part_mac not implemented
Use pdisk to recreate the missing partition using values displayed by TestDisk".

So I did some research and read that this can be done manually using parted. First by restoring the partition table with the mklabel command and then by writing the partitions with mkpart, using the start and end info from testdisk. Only I'm afraid if I do this and it goes wrong I might lose access to this drive from the Mac, which is the only way I can read it right now.

Should I attempt this or is there a better way?

---

### Post by walawa on 2010-11-14
Also, parted lists the partition table of the drive as "msdos" but Disk Utility says it's Apple. If I use mklabel, just I make it mac or msdos?

---

### Post by srs5694 on 2010-11-14
OS X is identifying the disk as an APM disk ("Apple_partition_scheme"), although the gdisk tests for APM data are failing to find an APM signature. My suspicion is that the disk is a perfectly valid APM disk but that some utility went and wrote an MBR on it because it didn't recognize the APM data, and this is confusing GParted and may even have overwritten the signature that gdisk normally uses to identify APM disks.

As the developer of gdisk, I'd appreciate getting a copy of the first few sectors of the disk so that I can study this and see if I should be updating my gdisk partition table identification code. Could you please run the following command and send me the resulting apm.out file at [email]rodsmith@rodsbooks.com[/email]? (This command sends me the first ten sectors of the disk, which should contain no sensitive data.)

```

sudo dd if=/dev/sdb of=apm.out bs=512 count=10

```

If you run it from OS X rather than Linux, change "/dev/sdb" to "/dev/disk1". Thanks.

As to how to proceed, I'm not sure precisely how to repair the damage, but I have several suggestions to try, in increasing order of desperation:


[list=1]
[*]Use Apple's Disk Utility to make some minor change to the disk, such as altering the name of a volume. With any luck, it will automatically fix the damage.
[*]Make a more extreme change to the volume using Apple's Disk Utility. For instance, you could delete a partition or create a new one (if there's any free space).
[*]Attempt to replace the bogus MBR data with valid APM data. Unfortunately, I know very little about the details of APM data, so my only suggestion is to create a valid APM volume (on a USB flash drive, say) using OS X's Disk Utility and then copy it over using dd, as in "dd if=/dev/disk2 of=/dev/disk1 bs=512 count=1". *Be sure to include the bs= and count= options!* You might need to increase the count value to 2. I have no idea if this will work, though; it could be that the APM sector 0 data must vary with the disk size or some other feature that varies with the disks.
[*]Copy the data off the affected disk, repartition using MBR or GPT rather than APM, and then copy the data back. You should probably do all this in OS X, although you could use Linux.
[*]Use TestDisk to attempt to recover the partitions as MBR partitions. You'll have to find some way to force it to treat the disk as an MBR disk, since from what you report, it seems to be detecting some APM data and is trying to treat it as an APM disk. I'm not an expert on APM, so I can't offer any specific suggestions for how to do this.
[/list]


As a general comment, it's best to use MBR or GPT these days; Apple has largely abandoned APM, although it's still supported in the OS and in Disk Utility. MBR (referred to as "ms-dos" in most libparted-based tools) is the old-style partitioning scheme that's used on most PCs, but MBR is living like the dinosaurs 65 million years ago: There's a giant meteor, in the form of the 2 TiB limit, that will soon cause MBR's extinction. GPT is the answer to this problem, and Apple has already embraced it on its Intel-based Macs. Linux is happy with any of these partition tables, although I'm not sure if it's possible to boot Linux from APM on a PC.

---

### Post by walawa on 2010-11-14
Thanks for your response.

I've emailed you the output of that command. In Disk Utility, I had previously tried to disable journaling and to "repair" one of the paritions. Both attemps failed. I don't know if that indicates anything. I will try to create a new partition, and see if that helps. 

So, does this mean writing a new partition table and restoring the partitions through parted would not be a good solution?


I intend to reformat that drive anyway, seeing how screwed up it is, I just need to be able to read it in Ubuntu so I can make a backup of it first.

---

### Post by walawa on 2010-11-14
I actually tried to repair the disk using Disk Utility again, but this time I noticed the problem it detected was with the volume's bitmap.

---

### Post by srs5694 on 2010-11-14
Creating a new partition table and restoring manually will also work, provided you can figure out the *exact* start and end points of the partitions. The OS X diskutil output you posted doesn't provide information to that level of detail, but perhaps there's a way you can get that. (TestDisk will do so, but it presents data in CHS values, at least for MBR disks; I don't know if it'll present LBA data for your disk. CHS values are weird and easy to mis-translate into LBA values.)

---

### Post by walawa on 2010-11-18
Well, I created a new partition table, restored the partitions and I've managed to salvage all of my files. 

Thanks to everyone who responded

---

