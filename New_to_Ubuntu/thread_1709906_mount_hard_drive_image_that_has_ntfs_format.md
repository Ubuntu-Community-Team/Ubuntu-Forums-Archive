---
title: "mount hard drive image that has ntfs format?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-03-19
ok wanted to image my mom computer. Her computer is windows 7 and has ntfs. So... how do I mount it? Below is what I did.

used ddrecuse from apt-get install gddrecuse

custom@custom:~$ sudo ddrescue -v /dev/sda ~/mom/mom03142011.img ~/mom/logfile


About to copy 320072 MBytes from /dev/sda to /home/custom/mom/mom03142011.img
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Max_retries: 0    
Direct: no    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:   320072 MB,  errsize:       0 B,  current rate:   17235 kB/s
   ipos:   320072 MB,   errors:       0,    average rate:   21384 kB/s
   opos:   320072 MB,     time from last successful read:       0 s
Finished       

custom@custom:/media/My Passport/mom$ sudo mount -t ntfs-3g -o loop mom03*.img /mnt
NTFS signature is missing.
Failed to mount '/dev/loop1': Invalid argument
The device '/dev/loop1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

custom@custom:/media/My Passport/mom$ file -s mom03142011.img
mom03142011.img: x86 boot sector; partition 1: ID=0x7, active, starthead 32, startsector 2048, 407552 sectors; partition 2: ID=0x7, starthead 126, startsector 409600, 598294528 sectors; partition 3: ID=0x7, starthead 254, startsector 598704128, 26435584 sectors, code offset 0xc0

custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d769ec6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       37268   299147264    7  HPFS/NTFS
/dev/sda3           37268       38914    13217792    7  HPFS/NTFS

---

### Post by taseedorf on 2011-03-19
not exactly sure, but remember when you mount something you are only mounting a partition and not an entire drive....so mounting it as an NTFS drive is incorrect, especially considering it is in an .img format....

try mounting it similar to mounting another img file.

---

### Post by quirks on 2011-03-19
taseedorf is right - you are trying to mount an **entire drive**, even though you should be mounting an **individual partition on the drive**. I can think of two ways to mount a partition, which is inside an image:

- extract the partition into a separate file (this requires extra disk space the size of the partition to be extracted)
- use the "offset" option of "mount -o loop"

In either case, you will need to find out, where the partition starts. I found an article that describes both methods:
[http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux]("http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux")

If you run into problems, just ask.

---

### Post by lance bermudez on 2011-03-19
thank you all for your help. below is how I got it to work with your help.
sudo apt-get install parted
sudo parted *.image
(parted) unit
Unit? [compact]? B
(parted) print
Model: (file)
Disk /media/My Passport/mom/mom03142011.img: 320072933376B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1048576B 209715199B 208666624B primary ntfs boot
2 209715200B 306536513535B 306326798336B primary ntfs
3 306536513536B 320071532543B 13535019008B primary ntfs
(parted) quit
mount -o loop,ro,offset=1048576 /media/M*assport/mom/mom03142011.img /mnt/1
mount -o loop,ro,offset=209715200 /media/M*assport/mom/mom03142011.img /mnt/2
mount -o loop,ro,offset=306536513536 /media/M*assport/mom/mom03142011.img /mnt/3

---

