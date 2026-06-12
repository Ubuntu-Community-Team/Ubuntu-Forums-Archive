---
title: "Partition Help - new partition?"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by dBuster on 2011-01-08
I am a NOOB when it comes to partitioning with Ubuntu.  When I originally setup my pc I had Vista and 9.04.  Didn't even think of a seperate /home partition at that time.  Now I am wanting to clean install to 10.04 but not lose anything hence the desire for the /home partition.  I have read and understand how to move the home to the new partition just location on the drive is what I am concerned about.

So far I have reduced the Vista partition and freed up some space, currently unallocated space.  Where it currently sits, do I just create a new primary partition ext3?  Primary partition is my only option in gparted, granted I am not booting off of a live cd though.  Should I boot off of a live cd and create what?  Will the location it is in cause me booting issues with my current setup?  

I do have clonezilla and plan on doing an image of the drive, preferably after I get my NAS drive up and running this next week when it arrives.  I would like to get the /home partition created before then if possible.  

Any assistance is greatly appreciated.

[IMG]http://ubuntuforums.org/picture.php?albumid=1154&pictureid=7298[/IMG]

---

### Post by Ekeluo on 2011-01-08
As long as your Vista boots fine after the reduction (though I don't know much you can do if it doesn't), you can create your new home partition there (ext3 or ext4 will do fine, as will a primary or logical partition). The grub update should handle any changes to partition nomenclature(for lack of a better word). Be careful, as with all things partitioning!

---

### Post by dBuster on 2011-01-08
> **Ekeluo said:**
> As long as your Vista boots fine after the reduction (though I don't know much you can do if it doesn't), you can create your new home partition there (ext3 or ext4 will do fine, as will a primary or logical partition). The grub update should handle any changes to partition nomenclature(for lack of a better word). Be careful, as with all things partitioning!

Thank you!  So I can do it then from the 9.04 I am running now using gparted?  And grub will update after I have it setup to mount?

---

### Post by Ekeluo on 2011-01-08
[This]("http://www.psychocats.net/ubuntu/separatehome") is the guide I used when separating my home partition, however, that was with grub1. Now, I'm not too sure if the grub version affects the process, seeing as there isn't actually an OS installed on your /home partition, but do follow the instructions **to the letter**. Especially about backing up.

---

### Post by psusi on 2011-01-08
The keys shown by the partitions indicate they are locked and you can not modify them, probably because they are in use.  You need to run gparted from the livecd if you want to modify them.  That is why you can only create a primary partition: the extended partition is locked.

---

### Post by dBuster on 2011-01-09
> **psusi said:**
> The keys shown by the partitions indicate they are locked and you can not modify them, probably because they are in use.  You need to run gparted from the livecd if you want to modify them.  That is why you can only create a primary partition: the extended partition is locked.

I do not want to do anything with the existing partitions, just create in the unallocated space a new partition for my /home.  Does that need to be an extended partition?

---

### Post by Quackers on 2011-01-09
In your case it wouldn't matter whether it was a primary or logical partition. However, if you wanted a logical partition you would need to extend the extended partition (dev/sda2) all the way to left, then create the new logical partition in that new space. This would need to be performed from the live cd so that the partitions are not being used at the time. You would also need to right-click the swap partition (/dev/sda6) and select "swapoff"

---

### Post by candtalan on 2011-01-09
Adding new partitions might cause existing partitions to get renamed. If so, this will disrupt your existing grub configuration. And when you then first try to boot ubuntu, it may not boot.
The grub update mentioned I think referred to command 
sudo update-grub (for grub2) which needs to be done from the running ubuntu system in which grub2 has been installed.

---

### Post by dBuster on 2011-01-09
> **candtalan said:**
> Adding new partitions might cause existing partitions to get renamed. If so, this will disrupt your existing grub configuration. And when you then first try to boot ubuntu, it may not boot.
The grub update mentioned I think referred to command 
sudo update-grub (for grub2) which needs to be done from the running ubuntu system in which grub2 has been installed.

So then the consensus is that it would be better to run it from the installed Ubuntu, since I just was a partition for the /home, and I do not want to extend or do anything with the existing partitions, then run the update-grub command to make sure grub is current??

---

### Post by psusi on 2011-01-09
> **candtalan said:**
> Adding new partitions might cause existing partitions to get renamed. If so, this will disrupt your existing grub configuration. And when you then first try to boot ubuntu, it may not boot.
The grub update mentioned I think referred to command 
sudo update-grub (for grub2) which needs to be done from the running ubuntu system in which grub2 has been installed.

This is not true for grub2 and Ubuntu 9.10 and later.  Grub uses UUIDs to identify partitions, so it does not matter if they move around.

---

### Post by dBuster on 2011-01-09
> **psusi said:**
> This is not true for grub2 and Ubuntu 9.10 and later.  Grub uses UUIDs to identify partitions, so it does not matter if they move around.

So if I am running 9.04 as I am, I do not have to worry about the grub2 thingy??  

It also would then mean that it doesn't matter if the unallocated space on the hdd before the Ubuntu partition or not.  Interesting!  Thanks!

---

### Post by psusi on 2011-01-09
> **dBuster said:**
> So if I am running 9.04 as I am, I do not have to worry about the grub2 thingy??  


Did you miss the part about 9.10 and later?  Or the part about it NOT being a problem there ( implying that is was before ).

---

### Post by dBuster on 2011-01-10
> **psusi said:**
> Did you miss the part about 9.10 and later?  Or the part about it NOT being a problem there ( implying that is was before ).

Gotcha, so then I would have to do the grub update...  

Just trying to alleviate issues before they arise.  

New NAS should be here today and I will set that up as soon as I can then clonezilla the drive and get to work on my partition.  Too bad I do not have the guts to do it before cloning the drive.  But I know I am working now, to where I can do 90% of what I want so that would be a good point to clone.

Just wishing that my gaming sites like yahoo games and pogo would work right now otherwise I wouldn't be taking this plunge I don't think.  Something about the newer than released flash I bet has to do with it somewhat.

Back to topic...  I will follow the tips here and it looks like I will create a primary partition in that unallocated space and then update the grub as my first steps.  I am thinking I am going to do this from a boot into the loaded 9.04 and go from there.  If I run into problems I will drop in the live cd and load.  After all I will have a backup/clone of the drive.

---

