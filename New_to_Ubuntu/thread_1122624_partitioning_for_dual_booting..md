---
title: "partitioning for dual booting."
date: 2009-04-11
forum: New to Ubuntu
---

### Post by linuxdualbooter on 2009-04-11
I have a linux live CD and want to install it, however when i get to the partitioning part of the installer, it shows 3 options. I click on the first option, but then that option goes away, and I'm left with either manual install, or only ubuntu. What do I do? Please help.

---

### Post by waspbr on 2009-04-11
What I normally do is the following.

choose manual (I reckon the last choice)

this is going to take you to another screen

there you can manage your hardDrive, I am assuming you already have your windows installed, windows will not erase the MBR and use its own. So install windows first, leave the space you want for ubuntu and then install ubuntu

So you have your windows partition(sda1[probably]), next you need to make a swap partition, rule of the thumb is 1.5 to 2 time the ammount of RAM you have. Create a new partition and set its size accordingly, as a filesystem you should select (linux) swap.

You can then create another partition for you ubuntu install, create a new partition, make it as big as you like. For the filesystem choose journalizing ext3 and for the mount point choose / , check the format box. 

this should do it. there are several videos on youtube about this if you need more visual help , search for ubuntu dual boot.

good luck

Remember to back up your important files

---

### Post by linuxdualbooter on 2009-04-11
thx :D

---

### Post by raymondh on 2009-04-11
> **linuxdualbooter said:**
> I have a linux live CD and want to install it, however when i get to the partitioning part of the installer, it shows 3 options. I click on the first option, but then that option goes away, and I'm left with either manual install, or only ubuntu. What do I do? Please help.

You ought to have the option to do a "guided resize" if you only have 1 OS installed right now. Am curious as to why you don't have that option.  Are you able to post a screenshot of your partitions?  Using the liveCD, go to Applications > Accessories > take a screenshot and post in this thread.

There are a lot of reads available which can help you decide which kind of manual install you'd like to make.  Google and Forum search for a "how-to" or info about manual install.  Am not trying to discourage you. "Manual" installs will give you so much options that unless you know what you want to accomplish (separate home partition, no swap, with SWAP, etc) it can be dangerous to one's sanity if/when you lose your files :)    Also, once you decide on the type of manual install, then the forum can help/guide you.

Let us know.

Raymond

---

### Post by linuxdualbooter on 2009-04-11
> **raymondhenson said:**
> "Manual" installs will give you so much options that unless you know what you want to accomplish (separate home partition, no swap, with SWAP, etc) it can be dangerous to one's sanity if/when you lose your files :)    Also, once you decide on the type of manual install, then the forum can help/guide you.

Let us know.

Raymond

What?! (separate home partition, no swap, with SWAP, etc) what does that mean ?! what is "swap"? or "seperate home partition"?
Here are the screenshots. Not very good though.
Hope it helps...

EDIT: I've seen some people say to shrink C:\ and then use free space. I did that and have over 85 GB, but when I choose that option, it shows 100% linux. Anyone know why?

---

### Post by Paqman on 2009-04-11
Aha, I see your problem. You already have 3 partitions.

The issue is that you can only have 4 primary partitions on a hard drive, and Ubuntu needs 2.

There is a way around this, but it will require manual partitioning. Basically you'll have to create enough free space at the end of your drive (min 20GB or so) Then you'll have to create a new "extended partition" in that free space.

An extended partition is a way to cheat the 4 partitions rule. It can house further partitions inside it.

So what you're going to want to do is create two new partitions *inside* the extended partition (they're called "logical partitions"). One should be formatted as "swap" and be the size of your RAM, the other should be formatted as "ext3" and have it's mount point defined as / from the drop down box. It should contain all of the remaining space on the drive.

Don't worry too much about the jargon, all will become clear soon enough.

A "separate home" is an option you have during manual partitioning. It's nice to have, but not compulsory. If you want to create one, then leave your / (aka root) partition at about 8-15GB, your swap the same as RAM like before, and give all the remaining space to an extra partition, which you then define the mount point as /home.

Manual partitioning is pretty bewildering the first time you do it, but after that you'll see it's actually pretty straightforward.

---

### Post by linuxdualbooter on 2009-04-11
how do you find RAM under linux?
nvm I found it. However it says I have 3028 MB RAM. Does that look reasonable? for desktop.
EDIT: Ok, I did that and this is what it looks like now:

---

### Post by Paqman on 2009-04-11
System > Admin > System Monitor. It's a lot like Task Manager in Windows.

---

### Post by linuxdualbooter on 2009-04-11
OK please say this is right:
I've given linux 62.5 GB.

---

### Post by linuxdualbooter on 2009-04-11
Thanks to everyone who helped.:D

---

### Post by raymondh on 2009-04-11
> **linuxdualbooter said:**
> Thanks to everyone who helped.:D

Glad to hear you've got your 2-boot running.  Enjoy the power :)

Kindly close this thread and consider it "solved" if all's ok.

Enjoy the learning.

Raymond

---

