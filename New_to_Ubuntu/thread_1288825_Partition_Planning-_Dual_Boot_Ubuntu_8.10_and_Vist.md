---
title: "Partition Planning- Dual Boot Ubuntu 8.10 and Vista"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Antiopa on 2009-10-11
Hi everyone,
 
I am new to Linux (and this site) and had installed (with some help from an acquaintance) Ubuntu 8.10 on my computer a couple of months ago. I tried to set up a dual boot between that and Windows Vista because I'm not ready to have just Ubuntu. However, once Ubuntu was installed I could not boot Vista because it said it had an error (discussed [here]("http://ubuntuforums.org/showthread.php?t=1288815")). As a result I am starting all over again with the set-up process for dual booting and would like to get some input on the partions I plan to make.
 
Here is the initial partition set up that I had (on roughly 232 GB), in the exact order they were listed in the Ubuntu partitions editor (sorry don't recall the exact program name):
 
/dev/sda1 extended 141 GB
/dev/sda5 linux swap 7 GB
/dev/sda6 ext3 38 GB (the / partition)
/dev/sda7 ext3 95 GB (the /home partition)
unallocated unallocated 30 GB
/dev/sda2 fat32 11 GB (Recovery partition)
/dev/sda3 ntfs 50 GB (Vista OS partition)
 
My first questions are, what is the 141GB "extended" partition for, why does it take up the first spot, and why aren't the GB included in the total that my computer has available? I have read that Vista may not work properly if it doesn't get the first spot, is this true and if so, how do I fix it?
 
I believe the plan during the first set up was that the /home folder was to act as a working folder that I could use to access documents from both Windows and Ubuntu but my research suggests that needs to be in fat32 format rather than ext3 in order to be accessed by Vista. Is this true?
 
Here is what I came up with for my partitions on my new set-up (approx. 232 GB):
 
/dev/sda1 extended 141 GB *
/dev/sda2 ntfs 90 GB (Vista OS partition) **
/dev/sda3 fat32 15 GB (Recovery partition)
/dev/sda5 fat32 80 GB (Shared Data partition)
/dev/sda6 etx3 20 GB (the / partition)
/dev/sda7 ext3 15 GB (the /home partition)
/dev/sda8 linx swap 8 GB
 
* as above, I have no idea what this is, I guess it is automatic?
**I wish I could shrink this to 50 GB for more shared space but this is as small as Vista wants me to make it when I resize and I am worried about using a non-Vista program to do it because I don't want the same error I had last time, see [other post]("http://ubuntuforums.org/showthread.php?t=1288815") for details.
 
I have changed things around a bit from the first partition set up that I had, based on my readings (specifically [here]("http://www.psychocats.net/ubuntu/partitioning")) so that there is a small separate /home for Ubuntu instead of just the shared data spot because I have read that this will be useful when I want to upgrade to another version of Ubuntu. But what I couldn't find information about was whether I should/could create a mount point (forward slash thing, right? I don't really know much about them) for the shared data folder if I did this. If I don't create one will I still be able to access it from Ubuntu? If I need to create one, is there a specific name it should be given since I will have already used /home?
 
Any other suggestions for the new partitions (or critiques of my proposed set up) would be welcome, and I can provide further information if required. 
 
Thanks for taking the time to read through all of this!
 
P.S. I don't know if this should be here (beginners) or in the regular installation section. I put it here because I am a beginner and don't know many of the Ubuntu terms yet.

---

### Post by sandyd on 2009-10-11
> **Antiopa said:**
> Hi everyone,
 
I am new to Linux (and this site) and had installed (with some help from an acquaintance) Ubuntu 8.10 on my computer a couple of months ago. I tried to set up a dual boot between that and Windows Vista because I'm not ready to have just Ubuntu. However, once Ubuntu was installed I could not boot Vista because it said it had an error (discussed [here]("http://ubuntuforums.org/showthread.php?t=1288815")). As a result I am starting all over again with the set-up process for dual booting and would like to get some input on the partions I plan to make.
 
Here is the initial partition set up that I had (on roughly 232 GB), in the exact order they were listed in the Ubuntu partitions editor (sorry don't recall the exact program name):
 
/dev/sda1 extended 141 GB
/dev/sda5 linux swap 7 GB
/dev/sda6 ext3 38 GB (the / partition)
/dev/sda7 ext3 95 GB (the /home partition)
unallocated unallocated 30 GB
/dev/sda2 fat32 11 GB (Recovery partition)
/dev/sda3 ntfs 50 GB (Vista OS partition)
 
My first questions are, what is the 141GB "extended" partition for, why does it take up the first spot, and why aren't the GB included in the total that my computer has available? I have read that Vista may not work properly if it doesn't get the first spot, is this true and if so, how do I fix it?
 
I believe the plan during the first set up was that the /home folder was to act as a working folder that I could use to access documents from both Windows and Ubuntu but my research suggests that needs to be in fat32 format rather than ext3 in order to be accessed by Vista. Is this true?
 
Here is what I came up with for my partitions on my new set-up (approx. 232 GB):
 
/dev/sda1 extended 141 GB *
/dev/sda2 ntfs 90 GB (Vista OS partition) **
/dev/sda3 fat32 15 GB (Recovery partition)
/dev/sda5 fat32 80 GB (Shared Data partition)
/dev/sda6 etx3 20 GB (the / partition)
/dev/sda7 ext3 15 GB (the /home partition)
/dev/sda8 linux swap 8 GB
 
* as above, I have no idea what this is, I guess it is automatic?
**I wish I could shrink this to 50 GB for more shared space but this is as small as Vista wants me to make it when I resize and I am worried about using a non-Vista program to do it because I don't want the same error I had last time, see [other post]("http://ubuntuforums.org/showthread.php?t=1288815") for details.
 
I have changed things around a bit from the first partition set up that I had, based on my readings (specifically [here]("http://www.psychocats.net/ubuntu/partitioning")) so that there is a small separate /home for Ubuntu instead of just the shared data spot because I have read that this will be useful when I want to upgrade to another version of Ubuntu. But what I couldn't find information about was whether I should/could create a mount point (forward slash thing, right? I don't really know much about them) for the shared data folder if I did this. If I don't create one will I still be able to access it from Ubuntu? If I need to create one, is there a specific name it should be given since I will have already used /home?
 
Any other suggestions for the new partitions (or critiques of my proposed set up) would be welcome, and I can provide further information if required. 
 
Thanks for taking the time to read through all of this!
 
P.S. I don't know if this should be here (beginners) or in the regular installation section. I put it here because I am a beginner and don't know many of the Ubuntu terms yet.
give the shared folder a mountpoint of
```

/media/shared

```
that **should** work from what i see, but one question. why are they all in an extended partition? (and no, it shouldn't be a problem)

---

### Post by powel212 on 2009-10-11
If it were me I'd;

1.)stick the live CD in and reformat the whole drive as empty space.

2.)Reboot, stick in the windows disk and install windows into a new 80G NTFS Partition, you can create this using the win install CD.

3.)Finish win install, Reboot to Ubuntu live CD and open Gparted.

4.)find the 150G of non windows space, format 100G as NTFS and format the last 50Gigs as unformatted or empty space.

5.) install ubuntu, when you get to the partition part select "use largest continuous free space" and don't touch the slider. Ubuntu will now install to the 50G empty space we created in the last step.

6.)Finish install. Reboot into Ubuntu, install NTFS configuration tool and configure it so you can see your NTFS drives in Ubuntu.

Your done.

Now you have a Grub controlled dual boot. Win has extra space, Ubuntu has extra space, and you have a hundred gigs to share between the 2. If you need more data space in the future go buy a 1 Terabyte drive and an enclosure, (100 Bucks) and then your golden.

I hope that helps

Powel

---

### Post by mikechant on 2009-10-12
> If you need more data space in the future go buy a 1 Terabyte drive and an enclosure,

Wandering offtopic here a bit:
Assuming there's room, I'd always fit a second internal drive rather than use it externally in an enclosure (or buying an external USB drive). Fitting internal drives is incredibly easy (open case, four screws to hold drive in postition, connect power and data cables, close case, done) and doesn't take up any any extra space, USB ports or power sockets. It's pretty well risk free as long as you disconnect the power before opening the case, and don't touch any circuit boards including the one on the bottom of the new drive (unlike fitting RAM, where you can easily 'static zap' the new module while holding it or damage the motherboard forcing it in etc.). Also you may get better performance, particularly from faster drives, if they are connected internally via SATA rather externally via USB, and USB is also more CPU intensive.

I think it's best to use internal drives for all 'online' storage if possible (i.e. all data you want immediately accessable) and use external ones only for backups/bulk transfer to other PCs etc., and keep them disconnected and stored seperately when not in use (so if your PC is stolen or destroyed you don't lose your backup as well). This is important these days since lots of home PC users have too much data to be practical to backup to DVD etc. and too little upstream bandwidth to easily back up everything to online backup services, so external drives are the most practical method - preferably at least two alternating!

---

### Post by mapes12 on 2009-10-12
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Antiopa on 2009-10-12
Thanks for your suggestions and advice everyone!  I have successfully set up my partitions using the partitioner on the Live CD for all of the partitions except Vista which I had sized previously in Vista. 

For the record, I ended up going with:

/dev/sda1 ntfs 90 GB (Vista partition)
/dev/sda2 fat32 105 GB (/media/shared partition)
/dev/sda3 etx3 20 GB (the / partition)
/dev/sda5 ext3 20 GB (the /home partition)
/dev/sda6 linx swap 8 GB

The shared folder appears to be working well and thus far I have been able to access the files I have tried  using either OS.

---

