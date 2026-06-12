---
title: "hard disk problem no partitions showing"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by kirkface8 on 2011-01-31
hey recoently i noticed that my windows partition had an ! in gparted. i ran the windows 7 recovery cd. this failed halfway through.

today i notice that gparted is not showing any partitions and my music partition is not visible in nautilus. nor can i mount my 153gb 


take notice of the screenshot below thats the error i get attempting to mount the ntfs 153gb windows partition.

thanks

---

### Post by ephexeve on 2011-01-31
I had the same problem, I found out I had a NTFS filesystem.

---

### Post by kirkface8 on 2011-01-31
its been working for 4 months now though.

---

### Post by kirkface8 on 2011-01-31
am i able to fix this within ubuntu?

---

### Post by coffeecat on 2011-01-31
Your first screenshot is describing one problem very clearly: the NTFS filesystem on your Windows C: drive is damaged. The fact that Gparted was showing a ! means that this may have been so before you ran the failed repair from the repair disc. You cannot repair this from Ubuntu. However, before you attempt to repair your Windows C....

The second screenshot with Gparted showing 'unallocated' suggests that the partition table may be damaged. Perhaps the Windows repair disc did this, perhaps not. You need to see whether this is so before doing anything else.

Boot up Ubuntu.* Open a terminal and post the output of:

```
sudo fdisk -lu
```Please post this between [noparse]```
 and 
```[/noparse] tags for legibility. This will tell us if there is partition table corruption.

**EDIT**: I'm assuming you can still boot Ubuntu despite these problems. If not, use the live CD.

---

### Post by kirkface8 on 2011-01-31
> **coffeecat said:**
> Your first screenshot is describing one problem very clearly: the NTFS filesystem on your Windows C: drive is damaged. The fact that Gparted was showing a ! means that this may have been so before you ran the failed repair from the repair disc. You cannot repair this from Ubuntu. However, before you attempt to repair your Windows C....

The second screenshot with Gparted showing 'unallocated' suggests that the partition table may be damaged. Perhaps the Windows repair disc did this, perhaps not. You need to see whether this is so before doing anything else.

Boot up Ubuntu.* Open a terminal and post the output of:

```
sudo fdisk -lu
```Please post this between [noparse]```
 and 
```[/noparse] tags for legibility. This will tell us if there is partition table corruption.

**EDIT**: I'm assuming you can still boot Ubuntu despite these problems. If not, use the live CD.

fdisk -lu
```

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd58e9730

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    78125055    39061504   83  Linux
/dev/sdb2        78127102   234375167    78124033    5  Extended
/dev/sdb3       234375168   234579967      102400    7  HPFS/NTFS
/dev/sdb4       234579968   532977663   149198848    7  HPFS/NTFS
/dev/sdb5       532977664   625141759    46082048    7  HPFS/NTFS
/dev/sdb6       205080576   234375167    14647296   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by coffeecat on 2011-01-31
Something is seriously wrong with your partition table:

> **kirkface8 said:**
> fdisk -lu
```

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd58e9730

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    78125055    39061504   83  Linux
[COLOR=Red]/dev/sdb2        78127102   234375167[/COLOR]    78124033    5  Extended
/dev/sdb3       234375168   234579967      102400    7  HPFS/NTFS
/dev/sdb4       234579968   532977663   149198848    7  HPFS/NTFS
[COLOR=Red]/dev/sdb5       532977664   625141759[/COLOR]    46082048    7  HPFS/NTFS
[COLOR=Red]/dev/sdb6       205080576   234375167[/COLOR]    14647296   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Partitions sdb5 and sdb6 should, by definition, be logical partitions because their numbers are 5 and above. Logical partitions are contained within an extended partition, in your case sdb2. But look at the numbers. sdb6 is within sdb2. So far, so good. But sdb5 is the other side of the primaries sdb3 and sdb4. You can't have a split extended partition like that. And you can't convert sdb5 to a primary because that would give you four primaries and one extended, which is illegal. Actually, it's impossible - you couldn't edit the partition table to effect this.

At the moment I have no idea how to repair this. Normally, you would edit the partition table to deal with partition table corruption but I can see no way of doing this that is legal or, indeed, possible. In case I have missed something I'll call up some other opinions. In the meantime, how much do you understand about partitions: primary, extended and logicals? Can you follow the paragraph above?

---

### Post by kirkface8 on 2011-01-31
> **coffeecat said:**
> Something is seriously wrong with your partition table:



Partitions sdb5 and sdb6 should, by definition, be logical partitions because their numbers are 5 and above. Logical partitions are contained within an extended partition, in your case sdb2. But look at the numbers. sdb6 is within sdb2. So far, so good. But sdb5 is the other side of the primaries sdb3 and sdb4. You can't have a split extended partition like that. And you can't convert sdb5 to a primary because that would give you four primaries and one extended, which is illegal. Actually, it's impossible - you couldn't edit the partition table to effect this.

At the moment I have no idea how to repair this. Normally, you would edit the partition table to deal with partition table corruption but I can see no way of doing this that is legal or, indeed, possible. In case I have missed something I'll call up some other opinions. In the meantime, how much do you understand about partitions: primary, extended and logicals? Can you follow the paragraph above?

I understand most of the above. I understand primary, extended not so much logical. My partitions where working fine except for the windows one until i ran the windows recovery CD. This must have been what caused the problems. God i hate windows. 
But thanks i'm really confused about what has happened i'm sure i've copied and pasted this right. Should i open a new thread or what? Below is a screenshot of disk utility which shows strange occurrences as well.

Thanks

---

### Post by coffeecat on 2011-01-31
> **kirkface8 said:**
> Should i open a new thread or what?

I'd keep this one going. You've already posted the relevant information and you'd just have to repost it in a new thread. 

> **kirkface8 said:**
>  Below is a screenshot of disk utility which shows strange occurrences as well.

I'm not surprised. The backend for Gparted is parted which is known to throw in the towel when confronted with certain inconsistencies in a damaged partition table. I don't know what the backend to Disk Utility is, but it's not going to tell us anything more than fdisk. fdisk reads and displays  partition table information, so we've got enough reliable information to be going on with.

I've had a reply from one of my contacts who doesn't find fault with my analysis. I'll pm someone else now, an expert in these matters, but he lives in another time zone from both you and so may not be around for some time. In the meantime, if the worst came to the worst, would you be prepared to do a complete re-install? I hate to suggest this, but it's useful to know how far someone with a complex problem like this is prepared to go before re-installing. You mentioned a Music partition. Is this what is showing as sdb5 in fdisk?

---

### Post by kirkface8 on 2011-01-31
> **coffeecat said:**
> I'd keep this one going. You've already posted the relevant information and you'd just have to repost it in a new thread. 



I'm not surprised. The backend for Gparted is parted which is known to throw in the towel when confronted with certain inconsistencies in a damaged partition table. I don't know what the backend to Disk Utility is, but it's not going to tell us anything more than fdisk. fdisk reads and displays  partition table information, so we've got enough reliable information to be going on with.

I've had a reply from one of my contacts who doesn't find fault with my analysis. I'll pm someone else now, an expert in these matters, but he lives in another time zone from both you and so may not be around for some time. In the meantime, if the worst came to the worst, would you be prepared to do a complete re-install? I hate to suggest this, but it's useful to know how far someone with a complex problem like this is prepared to go before re-installing. You mentioned a Music partition. Is this what is showing as sdb5 in fdisk?

thanks. the thing is ubuntu is working perfectly no errors at all. by reinstall i assume u mean starting the hard disk from scratch. i'm happy to if theres no other fixes and would love to back up my music.

i'm not sure if its sdb5

but i had a 45gb ntfs music partition
a 60gb ntfs data partition
and a 153gb ntfs windows partition (which i have no care for at this point of time)

i don't believe i made a swap partition due to using small percentages of my ram.
my drive is advertised as a 320gb drive if that helps.

i should be awake for another 4 hours and will be checking this thread every 10 minutes.

thanks

---

### Post by coffeecat on 2011-01-31
> **kirkface8 said:**
> i'm not sure if its sdb5

but i had a 45gb ntfs music partition
a 60gb ntfs data partition
and a 153gb ntfs windows partition (which i have no care for at this point of time)

i don't believe i made a swap partition due to using small percentages of my ram.
my drive is advertised as a 320gb drive if that helps.


You did make a swap. Anyway, from your fdisk output:

```

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd58e9730

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    78125055    39061504   83  Linux
/dev/sdb2        78127102   234375167    78124033    5  Extended
/dev/sdb3       234375168   234579967      102400    7  HPFS/NTFS
/dev/sdb4       234579968   532977663   149198848    7  HPFS/NTFS
/dev/sdb5       532977664   625141759    46082048    7  HPFS/NTFS
/dev/sdb6       205080576   234375167    14647296   82  Linux swap / Solaris

```sdb1 = 40 GB
Apparently unused space between sectors 78127102 and 205080576 in sdb2 = 65 GB
sdb3 = 105MB
sdb4 = 152.8 GB
sdb5 = 47.2 GB
sdb6 = 15GB (your swap partition)

The space that is now not a partition must have been your NTFS data partition, and your music partition would be now what is posing as sdb5. By the way, your swap partition is enormous at 15GB, but that's the least of your worries.

I have this thread subscribed, but I won't post unless I have any other ideas or until one of my contacts posts - and only then if I have something useful to say. :)

---

### Post by Quackers on 2011-01-31
Which operating system was installed first on this hard drive please?

---

### Post by kirkface8 on 2011-01-31
windows 7 was first.
then made the music partition
then ubuntu

than recently made the data partition

---

### Post by Quackers on 2011-01-31
That's what I expected, but how did you get a Linux partition on sdb1, if Windows was there first?
Also, did you say that a Windows recovery failed? Did it fail because there wasm't enough disk space?

---

### Post by kirkface8 on 2011-01-31
> **Quackers said:**
> That's what I expected, but how did you get a Linux partition on sdb1, if Windows was there first?
Also, did you say that a Windows recovery failed? Did it fail because there wasm't enough disk space?

im not to sure. this is thinking back a while ago. i think diskpart or the windows disk utility shrink put it in front.

and it failed because it was mounting the 60gb drive as c: and the 45gb drive as d:.

remember gparted showed an !(icon) next to the 153gb ntfs partition before using the windows recovry cd. how would i get the windows recovery cd to mount the right drive so i can repair the 153gb partition and then figure out on repairing the others.

---

### Post by Quackers on 2011-01-31
Normally the Windows recovery dvd's ( or partition) wants to use the whole hard drive to recover Windows to.

---

### Post by kirkface8 on 2011-01-31
> **Quackers said:**
> Normally the Windows recovery dvd's ( or partition) wants to use the whole hard drive to recover Windows to.

ahk well i have no idea what to do. ima run the recovery cd again. see if it has any issues

if not ill figure out later
haha
thanks though:)
night from aus

---

### Post by Quackers on 2011-01-31
You keep referring to a recovery cd. How does that work? Normally recovery dvd's are used, to my knowledge. The recovery program being too large for a cd. How was this recovery cd made? Through Control Panel?

---

### Post by srs5694 on 2011-01-31
I'm one of the people coffeecat contacted.

Before you attempt anything, be sure to read this whole message, including my caveats at the end.

Anyhow, repair of the partition table *is* possible, but the end result will be a bit weird. Your goal state is to have an extended partition at the *start* of the disk with your two Linux partitions (currently /dev/sdb1 and /dev/sdb6) within it as logical partitions. There will also be a gap within the extended partition between the two Linux partitions. You'll then have room for three primary partitions, each of which will be one of your NTFS partitions (currently /dev/sdb3, /dev/sdb4, and /dev/sdb5). It's weird, but legal, to have an extended partition at the start of the disk. That's the only way I can see that these partitions could have been created, though.

You can do this with sfdisk, using a procedure similar to the one described [on this Web page of mine;](http://www.rodsbooks.com/missing-parts/index.html) however, you'll need to do a lot of juggling to get it right. You must also have a good conceptual understanding of the difference between primary, extended, and logical partitions. (Googling on "primary extended logical partition" turned up [this page,](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html) which seems to do a decent job of explaining the concepts, although I've only skimmed it and so can't vouch for it being 100% accurate.) If you attempt this approach, I recommend you first cut-and-paste the fdisk output you've posted, remove /dev/sdb2 (since it's useless as-is), and rearrange the partitions in order of their start sectors. This will show you how things should be grouped. Then get the sfdisk output, as described on my Web page, and re-order and re-number the partitions to match the re-ordered fdisk output. (You'll have to renumber at least /dev/sda1 and /dev/sda5; in fact, swapping those two numbers is one simple way to go. This would result in partition numbers that don't match the storage-space positions, which is legal but potentially a bit confusing. Whatever you do, remember that primary and extended partitions are numbered 1 to 4, while logical partitions are numbered 5 and up.) Once you've re-ordered the sfdisk output, tackle the extended partition: You'll need to give it a start sector that's at least one sector earlier than the first partition (in other words, 2047 or earlier) and a length to precisely cover all the logical partitions (234373121 if you use a start sector of 2047 and if I've done the arithmetic correctly -- please double- and triple-check that detail!). Once this is done, feed the result back into sfdisk, as described on my Web page, and hope for the best!

A somewhat simpler way to do this would be to use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program, which is intended to edit GUID Partition Table (GPT) disks rather than the Master Boot Record (MBR) disks that yours is. GPT fdisk can convert back and forth, though, and GPT lacks the concept of a logical partition, so it should be able to load the MBR data (converting automatically to GPT format) and then save it out as MBR, which will cause gdisk to automatically create a legal extended partition. The procedure would be:


[list=1]
[*]Download and install GPT fdisk from [its Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) Do *not* use the version in the Ubuntu repositories; it's hopelessly out of date and will not work for this procedure. Alternatively, you can use the latest version (2.0.0) of [System Rescue CD,](http://www.sysresccd.org/Main_Page) which has a recent enough version of GPT fdisk to work.
[*]Type "sudo gdisk /dev/sdb" to launch it on your disk.
[*]Type "p" to display your partition table and verify that it's correct. If it's not, type "q" to exit without saving your changes.
[*]Type "r" to get into the recovery & transformation menu.
[*]Type "g" to transform from the in-memory GPT version of your partitions back to MBR form. You'll see a summary of what the program intends to do. It will probably have all the primary/logical assignments right (it won't mention the extended partition), but if not, you can change them here. You will need to change the type code of your Linux data partition (currently /dev/sdb1; it'll still be identified as such at this point) to "83". (In GPT form, Linux and Windows use one partition type code, so the distinction between MBR's 0x07 and 0x83 is lost, and you must re-create it manually.) See the "Converting from GPT to MBR" section of [this page](http://www.rodsbooks.com/gdisk/mbr2gpt.html) for details of how to use the GPT-to-MBR conversion feature of gdisk.
[*]When you're satisfied, type "0" to save your changes. You'll have to type "y" to verify this.
[/list]


If you've got GRUB installed in the MBR of your disk, you may have to re-install it with either procedure, and especially with the gdisk method. Since this is /dev/sdb, though, this may be necessary; GRUB might be installed on /dev/sda.

Now, the caveats I mentioned: Either of these procedures will repair the *partition table* damage. Your problem as a whole seems to involve much more than this. You've probably got damage to at least one NTFS filesystem, there may be Windows boot loader issues, and you seem to have one missing partition that this procedure will not recover. It's conceivable that juggling partitions around in this way will make Windows even more unhappy and unwilling to boot. Nonetheless, IMHO fixing the corrupt partition table must be your first priority; if you don't do that, you run the risk of causing more damage when you attempt to fix the NTFS or Windows boot problems.

If possible, I recommend you back up your important data before doing anything else. If necessary, go out and buy an external hard disk for this purpose. It's conceivable that attempting to repair the corrupt partition table will make matters worse, so having a backup is very very prudent.

As to your lost partition(s), your best bet at recovery is [TestDisk,](http://www.cgsecurity.org/wiki/TestDisk) which can scan a disk for filesystem "signatures" and create new partitions to match any that it finds. I recommend you run TestDisk *after* repairing the damage in the way I've identified; however, I also recommend that you back up your partition table by typing "sudo sfdisk -d > sdb-parts.txt" and saving the resulting sdb-parts.txt file on a USB flash drive or some other medium other than /dev/sdb before you run TestDisk. That way, if TestDisk makes things worse (as it sometimes does), you'll be able to use sfdisk to restore your partition table as it will be prior to running TestDisk, even if there's a missing partition.

Good luck!

---

### Post by srs5694 on 2011-01-31
Oh, I forgot something: One of your screen shots shows a SMART status output that's green but that reads "Disk has a few bad sectors." You should investigate this. It's conceivable that it was this "few bad sectors" that caused your problems to begin with.

In fact, you might want to consider just buying a new hard disk, creating suitably-sized (and sensibly-arranged) partitions on it, and then using ntfsclone, dd, tar, or other programs to copy your current disk to the new one. That way you won't need to deal with fixing the current partitions, although you may need to deal with making everything bootable from the new disk.

---

### Post by coffeecat on 2011-01-31
@srs5694, thanks for responding to the call and, as ever, your posts are an education. One comment/question.

There are apparently, according to fdisk, unused sectors between 78127102 and 205080576 which, according to my calculation are equal to 65GB (That's real GB = to base 10). The OP mentions a data NTFS partition of 60GB, on which presumably they have personal data which they would want to recover. If the OP really meant 60 GiB (seeing that 65GB = 60.5 GiB), then it's possible the NTFS data partition is in that "free" space within the extended partition. My question is: would it be helpful for the OP, when editing the partition table, to create an entry for a logical partition covering that span of sectors, with the ID code for NTFS? Then, if the filesystem is not corrupted, the OP might be able to mount and read the data there.

**EDIT**: I've just had another look at the Disk Utility screenshot and the 47GB partition at the end is showing up as "Data". So perhaps the 60/65 is "Music" and the OP got them the wrong way round in post #10. Whichever, data or music, I'm sure the OP wants to rescue anything inside.

---

### Post by perspectoff on 2011-01-31
> **srs5694 said:**
> Oh, I forgot something: One of your screen shots shows a SMART status output that's green but that reads "Disk has a few bad sectors." You should investigate this. It's conceivable that it was this "few bad sectors" that caused your problems to begin with.

In fact, you might want to consider just buying a new hard disk, creating suitably-sized (and sensibly-arranged) partitions on it, and then using ntfsclone, dd, tar, or other programs to copy your current disk to the new one. That way you won't need to deal with fixing the current partitions, although you may need to deal with making everything bootable from the new disk.

+1

I loved the advice about editing the Partition Table, also, something I have been trying to figure out for a long time (but certainly not something to be undertaken by amateurs). 

I recently didn't realize that the Partition Table was within my second Windows partition (which I had thought was merely a Recovery Partition for the OS only). I reformatted that partition, intending to use it for a Linux OS. That erased the Partition Table entirely, and then no OS or partition was recognized at all and GParted definitely was of no use. So are the tools you mention available on a LiveCD? Ok, yes, I see from the wiki that SystemRescueCD, one of my favorites, has the tools on it already.

Fortunately, I had already backed up my NTFS partitions using partimage and my Linux filesystems using FSArchiver (which is also on SystemRescueCD).

I had wanted to re-organize my hard drive anyway, so I re-formatted it, used GParted to establish the partitions in the sizes and order I wanted them, and then copied the NTFS partitions back using partimage and the Linux OS(s) using FS Archiver.

Probably not as elegant as editing the Partition Table as CM suggests, but it did allow me to re-arrange my hard drive from the hokey way my original equipment reseller did it to the way I like it.

---

### Post by srs5694 on 2011-01-31
> **coffeecat said:**
> There are apparently, according to fdisk, unused sectors between 78127102 and 205080576 which, according to my calculation are equal to 65GB
...
My question is: would it be helpful for the OP, when editing the partition table, to create an entry for a logical partition covering that span of sectors, with the ID code for NTFS? Then, if the filesystem is not corrupted, the OP might be able to mount and read the data there.

If you got very very lucky, you might recover the partition this way. The trouble is that it's impossible to know the precise start sector of the partition. You could make guesses based on both cylinder and 1 MiB alignment assumptions, but they'd just be guesses. TestDisk will actually scan that area to find the actual filesystem data, which takes the guesswork out of it -- at least in theory. (In practice, stray data from old partitions can sometimes cause TestDisk to produce "false alarms" in situations like this.)

I'm not going to speculate about what's what on the three known and one presumed NTFS partitions; just recover them all and then figure it out afterwards.

---

### Post by srs5694 on 2011-01-31
> **perspectoff said:**
> I recently didn't realize that the Partition Table was within my second Windows partition (which I had thought was merely a Recovery Partition for the OS only).

With the exception of disk image files and certain types of partition backup files, you won't find partition tables inside Windows (FAT or NTFS) partitions. I see three possibilities to explain your statement:


[list]
[*]You're mistaken, and the problems that you describe when you tried to re-use the partition for Linux were a result of some other problem, like a damaged partition table.
[*]The partition you've identified as a "Windows partition" was actually an extended partition. (Linux's fdisk, for one, identifies one type of extended partition as "W95 Ext'd (LBA)", so this misidentification is understandable.) Extended partitions serve as placeholders for logical partitions, so if you attempted to overwrite the contents of an extended partition, you'd lose all your logical partitions; but you wouldn't lose your primary partitions, assuming everything else was OK.
[*]The partition you've identified as a "Windows partition" was a Windows SFS (aka logical disk management, or LDM; or "dynamic disks") partition, which is Windows' equivalent to Linux's LVM subsystem. If you overwrote such a partition, you'd destroy your Windows LDM volumes, but not any other conventional MBR partitions on the disk.
[/list]


> I had wanted to re-organize my hard drive anyway, so I re-formatted it, used GParted to establish the partitions in the sizes and order I wanted them, and then copied the NTFS partitions back using partimage and the Linux OS(s) using FS Archiver.

Probably not as elegant as editing the Partition Table as CM suggests, but it did allow me to re-arrange my hard drive from the hokey way my original equipment reseller did it to the way I like it.

In your situation, restoring from a backup was probably the best course of action, since when you installed Linux over whatever had been there before, you almost certainly overwrote critical NTFS data structures and file contents. This would make recovery of the original Windows partitions next to impossible. It doesn't sound like kirkface8 has caused this sort of damage, so recovery of the original partitions is probably still possible -- although the possibility of bad sectors developing on the disk makes transfer to another disk (before or after partition table repairs) advisable, at least if the bad sectors prove to be real and more than just one or two that the drive can remap and handle.

---

### Post by kirkface8 on 2011-02-01
> **srs5694 said:**
> I'm one of the people coffeecat contacted.

Before you attempt anything, be sure to read this whole message, including my caveats at the end.

Anyhow, repair of the partition table *is* possible, but the end result will be a bit weird. Your goal state is to have an extended partition at the *start* of the disk with your two Linux partitions (currently /dev/sdb1 and /dev/sdb6) within it as logical partitions. There will also be a gap within the extended partition between the two Linux partitions. You'll then have room for three primary partitions, each of which will be one of your NTFS partitions (currently /dev/sdb3, /dev/sdb4, and /dev/sdb5). It's weird, but legal, to have an extended partition at the start of the disk. That's the only way I can see that these partitions could have been created, though.

You can do this with sfdisk, using a procedure similar to the one described [on this Web page of mine;]("http://www.rodsbooks.com/missing-parts/index.html") however, you'll need to do a lot of juggling to get it right. You must also have a good conceptual understanding of the difference between primary, extended, and logical partitions. (Googling on "primary extended logical partition" turned up [this page,]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html") which seems to do a decent job of explaining the concepts, although I've only skimmed it and so can't vouch for it being 100% accurate.) If you attempt this approach, I recommend you first cut-and-paste the fdisk output you've posted, remove /dev/sdb2 (since it's useless as-is), and rearrange the partitions in order of their start sectors. This will show you how things should be grouped. Then get the sfdisk output, as described on my Web page, and re-order and re-number the partitions to match the re-ordered fdisk output. (You'll have to renumber at least /dev/sda1 and /dev/sda5; in fact, swapping those two numbers is one simple way to go. This would result in partition numbers that don't match the storage-space positions, which is legal but potentially a bit confusing. Whatever you do, remember that primary and extended partitions are numbered 1 to 4, while logical partitions are numbered 5 and up.) Once you've re-ordered the sfdisk output, tackle the extended partition: You'll need to give it a start sector that's at least one sector earlier than the first partition (in other words, 2047 or earlier) and a length to precisely cover all the logical partitions (234373121 if you use a start sector of 2047 and if I've done the arithmetic correctly -- please double- and triple-check that detail!). Once this is done, feed the result back into sfdisk, as described on my Web page, and hope for the best!

A somewhat simpler way to do this would be to use my [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") program, which is intended to edit GUID Partition Table (GPT) disks rather than the Master Boot Record (MBR) disks that yours is. GPT fdisk can convert back and forth, though, and GPT lacks the concept of a logical partition, so it should be able to load the MBR data (converting automatically to GPT format) and then save it out as MBR, which will cause gdisk to automatically create a legal extended partition. The procedure would be:


[LIST=1]
[*]Download and install GPT fdisk from [its Sourceforge download page.]("http://sourceforge.net/projects/gptfdisk/files/") Do *not* use the version in the Ubuntu repositories; it's hopelessly out of date and will not work for this procedure. Alternatively, you can use the latest version (2.0.0) of [System Rescue CD,]("http://www.sysresccd.org/Main_Page") which has a recent enough version of GPT fdisk to work.
[*]Type "sudo gdisk /dev/sdb" to launch it on your disk.
[*]Type "p" to display your partition table and verify that it's correct. If it's not, type "q" to exit without saving your changes.
[*]Type "r" to get into the recovery & transformation menu.
[*]Type "g" to transform from the in-memory GPT version of your partitions back to MBR form. You'll see a summary of what the program intends to do. It will probably have all the primary/logical assignments right (it won't mention the extended partition), but if not, you can change them here. You will need to change the type code of your Linux data partition (currently /dev/sdb1; it'll still be identified as such at this point) to "83". (In GPT form, Linux and Windows use one partition type code, so the distinction between MBR's 0x07 and 0x83 is lost, and you must re-create it manually.) See the "Converting from GPT to MBR" section of [this page]("http://www.rodsbooks.com/gdisk/mbr2gpt.html") for details of how to use the GPT-to-MBR conversion feature of gdisk.
[*]When you're satisfied, type "0" to save your changes. You'll have to type "y" to verify this.
[/LIST]


If you've got GRUB installed in the MBR of your disk, you may have to re-install it with either procedure, and especially with the gdisk method. Since this is /dev/sdb, though, this may be necessary; GRUB might be installed on /dev/sda.

Now, the caveats I mentioned: Either of these procedures will repair the *partition table* damage. Your problem as a whole seems to involve much more than this. You've probably got damage to at least one NTFS filesystem, there may be Windows boot loader issues, and you seem to have one missing partition that this procedure will not recover. It's conceivable that juggling partitions around in this way will make Windows even more unhappy and unwilling to boot. Nonetheless, IMHO fixing the corrupt partition table must be your first priority; if you don't do that, you run the risk of causing more damage when you attempt to fix the NTFS or Windows boot problems.

If possible, I recommend you back up your important data before doing anything else. If necessary, go out and buy an external hard disk for this purpose. It's conceivable that attempting to repair the corrupt partition table will make matters worse, so having a backup is very very prudent.

As to your lost partition(s), your best bet at recovery is [TestDisk,]("http://www.cgsecurity.org/wiki/TestDisk") which can scan a disk for filesystem "signatures" and create new partitions to match any that it finds. I recommend you run TestDisk *after* repairing the damage in the way I've identified; however, I also recommend that you back up your partition table by typing "sudo sfdisk -d > sdb-parts.txt" and saving the resulting sdb-parts.txt file on a USB flash drive or some other medium other than /dev/sdb before you run TestDisk. That way, if TestDisk makes things worse (as it sometimes does), you'll be able to use sfdisk to restore your partition table as it will be prior to running TestDisk, even if there's a missing partition.

Good luck!

Thank you for your response. As you have said this is a large amount of work for an amateur. I have come to the conclusion that i want to back up the data on the 65gb "music" partition and can live without the rest. Whats the simplest way of restoring this data for backup?

> You keep referring to a recovery cd. How does that work? Normally recovery dvd's are used, to my knowledge. The recovery program being too large for a cd. How was this recovery cd made? Through Control Panel?I am using the windows recovery Cd as advertised on the Microsoft site.


> EDIT: I've just had another look at the Disk Utility screenshot and the 47GB partition at the end is showing up as "Data". So perhaps the 60/65 is "Music" and the OP got them the wrong way round in post #10. Whichever, data or music, I'm sure the OP wants to rescue anything inside.Yes sorry i must have got them mixed up.

Thanks all

---

### Post by coffeecat on 2011-02-01
> **kirkface8 said:**
>  I have come to the conclusion that i want to back up the data on the 65gb "music" partition and can live without the rest. Whats the simplest way of restoring this data for backup?

If I'm reading things correctly, that's going to be the most difficult to recover. Your music partition would seem to be somewhere in the space between sectors 78127102 and 205080576 which fdisk at the moment shows as not being allocated to a partition. Have a look at my post #21 and srs5694's reply at #23. What I suggested in #21 doesn't appear to be viable but srs5694 refers to testdisk which would be the way to go. If the thought of editing the partition table is too daunting, you could go straight to testdisk which seems to be your only chance of recovering the music partition. Believe me, testdisk is not as forbidding as it might first appear.

I don't believe you can run testdisk from your still bootable Ubuntu - you wouldn't be allowed to work on the disk you are running the OS from. Or so I believe - I'm happy to be corrected. But you can from the Ubuntu live CD so long as you can connect to the internet; you have to install testdisk in the live session.

Have a look here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

and...

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I really don't know how testdisk will fare with the impossibilities you already have in your partition table. You might want to wait for srs5694's comments before you go ahead. One tip I do have is to save the testdisk logs to a usb drive. You will be in a live session; anything saved will be lost when you power down unless you do. You might need those logs.

---

### Post by srs5694 on 2011-02-01
> **kirkface8 said:**
> Thank you for your response. As you have said this is a large amount of work for an amateur. I have come to the conclusion that i want to back up the data on the 65gb "music" partition and can live without the rest. Whats the simplest way of restoring this data for backup?

Try this from a Linux command prompt:

```

sudo mkdir /mnt/sdb3
sudo mkdir /mnt/sdb4
sudo mkdir /mnt/sdb5
sudo mount /dev/sdb3 /mnt/sdb3
sudo mount /dev/sdb4 /mnt/sdb4
sudo mount /dev/sdb5 /mnt/sdb5

```

The last three commands mount your three NTFS partitions. If they complain that you must specify the filesystem type, add "-t ntfs-3g" between "mount" and the device filename. These commands may or may not work. If they work (or if the partitions are already mounted), you should be able to identify their contents to figure out which is which. If one of them is your music, you should be able to copy it over to another disk.

If you can't mount one or more of those partitions, it'll be hard to identify, at least in Linux. Perhaps some Windows utilities would help, but I know relatively little about them. One that I do know is CHKDSK, which fixes disk errors; you'd call it like "CHKDSK C:" -- but what drive letters correspond to the Linux device filenames is something nobody can tell you with certainty at this point. Also, any utility that modifies the disk runs the risk of making things worse.

If none of those partitions is your music partition, you'll have to cross your fingers and use TestDisk; however, my suspicion is that TestDisk will be more likely to work if you've fixed your disk's partitions first. The strange partition table might confuse it. I don't know offhand if you could run TestDisk on an in-use disk. The limitation to which oldfred refers is a limitation of libparted; tools that work more directly on disks, such as fdisk and gdisk, don't have this problem. I don't know if TestDisk imposes such a limitation.

If you have problems with TestDisk and get really desperate, you could use Linux's fdisk to delete all your partitions and then run TestDisk from an emergency CD. There's a decent chance that TestDisk will recover everything, but if it doesn't, you won't be able to boot the computer at all. Do this only after you back up any important Linux-accessible data. Also, you can back up the partition table by typing "sudo sfdisk -d /dev/sda > parts-sda.txt" and saving the parts-sda.txt file on a USB flash drive, CD-R, or whatnot. This should at least give you the ability to restore the partition table by typing "sudo sfdisk --force /dev/sda < parts-sda.txt"; however, I can't promise that sfdisk won't choke on your bizarre partition table. You'd be able to recover, but only by editing it as I described earlier.

If even TestDisk fails, you could try [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which scans a disk for individual files. The problem is that PhotoRec doesn't recover full filenames, so you'll have to manually rename all your files, which will be a pain.

In any event, before you do anything else, I recommend you look into that SMART status issue in more detail. A tool like GSmartControl (it's in the Ubuntu software repository) will produce far more data. Look for anything that's red-flagged as a problem, and look for a report on bad or remapped sectors.

---

### Post by kirkface8 on 2011-02-02
> **srs5694 said:**
> Try this from a Linux command prompt:

```

sudo mkdir /mnt/sdb3
sudo mkdir /mnt/sdb4
sudo mkdir /mnt/sdb5
sudo mount /dev/sdb3 /mnt/sdb3
sudo mount /dev/sdb4 /mnt/sdb4
sudo mount /dev/sdb5 /mnt/sdb5

```

The last three commands mount your three NTFS partitions. If they complain that you must specify the filesystem type, add "-t ntfs-3g" between "mount" and the device filename. These commands may or may not work. If they work (or if the partitions are already mounted), you should be able to identify their contents to figure out which is which. If one of them is your music, you should be able to copy it over to another disk.

If you can't mount one or more of those partitions, it'll be hard to identify, at least in Linux. Perhaps some Windows utilities would help, but I know relatively little about them. One that I do know is CHKDSK, which fixes disk errors; you'd call it like "CHKDSK C:" -- but what drive letters correspond to the Linux device filenames is something nobody can tell you with certainty at this point. Also, any utility that modifies the disk runs the risk of making things worse.

If none of those partitions is your music partition, you'll have to cross your fingers and use TestDisk; however, my suspicion is that TestDisk will be more likely to work if you've fixed your disk's partitions first. The strange partition table might confuse it. I don't know offhand if you could run TestDisk on an in-use disk. The limitation to which oldfred refers is a limitation of libparted; tools that work more directly on disks, such as fdisk and gdisk, don't have this problem. I don't know if TestDisk imposes such a limitation.

If you have problems with TestDisk and get really desperate, you could use Linux's fdisk to delete all your partitions and then run TestDisk from an emergency CD. There's a decent chance that TestDisk will recover everything, but if it doesn't, you won't be able to boot the computer at all. Do this only after you back up any important Linux-accessible data. Also, you can back up the partition table by typing "sudo sfdisk -d /dev/sda > parts-sda.txt" and saving the parts-sda.txt file on a USB flash drive, CD-R, or whatnot. This should at least give you the ability to restore the partition table by typing "sudo sfdisk --force /dev/sda < parts-sda.txt"; however, I can't promise that sfdisk won't choke on your bizarre partition table. You'd be able to recover, but only by editing it as I described earlier.

If even TestDisk fails, you could try [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which scans a disk for individual files. The problem is that PhotoRec doesn't recover full filenames, so you'll have to manually rename all your files, which will be a pain.

In any event, before you do anything else, I recommend you look into that SMART status issue in more detail. A tool like GSmartControl (it's in the Ubuntu software repository) will produce far more data. Look for anything that's red-flagged as a problem, and look for a report on bad or remapped sectors.

I get back an error after inputting above said commands.

```

Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


```

---

### Post by srs5694 on 2011-02-02
If you get that error for all three partitions, then the only in-Linux solutions are rather drastic. You can try TestDisk to see if you can recover your missing partition and hope it's in better shape, but that runs the risk of doing further damage to your disk.

From here, this is what I recommend:


[list=1]
[*]Buy a backup/replacement disk. Make it a little bit bigger than your current disk, just to give yourself some wiggle room in partition sizing.
[*]Create partitions on the new disk in your desired layout. Be sure to include at least one partition for each partition on your current disk, and make each partition at least as large as its current-disk counterpart.
[*]Use ntfsclone to copy the NTFS partitions to the new disk. The command to copy /dev/sdb3 to /dev/sdc1 would be "ntfsclone --overwrite /dev/sdc1 /dev/sdb3". If this fails, use dd instead, as in "dd if=/dev/sdb3 of=/dev/sdc1". *Be very careful in your partition specifications; if you get them backwards, you'll wipe the data you're trying to preserve!*
[*]Use any tool like like (Clonezilla, tar, cpio, whatever) to copy your Linux partition to the new disk.
[*]Use the Windows recovery tools on the new disk to try to recover the data in the NTFS partitions.
[*]Use TestDisk on the old disk to try to recover the lost partition.
[*]If TestDisk is unsuccessful, use fdisk to try to create a partition that matches the lost NTFS partition. Launch fdisk with its "-l" option and try creating partitions that start on 2048-sector, 16065-sector, and 63-sector boundaries; these are the most likely starting locations of the missing partition. Once you've created a partition, use blkid to see if it's valid NTFS data ("sudo blkid /dev/sdb7", or whatever the partition ID is). If it is, try to copy it with ntfsclone and recover it on the new disk. If not, try another start location. Note that you may need to delete some or all of the old disk's partitions before fdisk will let you create new partitions.
[/list]

---

