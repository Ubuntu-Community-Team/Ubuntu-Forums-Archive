---
title: "Guide to Linux and Ubuntu"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by Whenry on 2011-08-23
Hi all,

I am an applied math grad student.  Most jobs I am interested in require experience in a unix/linux environment.  My research advisor/prof also uses unix exclusively.  I am also taking some programming courses that require using a unix environment.

I am looking for a basic guide to using the command line, as well as just basics about linux/unix ubuntu, how things are installed, what a kernel is etc.....I know absolutely nothing.

I have already installed ubuntu 11.04 on a partition of my macbook pro.  Seems to be working. I installed the wireless card fix as well.

Thank you
Will

---

### Post by JC Cheloven on 2011-08-23
Hi, and welcome. 

Your question being rather unspecific, probably the best is to adress you here [https://help.ubuntu.com/](https://help.ubuntu.com/)

The ubuntu community contributed documentation is awesome. You can use the search function to find out almost everything imaginable about ubuntu, most of what is apllicable to gnu-linux in general.

---

### Post by M1ttenz11 on 2011-08-23
> **JC Cheloven said:**
> Hi, and welcome. 

 [https://help.ubuntu.com/](https://help.ubuntu.com/)

The ubuntu community contributed documentation is awesome. You can use the search function to find out almost everything imaginable about ubuntu, most of what is apllicable to gnu-linux in general.

This guy couldnt have said it better. Everything you need to learn about unix/linux/ubuntu can be found on the help site, or this forum, just by looking at peoples problems and reading up on how they are solved, also alot of terminal will just come to you,[when you need it most - you'll find the solution] + always keep your computer backed up when exploring terminal codes as you may break your OS and have to re-install, however, this hasnt happend to me yet, although I have heard stories so becareful with what your entering in there.
Also, the Ubuntu website sells books, and your local library will have books on how the operating system works.

---

### Post by Whenry on 2011-08-23
Thank you sounds good.  What is the simplest way to back up my install?  I will use an external HD to do so.

---

### Post by JC Cheloven on 2011-08-24
> **Whenry said:**
> Thank you sounds good.  What is the simplest way to back up my install?  I will use an external HD to do so.

So let's carry on with that important "lesson one" :)
Go to the aforementioned web page and simply type "backup" in the search box (hit enter). You'll be presented to a bunch of entries. The first one is:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 
Here you find a collection of apps that you can use to backup, depending on the type of backup you need/want. Reading a bit on this page to get informed before using any of the links provided, would be advisable.

If you write "partition image" in the search box, the first link offered is:
[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)
Here you have tools to make an image of your partition, and eventually restore it when problems happen. The idea with this kind of methods is to get a system in a state you like (whith your preferred apps instaled, personal settings for all programs, etc). Then, before messing around, make a backup of the whole partition. If you restore it in the future, you'll come back to the exact state you had at that moment.

Finally, there is a tool of the category above (whole partition backup), which I liked and used quite a lot. It's called [FSachiver]("http://www.fsarchiver.org/Main_Page"). You can install it from the repository, but that may be a bit of nonsense, as you can't backup the partition you've booted from. The best course of action may be to get [SystemRescueCD]("http://www.sysresccd.org/Main_Page"), which is a live CD which includes FSarchiver, boot from that, and "archive" (=backup) your ubuntu partition in a file in your external disk. The image is compressed so the file will take usually much less than the actual size of your partition.

Note: to keep the topics clean, it's customary over here to start a new thread for a different subject.

Enjoy!

---

### Post by aeiah on 2011-08-24
just as an aside:

ubuntu uses bash as its command line shell, and so does os x. so whilst there are a lot of differences between os x and linux/unix, bash scripts and such are fairly universal. os x is based on unix, but its so abstracted that really the only things that are similar is the bash command shell and a few other bits and pieces. still, it means you dont necessarily have to be in ubuntu on your macbook to mess with bash scripts and the like.

---

