---
title: "Gparted problems"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by pendulum101 on 2010-01-23
Hey i can't seem to format my external harddrive 1TB to fat32 using Gparted using msdos partition table, fat32 filesystem, primary partition round to cylinders checked. has anyone had any experience with this ?
thanks in advance

---

### Post by warfacegod on 2010-01-23
Have you unmounted the hard drive?

---

### Post by x33a on 2010-01-23
what problem are you facing exactly?

if the fat32, ntfs etc. option is grayed out, it means you don't have dosfstools installed.

to install it, use:
```
sudo apt-get install dosfstools
```

---

### Post by warfacegod on 2010-01-23
> **x33a said:**
> what problem are you facing exactly?

if the fat32, ntfs etc. option is grayed out, it means you don't have dosfstools installed.

to install it, use:
```
sudo apt-get install dosfstools
```

dosfstools comes preinstalled in 9.10

---

### Post by pendulum101 on 2010-01-23
> **warfacegod said:**
> Have you unmounted the hard drive?

When do you mean ? Its mounted when i try to format it.

---

### Post by cenzorrll on 2010-01-23
> **pendulum101 said:**
> When do you mean ? Its mounted when i try to format it.

you need to unmount it in order to format it.  right click on the drive in gparted and there should be an option to unmount it. There should also be a key or a lock symbol next to the partition name if it's mounted.

---

### Post by luffy_chan_19 on 2010-01-23
I have actually had a similar problem.  If you are trying to format the drive for use as a secondary drive, you must format it as an "extended partition" and then after you have done this you can  actually format the new partition. i have had the same problem, a primary partition can only be used for drive that are going to hold an operating system. even though it is a secondary drive it is still considered an "extension" of the  primary drive


hope this was helpfull to you

---

### Post by egalvan on 2010-01-23
> **luffy_chan_19 said:**
> I have actually had a similar problem.  If you are trying to format the drive for use as a secondary drive, you must format it as an "extended partition" and then after you have done this you can  actually format the new partition. i have had the same problem, **a primary partition can only be used for drive that are going to hold an operating system. **even though it is a secondary drive it is still considered an "extension" of the  primary drive


hope this was helpfull to you

sorry, NOT TRUE.

A primary can hold ANYTHING, 
an extended can hold ANYTHING (well, ok, not a MS Windows boot :) )

A standard HD partition table can accommodate up to four primary partitions,
or a maximum of one extended partition.
or any combination.

He doesn't state what his problem was with the formatting,
but GPARTED will not format a parition that is in use...
it needs to be un-mounted.

My question is...

Why FAT32?

It's a bit unstable, especially for large drives,
has limits on root directory sizes,
limits on single file sizes,
it's unstable...

I hope he has a technical NEED for FAT32.

---

### Post by luffy_chan_19 on 2010-01-23
> **egalvan said:**
> sorry, NOT TRUE.

A primary can hold ANYTHING, 
an extended can hold ANYTHING (well, ok, not a MS Windows boot :) )

A standard HD partition table can accommodate up to four primary partitions,
or a maximum of one extended partition.
or any combination.

He doesn't state what his problem was with the formatting,
but GPARTED will not format a parition that is in use...
it needs to be un-mounted.

My question is...

Why FAT32?

It's a bit unstable, especially for large drives,
has limits on root directory sizes,
limits on single file sizes,
it's unstable...

I hope he has a technical NEED for FAT32.




i just have this to say

_Primary partitions_: The original partitioning scheme for PC hard disks allowed only four partitions, thus you are allowed up to 4 primary partitions(per physical hard disk). Linux numbers primary partitions 1-4.[INDENT][COLOR=darkred]_Note_: Some OSs (Windows, BSD) can ONLY be installed into a PRIMARY partition.[/COLOR]
Linux (and swap) can be installed into a primary or logical partition.[/INDENT]_Extended and Logical partitions_: To overcome this limitation, extended partitions are used. A single primary partition may "converted" into an "extended" partition which is then further divided into sub-partitions called logical partitions. Sorry you may not convert more then 1 primary partition into an extended partition. You then create logical partitions within the extended partition. It may be possible to create further extended partitions within an extended partition, although this becomes complicated and I am not sure of any advantage this offers.

Linux numbers Logical partitions starting with 5: The numbers 1,2,3 and 4 are reserved for the primaries, even if you have just one primary partition. So if you make one primary partition and one extended extended partition with one logical partition:

The primary would be sda1
The entire extended partition (and any logical partition(s) it contains) would be sda2.
The logical partition within the extended partition would be sda5.




bassicaly what i am trying to say is that if the entire primary disk is utilised for the Primary partition than you have no room to make any mor patitions in the drive for a primary partition thus you need to create an extended partition. i have tried many times to fomat a secondary drive to a primary partition with no avail. io had even unmounted the drive, it didn't work. if i am wrong please, please explain to me how i am wrong in my thinking. oh and no you don't necessarily have to unmount the drive that i have noticed. i have formatted my secondary and my external drives many times without unmounting it.

---

### Post by warfacegod on 2010-01-23
For a Primary partition you must unmount it to format it. An extended partition must also be unmounted, however, the logical partition with in the extended partition does not. For example:

A Linux swap space is in a logical partition inside of an extended partition. Unmounting is unnecessary to format or resize it, although turning swap off is. Unmounting or turning swap off still do, in essence, the same thing. They both mark that drive or partition as not in use.

> you don't necessarily have to unmount the drive that i have noticed. i have formatted my secondary and my external drives many times without unmounting it.

I suspect that you were formating drives that never mounted when you booted. Gparted has never allowed me to format anything without unmounting it first, except swap space. An obvious test would be to try and format the partition that Linux is installed on. You can't because you can't unmount it. To perform a format or resize operation on that partition, you must be outside of the operating system.

I feel I must reiterate egalvan's question. Why FAT32? Unless you have a very specific need for that filesystem, there are much better options. If you need to have Windows compatibility with the drive then NTFS is a much better option. If Windows is not a consideration, thenI would go with ext4.

---

### Post by leclerc65 on 2010-01-24
> If you need to have Windows compatibility with the drive then NTFS is a much better option.
I have an external 2" USB drive formatted in NTFS to shuffle files between my Windoze & Ubuntu computers. Somewhere somehow the drive was messed up (can't be read by Ubuntu). I find that Fat32 is much better for such use. The only limitation is you cannot put any file bigger than 4G on it.

---

### Post by warfacegod on 2010-01-24
Okay. Sounds like a personal preference thing. That's cool. Did unmounting the drive work?

---

### Post by luffy_chan_19 on 2010-01-24
> **leclerc65 said:**
> I have an external 2" USB drive formatted in NTFS to shuffle files between my Windoze & Ubuntu computers. Somewhere somehow the drive was messed up (can't be read by Ubuntu). I find that Fat32 is much better for such use. The only limitation is you cannot put any file bigger than 4G on it.


why you would have any file on your computer that is 4 GiB or bigger is beyond me, unless you use your computer for ISO's you shouldnt have many files that are 4GiB  that you need to store on you HDD

---

### Post by warfacegod on 2010-01-24
> **luffy_chan_19 said:**
> why you would have any file on your computer that is 4 GiB or bigger is beyond me, unless you use your computer for ISO's you shouldnt have many files that are 4GiB  that you need to store on you HDD

I'm currently downloading a torrent with a 73.5 GB file in it. No, I'm not telling what it is. The raw data from a Hollywood movie, before it's processed and compressed, is usually in the 5 - 15 TB range.

---

### Post by oldfred on 2010-01-24
Three or four years ago I had windows on one drive and Ubuntu on another. Since back then NTFS driver was still not 100% I went with a FAT partition on my windows drive for sharing data.

Since I wanted my backups on another drive I put them into the FAT partition and they always were 4GB. I just thought that was my size of the Uubntu backup. When I converted my systems and added a drive so I could backup to an ext3 partition was I surprised at the size. Fortunately I never needed the backup, but learned about the FAT limits.

[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
Fat also has maximum size limits.
32GB for all OS.
2TB for some OS

---

### Post by warfacegod on 2010-01-24
> **oldfred said:**
> Three or four years ago I had windows on one drive and Ubuntu on another. Since back then NTFS driver was still not 100% I went with a FAT partition on my windows drive for sharing data.

Since I wanted my backups on another drive I put them into the FAT partition and they always were 4GB. I just thought that was my size of the Uubntu backup. When I converted my systems and added a drive so I could backup to an ext3 partition was I surprised at the size. Fortunately I never needed the backup, but learned about the FAT limits.

[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
Fat also has maximum size limits.
32GB for all OS.
2TB for some OS

If you do a complete system backup (including personal files), in my experience, a Windows backup will 2 or 3 times the size of an Ubuntu backup. My 9.10 install is probably somewhere around 6 - 7 GB so if I made a tarball of it (no personal files) it could easily be over 4 GB.

---

### Post by mikechant on 2010-01-25
Luffy_chan_19 said:
> bassicaly what i am trying to say is that if the entire primary disk is utilised for the Primary partition than you have no room to make any mor patitions in the drive for a primary partition thus you need to create an extended partition. i have tried many times to fomat a secondary drive to a primary partition with no avail. io had even unmounted the drive, it didn't work. if i am wrong please, please explain to me how i am wrong in my thinking. oh and no you don't necessarily have to unmount the drive that i have noticed. i have formatted my secondary and my external drives many times without unmounting it.

I'm not sure exactly what you are saying here, but I think it's in danger of confusing people.

Each physical drive has its own MBR (Master Boot Record) containing a partition table with four slots. So If you have four physical drives (as I do - two internal, two external), you can have a total of sixteen primary partitions, four on each disc. The number of primary partitions on one physical disc has **no** influence on the others. Having your 'first' hard drive formatted entirely as one primary partition has no effect on what you can do with the other drives.

Also, each physical drive can use one of its primary partitions as an extended partition containing one or more logical partitions so you can have more than four partitions on a phyiscal disc.

As for formatting, you can format partitions on a disc that is in use (i.e. that has some partitions mounted), but you can't format a partition that is mounted (or you certainly shouldn't be able to).

Particular Operating systems (e.g. different versions of Windows) may have restrictions about which partitions/discs they can be installed on or booted from. Linux can generally be installed anywhere you like.

---

### Post by luffy_chan_19 on 2010-01-25
sorry i were havin me a brain fart at that moment  when i made that post see what i was saying is that you may be able to have up to 4 primary partitions on one drive, it has been said that you can have more than 1 primary partition on a system, but answer me this when you right click a secondary drive drive and select format drive under ubuntu 9.10 (after selecting file system to format to) if you are allowed more than one "primary partitioned" drive on a system why does it format it to an extended partition?

---

### Post by warfacegod on 2010-01-25
This is a lesson on: W[SIZE="4"]hat Not To Do To Your Hard Drive[/SIZE]

[http://ubuntuforums.org/showthread.php?t=1387623]("http://ubuntuforums.org/showthread.php?t=1387623")

---

### Post by audiomick on 2010-01-25
> **warfacegod said:**
> This is a lesson on: W[SIZE="4"]hat Not To Do To Your Hard Drive[/SIZE]

[http://ubuntuforums.org/showthread.php?t=1387623]("http://ubuntuforums.org/showthread.php?t=1387623")

your right, but that wasn't "nice"...:D

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> your right, but that wasn't "nice"...:D

I am ashamed. (warfacegod hangs head in remorse at the failure of his divine powers to tell him right from wrong)

---

### Post by audiomick on 2010-01-25
> **warfacegod said:**
> I am ashamed. (warfacegod hangs head in remorse at the failure of his divine powers to tell him right from wrong)

thought I'd never see the day (dancing in victory and praising his luck!!!)

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> thought I'd never see the day (dancing in victory and praising his luck!!!)

What? No sinister cackling? Or do you not wish to push your luck and anger the code gods so that they won't smite thee with a broken GRUB like me?

---

### Post by audiomick on 2010-01-25
> **warfacegod said:**
> What? No sinister cackling? Or do you not wish to push your luck and anger the code gods so that they won't smite thee with a broken GRUB like me?

Perish the thought. (I was laughing up my sleeve...)

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> Perish the thought. (I was laughing up my sleeve...)

Was there enough room for all that laughter?

---

### Post by audiomick on 2010-01-25
mwaahahahaha doesn't need much room.

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> mwaahahahaha doesn't need much room.

All the world isn't enough room for sinister laughter.

---

### Post by audiomick on 2010-01-25
Is that why I have been feeling cramped lately?
By the way, where's the OP?

---

### Post by warfacegod on 2010-01-25
> **audiomick said:**
> Is that why I have been feeling cramped lately?
By the way, where's the OP?

I assume, hiding from all your sinister laughting. We did hijack the thread, huh?

---

### Post by audiomick on 2010-01-25
> **warfacegod said:**
> We did hijack the thread, huh?

only a bit. ;)

---

### Post by egalvan on 2010-01-26
> **luffy_chan_19 said:**
> what i was saying is that you may be able to have up to 4 primary partitions on one drive,

No "may be" about it, a standard partition table CAN hold up to four primary partitions.

A maximum of four primary partitions
-- or
a maximum of one extended partition
-- or
a maximum of one extended partition PLUS one, two or three primary partitions.

(please note... there are hardware/software "tricks" that can extend these limits... they are not looked at here.)

> it has been said that you can have more than 1 primary partition on a system,

It has been said correctly; you are allowed more than one primary partition on a system.

The **Partition Information** resides in the **Partition Table**
The **Partition Table** in turn resides in the **Master Boot Record** aka **MBR**
The **MBR** resides in the first 512 bytes of the Hard Drive.
Each MBR is INDEPENDENT OF ANY OTHER  MBR.
No MBR "knows" or has any info on any other MBR,
(unless there is code written to allow this)
Each MBR stands alone. Each Partition Table stands alone.
they do not influence or limit each other.

> answer me this 
when you **right click a secondary drive drive **and **select format drive **under ubuntu 9.10 (after selecting file system to format to)
 if you are allowed more than one "primary partitioned" drive on a system why does it **format it to an extended partition?**

First, **FORMATTING** has nothing to do with PRIMARY or EXTENDED or LOGICAL **PARTITIONING**.

PARTITIONING is done with PARTITION UTILITIES
FORMATTING is done with FORMAT UTILITIES

A piece of software can contain both type of utilities, 
as indeed gparted does

That said....
many, many, *many* years ago, when 5 MEGA-byte drives were starting to appear,
 the word "format" was used for *all* the operations needed to allow a hard drive to be used by the OS
"low-level" format (done by software embedded in the  controller card... usually accessed through a 'debugger')
"partition formatting" (done usually by 'fdisk' or similar
"file system" formatting (done by  formatting utility, usually 'format'
yeah, right... lotsa fun in those days...one even had to select the sector order...

Consider...
An EXTENDED partition can be considered more efficient,
since it does not have such a severe restriction on the number of partitions allowed on a drive.


Now...
Some external drives come from the factory already partitioned.
Some also come already formatted.
(one poster on this forum stated his Western Digital 1TB drive was formatted FAT32 :!:)

Try this...
Take a drive that is empty and erase it, totally.
Use something like dban (Duke's Boot and Nuke)
( if you use dban, be aware that IT WILL ERASE A DRIVE TOTALLY... 
be careful when you use it.
YOU WILL LOSE DATA IF YOU ARE NOT CAREFUL. 
Consider that one of it's uses is 'TO PREVENT FORENSIC ANALYSIS OF A HARD DRIVE 
I have used it for some three years, and with care, I HAVE NEVER LOST DATA I DID NOT WANT LOST )

then attach it as a secondary drive and let gparted take a look at it.

Create a primary partition on it.

It can be done.
It has been done.

Consider that forensic analysis starts by removing the hard drive from  the original machine, making a bit-for-bit clone,
  and connecting that clone to the work machine.
If, as you have been led to believe, only ONE primary partition was allowed per machine, would this forensic approach work?
It's been in use for over three decades.
It does work.
Recovery software does this all the time...


And I'll leave you all with this....

My last home server cabinet had a mother-board with:
four on-board ATA channels,
four add-on ATA channels (via two add-on PCI ATA boards)
these had a capacity of 16 PATA-IE drives (two drives per channel)

it also had
four SCSI channels (via two add-on PCI SCSI cards)
these had a capacity of 60 drives (15 drives per channel)

so that cabinet could have held (theoretically) SEVENTY-SIX drives.
with a theoretical maximum of 304 PRIMARY PARTITIONS ! :!:

The max it ever held was 16 drives (12 IDE, 4 SCSI)
quite a load on the power supply (which was separate from the mother-board supply),
 The SCSI's would "stagger start" after a thirty second wait on the IDE drives :) )

Good Old Days, indeed !

---

### Post by mikechant on 2010-01-26
> when you right click a secondary drive drive and select format drive under ubuntu 9.10 (after selecting file system to format to) if you are allowed more than one "primary partitioned" drive on a system why does it format it to an extended partition?

I think the Ubuntu installer is just being cautious by default. It will often encounter situations where there are already Windows primary partitions and will typically be creating 2, 3 or more extra partitions itself so it's more likely to suceed if it uses the extended partition and if possible will leave some primary partitions free. It maybe doesn't have the full flexibility of gparted.

Personally I'm not that familiar with the exact installer partitioning options since I usually create my partitions manually with gparted before installing. That way I can create the exact mix of primary/extended/logical partitions exactly as I please and then direct the installer to use them.

---

