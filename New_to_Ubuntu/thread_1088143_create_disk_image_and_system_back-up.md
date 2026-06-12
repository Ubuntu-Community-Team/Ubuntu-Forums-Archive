---
title: "create disk image and system back-up"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by raymondh on 2009-03-05
From a newbie's standpoint, I'm close to creating/tweaking my MSI wind 3-boot to where "I want it ... so far". Now to back-up and protect all these late night researching, time and learning "investments".   

1. I have system restore points in the XP side.  The OSX side is thru Time Capsule.  I don't know what to use for ubuntu (i read somewhere ubuntu does NOT have a system restore sort-off-app though I may be wrong).

2. I'd like to create an image of the whole disk .... just in case something BIG happens, with the goal of loading my exact disk in a new HDD if needed, without going thru each individual install (sorry, am thinking Mac's Time Capsule).  Is this possible? If so, what linux app?

Thanks for any tip :)  MY wife's starting to enjoy this MSI wind and she may do something "irrevocable".

---

### Post by pytheas22 on 2009-03-05
Unfortunately Ubuntu doesn't have any built-in "go back" function like Windows (have you ever actually had Windows restore points work?  I haven't), but there are other ways to do what you need relatively easily.  One option is to use [partimage]("http://www.partimage.org/Main_Page") to make a disk image of your Ubuntu partition(s), which you can easily restore later.

A second and possibly easier approach is [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"), which will back up your system onto a custom live CD that you can use to reinstall your personalized version of Ubuntu later.  The downside to this approach is that it copies everything into an ISO file, and if you have too many files to back up, it might be larger than you can fit onto a DVD.  In that case, however, you could probably still make a bootable USB drive using the oversized ISO image by going to System>Administration>Create a USB Startup Disk.

Either option will give you what you need.  remastersys is available through Synaptic and is pretty easy to use (I believe you just type 'sudo remastersys' to launch a GUI that will guide you through everything else), and you can find instructions for using partimage on the project's site.

---

