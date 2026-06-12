---
title: "Partitioning: much Ubuntu, little Windows"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Phlex_de on 2009-06-16
I'm am planning to do the switch to ubuntu and would like to prepare my hard drive. 

Currently it is 100GB for windows and programms, 200GB for documents, videos and stuff like that. I am wondering what's best for a ubuntu setup.

Can you give me some advice how I should partition my 320GB?
And I got 4GB of ram, what is the best swap size? Twice the ram still up to date?

It should me mostly for ubuntu but some space left for windows in case I need a system I am familiar with (maybe few games, too).

---

### Post by Reymond on 2009-06-16
> **Phlex_de said:**
> 
It should me mostly for ubuntu but some space left for windows in case I need a system I am familiar with (maybe few games, too).

I've partitioned my hard drive like you are wishing to do few days ago with ubuntu 9.04 & M$ windows XP (sp 2). I've fixed space for linux swap 1.5 times of RAM. 20% & 33% of rest of the space I've allocated for linux(format in ext4 filesystem) & windows(format in ntfs) respectively. Rest is allocated for storing data(ntfs)(47%).
 
But to be honest,ubuntu does not take more than 35 GB (with all its packages installed & with all updates).

Hope this will help you.

---

### Post by snakeman21 on 2009-06-16
It is always a good idea to keep windows around for a while while you switch... I dual booted for about six months before taking the full plunge.  

Honestly, I guess how you partition it is up to you.  If you don't use the full 200 GB for files, maybe you could set aside like 75 GB or so just for now.  

And twice the RAM is good, but four gigs is a lot of RAM, so you'd be perfectly fine with 1.5, which would be 6 GB of swap.  

Hope this is helpful.

---

### Post by SoftwareExplorer on 2009-06-16
If you are storing your files elsewhere, 8-10 GB is plenty for ubuntu. Heck, a fresh install might fit in half that.

---

### Post by KIAaze on 2009-06-16
Both Windows (XP at least) and Ubuntu should hold on 5GB after a clean install (not 100% sure for Windows).
But you should allocate at least 10GB to each if you plan to install lots of programs.

If I had 320GB, here's what I think I would do:

> 60 GB ntfs Windows (10 GB for a bloated Windows + 50 GB for games (5 modern games using 10GB disk space for example))
35 GB ext4 / (since it takes up 35 GB with all packages installed according to Reymond)
5 GB ext3/ext4 unallocated to test some other distros eventually
214 GB ext4 /home
6 GB swap (following advice given by others here)


You could also experiment with a separate /usr to share between distros, but I'm not sure how well this works.

Note: It is possible to resize partitions later with gparted.

---

### Post by Aralhach on 2009-06-16
6 GB of swap!!!! Wow... that's a lot.  I've always felt that 1 GB of swap is more than enough.  I've got 2.5 GB of RAM and 1 GB of swap and I NEVER use the swap (I don't fill up the RAM).  

One thing you can do is have a big partition or several partitions formatted with NTFS or whatever that you can access with Ubuntu OR Windows.  I'd say to put about 200 GB in shared partitions like that (5 modern games will not fit on 10 GB anymore.... xD).  And do keep a separate /home partition for safety.

Hope this helps... ;)

---

### Post by KIAaze on 2009-06-16
I meant 10 GB per game approximately. ;)
Seems appropriate to me after some research. Max I've found was 12 GB for games like Crysis or Mass effect.

Anyway, it's unlikely, I'll buy any Windows-only games in the near future, except maybe Starcraft 2. :)

---

### Post by H2SO_four on 2009-06-16
I thought the whole 2x ram for swap was for back in the day when 128mb ram was plenty.  I have 1GB swap and it runs perfectly.  I have never used over 2.5GB ram, and thats with multiple VM's running and other apps.  I don't see the need for a huge swap partition when I can't "fill" up my dedicated ram.

---

### Post by billgoldberg on 2009-06-16
> **Phlex_de said:**
> I'm am planning to do the switch to ubuntu and would like to prepare my hard drive. 

Currently it is 100GB for windows and programms, 200GB for documents, videos and stuff like that. I am wondering what's best for a ubuntu setup.

Can you give me some advice how I should partition my 320GB?
And I got 4GB of ram, what is the best swap size? Twice the ram still up to date?

It should me mostly for ubuntu but some space left for windows in case I need a system I am familiar with (maybe few games, too).

200mb /boot
10gb /
3xxgb /home

Is what I use on my laptop running Fedora. You could also do swap, but I don't even have swap with 3gb or ram.

---

### Post by Lazy-buntu on 2009-06-16
I just built my first PC and this is how I partitioned my hard drive:

Partition 1: Windows 7 (235GB NTFS)
Partition 2: Data (370GB NTFS)
Partition 3: Extended Partition
Partition 3a: Ubuntu 9.04 (~70GB ext4)
Partition 3b: Swap (~8GB)

I use Windows 7 most of the time, and all of my games/applications are on that partition so I gave it plenty of space. Data I use between Ubuntu and Windows 7 for storing music, documents, etc. Ubuntu I haven't gone above 25GB on my laptop even with a virtual box installed so I was generous with 70-75GB of space. Swap I'm not very familiar with, so I went with the old saying of 2x my RAM size. I can always shrink it if need be. 

It's hard to load up an Ubuntu partition if you're not putting your data on it, so if you're keeping your data separate like I am, you could keep Ubuntu at 30-40GB. I'd say 35GB Ubuntu, 210 GB Data, 1-2GB swap, and Windows can have the left-overs if you're really looking to use Windows for just basic things.

---

### Post by Aralhach on 2009-06-17
Well, like I said before 1 GB of swap is PLENTY.  I've never filled up my 2.5 gigs with several things running (VMs, browser, music, downloads etc.)

Those 8 gigs of swap are just sitting there.. put 'em to better use! ;)

---

### Post by mikechant on 2009-06-18
> Well, like I said before 1 GB of swap is PLENTY. 

True for normal swap usage, but if you want to be able to hibernate you need swap size at least equal to RAM size. Anything bigger than that is a waste.

---

### Post by Phlex_de on 2009-06-19
Thanks for you help.
Ok, an estimate of my new partition:
```

/boot      0.200
/         35      ext4
/home    100      ext4
/data    100      ntfs
/win      55      ntfs
/swap      6

```
Is ext4 ok for /boot?
Does the order make any difference? 
And I don't really know what primary or logical means. Should I?

---

### Post by KIAaze on 2009-06-21
> Is ext4 ok for /boot?
Yes it is.
However, you should be aware that not all distros can mount ext4 partitions.
I currently have this problem with Puppy Linux not being able to read my data on ext4 for example.
But this will probably change quickly and the Ubuntu 9.04 Live CD can read them, so it's not such a big issue.

> Does the order make any difference?
Not directly.
But resizing a partition to the "right" is faster than resizing it to the "left" because the data at the beginning of the partition doesn't need to be moved. Also, ntfs partitions can't be resized to the "left" as far as I know, so it's better to place them at the beginning.
So you might want to keep that in mind in case you plan to resize partitions.

> And I don't really know what primary or logical means. Should I? 
Logical partitions are a way to get around the limit of 4 primary partions (You cannot have more than 4 primary partitions).
To create logical partitions, you first have to create an extended partition containing them.
The main difference between primary and logical as far as I know is that the boot flag can only be set on primary partitions.

Windows should be installed on a primary partition ([but you don't have to]("http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition")).
GNU/Linux distros can be installed on primary or logical partitions.

[http://en.wikipedia.org/wiki/Disk_partitioning#PC_BIOS_partition_types](http://en.wikipedia.org/wiki/Disk_partitioning#PC_BIOS_partition_types)

---

