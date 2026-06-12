---
title: "no partitions!"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by anEarthCitizen on 2011-03-15
hi, 

I installed kubuntu 10.04 Lts from a live cd. And chose the second option of installation "Erase partitions".

Now, I cannot find any partition in "media".

I installed GParted and when I launched it there was:

a large partition (230 GB) of type ext3

two small other parttions.

So, how can i make partitions to store my data properly (where I can see them)?.

thanks.

---

### Post by ChipOManiac on 2011-03-15
There are no actual partitions other than the ones you have said. The big ext3 is where the default Ubuntu OS is and the othe two are just the swap and an extra external... the last two you cannot access directly like in Microsoft Windows ©®(TM) and neither can you do the same for the ext3 since linux works from it...

---

### Post by crispy_420 on 2011-03-16
Pick a partition format that can be seen by both operating systems can see. So NTFS or a variation of FAT. Then it should show as a drive in Windows and under Places -> Computer in Ubuntu.

---

### Post by srs5694 on 2011-03-16
In Linux, user files are stored in the /home directory. In your case, it sounds like /home is part of the root (/) partition. If you want to separate your user data from your OS installation, you can create a separate partition and mount it at /home. This will work almost identically to your current setup from a day-to-day use perspective, but it will have the advantage that you'll be able to completely wipe and re-install Linux without affecting your user data, should the need arise.

Given the way Ubuntu works, there's seldom any advantage to putting user data anywhere but in /home and in one or two other standard locations (such as /tmp for temporary files or /var/spool/mail for incoming e-mail). These other locations typically hold only very small amounts of data, and mostly unimportant data on a desktop system. I realize that in Windows you might want to create a separate E: partition (or whatever) to hold user data, but that's the point of a separate /home partition in Linux.

One exception to all of this is removable media (CD-ROMs, DVDs, USB flash drives, etc.). Ubuntu is designed to automatically mount these media in subdirectories of /media, and of course you'll want to read, and perhaps write, to these directories. Another exception is if you dual-boot and want a separate partition for exchanging data with your other OS, but your description sounded as if you intended to replace Windows with Ubuntu.

If you want to create a separate /home partition, you can either re-install the OS but select manual partitioning and create the /home partition then, or you can modify your current setup. The process for the latter is described [here,](http://www.psychocats.net/ubuntu/separatehome) among other places. If you don't yet have much in the way of user data, re-installing is probably the easier course of action -- just be sure to back up any data you *do* want to preserve before you begin!

---

### Post by cmcanulty on 2011-03-16
Yes after deleting paritions click area and select new and pick primary partition ext 3 or 4 and decide the size. Make sure one partition is / and if separate home one has to be /Home then a small swap area -maybe 2x the size of your RAMI deleted all partitions by mistake once and used the knoppix live cd to fix it.

---

### Post by anEarthCitizen on 2011-03-24
Hi, 

    It's me again!. :D. sorry for late post.

 thank god, it is solved!.

the solution ----> Gparted Live CD. very simple and intuitive.

the link below is very helpful for first time Gparted live cd.

thanks everyone.

[http://www.bleepingcomputer.com/tutorials/tutorial152.html](http://www.bleepingcomputer.com/tutorials/tutorial152.html)

---

### Post by cmcanulty on 2011-03-25
One thing that wasn't real intuitive with gparted to me was the idea that to create new partitions you have to first delete the ones you have or resize them to get space. Otherwise it appears to not work.

---

