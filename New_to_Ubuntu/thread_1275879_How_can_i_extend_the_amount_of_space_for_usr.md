---
title: "How can i extend the amount of space for /usr"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by kevinhobson2000 on 2009-09-26
Hi,

I am trying to install VMware Server but my installation fails as it says there is not enough space on /usr.

Can anyone advise me how i can extend or add more space for this part of the file sytem?

Thanks

Kev

---

### Post by louieb on 2009-09-26
The basic of it is to use Gparted run from a live CD to rob space from another partition, get the free space in a place where it can be added. Then expand the one you want bigger.

[Expanding an Ubuntu System Partition - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by pauna on 2009-09-26
Could you please post the results of the terminal command "df -k", that would help in determining what is the status of your disk space and how it is set up. I suspect it's not /usr that has run out of disk space, that should not normally happen, maybe it's the whole root file system.

The simplest solution, which does not require any changes to partitioning, is to make room in the full file system by either removing unwanted stuff or moving necessary stuff elsewhere.

As the first task, clean up some stuff from package management:
  $ sudo apt-get clean  
  $ sudo apt-get autoclean

Then, you can very easily get additional 20-25 megs of free space if you get rid of unwanted language files. Localepurge should manage that for you: 
  $ sudo apt-get install localepurge
  $ sudo localepurge

These tasks should give you some more disk space on root file system in general. However, they may not be enough for you especially if you have interesting partitioning and it's really /usr that is full. If that's the case, post the "df -k" output and we'll think some more. Growing/shrinking partitions is somewhat risky and I'm not the first to recommend that.

---

### Post by kevinhobson2000 on 2009-09-26
HI,

Thanks for the help with this output below:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              2395540   2314500         0 100% /
tmpfs                  4036276         0   4036276   0% /lib/init/rw
varrun                 4036276        84   4036192   1% /var/run
varlock                4036276         0   4036276   0% /var/lock
udev                   4036276       160   4036116   1% /dev
tmpfs                  4036276        84   4036192   1% /dev/shm
lrm                    4036276      2760   4033516   1% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024        16      1008   2% /tmp

Thanks 

Kev

---

### Post by louieb on 2009-09-26
pauna is right to say its somewhat risky to shrink a partition. However you don't have much choice unless you want to buy another hdd.

There is a problem with the installer - its default is to allocate 2.3GB for the Ubuntu install partition.  When the absolute minimum  is about 4GB and the recommended minimum is 8GB.  You will need more than that just for a disk for your virtual machine.  -  it was for just this reason drs305 wrote the how to I linked in post #2.  

If you have questions about the process. I'll try to answer.

---

### Post by kevinhobson2000 on 2009-09-29
Hi,

I just reinstalled Ubuntu and gave it 5 gig.

Thanks for the help

Kev

---

