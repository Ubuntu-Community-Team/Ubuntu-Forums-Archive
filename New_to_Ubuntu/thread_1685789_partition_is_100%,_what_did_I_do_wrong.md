---
title: "/ partition is 100%, what did I do wrong?"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by texstar420 on 2011-02-11
Hello ubuntu forum,

This is my second post here and I am totally excited to finally take the plunge in the the linux world. I have been reading all kinds of books and trying to get well versed in ubuntu.

So I tried installing ubuntu in the past and I learned quickly that you have to make a separate partition for ubuntu if you plan to dual boot cause doesn't play nice with any other OS. 

I have installed ubuntu 10.10 successfully and began some tutorials I read in a book. My first terminal command sudo apt-get update so that I could update software. After doing this I could not authenticate the updates because it kept saying that I was out of space. So I did some research and it said to enter the df -h command and mine showed the / which I know stands for root partition as being 100% full. I had allocated 3.3GB's for root so I should have had a bunch of space. I had only downloaded chrome browser and checked to update when I was installing initially. 

So what did I do wrong here? Is there a way to fix this? Did I install ubuntu on the wrong partition. I left about 12.5GB's for my /home partition also. I am not opposed to reinstalling and starting from scratch but if I have to I would like to know how much space I should leave for each partition and what partitions I should make. 

The book I read said to make 3 partitions, one for root should be about 3GB's, one for /swap which should be 1.5 times the size of your ram in my case 12GB's, and one for /home which the rest of the space should be left for. I had a total of 26GB to work with for ubuntu FYI. 

I am sorry if this has already been asked and thank in advance.

---

### Post by SavageWolf on 2011-02-11
It must be a really old book, 10GB is about good for /, 4GB for swap and the rest for /home. Nowadays hard disks are much bigger than in the olden days.

If you only have 26GB HDD space (and can't get any from Windows), I would recommend getting an external drive to store your files.

---

### Post by ajgreeny on 2011-02-11
> **SavageWolf said:**
> It must be a really old book, 10GB is about good for /, 4GB for swap and the rest for /home. Nowadays hard disks are much bigger than in the olden days.

If you only have 26GB HDD space (and can't get any from Windows), I would recommend getting an external drive to store your files.
+1

If you have a computer with 8GB of ram, I would presume it also has a large hard disk, so I would certainly agree that you need a lot more space for the Ubuntu OS.

How much do you intend to use Ubuntu?  I will be very surprised if you don't end up using it a great deal more than you might think at the moment.  When I started about 5 years ago I set a ubuntu partition of 20GB with root and home together, and the rest of the disk total of 160GB for winXP.  As I updated the ubuntu from version to version I gradually increased the ubuntu size, and moved to a separate /home partition, shrinking the winXP partition each time until it would shrink no further.

I then realised that I was not using winXP any more, just booting it occasionally to update it; totally pointless, so it then went completely, and I used ubuntu alone.  I have a root partition of 10GB, home of 148GB and swap of 2GB, as my hardware will not hibernate, and 2GB is therefore plenty.

A new root partition with nothing new added in the way of applications, temporary files, and various configurations, is about 2.6GB so you will see that your 3.3 is very tight and will quickly become problematical to you.

I would bite the bullet and start again with 10GB for root, 4GB for swap and make /home as large as you possibly can without compromising your windows OS.  Start by using windows own utility to shrink its partition, or one of them at least, depending on your partition layout.  Then boot to ubuntu live CD and delete your current ubuntu partitions to leave a single large unallocated space into which, by using the manual partitioning in the installation, you can make a new root swap and home partition.  Come back again if you need any more help with suggestions for partitioning layout.

Better luck this time!

---

### Post by texstar420 on 2011-02-11
I feel that I will end up using Ubuntu more like you did ajgreeny. I am beginning to see that I like it more them windows already and it has only been the third day since I used it.

I know have a new problem which is as follows when I boot up ubuntu 10.10 which I am guessing is because I am running out of root space:

The configuration defaults for Gnome power manager have not been installed please contact your sys admin.

Why did I get this error. Is it because I am running out of space? I haven't changed anything the last time I used it except trying to update.

Thanks for your help ajgreeny and SavageWolf.

---

### Post by drs305 on 2011-02-11
You can try to set the Gnome Power Manager settings from the menu: System > Preferences > Power Management.

It might be more useful to try to set them via the terminal, so you can see any error messages that are generated when you try to set them.

Run this in a terminal, and if you get errors, copy them in a post:```

gnome-power-preferences
```

---

### Post by oldfred on 2011-02-11
It looks like your running out of space is the reason for the error.
[http://ubuntuforums.org/archive/index.php/t-980711.html](http://ubuntuforums.org/archive/index.php/t-980711.html)

Some were solved by completing the install with apt-get from recovery mode. But you have to have space.

If you are dual booting, you may want to also consider a shared NTFS partition. When first starting with Ubuntu, I would get frustrated that my wife wanted to check email or use the browser and all the bookmarks were in the XP install versions. I then created a shared partition and moved my Firefox & Thunderbird profiles to the shared. Then all of a sudden we were not booting XP much at all.

---

### Post by texstar420 on 2011-02-11
Ok here is what I decided to do but I need help with figuring out how to do it right. I want to reinstall ubuntu as instructed and shrink one of my partitions in half so I can put /home on it. Here is my layout. I have a 1TB harddrive with windows 7 partitioned in half so 488gb for windows os and 423gb which I use for movies and stuff.
 So my plan was to split what is left of the 423gb which is 216gb in half so I have 116 for /home. 
I plan on reformatting the root and swap partitions which are on an entirely different harddrive then my /home will be. I would like to use 4 GB for swap 24 for /root.

So my questions are 

1. Does this sound like a good idea.

2. What is the best way to shrink that 423 gb partition that has 216gb free, should I use gparted? I have read that if I use gparted that I may have to fix my boot partition according to [this.]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") 

3. I can't afford to loose windows right now that is why I am scared to use gparted if it will mess up my boot sector and possibly cause me to reinstall windows.

4. Will my boot partition even be affected if it is on another partition?

---

### Post by oldfred on 2011-02-11
If the 423GB partition is not a boot partition then it should not matter.

The old issue was when Linux & XP started at sector 63 and then Vista changed to sector 2048, some versions of gparted or the installer would move the start of the Vista partition to 63 if a checkbox, that no one that was a Windows user knew they had to check off. (Also easily repaired, but many did not know how.) So it has been easier & safer just to say to use Windows tools for Windows and Linux tools for Ubuntu. 

Now with SSD and 4K sector drives new gparted also starts Linux partitions at 2048 and rounds to 1K, not cylinders which really have not been used for years anyway.

With large drives I like to keep system partitions small, so drive's head does not have to search entire drive and also have all of one system on one drive including MBR. Then each drive is bootable, in case of the other drive having issues.

---

### Post by The Cog on 2011-02-11
I would advise using the windows7 disk management utilities to shrink that data partition. Firstly because it is probably an NTFS partition, and the MS tools are probably safer for doing that. Secondly, a selfish reason, if win7 scrambles the partition while it's being shrunk then you can't put the blame on Linux.

You will have to use gparted or the Ubuntu installation partitioning tool to create the new partitions /, /home and swap though. The default format for / and /home is ext4 these days (neither will work on NTFS).

Any kind of resizing or repartitioning carries a small but non-zero risk of mishap. I advise backing your important data up elsewhere before you start.

---

### Post by texstar420 on 2011-02-15
> **texstar420 said:**
> Ok here is what I decided to do but I need help with figuring out how to do it right. I want to reinstall ubuntu as instructed and shrink one of my partitions in half so I can put /home on it. Here is my layout. I have a 1TB harddrive with windows 7 partitioned in half so 488gb for windows os and 423gb which I use for movies and stuff.
 So my plan was to split what is left of the 423gb which is 216gb in half so I have 116 for /home. 
I plan on reformatting the root and swap partitions which are on an entirely different harddrive then my /home will be. I would like to use 4 GB for swap 24 for /root.

So my questions are 

1. Does this sound like a good idea.

2. What is the best way to shrink that 423 gb partition that has 216gb free, should I use gparted? I have read that if I use gparted that I may have to fix my boot partition according to [this.]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") 

3. I can't afford to loose windows right now that is why I am scared to use gparted if it will mess up my boot sector and possibly cause me to reinstall windows.

4. Will my boot partition even be affected if it is on another partition?

I want to thank you all for your help. I got over this hurdle by making swap 4 gb, / 24 and /home 130. I am absolutely loving ubuntu and this forum. Thanks everybody

---

