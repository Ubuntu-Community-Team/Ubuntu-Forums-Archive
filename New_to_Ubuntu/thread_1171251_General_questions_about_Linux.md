---
title: "General questions about Linux"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by zortec on 2009-05-27
Please let me know if I posted this in the wrong forum.  I have been running Ubuntu 9.04 in VirtualBox and love it.  But I want to dual boot Windows/Linux and make the switch to using only Linux, though I know gaming support is one of the areas that Linux is not very strong in so that is why I want to keep Windows around.  I do know about Wine for running Windows games.

I would like to get some more info about a few things and hope that people can help.

What is the best partition scheme for a dual boot system?  There has been a lot of debate over whether or not you should allocate space for a swap file.  Is this worth doing and is 512MB enough?

Next up is KDE and Gnome.  I used Kubuntu in the past, but my experience with Ubuntu has been pleasant and I prefer it over KDE.  Are there any reasons for going with KDE over Gnome?

This might have been asked in the forum already, forgive me for not searching.  What are the Twitter clients that everyone is using in Linux?  I want to replace TweetDeck and Twhirl.

Where can you get clear and nice fonts in Linux?  Does ClearType work in Linux as well as Windows?

I hope to remove Windows and just use Linux.

---

### Post by Sef on 2009-05-27
> Next up is KDE and Gnome. I used Kubuntu in the past, but my experience with Ubuntu has been pleasant and I prefer it over KDE. Are there any reasons for going with KDE over Gnome?

Ultimately, it is preference.   Use what you prefer.

---

### Post by mike555 on 2009-05-27
I like Gnome better , but that's me.......... as far as swap I would make it twice your RAM size .... I would not make a separate home partition, but instead make a separate partition for backups,perhaps fat32 or ntfs ,so both Windows and Ubuntu can use it ......  good luck.

---

### Post by Mornedhel on 2009-05-27
> **zortec said:**
> What is the best partition scheme for a dual boot system?  There has been a lot of debate over whether or not you should allocate space for a swap file.  Is this worth doing and is 512MB enough?

The first step is to install Windows (you can of course keep your current Windows install if you have one). This should be on the very first partition of your first drive ; otherwise, depending on versions, there can be issues if the MBR is somewhere else. This will result in an NTFS partition (unless you dual boot XP, in which case you could use FAT32 if you really wanted to).

Next come the Linux partitions. You need at least one for the root mountpoint on / ; some people advocate using a separate /home partition. This is subject to debate. ext3 is the default and tested choice. ext4 is bleeding edge and not yet recommended for stable systems. Other filesystems to taste.

Having a swap partition is recommended for two reasons : in case you use all your RAM, you can still have a usable system ; and if you do things like suspend/hibernate, the system will in some cases suspend to swap and resume from there. Allocate twice the amount of RAM you have (less if you really do not plan to suspend/hibernate).

Then you could have a shared partition for data in a filesystem both OSes understand : FAT32 or NTFS. NTFS is recommended since it is now well supported in Linux and FAT32 doesn't have as many features.

> **zortec said:**
> Next up is KDE and Gnome.  I used Kubuntu in the past, but my experience with Ubuntu has been pleasant and I prefer it over KDE.  Are there any reasons for going with KDE over Gnome?

A matter of taste, as other posters have said. KDE seems to have more fancy applications and eye candy. It also has waaaaaay too many configuration options, in my humble opinion. I keep Gnome because it gets the job done : more features than lightweight environments like XFCE, less bloat than KDE.

> **zortec said:**
> Where can you get clear and nice fonts in Linux?  Does ClearType work in Linux as well as Windows?

ClearType is proprietary Microsoft technology IIRC. However, you can play with the Fonts tab in Appearance (including the Details button) and achieve similar effects.

---

### Post by halitech on 2009-05-27
> **zortec said:**
> I would like to get some more info about a few things and hope that people can help.

What is the best partition scheme for a dual boot system?  There has been a lot of debate over whether or not you should allocate space for a swap file.  Is this worth doing and is 512MB enough?

512 is enough for ram but I would use a swap space of at least 1.5 times the ram. As far as a partitioning scheme, depends on how much space you will be giving to linux.

> Next up is KDE and Gnome.  I used Kubuntu in the past, but my experience with Ubuntu has been pleasant and I prefer it over KDE.  Are there any reasons for going with KDE over Gnome?

a lot of people prefer Gnome as it is simple to configure. Personally I use XFCE because I find it faster and works better for me. Everyone has their own tastes though.

> This might have been asked in the forum already, forgive me for not searching.  What are the Twitter clients that everyone is using in Linux?  I want to replace TweetDeck and Twhirl.

not sure as I don't use twitter

> Where can you get clear and nice fonts in Linux?  Does ClearType work in Linux as well as Windows?

I hope to remove Windows and just use Linux.

not sure cleartype works but you can install the msttcorefonts as part of the (x)(k)ubuntu-restricted-extras. Also any fonts that have a .ttf extension can be used.

---

### Post by BlackMeTaL on 2009-05-27
Why is everybody going on about x times your RAM for the swap space? The less RAM you have the more swap space you should use. Personally I use 2GB for swap and it seems to be more than enough for normal usage.

---

### Post by albinootje on 2009-05-27
> **zortec said:**
>  There has been a lot of debate over whether or not you should allocate space for a swap file.  Is this worth doing and is 512MB enough?

If you have a laptop and you want to use hibernate, then need enough swapspace, and this depends on your RAM memory amount.

You cannot save a fully used 2 Gb of RAM in 512 Mb swapspace.

---

### Post by halitech on 2009-05-27
> **BlackMeTaL said:**
> Why is everybody going about x times your RAM for the swap space? The less RAM you have the more swap space you should use. Personally I use 2GB for swap and it seems to be more than enough for normal usage.

depends on the amount of ram you have, I have 2 gig of ram and set up a 2 gig swap space but I've only used 2.05meg of swap. Once you hit a gig of ram, swap space because less needed. With 512meg, he'll want to use swap and the "standard" was 1.5 or 2 times the amount of ram. Swap was not designed to be a replacement for ram, just to suppliment it in case it was needed.

---

### Post by lisati on 2009-05-27
A couple of extra thoughts: [LIST=1]
[*]Make sure you have a backup of important data, including things like recovery partitions, before you begin
[*]It can be easier if you have Windows installed first due to the way the installers for Windows & Ubuntu cope with other operating systems being present (Ubuntu is generally friendlier, and installing Ubuntu after Windows can mean less work to do once they're both installed)
[*]Defragment your Windows partition before resizing it
[/LIST]

---

### Post by presence1960 on 2009-05-27
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

**Make sure you back up your data- Don't be the one that gets burned!** Although partitioning works very good there is always the chance something can go wrong. So live by the rule " Anything can go wrong at any time." Back up always, especially prior to partitioning.

I would defrag windows prior also, this will save you some potential headaches.

---

### Post by zortec on 2009-05-27
Just a couple points, I have a 250GB drive and created a 100GB for Windows.   So I was going to install Ubuntu on a separate partition of about 10-20GB.  This machine has 2.93GB RAM and that is not including the 256MB for my NVIDIA GeForce 7050 / NVIDIA nForce 610i video adapter.  As a sidenote, will I have any issue finding drivers for my video to enable Compiz and 3D effects?

> 
Next come the Linux partitions. You need at least one for the root mountpoint on / ; some people advocate using a separate /home partition. This is subject to debate. ext3 is the default and tested choice. ext4 is bleeding edge and not yet recommended for stable systems. Other filesystems to taste.


Do I need a /var or partition for NTFS?  I have only used the ext3 filesystem.  Is ext4 faster than the others?  Will there be any performance boost?  You did mention that it was bleeding edge.

> depends on the amount of ram you have, I have 2 gig of ram and set up a 2 gig swap space but I've only used 2.05meg of swap. Once you hit a gig of ram, swap space because less needed. With 512meg, he'll want to use swap and the "standard" was 1.5 or 2 times the amount of ram. Swap was not designed to be a replacement for ram, just to suppliment it in case it was needed.

Should I create a 4GB swap file given the 1.5x amount of RAM?  I think that is big.

As for desktop environments, I will stick with Gnome but I have never tried XFCE or Fluxbox.  

I did a bit of searching on Google for Twitter clients under Linux.  The two that work surprisingly well are Twhirl and TweetDeck, both Adope Air apps.

Thanks for all the info.

---

### Post by halitech on 2009-05-27
> **zortec said:**
> Just a couple points, I have a 250GB drive and created a 100GB for Windows.   So I was going to install Ubuntu on a separate partition of about 10-20GB.  This machine has 2.93GB RAM and that is not including the 256MB for my NVIDIA GeForce 7050 / NVIDIA nForce 610i video adapter.  As a sidenote, will I have any issue finding drivers for my video to enable Compiz and 3D effects?

I would probably go a bit bigger if you have 150 gig to play with. NVidia generally plays well with Linux so driver shouldn't be a problem.

> Do I need a /var or partition for NTFS?  I have only used the ext3 filesystem.  Is ext4 faster than the others?  Will there be any performance boost?  You did mention that it was bleeding edge.

/var will be created by default under / unless you manually create your own which isn't necessary. If you have an NTFS partition then you can mount it after you have the install done. I've never used ext4 so can't speak on it.

> Should I create a 4GB swap file given the 1.5x amount of RAM?  I think that is big.

I would probably create one cause linux does expect to see one but I would probably go with 1 gig and not 4

> As for desktop environments, I will stick with Gnome but I have never tried XFCE or Fluxbox.  

XFCE looks a lot like gnome but is lighter and runs better, not that performance will be an issue with the system you have.

> I did a bit of searching on Google for Twitter clients under Linux.  The two that work surprisingly well are Twhirl and TweetDeck, both Adope Air apps.

Thanks for all the info.

good luck and welcome :)

---

### Post by zortec on 2009-05-30
Almost there, just a few more questions before I begin.  Should I use Windows to create the partition for Ubuntu or go through the LiveCD?  For the partition, is 50GB plenty of space?  I want to leave some room for more software later. 

I will give the swap 1GB.  According to what I read in another thread, you should only use 2GB if you are going to hibernate.  Do I have that right?

Any other advice would be most helpful.

Looking forward to an exciting adventure.  I hope there will not be too many bumps along the way. :)

---

### Post by zortec on 2009-05-30
*bump*

---

### Post by overdrank on 2009-05-30
> **zortec said:**
> Almost there, just a few more questions before I begin.  Should I use Windows to create the partition for Ubuntu or go through the LiveCD?  For the partition, is 50GB plenty of space?  I want to leave some room for more software later. 

I will give the swap 1GB.  According to what I read in another thread, you should only use 2GB if you are going to hibernate.  Do I have that right?

Any other advice would be most helpful.

Looking forward to an exciting adventure.  I hope there will not be too many bumps along the way. :)

Hi and you can use the live cd to create the partition. 50gb is a good start and you can alway resize later. Swap is twice that of the memory in the system, in my opinion :) you may look at the link in my signature also about New To Ubuntu start here
[COLOR="Red"]Edit as I said in your other thread about bumping once a day not 2 hrs[/COLOR] :(

---

