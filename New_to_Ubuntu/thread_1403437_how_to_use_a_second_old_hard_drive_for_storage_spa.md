---
title: "how to use a second old hard drive for storage space?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by cottager on 2010-02-10
I have two old Dell towers. I've installed linux on one, and want to stick the other hard drive in it for more storage. 
How do I get rid of WinXP that's on it and just have it empty to use for storage??
Thanks!

---

### Post by nothingspecial on 2010-02-10
sudo apt-get install gparted.

Identify the correct hard drive (partition) in the top right of the screen.

Unmount it if it`s mounted.

Delete the partition.

Create a new ext3 partition in its place (or other file system if plan on using it with other operating systems)
[SIZE="3"][COLOR="Red"]
Make sure you do it to the correct drive[/COLOR][/SIZE]

---

### Post by audiomick on 2010-02-10
The application you need for the partition work is gparted. If it is not installed, you can get it through synaptic or
```
sudo apt-get install gparted
```

Just remove the partitions on the drive and create the new one(s) you want.
There is partitioning info here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

you will have to set up a permanent mount for the new partition
go through this,
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
and then the link at the end about automatically mounting partitions.

---

### Post by mwcrowley on 2010-02-10
I'm assuming you know how to install the old drive in your pc.
Once it's installed:
sudo aptitude install gparted

Warning: you can hose your whole system if you repartition and format the wrong drive.  You have been warned.  Take the time to familiarize yourself with the concepts of partitioning a hard drive.  It's kind of like slicing a pie.  The windows drive will show up as a fat32 or ntfs partition.  Delete and reformat.  Ext3 is fine.

sudo gparted, take your time and ask questions first, once your reformat a drive all old data is essentially gone.

---

### Post by cottager on 2010-02-10
Thanks! [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Jefferythewind on 2010-02-10
I guess i don't need to say it again, but... get gparted.  Just make sure you read the how-tos on-line, cause if you are not careful you can erase things you didn't want to.

[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html")

---

### Post by superprash2003 on 2010-02-10
if you got your answer , then please mark this thread as solved

---

### Post by egalvan on 2010-02-10
several posters have given excellent advice as to making SURE you work on the correct hard drive.

Since I am lazy, I would use the following to be SURE the correct drive is erased/formatted.

DO ALL THE ERASING AND FORMATTING ON THE DRIVE **BEFORE** YOU TAKE IT OUT THE SECOND TOWER. 
That way you **know** which drive is which :p

I would also suggest the following...
(this is what I use for all blank drives I install)

Download and burn the following two iso's

dban (Darik's Boot And Nuke)
[www.dban.org](www.dban.org)

PartedMagic LiveCD (a mini-distro with lots of drive and partitioning software)
[www.partedmagic.com](www.partedmagic.com)

boot with dban.
do a full erase, the shortest options are enough.

now boot with PartedMagic.
run the disk partitioner (gparted)
partition and format as your needs/wants dictate.

remove drive from second computer,
install in first computer.


You can install the drive as a slave on th first channel,
or master or slave on the second channel.
Jumpers need to be set to what you decide.

---

