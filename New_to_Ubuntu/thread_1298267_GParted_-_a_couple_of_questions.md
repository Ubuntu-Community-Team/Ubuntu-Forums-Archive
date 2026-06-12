---
title: "GParted - a couple of questions"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by jmundinger on 2009-10-22
I am considering converting my Acer netbook from a Windows XP to a dual boot machine.  The hard drive has two primary partitions - one a utility/re-installation and the other with Windows (142 gb).

Based on what I have read, it sounds as though the better approach for installing Ubuntu into a partition with Windows already installed would be to first run GParted to create the partition.  That would allow the opportunity to first reboot and then run chkdsk in Windows, prior to the installation.  That leads to two questions:

1.  Is it possible to install/boot GParted on a thumb drive?  This is more for academic curiosity than for application because I do have a usb cd/dvd drive for the netbook.
2.  Am I correct in assuming that I could also use GParted to create a new primary partition within the existing Windows partition and then format it for use with Windows if I decide to not install Ubuntu on this machine?
3.  Am I also correct in assuming that, if I am going to install Ubuntu, I should create both a primary partition for Ubuntu and an extended partition.  Or should I just create a large unformatted space and let Ubuntu do it's thing with the free space?

---

### Post by yeats on 2009-10-22
> 1. Is it possible to install/boot GParted on a thumb drive? This is more for academic curiosity than for application because I do have a usb cd/dvd drive for the netbook.

Yes - if you are using Windows, I suggest downloading the .iso file for GParted and using Unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to create the USB disk.  Run a defrag (perhaps more than one) before resizing.

> 2. Am I correct in assuming that I could also use GParted to create a new primary partition within the existing Windows partition and then format it for use with Windows if I decide to not install Ubuntu on this machine?

I would just use Windows' own partitioning tool for this...

> 3. Am I also correct in assuming that, if I am going to install Ubuntu, I should create both a primary partition for Ubuntu and an extended partition. Or should I just create a large unformatted space and let Ubuntu do it's thing with the free space?

The latter is simplest and recommended for beginners.  If you really like Ubuntu, you might consider a separate /home partition, which makes upgrades and distro changes easier down the road.

---

### Post by whitethorn on 2009-10-22
Like someone mentioned I'd use a windows partitioner to shorten the windows partition and then you can install ubuntu into whatever u've been able to free up.  This is very important with vista and Windows 7.  

You don't really need a different .iso for gparted.  Just use Unetbootin to put a live Ubuntu on your usb stick.  Gparted is on the live cd under System -> Administration -> Gparted.  

As for seperate partitions you're going to need a couple.  First you'll need a swap partition this depends on the size of your ram, then you might want to also create a /home partition so when you reinstall ubuntu you won't lose you user data.

---

### Post by QIII on 2009-10-22
Rather that "might", I would say you ought to create a separate /home partition.

If you like Ubuntu and want to eventually stick with it, then you really ought to have a separate /home partition for new clean installs.

I have experimented with a number of ways to create a new /home partition post-install and then move your current /home contents to the new separate /home partition.  I've had mixed results -- from utter disaster to nearly done but requiring some further work.  None of them were what I would consider to be satisfactory.  This has always been done on test machines, mind you, and I was never worried about loss of data.  (But you should BACK UP ANYWAY whenever you update/upgrade/reinstall.)

Just create a /home partition to begin with.  Makes things less complicated all the way around.

---

### Post by oldos2er on 2009-10-22
> **jmundinger said:**
> Am I also correct in assuming that, if I am going to install Ubuntu, I should create both a primary partition for Ubuntu and an extended partition.

 Ubuntu's perfectly happy on an extended logical partition.

---

### Post by sgosnell on 2009-10-22
You don't necessarily need a swap partition.  I've never used one on my EEE laptop, and never had a problem.  The only time you have to have a swap partition is if you use hibernate, which I never do, or if your RAM gets filled and you need to swap some of it to disk to load more data.  I haven't needed that, either.

---

### Post by jmundinger on 2009-10-22
> **whitethorn said:**
> Like someone mentioned I'd use a windows partitioner to shorten the windows partition and then you can install ubuntu into whatever u've been able to free up.  This is very important with vista and Windows 7. 

I'm running XP.  I don't think disk manager would let me create a new partition within a partition in which windows is installed, thus the question about doing with GParted, even if I did not install Ubuntu in the new partition.

> **whitethorn said:**
>  You don't really need a different .iso for gparted. Just use Unetbootin to put a live Ubuntu on your usb stick. Gparted is on the live cd under System -> Administration -> Gparted. 

thanks for that tip.

> **whitethorn said:**
>  As for seperate partitions you're going to need a couple. First you'll need a swap partition this depends on the size of your ram, then you might want to also create a /home partition so when you reinstall ubuntu you won't lose you user data.

If I create a large, unformated free space and then tell Ubuntu to use that space, won't it create an extended partition, with the swap partition inside, during the installation?

---

### Post by jmundinger on 2009-10-22
> **QIII said:**
>  Just create a /home partition to begin with.  Makes things less complicated all the way around.

Is there a tutorial to explain how to do that?

And, if I create a /home partition, am I correct in assuming that I would end up with an extended partition with three logical drives - one for /root, one for /home and one for SWAP (assuming that I do want a SWAP partition and I think I do)?

---

### Post by laffinet on 2009-10-22
> **jmundinger said:**
> Is there a tutorial to explain how to do that?

There are, don't have one handy at the moment, just search for ubuntu install separate home partition.

It's fairly simple though. Start up the partitioner (either from liveCD or separate Gparted CD/USB stick.
Create the partition, selecting the appropriate mount points:
1 for root (mount point "/")
1 for home (mount point "/home")
1 for swap if you want swap (select swap as partition type)

Then install Ubuntu, selecting manual partition and point the install to the right partitions. Done.

> **jmundinger said:**
> 
And, if I create a /home partition, am I correct in assuming that I would end up with an extended partition with three logical drives - one for /root, one for /home and one for SWAP (assuming that I do want a SWAP partition and I think I do)?
Not so much logical drives, more partitions. Not an expert myself, so can't explain in great detail. You basically end up with an extended partition, containing 3 (logical?) partitions, root, home, swap

---

### Post by QIII on 2009-10-23
> **jmundinger said:**
> Is there a tutorial to explain how to do that?

Yes, several.

I'm not going to give you the "RTFM" treatment, but I don't have the time just right now to look through all of the ones that exist and pick out the one that I think explains it best (and is the most correct!)

I will try to get this done this weekend if you have not had a chance to do so yourself and post a link.

A poster above as given you a schematic.  It makes perfect sense if you happen to be familiar with what he is saying.  If it makes sense to you at your skill level, just follow his instructions.

---

### Post by jmundinger on 2009-10-23
> **QIII said:**
>  A poster above as given you a schematic.  It makes perfect sense if you happen to be familiar with what he is saying.  If it makes sense to you at your skill level, just follow his instructions.

I think I understand it - create the three partitions prior to doing the installation and, if I have identified the mount points for each corrrectly, the installation process will sort them out.

---

### Post by egalvan on 2009-10-23
> **whitethorn said:**
> ...I'd use a windows partitioner to shorten the windows partition...
 This is very important with vista and Win7.

Absolutely, +1
they are happier with their own Disk Management Tools.

> You don't really need a different .iso for gparted.
  Just use Unetbootin to put a live Ubuntu on your usb stick.
  Gparted is on the live cd under System -> Administration -> Gparted.

No, you don't NEED a different ISO, but using one, such as gparted, or PartedMagic LiveCD, will give you the latest gparted.
The Ubuntu ones tend to be slightly behind.
PartedMagic is an especially nice "mini-distro" for partitioning and formatting needs.

---

