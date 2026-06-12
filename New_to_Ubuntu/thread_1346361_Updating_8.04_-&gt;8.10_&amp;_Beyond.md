---
title: "Updating 8.04 -&gt;8.10 &amp; Beyond"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by spiritsongtress on 2009-12-05
So far I've gotten the packages for install downloaded to 8.04. Anyway, I've gotten them in but each time I try to update its telling me I don't have enough /boot space.

I am using 8.04 and simply trying to get up to them ost current version. My laptop is currently Dual booting Windows Vista (the linux partion is much smaller than the  Windows).

i've tried cleaning it but still says its not enough space. Suggestions. I've done: sudo apt-get clean to trying clean it up but still no luck.

---

### Post by lindsay7 on 2009-12-05
Run Gparted and see if there is space to increase your Ubuntu partition.  Before you increase the ubuntu partition and shrink the windows partition be sure to do a defrag under windows to make sure that you do not have problems.

---

### Post by ranch hand on 2009-12-05
First, are you sure that all you have is one MS partition?

There should be two.  One with, probably, the name of your computer manufacturer that is the actual OS and another labeled something like "data" which is a nearly empty recovery partition.

You should pull up System>Administration>System Monitor and click on the "File Systems" tab.  This will tell you haow much you are using of all mounted partitions.

If you have 8.04 installed, it is a LTS release (Long Term Service).  You are supposed t obe able to upgrade from LTS to LTS without going through all the ones in between.  10.04 (Lucid Lynx) is the next LTS, so I would just work on getting Hardy Heron setup right before you upgrade to Lynx.

With that in mind;
A>Are you installed on 1 or 2 partitions (not counting Swap)?
B>What are the sizes of your partitions?

As for both those questions if you would post the out put of;
```

 sudo sfdisk -l

```
That is a lower case L (-l).

If you do not have a lot of data to back up from Ubuntu, let us get you set up on 2 partitions / (root) and /home.  This will make your life, in the long run, a lot easier.

The problem with this is that you are limited to 4 primary partitions and if you have 2 MS and 2 Ubuntu a 1 Swap, you have 5.  Won't work.

If you shrink your MS recovery partition and maybe the Win JerryLewis Pro partition and movethe recovery partition over to it, you can make the rest of the drive into an "extended" partition.

This is actually a type of Primary partition that you can make as many "logical" partitions in that you want.  Three more is not a problem.

Here is the "sudo sfdisk -l" for my sda drive with 4 OS' on it.  One is on only 1 partition.
```

jak@jak-desktop:~$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   4697    4698-  37736653+  83  Linux
/dev/sda2      24583   38912   14330  115105725    5  Extended
/dev/sda3      18209   24582    6374   51199155   83  Linux
/dev/sda4       4698   18208   13511  108527107+  83  Linux
/dev/sda5      37777+  38912    1136-   9124888+  82  Linux swap / Solaris
/dev/sda6      24583+  26482    1900-  15261687   83  Linux
/dev/sda7      26483+  31609    5127-  41182596   83  Linux
/dev/sda8   *  31610+  32916    1307-  10498446   83  Linux
/dev/sda9      32917+  37776    4860-  39037918+  83  Linux

```
This drive is the first drive I set up and it is about to be wiped and redone.  I was real proud of it when I did it, not so impressed now.  Too much wasted space with 3 Primary partitions.  Less flexible.

If you are on 2 partitions and you really screw your installation, you can reinstall without formating your /home partition.  While you should back up your data, 95% of the time you will have no data loss.  You just replace the / partition.

---

