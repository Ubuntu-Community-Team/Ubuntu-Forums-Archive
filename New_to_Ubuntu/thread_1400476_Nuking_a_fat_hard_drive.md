---
title: "Nuking a fat hard drive"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by lile001 on 2010-02-06
I am the proud owner of a Western Digital 1 Terabyte external hard drive, bought on sale cheap!  Just the thing for backups.  However, I find that it will not hold any files over 4GB, because it is FAT32.  Is there a way that a fat-fingered N00B can fatten up this FAT32 drive to be a different file system that can handle large files, or am I over my fat little head here?  Nothing on the drive now that needs to be kept, it can all be wiped.

---

### Post by NCLI on 2010-02-06
Like I said it in the other thread, install gparted from the Software Center, and format it as NTFS if you want Windows compatibility, an as ext4 if you don't care. If you have Karmic, the built-in Disk Utility might be easier for you.

(To be completely honest, the easiest way would be to plug it in to a Windows computer, right-click it and press format >.>)

---

### Post by Gone fishing on 2010-02-07
You really don't want to be using Fat32 (Windows 98 era legacy crap). If the drive has no files on it then install gparted

[CODE]sudo apt-get install gparted[/QUOTE]

You will then find partition editor in System > Administration. Then partition the drive with the partitions you need you can use ext3, ext4 and for windows use ntfs (be careful you can do real damage with gparted). If the drive has got files then back them up and do the above. If backing up isn't possible then there two further options, gparted can resize drives (this takes time). Windows has a commandline tool for converting fat32 to ntfs.

---

### Post by nhasian on 2010-02-07
you can format the drive to NTFS or EXT4 as mentioned above, but i just wanted to warn you that you will want to remove the western digital smartware from the drive if that model came with it pre-installed.

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

---

### Post by cwalker1960 on 2010-02-07
where did you get this it won't hold a file over 4 gig cuz it's fat32??? 
run gparted or partition magic or swissknife or any other of a hundred partition managers i can think of to format it to what ever.. but if you want a windows os to recognize it it better be be fat or ntfs... if you don't care about some win os seeing it, format it to whatever

---

### Post by cwalker1960 on 2010-02-07
the smart ware on the drive will hardly effect any partition you format... if it has any.. it's not even recognized by the bios in boot up

---

### Post by cwalker1960 on 2010-02-07
i don't much about a lot ,,but i know about drives

---

### Post by Isyaltut on 2010-02-07
Gparted is good, it does the job well and easy to use.

If you still want that  harddrive can be read by windows computer, I also recommend to make two partition, one can be fat32/ntfs and the other ext3/ext4.  I do this because I share my external harddrive with my sister and she's using windows. And making two partition or more is a sensible things to do to spread the risk of disk failure when one partition is broken (let's say nasty virus messed it up)

---

### Post by Puzzled Guy on 2010-02-07
Install gparted

Plug in your external hard drive

Run GParted

Choose the drive

Click on the partition

Partition>Format

Then choose ntfs for Windows-Linux compatibility

Wait for it to finish formatting

Done!

---

### Post by The Cog on 2010-02-07
I must wade in and argue against ext4. Every system I have ever installed ext4 on has sooner or later undergone catastrophic firesystem corruption and data loss. The last remaining ext4, my netbook, became unbootable two days ago. It seems that lots of system files had disappeared. It took me a couple of hours to reformat and reinstall.

ext3 is a good choice - it has been around for a long time and is well known and trusted. I tend to use jfs because it seems faster to mount or format than ext3, but I know I am unusual in choosing jfs.

---

### Post by CharlesA on 2010-02-07
I use EXT4 for the OS and EXT3 for any partition that has user data on it. I don't feel like changing file corruption with EXT4.

---

### Post by NCLI on 2010-02-07
This has already been solved in his other thread, so there's no reason to post more suggestions ;)

---

### Post by halitech on 2010-02-07
> **cwalker1960 said:**
> where did you get this it won't hold a file over 4 gig cuz it's fat32??? 
run gparted or partition magic or swissknife or any other of a hundred partition managers i can think of to format it to what ever.. but if you want a windows os to recognize it it better be be fat or ntfs... if you don't care about some win os seeing it, format it to whatever

from here: [http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

> You cannot create a file larger than (2^32)-1 bytes (this is one byte less than 4 GB) on a FAT32 partition.

---

### Post by lile001 on 2010-02-07
> **NCLI said:**
> Like I said it in the other thread, install gparted from the Software Center, and format it as NTFS if you want Windows compatibility, an as ext4 if you don't care. If you have Karmic, the built-in Disk Utility might be easier for you.

(To be completely honest, the easiest way would be to plug it in to a Windows computer, right-click it and press format >.>)

Yes, I took your advice from the other thread and started a new thread here just to focus on one issue.  Thanks!  Gparted wasn't too hard to figure out. 

Having successfully reformatted this drive to ext4, and now reading someone advising against that, I wonder if I'll have trouble later on?  

Meanwhile, I did something intelligent:  cd to the external drive, then launch tar to back up my entire fixed drive directly to a tar file on the external drive (DUH!) instead of having tar make a huge backup on the fixed drive then later trying to move it over to the external drive. 

Tar has finished, I have a 65 GB backup file on my external drive, so far so good.  BUT, tar ended with this cryptic error message:

"tar: Error exit delayed from previous errors".  What does this mean? 
Is my backup corrupt, or not?

---

### Post by lile001 on 2010-02-07
> **Gone fishing said:**
> You really don't want to be using Fat32 (Windows 98 era legacy crap). If the drive has no files on it then install gparted

[CODE]sudo apt-get install gparted

You will then find partition editor in System > Administration. Then partition the drive with the partitions you need you can use ext3, ext4 and for windows use ntfs (be careful you can do real damage with gparted). If the drive has got files then back them up and do the above. If backing up isn't possible then there two further options, gparted can resize drives (this takes time). Windows has a commandline tool for converting fat32 to ntfs.[/QUOTE]

Key information for n00bs:  Gparted can be started from the partition editor in system > administration as the man sez.  Thanks for this!  I searched and searched, most people have advised "use GParted" without this key, simple, but essential bit of information.  If someone else is reading this thread (I know they will) to figure out the same issue, they'll need to know that.   Thanks, Gone Fishing!

---

### Post by nhasian on 2010-02-07
its common knowledge

[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

> **cwalker1960 said:**
> where did you get this it won't hold a file over 4 gig cuz it's fat32???

---

### Post by lile001 on 2010-02-07
> **lile001 said:**
> Yes, 
Tar has finished, I have a 65 GB backup file on my external drive, so far so good.  BUT, tar ended with this cryptic error message:

"tar: Error exit delayed from previous errors".  What does this mean? 


So here is the last question for this thread - is this error message signifigant?

---

### Post by nhasian on 2010-02-09
i would be suspicious of that error.  you should test the tar archive

[http://www.g-loaded.eu/2007/12/01/veritar-verify-checksums-of-files-within-a-tar-archive/](http://www.g-loaded.eu/2007/12/01/veritar-verify-checksums-of-files-within-a-tar-archive/)

> **lile001 said:**
> So here is the last question for this thread - is this error message signifigant?

---

