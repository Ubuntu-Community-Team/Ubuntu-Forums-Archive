---
title: "Stuck during installing 11.04"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by SuchetBargoti on 2011-07-21
Hi guys, Installing Ubuntu 11.04 right now, and get a popup saying:

Do you want to resume partitioning?
The attempt to mount a file system with type swap in SCSI2 (0,0,0), partition #6 (sdb) at none failed. 
You may resume partitioning from the partitioning menu.

The options are: [Go Back], [Continue]

I try pressing either of them and nothing happens. 

Down below on the installation status it says
"Creating ext file system for / in partition #5 of SCSI2 (0,0,0)(sdb)..."

Please help urgently as the installation is current in progress on my other computer. Thanks in advance

---

### Post by candtalan on 2011-07-21
My inclination is to consider stopping the PC elegantly if possible, but if not then force shutdown. Then examine the hard drive using Live session, including disc utility, and also gparted. Then make decisions from what you see.

Then confirm other OSs work ok still, if not, repair, consider what has happened maybe.

Then, using live session, prepare for a second attempt at install, maybe by preparation of partitions manually and use of manual not automatic install allocations.

---

### Post by jjex22 on 2011-07-21
Hi there, could you provide a partition list for what you have installed and what you're trying to install? many thanks!

---

### Post by SuchetBargoti on 2011-07-21
Lost some patience there and the only option I was left with was to force shut down (Windows was still working there). 

In drive 0 
- OEM partition (~ 100 Mb)
- C drive (with windows ~600 GB)
- Recovery Drive

In drive 1 
- D drive (for windows ~500 GB)
- this new drive that i just created for ubuntu (~100 GB)
- another drive, roughly 8 GB

I cant give you exact information as the installation is currently under progress. Installing it the second time around, Chose the 3rd option for installation where it lets me set my own drives, and i just set it to that 100 GB one into which I was trying to install before. 
Lets see how this installation goes and I will get back to you guys

---

### Post by candtalan on 2011-07-21
> **SuchetBargoti said:**
> this new drive that i just created for ubuntu (~100 GB)


Not sure I understand you clearly here. How have you 'created' a 'drive'? I am aware that in Windows, partitions are often actually known as 'drives', however this can be misleading when you come to deal with real partitions.
Gparted (as in my earler post)  will offer a good view of the partitions and drives.

hth

---

### Post by jjex22 on 2011-07-21
I would recommend getting a clear plan of how you want your hard drive(s) to be laid out once it's all set up and working towards this first.
 
My recomendation is to get windows and ubuntu on the same physical hard drive and let them share their data on FAT32 partitions.
 
1 First back up everything - and check backup
2 use Gparted to free up as much space as possible (by shrinking partitions) and if possible get it    all on one drive.
3 create a primary drive on the othe HDD for all of your stuff formatted in FAT32
4 use windows to move Users, Program Files, Program Data to the nely created partition. (this should leave windows at around 20GB.
5 Back in Gparted shrink windows parition to say 50GB and next to it creats a EXT4 partition around the same size, but could easily be 30GB with no probs, and a swap partition twice the size of your ram. Finally create another data partition in FAT32 to make use of the rest of the drive
6 install ubuntu, moving your /home folder to one of your data partitions so all data is accessable to both OS. 
 
the fine tuning is up to you depending on your data usage... if you can get everything on one drive with lots of room to spare you may concider setting up a raid 1 array to automatically protect you from HDD failure

---

### Post by SuchetBargoti on 2011-07-21
Thanks for your time jjex, luckily the re installation after the hard shutdown worked well. I am just stuck with a graphics card problem which I have had from the start - I am unable to load unity. I started a thread [here]("http://ubuntuforums.org/showthread.php?t=1808410&page=3") earlier, so just browse through it and let me know if you can assist.

---

