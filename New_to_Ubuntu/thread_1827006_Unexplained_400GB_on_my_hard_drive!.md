---
title: "Unexplained 400GB on my hard drive!"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by chrisp3047 on 2011-08-17
Hi there,
 
I ran disk usage analyser on Ubunutu 11.04 last night, and it told me that I have used 838GB and have available 69GB.
 
But when i click 'scan filesystem' it says the size of the entire filesystem is 404GB. This accounts for all my 'known' data on the drive.
 
Could someone explain how I can find out what is using up the rest of my hard drive?
 
There is over 400gb that I don't understand what it is! I've looked at the recycle bin and cache, and these are small amounts. I'm starting to get worried that it's a virus??? Or a problem with my hard-drive?

---

### Post by chrisp3047 on 2011-08-17
Bump - please help someone!

---

### Post by chrisp3047 on 2011-08-17
Hi there,

I ran disk usage analyser on Ubunutu 11.04 last night, and it told me that I have used 838GB and have available 69GB.

But when i click 'scan filesystem' it says the size of the entire filesystem is 404GB. This accounts for all my 'known' data on the drive.

Could someone explain how I can find out what is using up the rest of my hard drive?

There is over 400gb that I don't understand what it is! I've looked at the recycle bin and cache, and these are small amounts. I'm starting to get worried that it's a virus??? Or a problem with my hard-drive?
 
Thanks to anyone who can help,
 
Chris

---

### Post by WorMzy on 2011-08-17
That's odd.

Can you run

```
sudo du -hxd 1 / | sort -h
``` and post the output here, please.

---

### Post by markp1989 on 2011-08-17
looks like most of that 400 is in the home folder.

try pressing the arrow next to "home" to see what folders under home are taking it up.

home holds every users home folder, so other users may be using it, or it may be in the waste basket if you haven't emptied it in a while.

---

### Post by cottfcfan on 2011-08-17
Disk Usage analyser isn't telling you how much data space you have left, but how much of the disk is being used by physical partitions.
For eg. If I installed Ubuntu and allowed it to take up my whole 1TB Disk, the analyser would tell me that the file system usage was 100%, even though I might only be using 10GB of the disk in data terms.
Hope that makes sense, it does to me:confused:

---

### Post by Elfy on 2011-08-17
Thread closed. Please do not post duplicates, it dilutes community effort.

---

### Post by Azdour on 2011-08-17
Hi,

Did you run the Disk Usage via gksu?:

```
gksu baobab
```

This gives a more accurate picture because if you just run it from the main menu you are running it as yourself and there will probably be directories and files it will not have access to and therefore these will not be part of the disk usage it displays.

---

### Post by Wim Sturkenboom on 2011-08-17
I think some of you ain't getting it; but I might be wrong ;) The top of the image shows 800-odd GB used / 69 GB free. The bars only show 400GB used; I think the question is where the other used 400 GB has gone to?

Next to the output as requested in post #4, I also like to see the output of
```

df -h

```

Possibly a silly question, but when last was the system rebooted?

---

### Post by b0b138 on 2011-08-17
The part at the top that says Total filesystem capacity: 907.1 GB (used 838.1 GB available: 69) is referring the the capacity of ALL your drives/partitions combined, whether they are mounted or not.

The 404 GB on / is just your current system, showing how much space is being used of partitions that are mounted.

So lets say for example you duel boot with windows, and its on a 400G partition, the top part shows ALL drives capacity, and the bottom won't show windows unless you mount that partition

---

### Post by Azdour on 2011-08-17
Hi,

@Wim not sure if you are referrng to my post or not :)

When I run the disk usage analyser it tells me my / is 56Gb. When I run the disk usage analyzer with gksu it tells me my / is actually 80Gb because it is able to include directories and files only accessible by root.

I was asking the OP if they have run the Disk Usage Anaylser with gksu to see if the missing 400Gb appears as part of / because there is 400Gb hidden in root only parts...

---

### Post by Iowan on 2011-08-17
Oops, :oops:
I didn't notice that the duplicate had been closed when I merged the threads.
Re-opened the merged thread.

---

### Post by Wim Sturkenboom on 2011-08-17
Yep, you made a nice mess ;) Now nobody knows what is what :D

---

### Post by scruffyeagle on 2011-08-18
Here's a question nobody else asked yet: Is your home directory encrypted? If it is, then Ubuntu creates a virtual filesystem when that directory is mounted. This was discussed in another thread (#1815216): []("http://ubuntuforums.org/showthread.php?t=1815216"). (Read esp. post #3 of the thread.) Basically, because the data exists in both the physical file system and is duplicated in a virtual file system, the data gets tallied in twice instead of just once when using certain tools.

The person who posted item #3 advised opening a terminal and entering
```
df -h
```
as the command for checking used & available drive space.

---

### Post by howefield on 2011-08-23
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?p=11178506#post11178506](http://ubuntuforums.org/showthread.php?p=11178506#post11178506)

---

