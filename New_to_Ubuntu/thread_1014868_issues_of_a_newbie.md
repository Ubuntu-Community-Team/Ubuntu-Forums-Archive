---
title: "issues of a newbie"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by umabatata on 2008-12-18
Hi. I'm enjoying running ubuntu 8.1 but it is not without its challenges. I have found forum and bug posts relating to some of these, but I guess my question is whether my set of problems is fairly standard when starting off, or is my set up especially problematic.
I am running [THIS]("http://uk.shopping.com/xPF-Fujitsu-Siemens-Fujitsu-Siemens-AMILO-L7310W-14-1-Widescreen-Celeron-M-360-256MB-40GB-DVDRW-DL-XP-Home") system. but with double that ram...
So, problems.

USB issues. I have found some forums/bug reports on this but not one has a solution.. also not everyone has the problem.. I used to have good USB transfer rates - not sure what they were as they were not an issue, but now it takes 4 hours to transfer files from a 4gb sd card to desktop. It was going to take 80 hours to transfer from external hd to internal hd. 

USB devices are generally not picked up until i do a lsusb a few times. and then often dont mount.

I've also had issues with ntfs read write...now sorted with ntfs-g3
but not really sorted - this provides access, but it is not practical so I am going to see if I can reformat/partition the drive in a more useful filesystem.. 

Also, when system hibernates there is no bringing it back. it needs restarted. 
When previewing some screen savers the system crashes.
when listeneing to mp3's in rhythm box they will periodically go silent for a second or two mid stream. 

~There is more stuff but I'll just leave it at that. I can search for each of these, but I wonder if there is a metaproblem and these problems are symptoms rather than things to be fixed bit by bit. 
obviously one problem is that my computer is not particularly powerful... but I was shifting big files around and editing them in gimp, and using usb sticks, and external hd's all the time with very few problems..

I love the idea of Ubuntu and all that it stands for but I did not expect to be hamstrung this much by changing to it.... I am enjoying learning, and love the whole forum/bug fixing community. I have a bit of DOS 3.0 knowledge under my belt, so i understand the terminal to some extent, but without that i'd be stuffed. I have a bit of spare time at the moment, but if I didn't I'd be up the creek without a functional computer. these are the reasons the huge majority of people can't just easily switch to ubuntu from windows (but i'm still glad I did). Any advice. . . where to next, did I miss something

---

### Post by gjoellee on 2008-12-18
> **umabatata said:**
> Hi. I'm enjoying running ubuntu 8.04 but it is not without its challenges. I have found forum and bug posts relating to some of these, but I guess my question is whether my set of problems is fairly standard when starting off, or is my set up especially problematic.
I am running [THIS]("http://uk.shopping.com/xPF-Fujitsu-Siemens-Fujitsu-Siemens-AMILO-L7310W-14-1-Widescreen-Celeron-M-360-256MB-40GB-DVDRW-DL-XP-Home") system. but with double that ram...
So, problems.

USB issues. I have found some forums/bug reports on this but not one has a solution.. also not everyone has the problem.. I used to have good USB transfer rates - not sure what they were as they were not an issue, but now it takes 4 hours to transfer files from a 4gb sd card to desktop. It was going to take 80 hours to transfer from external hd to internal hd. 

USB devices are generally not picked up until i do a lsusb a few times. and then often dont mount.

I've also had issues with ntfs read write...now sorted with ntfs-g3
but not really sorted - this provides access, but it is not practical so I am going to see if I can reformat/partition the drive in a more useful filesystem.. 

Also, when system hibernates there is no bringing it back. it needs restarted. 
When previewing some screen savers the system crashes.
when listeneing to mp3's in rhythm box they will periodically go silent for a second or two mid stream. 

~There is more stuff but I'll just leave it at that. I can search for each of these, but I wonder if there is a metaproblem and these problems are symptoms rather than things to be fixed bit by bit. 
obviously one problem is that my computer is not particularly powerful... but I was shifting big files around and editing them in gimp, and using usb sticks, and external hd's all the time with very few problems..

I love the idea of Ubuntu and all that it stands for but I did not expect to be hamstrung this much by changing to it.... I am enjoying learning, and love the whole forum/bug fixing community. I have a bit of DOS 3.0 knowledge under my belt, so i understand the terminal to some extent, but without that i'd be stuffed. I have a bit of spare time at the moment, but if I didn't I'd be up the creek without a functional computer. these are the reasons the huge majority of people can't just easily switch to ubuntu from windows (but i'm still glad I did). Any advice. . . where to next, did I miss something

I dont have the same computer. but I had the many of the same issues in Hardy, they where all fixed in Intrepid

---

### Post by ieee488 on 2008-12-18
I have 8.10 dualbooting on a 1GHz 512MB RAM Dell PC with Windows 2000.

I mainly mount my Windows NTFS partition to read files from it. Haven't done writing to them.

If you want a partition to share, you can create a FAT32 partition but then you are limited by the maxium file size 4GB of a FAT32 partition.

I mainly use USB to transfer small files to/from thumb drives. No problems with them being recognized instantly.

---

### Post by umabatata on 2008-12-18
oops. i am using intrepid 8.10. I've been reading too much about 8.04 and got confuzzed

---

