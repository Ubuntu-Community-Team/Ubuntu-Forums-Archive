---
title: "What is Fastest file systems for USB in a PURE Linux Setting"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Ronok on 2010-09-03
What is the _Best_ 
(and most importantly The _**Fastest**_)
**["File System Type"]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")** for Copying To & From **[SIZE="4"]USB[/SIZE]**

in a **PURE:  [ UBUNTU LINUX  <--- TO --->  UBUNTU LINUX ]** scenario

(no [MSFT]("http://en.wikipedia.org/wiki/Infectious_diseases") anywhere)
although there is a Lot of Chatter about how to this or that with [MSFT]("http://en.wikipedia.org/wiki/Infectious_diseases") in the [UBUNTU Forums]("http://ubuntuforums.org/index.php?page=about")
I Have NO need of EVER interacting with anything [MSFT]("http://en.wikipedia.org/wiki/Infectious_diseases") at all

_Only with_ an:
-> **Ubuntu Linux** Computer & 
-> a Backup external **USB** Hard drive (about 500GB) or
-> **USB** thumb drive (about 8GB)
-> and or another **UBUNTU Linux** Machine

Not Sure which might be best:
[_ext3_]("http://en.wikipedia.org/wiki/Ext3"), [_ext4_]("http://en.wikipedia.org/wiki/Ext4"), or some other "[_Btrfs_]("http://en.wikipedia.org/wiki/Btrfs")" or "[_FFS_]("http://en.wikipedia.org/wiki/Berkeley_Fast_File_System")" or "[_XFS_]("http://en.wikipedia.org/wiki/XFS")", Not Sure, but

it does _Not_ need to be Universal, 
it _Just_ Needs to Work **Best** 
on _Just_ Ubuntu **Linux**
It needs to be **FAST** & predictable 
and Pragmatic for the entry level user
**Thanks** for any suggestions
[Ronok]("http://www.gongkuo.com/index.htm")

on typically this or a better but similar machine:
Ubuntu: 9.10
Linux: 2.6.31-22-generic
Gnome: 2.28.1
CPU: Intel 2 @ 2GHz
L2 cache: 512 KB
&
Typically Moving 100 GB of files sized 80KB to 800MB But average 800KB

---

### Post by ajgreeny on 2010-09-03
I'm not sure this answers your question completely, but my USB hard disk is formatted to ext3, as I also only need linux file systems (no M$).

One big advantage of that and other linux file systems over ntfs or the more common fat32 is in file permission retention.

---

### Post by HermanAB on 2010-09-03
Well, of the journaled file systems, JFS is probably the fastest.  Ext2 would be faster than any, but using a non-journaled FS on a removable device would be irresponsible.

---

### Post by Ronok on 2010-09-03
Thanks: _ajgreeny_  for your fast reply and insight
Thanks: _HermanAB_  for tip to Look at "JFS"

I am looking in to it here: [_Journaled File System or JFS_]("http://en.wikipedia.org/wiki/JFS_%28file_system%29#JFS_in_Linux")

ok in 
Palimpsest Disk Utility 2.28.0
I don't see an option to choose JFS
and in 
GNOME Partition Editor: GParted 0.4.5
for me it Grayed-out, so I can't pick it from the list ? not sure why

also not sure if there is anything Advantageous or
if it is imperative that I choose anything different at

System > Administration > Gparted > Device > Create Partition Table > Advanced > Select New Partition Table Type > (list of)

or Just "MSDOS" ?

would someone using JFS also need to Make a Slack Allocation ?
also is there a reason not to use ext4 over ext3 ? 
for the above scenario

ok I will do Some tests Tomorrow
Thanks again

---

### Post by Ronok on 2010-09-17
Test **Report:**

(Basically happy and 
would like to Mark as Solved, 
Yet there are a few Lingering Questions)

I tried Both **EXT3** & **EXT4** and found Both to be LIKE _WAY Faster_ than **Fat32**
with **EXT4** Seeming to be a Little faster than _EXT3_

**Fat32** = many hours maybe hangs or has an Error
**EXT4** = Backed up whole Hard Disk in a Few Minutes

I also tried this code:

me@my-computer-name:~$ **sudo hdparm -Tt /dev/sda && sudo hdparm -Tt /dev/sdb**

/dev/sda:
 Timing cached reads:   1296 MB in  2.00 seconds = 648.24 MB/sec
 Timing buffered disk reads:  200 MB in  3.01 seconds =  **66.44 MB/sec**

/dev/sdb:
 Timing cached reads:   1226 MB in  2.00 seconds = 613.48 MB/sec
 Timing buffered disk reads:   90 MB in  3.06 seconds =  **29.38 MB/sec**

ok so I am Happy...

But Curious if anyone Can answer these **3** Questions:


**1)**
on a 160 GB Verbatim Remote USB Backup Hard Disk
well is "29.38 MB/sec" Fast or just OKish any opinions ?

[B]
2)[/B]
I tried: 

me@my-computer-name:~$ sudo hdparm **-I** /dev/sd**a**

/dev/sda:

ATA device, with non-removable media
	Model Number:       etc...                   
	Serial Number:      etc...  
	Firmware Revision:  etc...  
etc...  etc...  etc...  LONG list of interesting info 

BUT 

me@my-computer-name:~$ sudo hdparm **-I** /dev/sd**b**

/dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange

Why this Error ?

**3)**
also not sure if there is anything Advantageous or
if it is imperative that I choose anything different at

System > Administration > Gparted > Device > Create Partition Table > Advanced > Select New Partition Table Type > (list of)

or Just "MSDOS" ?

Thanks Again
Ronok

[SIZE="1"][http://www.gongkuo.com/index.htm]("http://www.gongkuo.com/index.htm")[/SIZE]

---

### Post by cariboo on 2010-09-17
> me@my-computer-name:~$ sudo hdparm -I /dev/sdb

/dev/sdb:
HDIO_DRIVE_CMD(identify) failed: Invalid exchange

Why this Error ?

Not all hdparm options work with usb drives.

The way to get a true reading of the speed of your usb drive is to use a command similar to this:

```
time dd if=/dev/zero of=/mountpoint/test.bin bs=1000000000 count=1
```

This will create 1Gb file and give the time it took to create the file. In the above command mountpoint, is where yor usb drive is mounted. The file system won't make that much difference, as you are limit to the data transfer speed of the USB bus.

I tried the above command on an 8Gb thumb drive, this is the results I get:

> time dd if=/dev/zero of=/media/1C0C-FE5F/test.bin bs=1000000000 count=1
1+0 records in
1+0 records out
1000000000 bytes (1.0 GB) copied, 97.5813 s, 10.2 MB/s

real	1m37.749s
user	0m0.000s
sys	0m4.040s

Just for comparison the result for an internal drive look like this:

> time dd if=/dev/zero of=test.bin bs=1000000000 count=1
1+0 records in
1+0 records out
1000000000 bytes (1.0 GB) copied, 20.4891 s, 48.8 MB/s

real	0m20.894s
user	0m0.000s
sys	0m3.490s

---

### Post by Ronok on 2010-09-18
**Thank you Kindly: cariboo907**

I am out at a Net-Bar at now,
when I get back to that Laptop
I will do your recommended Test
and Report back here,

Thanks Again !

---

