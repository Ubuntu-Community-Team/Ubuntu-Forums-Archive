---
title: "New, dual boot install. help with optimal partitioning"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by halexmar6 on 2011-05-30
Hi all!

So I have been doing some research and I am ready to install but have a question I was hoping to get some opinions on!

I have a win7 partition for school work, just autodesk and photoshop really but I dont find windows reliable for saving my life's work on so I want ubuntu to be my personal OS.

I have gotten to setting up my partitions and want to know what is a good way of dealing with partitioning the drive.  So maybe a separate one for my personal and work files that can be shared by both OS? how should i label them in the Mount Point?

my HD is 500 gb.  157 for windows, the rest is free to be allocated.

maybe you can recommend some ways of keeping your data safe from OS crashes, have a partition strictly for backing up?, etc.

also i should mention that 8.04 was the only one i was able to get to boot, but thats another topic.

thanks so much!

-Hm

---

### Post by entropy1 on 2011-05-30
I recommend an ext4 partition for /
an ext4 partition for /home
an NTFS partition for files files to share between windows and linux.
And also a swap partition.

Since a hard drive can have at most 4 regular partitions, you will need to make one of these four an extended partition inside of which you can put any number of logical partitions.

For backups, I recommend using an external drive - either a flashdrive or an external hard drive.

---

### Post by entropy1 on 2011-05-31
I've attached an image of the layout of my hard drive and of my home directory.  Notice that "Documents" in the home directory is a symbolic link.  It points to a place in my NTFSdata partition where I keep most of my stuff.  In win 7's windows explorer, I have favorites that also point to this partition.  I don't use my user directory on the C drive for much at all.  Since I keep most of my stuff in the NTFS partition, my /home partition is quite small.

---

### Post by dFlyer on 2011-05-31
> **halexmar6 said:**
> Hi all!

So I have been doing some research and I am ready to install but have a question I was hoping to get some opinions on!

I have a win7 partition for school work, just autodesk and photoshop really but I dont find windows reliable for saving my life's work on so I want ubuntu to be my personal OS.

I have gotten to setting up my partitions and want to know what is a good way of dealing with partitioning the drive.  So maybe a separate one for my personal and work files that can be shared by both OS? how should i label them in the Mount Point?

my HD is 500 gb.  157 for windows, the rest is free to be allocated.

maybe you can recommend some ways of keeping your data safe from OS crashes, have a partition strictly for backing up?, etc.

also i should mention that 8.04 was the only one i was able to get to boot, but thats another topic.

thanks so much!

-Hm

Is photoshop required for school or can it be replaced with GIMP or some other linux program like lightzone or bibble5? I also just notice that 8.04 was the only version you were able to get to boot? You really need to figure out how to get at least 10.04 to install. If you list some of your problems maybe someone can help.

---

### Post by mike_f on 2011-05-31
I would repartition your hard drive to create at least one shared NTFS partition. Linux NTFS read/write support is pretty solid. My dual boot systems are partitioned like this:

- sda1 - primary for Windows 
- sda2 - primary for Windows (if needed)
- sda3 - spare primary
- sda5 - extended
- sda6 - logical - NTFS shared data
- sda7 - spare logical
- sda8 - logical - Ubuntu root partition
- sda9 - logical - Linux swap

BEFORE ANYTHING ELSE, BACK UP CRITICAL CONTENT to two places - external hard drives and/or an Internet service like mozy or carbonite. 
To make navigation easy, I would create a large /data directory (in /) and mount sda6 there, alternatively you could mount it under /home/data. If you are paranoid about some Ubuntu apps corrupting NTFS, use a different data partition (ex: sda7) for those. I've had issues with updating large files from Linux but it could be something else. 
I'm not a Win7 expert so you'll have to search for details on moving the 'My Documents' equivalent and other personal content folder(s) to the shared data partition.
I'd use sda3 for a new test install of Windows if you need to try something risky. Flag it as hidden to avoid screwing up your drive lettering. This touches on other multiple boot issues and is a whole different topic.
The Ubuntu partition can be pretty small unless you keep large files in your /home directory.
HTH!

---

### Post by mastablasta on 2011-05-31
8.04 support is being dropped if it wasn't dropped already. you really need 10.04. 
 
btw linux can do automatic partitioning. you can use windows NTFS partition to keed data on it as it iwll be accessible form both systems.
 
so just give 30 GB free space for linux (it will be autopartitioned during install) and the rest is NTFS.
 
keep it simple.

---

### Post by nzjethro on 2011-05-31
I have 3 partitions, one for Win 7, one for Meerkat, and one for shared files. I back up on an external hard-drive, and created a swap file within my Ubuntu partition. That way, I don't have to use up one of my four possible partitions for a little 2GB swap.If you want to do that rather than have a separate swap partition see:
[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)
It depends on your RAM, and how you use your computer. I have 2GB of RAM, and rarely suspend my laptop, so I created 2GB of swap in my Ubuntu partition. I've had no issues, and have a spare partition if I wanted to install another OS or something! Ideal.

---

### Post by trizrK on 2011-05-31
I personally suggest adding a complete new drive if you have one available. This prevents all the potential horrors that partitioning can cause in the future. I have windows 7 on a 400GB hdd for Steam.

---

### Post by halexmar6 on 2011-05-31
Hey thanks for all the feedback and options everyone! It really got me in the right direction as far as what I might need.

So maybe you can proofread my plan here. 

Alright, looks like windows7 has a little swapish looking partition I dont want to delete so I already have sda1 and 2 used up... leaving me with 2 to use since I hear that a HD only takes 4 partitions.  (but I can make subs in one it seems...so maybe a quick rundown on how to make that? )

Also, I was thinking of using gparted to format a NTFS for all my data, like 300gb or so.  
(mainly to keep my life stored and safe and not really for daily access)

Then later once i figure out how to get a more updated version loading, get ubuntu to an install in the remaining unallocated?  I wont do manual, ill just let it set it up as it sees fit.  how does that sound?

Thanks again for the help!

---

### Post by halexmar6 on 2011-05-31
> **trizrK said:**
> I personally suggest adding a complete new drive if you have one available. This prevents all the potential horrors that partitioning can cause in the future. I have windows 7 on a 400GB hdd for Steam.

:( I dont really want to dig up a separate HD, but...what types of horrors are we talking here?  you got me a bit concerned.

---

### Post by el_koraco on 2011-05-31
If it were me, I'd make an extended partition for / and /swap, say 30 and whatever GB each. Keep /home in the / partition, put everything else on the NTFS data partition, and just symlink everything to the folders in /home. That way your data is as safe as it gets. Don't see a reason for a separate /home partition on dual boot really.

---

### Post by oldfred on 2011-05-31
If you are putting all your data in a NTFS partition, then you do not have to have a separate /home.

What version are you installing? 10.10 has a description error where it says use entire partition it just goes ahead and erase drive and uses entire drive. For that reason I always suggest manual partitioning and manual install. I always want control over where and how large partitions are.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Psychocats has not updated to show shared as NTFS, do not use FAT.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

