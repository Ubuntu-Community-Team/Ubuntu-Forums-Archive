---
title: "Blanking a hard drive"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-08-02
Hi, I've been trying to research what I need to do here... My school has let me use a computer, but I'm about to graduate, so they will want it back. Before I give it back though, I want to make sure all the data I had on it won't be accessible by the next person who gets it. So I've been looking around, and I've found several versions, but I'm not exactly sure what all the differences are. Here is what I've found, if someone could tell me what I'm missing, or correct what I miss, I'd be very grateful.

Option 1: ```
dd if=/dev/zero of=/dev/sda bs=1M
```
Writes zeros to your entire hard drive. Fastest, but people claim regular old file recovery programs can sometimes get things back.

Does "bs=1M" just attempt to speed up the write? If not, what is it there for?

Option 2: ```
dd if=/dev/random of=/dev/sda
```
Writes random numbers to hard drive, making it harder to get data back.

Why is "bs=1M" not used here?

Option 3: ```
dd if=/dev/urandom of=/dev/sda
```
I'm not exactly sure what the difference is between this one and the previous one...

Sorry for asking a question that does seem to have answers around... I just can't seem to figure out why there are so many DIFFERENT answers :D

---

### Post by nmaster on 2010-08-02
to learn about dd just check out the man page: ```
 man dd 
```the "bs" stands for block size.  for what you want to do, the block size doesn't matter, so leaving it blank is fine. however, the commands you posted won't actually do what you want them to.  as you mentioned, it is in fact possible to recover some of the information.  

this is a much better tool: [http://www.dban.org/](http://www.dban.org/)  it is used by many private companies and consumers.  its secure.  however, it will also remove the operating system.  i'm not sure if that's what you want, but it is the most secure thing to do.

---

### Post by Ozymandias_117 on 2010-08-02
> **nmaster said:**
> to learn about dd just check out the man page: ```
 man dd 
```

I had already checked it. All it tells me is "bs=BYTES read and write BYTES bytes at a time." which doesn't really tell me what the point of using it is :D

to wipe your hard drive, use this: [http://www.dban.org/](http://www.dban.org/)

Alright, I'll check it out. Thanks.

---

### Post by jtarin on 2010-08-02
I swear by [ActiveKillDisk]("http://www.killdisk.com/downloadfree.htm"). The free version is more than adequate for one drive at a time.
> Active@ KillDisk  FREE version features:

    * Detects and displays information about all partitions, hard disks and floppy drives currently connected to your computer 
    * Wipes out all floppies and hard disk drives completely by secure overwriting data on physical level using [One Pass Zeros] data destruction method
    * Erases partitions, logical drives and even not used disk space
    * Erasing report is created and can be saved as a file
    * Supports SSD, IDE, SATA and SCSI drives 
    * Supports larger than 128GB hard disks via using LBA/LBA48 mode to access drive's data 
    * File systems (FAT, FAT32, NTFS, etc) on the drive do not matter, detected physical drive is erased using low-level disk access 
    * Double confirmation excludes possibility of accidental erasing of data on a drive
    * Very easy to use, utility has intuitive console interface and command line mode for the advanced users 
    * Works on any system capable of boot from floppy in DOS mode
    * Utility is so compact that can be placed on bootable diskette and used from it. You do not even need to boot from the hard drive to destroy it 
    * Cleans hard drive, floppies, etc.
    * FREE product updates from the Web   



---

### Post by -kg- on 2010-08-02
You know, unless the next person has (very expensive) Forensic software and equipment, I think you would be safe wiping the drive using the method you mentioned.  According to [this article from Wikipedia]("http://en.wikipedia.org/wiki/Data_remanence#Feasibility_of_recovering_overwritten_data"):

> according to the 2006 NIST  Special Publication 800-88 (p. 7): "Studies have shown that most of today’s media can be effectively cleared by one overwrite" and "for ATA disk drives manufactured after 2001 (over 15 GB) the terms clearing and purging have converged."[1]  An analysis by Wright et al. of recovery techniques, including magnetic force microscopy, also concludes that a single wipe is all that is required for modern drives.

If you have *_**extremely**_* sensitive data on it, or it will be used by someone with the wherewithal to actually retrieve such data (do you go to a computer school with such equipment and training?), the only truly safe way to ensure your sensitive data cannot be retrieved is to remove the drive, destroy it, and replace it with a new one.

---

### Post by nmaster on 2010-08-02
the point of choosing the block depends on what people are trying to do.  for example, a very (very, very) crude form of disk benchmarking is to dd a file to a drive while running iostat.  in this case, it would be very useful to change the block size.

---

### Post by lyall on 2010-08-02
first check with your school's it department before using Boot & Nuke
or any other program to wipe the hard drive clean
they might charge you for the laptop/pc if you do
tell them what you want to do
and asked them if they can place a fresh image on it or install the OS back on it, if so they might let you run Boot & Nuke or any other program to clean the hard drive

good luck and have fun learning

---

### Post by k3lt01 on 2010-08-02
Because I now refurbish PCs to give away and they are initially given to me by various sectors of society (legal offices, libraries, schools etc) I use Dban. It is the only thing I'm comfortable using with what can be very sensitive information.

---

### Post by Nostalos on 2010-08-03
While just using output of /dev/zero is not enough to completely wipe it.  Dban and the others are doing the exact same thing as the dd if=/dev/urandom commands above except it runs them many many times.   


If you are truely paranoid and keep very sensitive data (not to smart on a PC you don't fully own anyway) sure run DBAN or dd if=/dev/urandom 35 times per disk.   Unless the next guy is running very expensive tools to get at the data you are wasting your time running the cycles anyway.   Once the data is overwritten, they are no longer looking at what can be read at a OS level, they are then starting to look at individual sectors and residual magnetic "impressions" left by previous writes.

As k3lt01 stated.  if its sensitive information or you are have a legal responsibility to utterly destroy any previous data, then burn the cycle time.  If you are just worried about the next guy grabbing a cookie to be able to login to your facebook account.   if=/dev/zero a couple of times will do the trick.

As for block size,  its just means "how much data write at once"  Small blocks will take longer since there are more operations to perform for a large number of 512byte blocks than a alot fewer 5MB blocks.

---

### Post by jtarin on 2010-08-03
> **Nostalos said:**
> While just using output of /dev/zero is not enough to completely wipe it.  Dban and the others are doing the exact same thing as the dd if=/dev/urandom commands above except it runs them many many times.   

What anyone has failed to mention is that these 3rd-party apps will run in memory from boot medium whereas dd if=/dev/urandom commands must be run from a live CD/DVD or another drive. This can very problematic to the uninitiated.BTW the free version of ActiveKillDisk makes one wipe per run. You would have to reboot to run another.

---

### Post by Ozymandias_117 on 2010-08-03
Okay, sounds like running /dev/zero to the drive a time or two should be enough. I think the most sensitive thing I had on it was address and phone number, but I had run some software on it and found tons of stuff from previous users... So I was a tad worried, lol. Thanks guys. :)

---

### Post by nmaster on 2010-08-03
> **Ozymandias_117 said:**
> Okay, sounds like running /dev/zero to the drive a time or two should be enough. I think the most sensitive thing I had on it was address and phone number, but I had run some software on it and found tons of stuff from previous users... So I was a tad worried, lol. Thanks guys. :)

just curious, but what software were you able to use?

---

### Post by Ozymandias_117 on 2010-08-03
From what everyone has said, it sounds like simply booting to a wolvix liveCD using the copy2ram option and the noslim option (for speed) then running ```
dd if=/dev/zero of=/dev/sda
``` should be secure enough for my needs. By the way... is there anything like /dev/zero for ones? (Like /dev/one although, that isn't there :D)

---

