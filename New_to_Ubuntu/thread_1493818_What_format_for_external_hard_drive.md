---
title: "What format for external hard drive?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by paker on 2010-05-26
I have a brand new SATA hard disk, Western Digital 5900 rpm 2 TB, to be specific. I will use it to store audio and video files through eSATA. It will be connected only when dumping internal hard disk. Otherwise, on shelf.

I need to retrieve files from the hard disk occasionally both from ubuntu 9.10 and Windows Vista. **What format would you recommend?**  

Use EXT3 and install driver on Windows Vista machine?
Use NTFS and install driver on ubuntu 9.10 machine?
Use FAT 32?

Or,

Use EXT3/4 and use USB thumb drive as go-between the hd and Vista machine?

Thanks.

---

### Post by sandyd on 2010-05-26
use ntfs. you dont need to install any driver on windows or linux for that. plug and play.

---

### Post by inameiname on 2010-05-26
I agree with Carlee. NTFS is the way to go.

---

### Post by rcayea on 2010-05-26
I agree with NTFS.

---

### Post by 3rdalbum on 2010-05-26
Fat32 if all files stored on it will be under 4 GiB (that's increasingly unlikely with video, though).

Ext2 if those Ext2 filesystem drivers for Windows are available for Vista, and you'll only be using the disk on your own computers.

NTFS if there's no Ext2 driver for Vista, or if you're going to be using the disk on computers that you don't own. NTFS is quite slow to write to, on Linux.

---

### Post by inameiname on 2010-05-26
I don't think the write speed for NTFS on Linux is all that bad. 

Besides, for just another drive that is planned to just be used for storage, it should be just fine.

---

### Post by CharlesA on 2010-05-26
+9000 for NTFS. That would work the best for going between Windows and Linux.

---

### Post by paker on 2010-05-26
I can sacrifice some write speed for convenience, unless it's WAY slow. I hope it's not USB-slow. I will be dumping 100-200 GB at a time. Most re-connections to computer will be for reading off the hard drive. 

I didn't know ubuntu can read ntfs. Apparently, WD20EARS comes preformatted to ntfs. I am all set to go.

Thank you.

---

### Post by srs5694 on 2010-05-26
> **paker said:**
> I didn't know ubuntu can read ntfs. Apparently, WD20EARS comes preformatted to ntfs. I am all set to go.

If the unit uses a WD20EARS internally, you should double-check the drive alignment, especially if you partition the disk yourself. (It's almost certainly OK if it really is set up with NTFS at the factory, but it won't hurt to check.) See [this piece I wrote for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for all the details.

---

### Post by paker on 2010-05-26
> **srs5694 said:**
> If the unit uses a WD20EARS internally, you should double-check the drive alignment, especially if you partition the disk yourself. (It's almost certainly OK if it really is set up with NTFS at the factory, but it won't hurt to check.) See [this piece I wrote for IBM developerWorks](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for all the details.

It's too much for me to read, I mean, too technical. Please kindly tell me "what to do." **NTFS or not?** Internal drive is Seagate 7200 rpm drive, ubuntu 9.10 single boot. It's not a 4KB sector hd. 

Thanks.

---

### Post by lil0tik on 2010-05-26
I use NTFS for all my external drives, as well as my internal "archiving" disk. The r/w speed doesn't seem too bad, even over USB (rather, USB access doesn't seem any slower than with any other USB drive).  

The only issue I've run into with NTFS is having to mount the drive (internal or external) manually via the terminal every time I want to use it, but this is an issue with my own slightly wonky setup and automounting tools are readily available for users on standard Ubuntu installs.

Now that I'm thinking about it, I wonder about fragmentation with NTFS in Ubuntu.  I'm just realizing I've never defrag'd the drive, and I don't think just using Linux solves the problem of NTFS and drive fragmentation, does it?

---

### Post by srs5694 on 2010-05-26
> **paker said:**
> [quote=srs5694]If the unit uses a WD20EARS internally, you should double-check the  drive alignment, especially if you partition the disk yourself. (It's  almost certainly OK if it really is set up with NTFS at the factory, but  it won't hurt to check.) See [this piece I wrote for IBM developerWorks]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/") for all  the details.It's too much for me to read, I mean, too technical. Please kindly tell me "what to do." **NTFS or not?** Internal drive is Seagate 7200 rpm drive, ubuntu 9.10 single boot. It's not a 4KB sector hd.[/QUOTE]

You strongly implied that the model number is WD20EARS:

[quote=paker]Apparently, WD20EARS comes preformatted to ntfs. I am all set to go.[/quote]

The WD20EARS *is* an Advanced Format drive with 4096-byte physical sectors and 512-byte logical sectors. To be the best of my knowledge, it doesn't come set up with NTFS (my WD10EARS certainly didn't); however, external disks based on this model might come this way. My impression is that pre-partitioning and formatting are more common with external drives than with internal drives. If you mis-stated the model number, then the issues with these drives may not apply to you. If it comes pre-partitioned at the factory, then those partitions are almost certainly set up properly. If you get a WD20EARS drive and need to create or modify partitions in Linux (using fdisk, parted, GParted, or any other Linux partitioning tool), you really *must* learn about the issues with these drives or risk *severe* performance problems.

I was not addressing the filesystem issue in my post, but the issue of filesystem performance. If the article to which I linked is written at too technical a level, then I have one suggestion: learn. WD tries to dumb it down in their own Web pages on Advanced Format, and they do Linux users a disservice by doing so because their attempts to simplify matters end up distorting the facts beyond recognition and to the point that most Linux users who believe them will be led astray. I don't think I could do any better, so when given the choice of dumbing it down further or referring to what I've already written, I'll refer to what I've already written. If you don't understand the issues involved, then the odds of your creating a configuration that will cause *severe* performance degradation are very high. Yes, I've emphasized that word twice now. Check Figure 2 in my article -- some operations can take *twenty-five times as long* on an improperly prepared disk as on one that's properly prepared.

If you don't want to learn about the issues, then you should avoid these drives like the plague. You can still do so, but other manufacturers are planning to introduce similar drives in the not-too-distant future, so sooner or later, you'll have to deal with them. By that time the Linux tools for partitioning disks will be more likely to handle the drives properly by default, but at the moment, you must understand how to ensure that the job is done right or you risk very poor performance.

---

### Post by paker on 2010-05-27
You were right. It doesn't come preformated to ntfs. 

Now I have a problem. When I connect Western Digital WD20EARS through eSATA, computer doesn't recognize it. Disk Utility doesn't show it. But when connected through USB (SATA-USB adapter), Disk Utility sees it as unformatted.

I select NTFS, and hit format. I get error.


Please help.

---

### Post by CharlesA on 2010-05-27
It helps to know the error.

Don't need you need reboot, so that the BIOS will detect an eSATA drive?

---

### Post by sebastien.r on 2010-05-27
> **paker said:**
> You were right. It doesn't come preformated to ntfs. 

Now I have a problem. When I connect Western Digital WD20EARS through eSATA, computer doesn't recognize it. But when connected through USB (SATA-USB adapter), computer sees it as unformatted.

I'll go out on a limb and guess that you plugged in the external 2T while the machine was on via eSATA ( correct me if this is wrong).
Connect the HDD with the machine powered down and use the disk utility to format the drive.

---

### Post by paker on 2010-05-27
I did exactly as you guessed. I thought SATA was a hot connection. I will power off the computer first and make connection. Thanks.

---

### Post by egalvan on 2010-05-27
> **paker said:**
> 

I need to retrieve files from the hard disk occasionally both from ubuntu 9.10 and Windows Vista. **What format would you recommend?**

Another idea, but feasible only if both machines are on your local network;

format the drive with a Linux file-system (ext3 or ext4).
only connect it to the Linux machine...
use SAMBA to access from Windows when needed.

---

### Post by cascade9 on 2010-05-27
> **paker said:**
> I can sacrifice some write speed for convenience, unless it's WAY slow. I hope it's not USB-slow. I will be dumping 100-200 GB at a time. Most re-connections to computer will be for reading off the hard drive. 

I didn't know ubuntu can read ntfs. Apparently, WD20EARS comes preformatted to ntfs. I am all set to go.

Thank you.

It shouldnt be USB slow, even if the partitions arent aligned. 

> **srs5694 said:**
> The WD20EARS *is* an Advanced Format drive with 4096-byte physical sectors and 512-byte logical sectors. To be the best of my knowledge, it doesn't come set up with NTFS (my WD10EARS certainly didn't); however, external disks based on this model might come this way. My impression is that pre-partitioning and formatting are more common with external drives than with internal drives. If you mis-stated the model number, then the issues with these drives may not apply to you. If it comes pre-partitioned at the factory, then those partitions are almost certainly set up properly. If you get a WD20EARS drive and need to create or modify partitions in Linux (using fdisk, parted, GParted, or any other Linux partitioning tool), you really *must* learn about the issues with these drives or risk *severe* performance problems.

Externals tend to come pre-partitioned. (not in this case though)

Just to make things even more annoying, I wouldnt be at all surpised if pre-partitioned externals come with the 'advanced format' (xp single partiton) jumper set. Which might not be a bad idea to do, if getting into the case to change the jumper isnt really hard and you are planning on having a single partition.

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5324&p_created=&p_cats=185&p_cv=1.185&p_pv=2.294&p_prods=227%2C294#jumper](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5324&p_created=&p_cats=185&p_cv=1.185&p_pv=2.294&p_prods=227%2C294#jumper)

BTW paker, I know it can be a pain to learn this sort of stuff, but really...its worth it, if you are going to be dumping a lot of files to this drive, you really want it to be nice and fast.

---

### Post by paker on 2010-05-28
Okay, now the hd is recognized by Disk Utility, unpartitioned and unusuable.
I have to choose format and partition table. I know I will be using ntfs. What about partition table? I have to choose from Master Boot Record, GUID, and No Partition. I will be using the hard drive as external storage and don't need multiple partitions.

I am still studying the disk alignment thing. Since I will be using the entire disk space as one partition, I can just use a jumper to move starting point to cylinder 63. Is this correct?

Thanks.

---

### Post by Kellemora on 2010-05-28
Hi Paker

As far as getting your drive going again, you will probably have to rewrite the MBR, then you should be good to go.

FWIW:  ALL but one of our external hard drives are formatted to NTFS for the simple reason someone not familiar with Linux may need to access those drives.

But our setup is fairly simple, an internal 500 gig sata formatted to ext3 and is used for quick access to data we use daily.  However, each night or more often, we mirror the internal 500 gig to an external 500 gig usb also formatted as ext3, then this is mirrored drive is mirrored to another external drive formatted to NTFS and it's plugged into a Linux only box used as a file server.  Then the NTFS drive is mirrored off-site, just in case the place burns down.  Most of our data is redundant in 3 locations, one location is over 500 miles from here too.
Rsync only copies the changed or new files to the off-site storage, we don't delete old files until the drives are nearly full.  

We have drives for Active Data, Archived but Current Data and one for Permanent Data that is strictly read only.  EG:  Image files of family photo's, copies of documents, closed accounting records, etc.  These are all NTFS drives so they can be read on Windows machines if necessary.

TTUL
Gary

---

### Post by srs5694 on 2010-05-28
> **paker said:**
> Okay, now the hd is recognized by Disk Utility, unpartitioned and unusuable.
I have to choose format and partition table. I know I will be using ntfs. What about partition table? I have to choose from Master Boot Record, GUID, and No Partition. I will be using the hard drive as external storage and don't need multiple partitions.

Master Boot Record (MBR) is the most broadly recognized; everything from DOS through to the latest modern OSes can handle MBR. OTOH, MBR has issues because of the distinction between primary, extended, and logical partitions and other annoyances. The GUID Paritition Table (GPT) scheme is more flexible and it's usable by modern OSes, including Linux, Windows Vista and later, and Mac OS; however, older OSes such as Windows XP can't read it, and even Windows 7 can't boot from it on BIOS-based computers. As this is an external storage-only drive, Windows' inability to boot from the disk isn't likely to be a big deal, but if you want to read the drive from XP, GPT might not be a good choice. If you expect to use only more recent OSes, GPT has its advantages.

> I am still studying the disk alignment thing. Since I will be using the entire disk space as one partition, I can just use a jumper to move starting point to cylinder 63. Is this correct?

I recommend against using the jumper, simply because you might want to modify the partitioning scheme in the future, and using the jumper will require you to use very strange partition alignment that may be very difficult to set.

The simplest approach is to use a Windows Vista or Windows 7 partitioning tool, since these OSes' native tools align partitions properly for Advanced Format disks. (Windows XP is a poor choice for this, since it creates cylinder-aligned partitions.) GParted still has very poor alignment options. If you must use a Linux tool, your best options are the text-mode tools, and especially fdisk (for MBR) or gdisk (for GPT), although the text-mode parted can work, too. If you use fdisk or gdisk, you'll have to use mkfs to create a filesystem on the partition. Both fdisk and gdisk are partitioning tools alone; they don't create or manipulate filesystems.

Whatever tool you use, you can double-check the alignment by typing "sudo fdisk -lu /dev/sdb" or "sudo gdisk -lu /dev/sdb" (changing "/dev/sdb" to whatever your disk device is). Check that the partition start points are all multiples of 8. If they aren't, the partitions aren't properly aligned.

---

### Post by paker on 2010-05-28
Thanks for the replies.

I selected NTFS and MBR and partitioned the hd. Moved 50 audio files 20-40 MB per file. I got 37-40 MB/s transfer rate (read from the file transfer dialogue). Okay?

I ran "sudo fdisk -lu /dev/sdb" and here is the output:

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002fdac

   Device Boot.....Start..........End....................Blocks............ID...........System
/dev/sdb1............63.....3907024064.....1953512001.....7..........HPFS/NTFS

Does this look okay? 63 (sectors/track) is not a multiple of 8.

Thanks.

PS: No Jumper used. Single partition

---

### Post by -humanaut- on 2010-05-28
Just depends what your gonna put on there if your going to be moving large files on it and you decide to put Linux on it I'd recommend XFS.

---

### Post by paker on 2010-05-28
> **-humanaut- said:**
> Just depends what your gonna put on there if your going to be moving large files on it and you decide to put Linux on it I'd recommend XFS.

Video files are 500 MB to 2 GB per file.
Audio files are 10 MB to 50 MB per file.

Unless I sacrifice a lot of speed, I want read access from both Windows Vista and Ubuntu. Write access will be exclusively from Ubuntu machine.

Someone please comment on **alignment** (2 posts above). Thanks.

---

### Post by QIII on 2010-05-28
The number of sectors is not required to be a multiple of 8.  63 is common.  What is generally of note is that there usually are 512 bytes of info per sector per track.

This is key, and in the information you included:

255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes

3907029168 * 512 = 2000398934451712 bytes ... actually slightly less than 2 TB.

Because of their geometry, disks are never exactly the "advertized" size.

If you were to use a tool to find how much space was available on the drive, you'd find it was less than exactly 2TB.  That is due to geometry and the overhead of the manner in which a disk is formatted.

---

### Post by srs5694 on 2010-05-28
> **paker said:**
> Device Boot.....Start..........End....................Blocks............ID...........System
/dev/sdb1............63.....3907024064.....1953512001.....7..........HPFS/NTFS

Does this look okay? 63 (sectors/track) is not a multiple of 8.

No. You're set up for degraded performance. How bad it will be depends on the filesystem and how large the files you'll be transferring are. I've not done tests using NTFS, but Linux filesystems are degraded up to 25 times on small files -- that is, an operation that takes 10 seconds on properly-aligned partitions could take up to 250 seconds on improperly-aligned partitions such as yours. I've seen reports from Windows users suggesting that there are big effects on NTFS in Windows, but I don't happen to have any URLs handy. Also, performance effects in Linux could be greater or lesser than in Windows, since the filesystem implementation can be as important as the filesystem data structures. Thus, I can't say precisely how bad the effect will be for you, but I can be pretty sure that there will be an effect.

Your easiest course of action at this point is to go to the [Western Digital Advanced Format](http://www.wdc.com/en/products/advancedformat/) page, download their utility that fixes these problems, and run it.

Alternatively, repartition the disk but use the advice on [this link I provided earlier](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) to do it properly. This is most easily accomplished using fdisk or gdisk, but the former only if you follow the advice for using non-default options and the latter only if you use a reasonably recent version of the program (the one in the Ubuntu repositories is ancient) or take care to start your partition on a sector with a multiple-of-8 value, such as 40 or 2048.

[quote=QIII]The number of sectors is not required to be a multiple of 8.  63 is  common.  What is generally of note is that there usually are 512 bytes  of info per sector per track.[/quote]

Although this is technically correct, in this case it's very bad advice. Paker has a Western Digital "Advanced Format" disk, which uses 4096-byte physical sectors and 512-byte logical sectors. The result is that if a write operation doesn't overwrite all eight sectors in the physical sector, the disk has to first read the physical sector, then modify part of it, then write it back out. This takes more time than it takes to simply overwrite all 4096 bytes. Since many disk structures come in 4096-byte blocks, disk performance is optimized if partitions begin on 4096-byte (8-sector) boundaries. If they don't, then when a 4096-byte data structure is modified, two read-then-write operations must be performed, and this degrades performance compared to a single write operation (with no need to read it).

[quote=QIII]Because of their geometry, disks are never exactly the "advertized"  size.[/quote]

This isn't true. The difference between advertized and measured capacity is an effect of power-of-2 vs. power-of-10 measurements. Disk manufacturers use the (more technically correct) power-of-10 measurements for disks. For instance, a 2TB disk is 2 x 10^12 bytes in size, but most disk utilities use power-of-2 measurements, such that 2TB is 2 x 2^40. In other words, many disk utilities define "TB" to be what is really tebibytes (TiB). A disk with a capacity of precisely 2TB, as disk manufacturers define things, is therefore more like 1.819TiB in capacity, and many disk utilities report "TiB" as "TB," so a disk utility will claim that a 2TB disk is 1.819TB in size. See [this Wikipedia entry,](http://en.wikipedia.org/wiki/Binary_prefix) [this NIST site,](http://physics.nist.gov/cuu/Units/binary.html) or many others you can find by Googling for more details. This has nothing to do with disk geometry, which today is a fiction maintained for reasons of backward compatibility with obsolete OSes and ancient data structures.

---

### Post by paker on 2010-05-28
> **srs5694 said:**
> .......Your easiest course of action at this point is to go to the [Western Digital Advanced Format](http://www.wdc.com/en/products/advancedformat/) page, download their utility that fixes these problems, and run it.

[COLOR="Navy"]They don't have a utility for Ubuntu. [/COLOR]

Alternatively, repartition the disk but use the advice on [this link I provided earlier](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) to do it properly. This is most easily accomplished using fdisk or gdisk, but the former only if you follow the advice for using non-default options and the latter only if you use a reasonably recent version of the program (the one in the Ubuntu repositories is ancient) or take care to start your partition on a sector with a multiple-of-8 value, such as 40 or 2048.

[COLOR="Navy"]How do I make the partition to start at sector 64?
[/COLOR]Thanks for helping me out.

---

### Post by geet89 on 2010-05-28
go with ntfs.. but your read and write speeds will be a bit slower on linux

---

### Post by QIII on 2010-05-28
(Please insert friendly discussion tone here ...)

I like the idea of larger sector sizes and greater efficiency.  If WD has this available, I'm all for it.  I made no recommendation, I only commented on commonality.

I will admit to haste, in that I used a prefix commonly rather than technically (in the light of a standard that has not yet been universally accepted).  Your heads-up on the prefixes came a little late.  I use the non-decimal prefixes in discussions about the ability of 32 and 64 bit OSs to address a given amount of memory.  

So, I will concede that a disk manufacturer can call it a 2TB disk exactly, under his definition and outweighed 1024 to 1000.

As for disk geometry, I do have to beg to differ.  

Disk geometry itself is not a fiction.  What about 512 bytes?  I wouldn't call that a "fiction" as much as an artifact from bygone days.  2^9.   Or is it? 

What are certainly no longer considerations are things like the old BIOS limitation of cylinders never exceeding 1023 and the tricks that had to be played to get around that limitation as disks grew large faster than BIOSs could handle them.  That discussion of geometry is long gone.

But the BIOS consideration of 512 byte sector sizes may still be an issue in some cases.  Not all technologies advance at exactly the same time.

While the use of WD's technology will create larger sectors for efficiency and error checking and shift the first sector, "geometry" is still a consideration.  And I am still not convinced that Vista and beyond will not expose new considerations as this sorts itself out.

Strict usage of powers of 10 is convenient for engineering (I am one, by the way, by education and a long career.  But I'm also a Mathematician and don't always feel frightened by stepping away from 10), but there are problems when that comes to actual "usable" space as it applies practically, which is what the user is interested in. There will still not really be the amount of usable space he expects, even if the theoretic improvements are realized, There will still be sector gaps for timing and the addresses and checksums for tracking/checking errors.  They will be smaller and the efficiency of the algorithms will improve, but they are, in fact, geometry considerations.  Gaps will still radiate from the spindle and will still be, physically, wider as one moves further out on the disk platter.  In terms of the angular velocity of any point on the disk at some distance from the axis, the traverse time stays the same.

Some portion of the sectors will still contain those reserved address locations.  Or are you saying that the disk manufactures say they have a 2TB disk PLUS additional space for all that?

---

### Post by srs5694 on 2010-05-28
> **paker said:**
> .......Your easiest course of action at this point is to go to the [Western  Digital Advanced Format]("http://www.wdc.com/en/products/advancedformat/") page, download their utility that fixes  these problems, and run it.[quote=srs5694]
[COLOR=Navy]They don't have a utility for Ubuntu.[/COLOR][/QUOTE]

True, but they do have a utility that runs from a bootable CD/DVD. Tell the Web page that you're using Windows 7, that you used a cloning utility, that the disk is your primary disk, and that you have two partitions on the disk. (Other answers will probably also get you to the right point; I've just checked that this specific set of answers will do so.) You'll then be able to download the Acronis Boot CD to do the realignment.

> **QIII]Disk geometry itself is not a fiction.  What about 512 bytes?  I  wouldn't call that a "fiction" as much as an artifact from bygone days.   2^9.   Or is it?[/quote]

The 512-byte sector size isn't a fiction for most disks, but it is for "Advanced Format" drives, as I described. My original objection, though, was your your specific statement:

[quote=QIII]Because of their geometry, disks are never exactly the "advertized" size.[/quote]

This statement is technically true, but given its context, I interpreted it as an attempt to explain the difference between, for instance, the claimed capacity of a "2 TB" drive and a disk utility's report that the drive is roughly "1.82 TB" in size. That ~0.18 TB difference is due to the differing definitions of "TB" used by the manufacturer and the disk utility. The disk's geometry doesn't enter into this difference except for a very minor effect several decimal points out.

If you simply meant to say that a "2 TB" drive might actually be 2.000398934451712 TB because of disk geometry effects, then you're right. That wasn't the context of the quote, though said:**
> Some portion of the sectors will still contain those reserved address locations. Or are you saying that the disk manufactures say they have a 2TB disk PLUS additional space for all that?

I didn't mean to get into a discussion of the inter-sector data on disks. Now that you bring it up, though, a "2 TB" disk *does* have 2 TB of user-addressable data storage, plus the space for the inter-sector checksums and other data -- *if* one accepts the disk manufacturer's definition of "TB". Consider Paker's original disk information:

[quote=paker]Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes[/quote]

That's 2.000398934016 TB, using "TB" to be 10^12 bytes. Disk manufacturers have always used this definition (or set of definitions, starting back in the days of hard disks with sizes measured in megabytes). Most, but not all, other computer measures have been in base-2, so the discrepancy has always caused confusion, and people have always misattributed the difference to "formatting overhead" and other irrelevant factors. I recall discussions on this issue in the mid-1990s on Usenet newsgroups, and I'm sure they occurred for years before that.

This discrepancy has historical roots outlined in the references I gave in my earlier post. FWIW, I used to complain about disk manufacturers' deception on this score, since they were bucking the usual industry definitions. Since the distinction between the power-of-2 and power-of-10 measures have been codified and accepted by standards organizations, though, and these definitions are slowly working their way into software, I no longer complain about the disk manufacturers' measures. I just try to explain why "formatting overhead," "disk geometry," and other factors are *not* the cause of the discrepancy that users perceive.

---

### Post by Jakiejake on 2010-05-28
Agreed NTFS

---

### Post by paker on 2010-05-28
Thank you all for your help.
This is the summary of what I learned about WD20EARS (or any other 4096B/sector hd) alignment. If not aligned...... Read this: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

1) Windows Vista or later will align the hd correctly. No special software needed. I could have mine connected to Windows Vista machine, because I needed NTFS anyhow. It would have been the simplest solution.

2) Download Acronis Alignment Tool Bootable CD ISO from [http://support.wdc.com/product/download.asp?groupid=805&lang=en](http://support.wdc.com/product/download.asp?groupid=805&lang=en)  Power off, connect hd, power up.  Follow prompts.

3) For Ubuntu, power off, connect hd, power up. From terminal, "sudo fdisk -l" and get the hd address (/dev/sdX) Follow this instruction:  [http://www.formortals.com/how-to-create-4kb-aligned-partitions-in-windows-xp-and-linux/](http://www.formortals.com/how-to-create-4kb-aligned-partitions-in-windows-xp-and-linux/)

---

