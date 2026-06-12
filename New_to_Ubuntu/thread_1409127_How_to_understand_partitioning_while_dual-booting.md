---
title: "How to understand partitioning while dual-booting?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by Laxman_prodigy on 2010-02-17
Hi.

I fell upon the FOSS culture recently and really like to start with Ubuntu. But as I need to do my daily work with softwares from Adobe and others, I still need XP. So, obviously I want to dual boot.

On googling around, I only learnt that "You should install XP first and not other way around".

On booting from the Ubuntu disk, I got confused.

I want to keep both in one harddisk as I have one. XP should take 150 GB and the rest for the UBUNTU:D( 1TB HD).

For 1TB my plan is:
XP - 150 GB
Ubuntu -rest.

I read somewhere that I should partition like this 
i.e. / - ...
/home - ...
swap - ...

Please suggest me for my 1 TB with 150GB allotted for XP how should I configure for the rest? 

One more thing to ask: I have i5 processor and 4GB DDR3 RAM; does Ubuntu fully support it or I have to do something to make it work?

**As you all can clearly see, I am new to linux; forgive me my ignorance.**

---

### Post by Laxman_prodigy on 2010-02-17
People?

---

### Post by audiomick on 2010-02-17
Hallo.
to find out if your hardware will work, boot from the live CD using the "try without changing" option. That loads OS into RAM and runs from there, loading things from the CD as it needs them. It is a bit slow, so don't worry about the speed, but if your computer boots and runs, you can expect it to not really have any problems with Ubuntu.

For the partitioning, there is a lot of information here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
and this is also useful before an install
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

With a drive that big, you would be well advised to create an extended partition and put the whole Ubuntu install in that. That way, if you want to add more partitions later, you wont come up against the problem of only being able to have 4 primary partitions on a drive. That is explained in more detail in the "how to partition" link somewhere.

For your Ubuntu install, you could use this scheme:
10 or 15 GB for the system mounted at /

a bit more than 4GB for the swap partition. The "hibernate" function writes the contents of the RAM into the swap space, so if the swap is smaller than the RAM, the hibernate function will likely not work. If you know you don't want to hibernate, you could get away with around 1GB of swap, unless you are intending to do extremely RAM intensive stuff like really large scale video editing. I have 4GB RAM, and effectively never get into Swap in normal use.

As much of the rest as you want to allocate at /home.

You might want to consider a data partition formatted in NTFS. That way, you would have some space equally accessible to windows and linux for files that you might want to access from both OSs.

---

### Post by mikewhatever on 2010-02-17
I think you should just follow one of the numerous installation guides, that is, if you want to install Ubuntu. If the goal is to understand partitioning, it's best to read about partitioning first and practice in Virtual Box.

---

### Post by anaconda on 2010-02-17
when you have as big a hard disk as you have you should definitely allocate atleast 20GB for your / (root) partition. 
And why?
Because every now and then someone complains that their 10GB rootpartition is full
It really can get full too easily. eg. apt-cache, root users trash and every program you install are located in / partition. Apt-cache has copies of all the program-packages you ever install to your system (it can be emptied though)... 

So if you like to install a lot of programs AND have a big hd, then 20GB shoud be the absolute minimum size of "/". 

Myself I prefer to have only 2 partitions for ubuntu. 2GB swap and the rest to ubuntu everything on the same partition. But I use an external usb-hd for my data storage (some people use their /home folder, but whatever.)

---

### Post by audiomick on 2010-02-17
> **anaconda said:**
> when you have as big a hard disk as you have you should definitely allocate atleast 20GB for your / (root) partition. 
And why?
Because every now and then someone complains that their 10GB rootpartition is full
It really can get full too easily. eg. apt-cache, root users trash and every program you install are located in / partition. Apt-cache has copies of all the program-packages you ever install to your system (it can be emptied though)... 
Fair comment.

---

### Post by Laxman_prodigy on 2010-02-17
Thank you people for your feedback. That was very informative. I will surely check out those links as specified and try to learn. But am very busy now.

So, I am going with this provisioning:
Windows XP -150GB
/ -20 GB
swap -8 GB (2*4GB DDR3)
and rest for the /home.

What is that data partitioning as you told. What does that do? Please elaborate briefly.

Thank you, as always.

---

### Post by mikewhatever on 2010-02-17
8gb is way too much for swap. Make it the size if RAM if you plan on suspending to disk, and less then that, if not.

Data partitions are usually for storing data, personal files, backups, etc.

---

### Post by bodhi.zazen on 2010-02-17
> **Laxman_prodigy said:**
> People?

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

My advice is three partitions ;

/ = root
/data = share data between Ubuntu and Windows
/swap. In general, the more RAM you have the less you need swap. If you have more then 1-2 GB , unless you are doing virtualization, you are very unlikely to need swap.

So, swap = RAM x2 , max 1 Gb (some say 512 Kb). The only exception is if you use slee / hibernation in which case swap = RAM.

You other option of course is to run Windows in VirtualBox. You can integrate very nicely with Ubuntu :

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by Laxman_prodigy on 2010-02-17
> **bodhi.zazen said:**
> See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

My advice is three partitions ;

/ = root
/data = share data between Ubuntu and Windows
/swap. In general, the more RAM you have the less you need swap. If you have more then 1-2 GB , unless you are doing virtualization, you are very unlikely to need swap.

So, swap = RAM x2 , max 1 Gb (some say 512 Kb). The only exception is if you use slee / hibernation in which case swap = RAM.

You other option of course is to run Windows in VirtualBox. You can integrate very nicely with Ubuntu :

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)


Thank you dear. That is a great stuff for a beginner like me.
=D>

---

### Post by oldfred on 2010-02-17
I had just root, swap and a small shared NTFS partition on my 160GB system for three years. The shared windows partition made conversion to Ubuntu a lot easier as my firefox and thunderbird profiles were in the shared partition, so my main applications had the same data in both systems.

Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

