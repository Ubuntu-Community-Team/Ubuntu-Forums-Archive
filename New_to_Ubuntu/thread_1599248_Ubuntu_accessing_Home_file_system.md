---
title: "Ubuntu accessing Home file system"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by zcahfg2 on 2010-10-17
Hello 
My Ubuntu has 3 file systems : root home and swap
root has 27 gig home 80 gig and 1 gig for swap

I am installing Tex live 2010 but it is giving out msg that i do not have enough space left.
How do I access my home partition?
I'm trying to move music, movies etc files in my document to home partition to free up some space for Root partition.
From disk analyser I have approximately 80gig free space left but I do not know how to access this partition.

Thanks.

---

### Post by delix on 2010-10-17
if the folder that the application is trying to install to is in the root partition then it would explain why you don't have acces to the home partition, try resizing the root partition or changing the installation to go into a different folder, one that is in your home partition

---

### Post by zcahfg2 on 2010-10-17
> **delix said:**
> if the folder that the application is trying to install to is in the root partition then it would explain why you don't have acces to the home partition, try resizing the root partition or changing the installation to go into a different folder, one that is in your home partition
I do not know where my home partition is, according to the disk analyser, 
my 'home' folder is located inside '/' partition, this is root right?
I cannot find 'home' partition nor swap. This is strange because it shows my correct total capacity 100s gig without other partitions and my actual usage 27gig

---

### Post by amjjawad on 2010-10-17
> **zcahfg2 said:**
> Hello 
My Ubuntu has 3 file systems : root home and swap
root has 27 gig home 80 gig and 1 gig for swap


These are not file systems, these are partitions :)

> 
I am installing Tex live 2010 but it is giving out msg that i do not have enough space left.
How do I access my home partition?
I'm trying to move music, movies etc files in my document to home partition to free up some space for Root partition.
From disk analyser I have approximately 80gig free space left but I do not know how to access this partition.

Thanks.

Places > Home Folder is supposed to be your /home partition.

---

### Post by amjjawad on 2010-10-17
> **zcahfg2 said:**
> I do not know where my home partition is, according to the disk analyser, 
my 'home' folder is located inside '/' partition, this is root right?
I cannot find 'home' partition nor swap. This is strange because it shows my correct total capacity 100s gig without other partitions and my actual usage 27gig

If "home folder" inside / partition (root), it means you don't have /home partition.

Could you please take a screen shot while you're on Disk Utility (System > Administration > Disk Utility) and attach it here?

---

### Post by zcahfg2 on 2010-10-17
I just realised I only allocated 10 gig to 'root'
Does that mean all my music, movies are in Home partition?

I only allocated 10 gig due to claims from other threads that this capacity is enough for most ubuntu users, but clearly it not enough for me.
Is there a way to increase root size, or move all applications to home partition?

I am having difficulty understanding the file system in Ubuntu because in Windows I could just go to 'my computer' to access all partitions. And Ubuntu software centre never ask the location for the software when installing.

---

### Post by amjjawad on 2010-10-17
> **zcahfg2 said:**
> I just realised I only allocated 10 gig to 'root'
Does that mean all my music, movies are in Home partition?

Still not sure whether you have /home partition or not but I can tell from your words that you don't have /home partition and your home folder is inside your / (root) partition.

> 
I only allocated 10 gig due to claims from other threads that this capacity is enough for most ubuntu users, but clearly it not enough for me.
Is there a way to increase root size, or move all applications to home partition?

10GB is the minimum and basic size for / (root) partition. Those who have 10GB as root, they do have more size for /home partition which I think you don't have. 

> 
I am having difficulty understanding the file system in Ubuntu because in Windows I could just go to 'my computer' to access all partitions. And Ubuntu software centre never ask the location for the software when installing.
Linux (Ubuntu) is quite different than Windows. I highly recommend to read more about Linux (Ubuntu) so that you could be familiar with it.
There are lots of threads, topics, articles, guides, etc that will make you understand many stuff especially if you're new to Ubuntu.

[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by zcahfg2 on 2010-10-17
[[URL=http://img843.imageshack.us/i/screenshotysf.png/][IMG]http://img843.imageshack.us/img843/4205/screenshotysf.th.png[/IMG]]("http://img843.imageshack.us/i/screenshotysf.png/")
[/URL]


[[IMG]http://img63.imageshack.us/img63/1838/screenshot1lg.png[/IMG]]("http://img63.imageshack.us/i/screenshot1lg.png/")

Thanks :)

---

### Post by amjjawad on 2010-10-17
109GB (the big partition in the middle) is for what exactly? 
you could use it to save your data files there.

If you click on it in Disk Utility, what does it say under "Mounted"? does it say mounted as /home?

---

### Post by Vaphell on 2010-10-17
check the properties of that 109GB ext3 partition, see if /home is its mount point

/ is where all the installed apps go, if you have installed plenty of programs it could run out of space (10GB currently assigned to it is not that much in such scenario). You need to resize it in gparted at the expense of that 109GB partition

---

### Post by zcahfg2 on 2010-10-17
> **amjjawad said:**
> 109GB (the big partition in the middle) is for what exactly? 
you could use it to save your data files there.

If you click on it in Disk Utility, what does it say under "Mounted"? does it say mounted as /home?
It is mounted as /home :)

---

### Post by amjjawad on 2010-10-17
> **zcahfg2 said:**
> It is mounted as /home :)

GOOD :D
Then, that 109GB is your /home partition. You have 3 partitions:
1- Root (/)
2- Home (/home)
3- Swap (swap)

---

### Post by amjjawad on 2010-10-17
If you're going to re-size your root (/) partition as suggested by Vaphell then you need to have a backup for your important files before anything else.

---

### Post by Vaphell on 2010-10-17
agreed, playing with partitions can blow up in your face so backing up is a must, better be safe than sorry

---

### Post by cariboo on 2010-10-17
No matter how much free space you have on /home, according to your screenshot, /  is used 100%, you have to free up some space before you can install anything. There are several gui utilities to make more free space, but the easiest way I know is to open a terminal and type:

```
sudo apt-get clean && sudo apt-get autoremove
```

The above two commands will clean all the archived packages in /var/cache/apt/archives, and the second command will remove any unneeded dependencies. If you have a typical installation you should free up at least 400-500Mb of space.

---

### Post by zcahfg2 on 2010-10-17
Thanks a lot guys,
It really helped.

I will read up the link posted above :)

---

