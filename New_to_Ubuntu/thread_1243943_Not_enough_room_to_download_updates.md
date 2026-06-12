---
title: "Not enough room to download updates?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by fatgreta on 2009-08-18
Hi,

I installed Ubuntu alongside windows. All of the installation guides I've read talked about sliders in the partitioning process, I did not have that option as far as I can tell (version 9.04, 64bit version). So it just created the partitions however it did that. Now, when I try to install the updates, I get a message saying there's not enough room on the disk. I have a 500GB hardrive, with only Windows XP installed and about 40 GB of data from my old computer, so there has to be enough room on the drive. I have no idea how to 

a) determine how much space each partition has;
b) determine how much space each partition reasonably needs;
c) free up more space on Linux
d) figure out if I'm even asking intelligent questions about this. 

In short, I am very, very confused right now. The user guides I've found are between 130 - 700 pages long, and as far as I can tell don't address this issue. The threads and other articles I've found about this contain too much technical jargon for me to understand.

Can anyone help me move forward on learning about Linux?

Thanks,

Chris

---

### Post by Kedster on 2009-08-18
Hey dude,

alight to look at the partition sizes you could use many tool but i think because you are going to be doing some partioning you may as well install Gparted
either by going to applications menu at the top and then "add and remove" and when that load search for "Gparted" or u could also use the command line and it would be something like
```
Sudo apt-get install gparted
```
but I don't know if that the exact name of the package.

then when u get that installed it will be in the top menu under System>Administration> partion Editor

then that will show you the sizes of the dive and partitions and give u a way to edit them BUT dont just go and do random stuff 


and id say 20 or up for windows 
10 or up for ubuntu system 
but it also depends where you are going to store your personal music movies and what ever else, in my opinion i think that  you should look at [this guide]("http://www.psychocats.net/ubuntu/partitioning") and I think the best one is the last one 

 and ummm I don't want to say any more because I am not the proffesional

---

### Post by chrisamiller on 2009-08-18
A few things may help you:

1) typing "df -h" from a terminal will give you a list of partitions and how full they are.  If you'd prefer a graphical way of looking at your disk space, including the ability to drill down into folders, you'll find a tool under Accessories > Disk Usage Analyzer

2) If you'd like to look at your partition table, gparted is an excellent utility.  Install with:
sudo apt-get install gparted, 

then run it fom the command line with 
sudo gparted.

3) If you're dual booting, the most sensible setup is to give Ubuntu about 10GB of space, but to make sure that you're saving all of your documents, videos, etc onto your big partition.  This might be your windows partition (if you use only two), or it may be on a third, seperate data partition, which is my preferred method.

---

### Post by llamabr on 2009-08-18
First, do:

```
sudo apt-get clean
```

Then, post the output of

```
df -h
```

---

### Post by fatgreta on 2009-08-18
> **chrisamiller said:**
> A few things may help you:

1) typing "df -h" from a terminal will give you a list of partitions and how full they are.  If you'd prefer a graphical way of looking at your disk space, including the ability to drill down into folders, you'll find a tool under Accessories > Disk Usage Analyzer

OK, doing that I got this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   32M  99% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  144K  2.0G   1% /dev
tmpfs                 2.0G  480K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             464G   44G  421G  10% /media/disk

The problem is, I don't know what any of that means. 

The Disk Usage Analyzer was a bit more confusing, I just couldn't figure out how to understand what it was telling me. When I first opened it, it showed me as using something like 93% of the space, but the space available was only a few GB? I tried some of the options, things changed and I'm now totally confused by that thing.

> **chrisamiller said:**
> 2) If you'd like to look at your partition table, gparted is an excellent utility.  Install with:
sudo apt-get install gparted, 

I did that, yea!

> **chrisamiller said:**
> then run it fom the command line with 
sudo gparted.

I'm holding off on this for now (see below)

> **chrisamiller said:**
> 3) If you're dual booting, the most sensible setup is to give Ubuntu about 10GB of space, but to make sure that you're saving all of your documents, videos, etc onto your big partition.  This might be your windows partition (if you use only two), or it may be on a third, seperate data partition, which is my preferred method.

This aspect of partioning confuses me a bit. If I have data, programs, documents, etc. stored on the C drive, that I put there after I first installed Windows XP, can Linux still find an use them? Or do I need to move them to a new location (the Linux partition??) first? If I have a third partition, can both Windows and Linux find things there? Do I move the relevant files there?

Thanks for your help so far,

Chris

---

### Post by Wim Sturkenboom on 2009-08-18
```

Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda5             2.3G  2.2G   32M  99% /**
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  144K  2.0G   1% /dev
tmpfs                 2.0G  480K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             464G   44G  421G  10% /media/disk

```The bold line is where your problem is.

With regards to the space required:
> 10GB for the **root** partition (/) is sufficient; I have 20GB allocated for it and after 3 years I've used around 4GB of it
> **swap** requirements depends on memory and use of th PC (it's also a persoanl thing)
>>> minimum 1GB
>>> if memory is less than 512MB, 2x size of memory
>>> if working with huge files, make it bigger
>>> if this is a laptop, minimum the size of your memory
> your data needs you can determine the size for **/home**.
> the rest for Windows

Linux will be able to give access to the Windows partition (it might show automatically). However you will not be able to run (most if not all) programs on the C drive as Linux can not run Windows applications.

---

### Post by 3rdalbum on 2009-08-19
> **fatgreta said:**
> Hi,

I installed Ubuntu alongside windows. All of the installation guides I've read talked about sliders in the partitioning process, I did not have that option as far as I can tell (version 9.04, 64bit version).

There is a slider. When you are asked whether you want to erase the drive, resize your partition etc, the bar graph at the bottom of the window has a slider.

You've not touched the slider, which means that you've installed Ubuntu with the absolute minimum of space.

Resizing the Ubuntu partition generally doesn't really work - it's usually inside an "extended" partition, and that extended partition can't be resized.

Better off to boot up with the Ubuntu live CD, delete the Ubuntu partition and the extended partition (it's the one with the blue border around it, that's surrounding the Ubuntu partition) and reinstall Ubuntu. This time, make sure you move the slider in the bottom bar graph.

---

### Post by isee on 2009-08-19
> If I have data, programs, documents, etc. stored on the C drive, that I put there after I first installed Windows XP, can Linux still find an use them?

Yes it can.  On my dual boot desktop it is called LOCAL DISK in the drop down Places menu.  It has to be mounted and you will get a password screen, but Linux can use things stored on your Windows partition.  The reverse will not work.  If you run OS Windows it cannot see your Linux partition, as far as I know.

Remember there is no C:\\ in Linux.

I would try GParted and reduce your MS partition to a minimum size, and use only Linux partitions for storage.  The difference is storage type, although vague to me, MS uses NTFS, while Linux uses FAT32, I believe.

Cheers!

---

### Post by fatgreta on 2009-08-19
> **3rdalbum said:**
> There is a slider. When you are asked whether you want to erase the drive, resize your partition etc, the bar graph at the bottom of the window has a slider.
 
You've not touched the slider, which means that you've installed Ubuntu with the absolute minimum of space.
 
Resizing the Ubuntu partition generally doesn't really work - it's usually inside an "extended" partition, and that extended partition can't be resized.
 
Better off to boot up with the Ubuntu live CD, delete the Ubuntu partition and the extended partition (it's the one with the blue border around it, that's surrounding the Ubuntu partition) and reinstall Ubuntu. This time, make sure you move the slider in the bottom bar graph.
 
OK, that sounds like the way for me to go at this point (I just installed it, so I don't have any data I'd have to back up or anything). I'll give that a try, thanks.
 
Chris

---

