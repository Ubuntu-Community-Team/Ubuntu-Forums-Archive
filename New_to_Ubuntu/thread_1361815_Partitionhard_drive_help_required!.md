---
title: "Partition/hard drive help required!"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by master_at_work on 2009-12-22
Hi everyone, I'm just loking for some help with the partitions on my hard drive. By way of background, the story so far...

I'm new to Ubuntu, but like what I've read: the Vista laptop I've had for a couple of years now runs *really* slowly (no matter how many times I defrag/tidy up unnecessary files etc.) and I'm looking for an OS which is safe and which won't require me to mess about endlessly with firewalls/antivirus/antispyware etc. 

So, I downloaded the 9.10 iso file, verified it with md5 sum, burned it to a CD and ran said CD in order to have a play around with Ubuntu before taking the plunge and installing it. Now this is where the problems begin... Thinking "what the hell, why not?", I started going through the stages to install as a dual-boot. My hard drive has a storage size of 180GB, split 50/50 between C and D drives, and where D is completely free. I wanted to use the D drive for Ubuntu, so I selected the "install side by side" option, thinking Ubuntu would use the free storage on the D drive. Now before I completed the installation, and with the options to go back or quit still available, I suddenly thought it might be a good idea to back up the C drive before going any further and so decided to quit and do this. However, when I went to look at the drives in Windows, it showed C as it was, but showed D as only 44.8GB. So my question is, where has the other half of the D drive disappeared to?! 

To see what would happen, I then ran the Live CD again, and Ubuntu now displays my drives as follows: 

/dev/sda1 (fat32)    7.8GB
/dev/sda2 (ntfs)      89.3GB
/dev/sda3 (ntfs)      44.9GB
Free space              44.4GB

So this indicates that the total size of the hard drive remains at 180GB, but that the D drive has been split in two. Is this a result of me going partway through the installation and then quiting? And why is only half the D drive visible in Windows? What I'd like to do is install Ubuntu onto the free space, but as it stands that is only 44.4GB: how do I get this back to 90GB? :confused:

Sorry for the long explanation and numerous questions, but, as I said, I'm new to Ubuntu and thought it better to detail the situation exactly as it is. Hopefully one of you good people can help?! 

Thanks in advance.

---

### Post by Paqman on 2009-12-22
> **master_at_work said:**
> Is this a result of me going partway through the installation and then quiting?


Yep, it must have started partitioning before you told it to quit.

> And why is only half the D drive visible in Windows? 

Only Windows knows!

> What I'd like to do is install Ubuntu onto the free space, but as it stands that is only 44.4GB: how do I get this back to 90GB? :confused:

That's pretty easy. Just boot up your LiveCD and go to System > Admin > Paritition Editor. This is an app called Gparted (it's the same thing the installer uses)

It might be simplest to just delete sda3, giving you 90Gb of free space. Then fire up the installer and tell it to use that free space.

---

### Post by cpplinux on 2009-12-22
The unallocated disk space is not visible to windows. You can use **parted** to resize your partitions. And you should choose ext3 -- not ntfs -- for linux partition.

---

### Post by hessczoo on 2009-12-22
Yes, you need to delete that partition by using Gparted, as it is probably the easiest. And use a better filesystem than NTFS

---

### Post by audiomick on 2009-12-22
Hi. It looks like you have reduced the partition size in /dev/sda3 down to 44.9 GB, leaving free space on the disc after it. /dev/sda3 is the third partition on the first drive. On a theoretical second drive, it would be sdb3 , or as the first partition on a third drive, for instance, sdc1.

The partition /dev/sda3 is, presumably, that which windows is seeing as D:
You need to be very sure about this. If you choose the wrong one in the install, you will shoot down your windows completely. One way to check is to boot into the live cd (option "try Ubuntu without changing the computer") and simply look at the partitions under "places" in the top bar. You should easily be able to recognize what is where. Given, however, that you can see that your D: has shrunk, it is fair to assume that it is sda3

There a few variations on how to continue, but I would do it this way.
From the live cd, open system>administration>gparted 
Remove sda3 (assuming you are convinced that this is the right one), so that you have 90GB of unallocated space. (or shrink it down to a couple of GB and leave it there as a data transfer partition between Vista and Ubuntu. It is not a bad idea to have one that you can write to from both systems.)

Start the installer, and when it gets to the partitioning step, choose the manual option.

Set up:
a partition of around 10 GB , file system ext4, mount point /
a swap partition a bit bigger than your RAM
a partition with the rest of the space, file system ext4, mount point /home

note: ext3 will also work, but Ubuntu has changed to ext4 since Karmic (newer version), so you might as well start with the new version instead of having to change it at some time in the future

The advantage of having /home on it's own separate partition is that, should you have to re-install for any reason, you can simply re-mount it at this point in the installation _without formatting_ and all your data and configurations will be retained.

---

### Post by houseworkshy on 2009-12-22
Yes not as bad as it looks.  Windows can't see anything other than ntfs and fats.  The best way, slaming the stable door after the horse has gone I know, is to use windows to shrink it's partition and then do the install.  As it stands now you could use puppy linux, which can be loaded to ram after which you can eject the cd, to make back ups of your work.  Or if it is all still present in windows use that, or the live ubuntu cd to put things onto a stick.  So not a big problem.  

Gparted is quite straight forward.  The easiest way is to format the intended destination for linux as ext2.  Not for its own sake, the installer will change things anyway, but so that you can then right click on it and open the flag manager and tick the "bootable" option.  Once that is done just install in the usual way, select use the whole partition and from then on it is all automated.

---

### Post by Paqman on 2009-12-22
> **audiomick said:**
> 
Start the installer, and when it gets to the partitioning step, choose the manual option.

Set up:
a partition of around 10 GB , file system ext4, mount point /
a swap partition a bit bigger than your RAM
a partition with the rest of the space, file system ext4, mount point /home


This is good advice, but be aware that you'll have to house some or all of these within an extended partition, as you're only allowed four primary partitions. An extended partition allows you to break this rule by putting partitions inside other partitions.

If that's all starting to sound a bit complicated then telling the installer to do it all for you is a perfectly good option too.

---

### Post by audiomick on 2009-12-22
> **Paqman said:**
> This is good advice, but be aware that you'll have to house some or all of these within an extended partition, as you're only allowed four primary partitions. An extended partition allows you to break this rule by putting partitions inside other partitions.

If that's all starting to sound a bit complicated then telling the installer to do it all for you is a perfectly good option too.

Correct of course, I forgot to add up...

I have seen several post advising to create an extended partition and put the whole show in there as logical partitions (not as hard as it sounds, it is all pretty self-explanatory when you have gparted open in front of you)
I would do that, if only because it is neater that way.

note: when you create partitions inside an extended, the numbers start from five, i.e sda5, sda6, sda7 and so on. Don't let this annoy you, it is just the way the thing works. 1 to 4 are reserved for primary partitions.

---

### Post by houseworkshy on 2009-12-22
I've been told that a swap file should be around two and a half times whatever your ram is. Audimic posted whilst I was still typing; mine was an easy way, Audiomic's advice is far better.

---

### Post by audiomick on 2009-12-22
> **houseworkshy said:**
> I've been told that a swap file should be around two and a half times whatever your ram is.

I think just a bit bigger is enough. The reason is, the hibernate function writes the contents of RAM to the swap space. If one never intends to use the hibernate function, a gig or so is probably ample.

---

### Post by Paqman on 2009-12-22
> **houseworkshy said:**
> I've been told that a swap file should be around two and a half times whatever your ram is.

These days machines have enough RAM that tons of swap isn't really needed. If you intend to use hibernation than you need to match your RAM plus a little extra. Likewise if you have under about 512MB of RAM you might want a good sized swap. If you have 1GB of RAM or more you'll find you use swap very little, if at all.

---

### Post by master_at_work on 2009-12-22
Wow! Thanks for the swift responses, everybody! I suspected that going partway through the installation process had created the problem. I'll follow the suggestions outlined above and use Gparted (when running the Live CD) to resize the partitions. I must admit that I wasn't aware of the need for a swap space, but I'll (eek!) have a go at creating a small partition for that. That way, I'll end up with C: (still with Windows untouched), a small swap partition, and a larger partition for Ubuntu.

Would that be much different from:

> Set up:
a partition of around 10 GB , file system ext4, mount point /
a swap partition a bit bigger than your RAM
a partition with the rest of the space, file system ext4, mount point /home??

What is the recommended 10GB partition for?

---

### Post by audiomick on 2009-12-22
[QUOTE=master_at_work;8543984
What is the recommended 10GB partition for?[/QUOTE]

Hi. You can install Ubuntu into one partition, this would then be / 
In addition, a swap partition is recommended.

If you separate out the /home directory onto it's own partition, it means that, in the case of a fresh install in the future for whatever reason, you can simply re-mount it and re-use it. /home has all your data in it, unless you have specifically saved it somewhere else, and all the config files for things like evolution and your desktop preferences.

In this case, / contains everything else in the system. You can further divide things up, with separate partitions for /root, /etc and what have you, but this isn't really necessary for a system with a single install and only one user.

10GB for / is ample room with enough elbow room to allow the system to grow a bit, which it does, depending on how you use it.

A recent install I did had about 2.7 GB in /, with a separate /home.
My system has been updated a few times, has Ubuntu Studio on it, i.e. quite a few more programs than a standard Ubuntu, and a number of others that I have installed in the course of time. I am up to about 6GB in /

---

### Post by master_at_work on 2009-12-22
Ah, I see. Well, at least I think I do!

I'll give that a whirl then. Expect to see me back shortly when it all goes horribly wrong...!

---

### Post by houseworkshy on 2009-12-22
As George Bernard Shaw said, he prefers to be a pessimist because then "life is full of pleasant little supprises"  :)

---

### Post by larrypoynor on 2009-12-22
I just downloaded and installed the newest Ubuntu 9.1(I think)  I then noticed it had a windows installer to down load.  Running the windows installer was the easist thing I've ever done with a Linux install.  It lists the hard drives as  C    D    F    just like in windows.

I just had to check which drive to use and how many gig to use....I chose 20 ....Checked the language to use and put in the password I wanted to use.....The installer did everything else.  About the time I thought the computer had hung up,  Ubuntu was installed.

I can't believe how many improvements that have been made.  It even picked up my wireless  USB keyboard and mouse.  The only slow part was the installation other than the download.

So whoever came up with that windows style installer....THANK  YOU!!:lolflag:

---

### Post by Paqman on 2009-12-23
> **master_at_work said:**
> 
What is the recommended 10GB partition for?

/ is pronounced "root". The filesystem starts at / and then branches into things like /dev, /etc and then each of those branches again. So you might have files in /home/dave/Documents/stuff.

So / is where the root of this whole tree is located, and usually contains most is fnot all of the whole filesystem. 

You can if you want mount other parts of the filesystem on other partitions (popular ones include /home and /boot) but you've always got to have /. Having a swap partition is also highly recommended, and unless you opt for manual partitioning one will be created for you automatically.

---

### Post by bilalakhtar on 2009-12-23
What has happened is,
when you selected "Install side by side", Ubuntu resized your D: partition to make space for Ubuntu. Since you aborted the installation, no partition was created in the empty space. What you can do is:-
Delete D from Gparted and tell installer to use free space or
Simply tell the installer to use free space since D: has already been resized to give 45GB free space. (recommended)

---

