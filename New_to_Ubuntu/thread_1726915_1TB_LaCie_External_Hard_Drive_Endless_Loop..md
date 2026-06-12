---
title: "1TB LaCie External Hard Drive: Endless Loop."
date: 2011-04-11
forum: New to Ubuntu
---

### Post by The_Orange on 2011-04-11
So I JUST got my HD today, plugged it in, and immediately ran into an error. )= I have Wine so when I opened the EXE to start formatting it, it came up with an error that said I **will** need to have an Admin username and login. ...I am Admin of my computer. x-x Whenever I click "**Continue**" it waits a few moments before bringing up the error again. 

I found this: [http://www.lacie.com/uk/support/drivers/driver.htm?id=10138](http://www.lacie.com/uk/support/drivers/driver.htm?id=10138) And downloaded, read the read me, which told me to download Avahi, which I did, and now I'm just lost. 

The Read Me for the driver:

Please read these instructions about LaCie Network Assistant 1.1 for linux.  
  
The software was tested on ubuntu 8.04, mandriva, and Suze, 32bits version.  
 
  
--Installation--  
  
To install LaCie Network Assistant, just double click on the .package file. You might need to check the file has execution permissions.If not, right click on the file, choose "properties", in the "permissions" settings check "allow executing file as program".  
Upon opening the .package, if the autopackage tools are not installed in your system, the installer will automatically offer you to install it.  
  
  
--Configuration--  
  
1/ If you have a 64bits system, you will need the Avahi libraries for 32bits.  
  
2/ Mandriva and suze automatically close ports for Avahi. The application can be launched but it does not list devices on your network. In this case you should open the right port for avahi (UDP 5353). We do not advise you to deactivate your firewall.  
  
3/ If you cannot mount volumes, make sure you have "smbfs" installed.  
  
 
[www.lacie.com]("http://www.lacie.com")  



The .package file won't open. It is mounted ( I think ) because I can go into it and stuff, but that's about it. I also tried to manually format it in Disk Utilities, but it says, "One or more partitions are busy on /dev/sdb". Which I've no clue what that means. x-x I know what a partition is, but I don't know what the /dev/sdb folder is.

Any help would be awesome. <3

---

### Post by jtarin on 2011-04-11
> So I JUST got my HD today, plugged it in, and immediately ran into an error.What was the error? Are you trying to partition and format the drive? How many partitions and what filesystem do you want? Will this drive be accessible by Windows machines? Try mounting the Live CD and using Gparted to work on the disk.

---

### Post by The_Orange on 2011-04-11
It says in the manual that I have to format it before use. The error was the endless loop telling me I had to be an admin. I am THE admin and every time I click the Continue button, it just brings it back. I'd like for it to be compatible with OSX so I can use it at school, but my mom just informed me that she'd like to use it to back up one of our laptops on it, which runs Windows. I don't think it'll be able to do all three OSs, so I'd really rather it be for Ubuntu and OSX if it can't be for Windows as well. 

"Try mounting the Live CD and using Gparted to work on the disk."

...Uhhh. xDDD Live CD as in the CD I used to install Ubuntu? If so, then...Gparted?

---

### Post by K_45 on 2011-04-12
Try loading G-Parted (its in Synaptic) and format it as NTFS. That should work across all three systems.

---

### Post by jtarin on 2011-04-12
> **The_Orange said:**
> 

"Try mounting the Live CD and using Gparted to work on the disk."

...Uhhh. xDDD Live CD as in the CD I used to install Ubuntu? If so, then...Gparted?Yes the one and the same. Select "Try Ubuntu" and when you get to the desktop Gparted will be in the menu Applications --> System Tools --> GParted. You can then partition your disk into more than one partition and use each for a different filesystem.

---

### Post by The_Orange on 2011-04-12
Alright, that all makes since. The only other problem I have is that whenever I try to do anything with it using the Ubuntu Disk Utility, it gives me this: "One or more partitions are busy on /dev/sdb" and I can't do anything. Do you think Gparted give me the same error or do I have to do something else?

---

### Post by jtarin on 2011-04-12
Shouldn't have that problem as GParted will be running from RAM.

---

### Post by The_Orange on 2011-04-12
> **jtarin said:**
> Shouldn't have that problem as GParted will be running from RAM.

AWESOME! Last question before I start this tonight: If I partition it into three parts ( Linux partition, Windows partition, and OSX partition ), how will each OS know which partition to enter? Or do I manually select it each time?

---

### Post by jtarin on 2011-04-12
You will need to manually enter them in most cases.

---

### Post by The_Orange on 2011-04-13
Alright, I've been trying to piece this together the past two days, but I'm a bit stuck now. I found this guide: [http://www.dedoimedo.com/computers/gparted.html#mozTocId133810](http://www.dedoimedo.com/computers/gparted.html#mozTocId133810) but it doesn't seem to answer my bigger questions. 

First off I guess I should mention that I will not be using a Live CD of Ubuntu since I tried my original CD, burned a new Live CD on a Fujifilm CD, and burned a new Live CD on a Memorex CD and none of them seemed to want to read (they start to boot up from the CD, but make random noises, fail, and thus continue in the normal start up way). So, I downloaded a live version of gParted and that seems to work. 

I also downloaded gParted on my desktop just so I can study it while looking at the guides. I'm lost. Here's a screen shot of what gParted gives me: [http://i53.tinypic.com/2uz6wsl.jpg](http://i53.tinypic.com/2uz6wsl.jpg)

I know I'm not supposed to touch the sdb1, but the others are free game right? What about the sdb2? Also, I can't make any more Primaries, I need to make one of them extended, but I don't know how. That guide kind of shows you, but not really. It loses me in that respect. I think I also need to create a partition table, but that would wipe out all the LaCie information, would it not? If so, does the HD need that information in order to work? If it'll work without that information, how so? Will it work more like a regular flash drive that doesn't need to be formatted for a specific software?

---

### Post by K_45 on 2011-04-14
Back up all the stuff off the drive, then delete all the partitions and start over would be a starting point.

---

### Post by jtarin on 2011-04-14
What is your intended use for this drive...try to be specific?
Here is a [link ]("https://help.ubuntu.com/community/HowtoPartition")to Ubuntu documentation using Gparted.If there's nothing on the disk you want to keep there is no problem experimenting with Gparted at this point.....just look at the documentation. Answer my question and then I can advise you better.

---

### Post by The_Orange on 2011-04-14
> **jtarin said:**
> What is your intended use for this drive...try to be specific?
Here is a [link ]("https://help.ubuntu.com/community/HowtoPartition")to Ubuntu documentation using Gparted.If there's nothing on the disk you want to keep there is no problem experimenting with Gparted at this point.....just look at the documentation. Answer my question and then I can advise you better.

I want to use it to back up my Ubuntu laptop and my school work that's on the school's Macs. My mom also wants to back one of our Windows laptops up on it. So basically, I just want it to be able to back up information from three different OSs. That's all. 

There is nothing on it I wish to keep unless some of those files are needed for it to work. ( I will back them up on my desktop just in case. )

---

### Post by jtarin on 2011-04-14
> **The_Orange said:**
> I want to use it to back up my Ubuntu laptop and my school work that's on the school's Macs. My mom also wants to back one of our Windows laptops up on it. So basically, I just want it to be able to back up information from three different OSs. That's all. 

There is nothing on it I wish to keep unless some of those files are needed for it to work. ( I will back them up on my desktop just in case. )So partition it for each file system then format each parition.Linux can read and write NTFS, Win cannot read or write but to Win. You should be able to format each partition as you like with Gparted.

---

### Post by The_Orange on 2011-04-14
> **jtarin said:**
> So partition it for each file system then format each parition.Linux can read and write NTFS, Win cannot read or write but to Win. You should be able to format each partition as you like with Gparted.

I guess I didn't word my question right. xD That's what I'm planning on doing; making a partition for each OS and then formatting them all for NTFS.

My question is: Are any of those files already on the LaCie drive ( the default ones they come with ) necessary to make it work? If I take them off will it work similar to a flash drive ( except far more reliable )? Because I think everything will be deleted if I make a new partition table, right?

---

### Post by K_45 on 2011-04-14
You don't need any of Lacie's "utilities", copy them somewhere else if you want to, but otherwise format away.

---

### Post by jtarin on 2011-04-15
> **The_Orange said:**
> I guess I didn't word my question right. xD That's what I'm planning on doing; making a partition for each OS and then formatting them all for NTFS.

My question is: Are any of those files already on the LaCie drive ( the default ones they come with ) necessary to make it work? If I take them off will it work similar to a flash drive ( except far more reliable )? Because I think everything will be deleted if I make a new partition table, right?Blow them off......not necessary for what you want. If you need the mfg's files later for something you can always find them on their site, but your not using the drive for an operating sysystem so their useless at thi point.

---

