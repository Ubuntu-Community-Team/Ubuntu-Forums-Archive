---
title: "Dual booting (Vista 1st then Ubuntu 9.10) installation - couldn't find any answers!"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by amjjawad on 2009-11-01
Hi,

Before few days, I installed Ubuntu on my PC (Vista installed 1st) and I got many problems so I had to remove Ubuntu (deleted the partitions where it was installed using Disk Management - under Windows) and decided to keep looking for answers before install Ubuntu again.

I tried my best to find similar scenario to mine but couldn't find any so I decided to start this thread, hope I can find some good answers/solutions.

My scenario is:
I have a Desktop PC (Intel P4) and TWO (2) Physical Hard Disc Drivers (HDD), one of them is 160GB and the other is 500 GB.

>>More info about my HDDs:

Disc1 (160GB): has 2 partitions, partition (C:) where Vista is installed and partition (E:) where my data is.

Disc2 (500GB): has 3 partitions, partition (D:) 100GB and it's empty, partition (F:) 144GB and it's empty too, and partition (G:) 221GB where some other data are stored.

NOTE THAT: ALL the above partitions are formatted using NTFS filing system.

BTW, partition D and F are empty bcoz I just formatted them (Ubuntu was installed there) and I don't need to use them now.

Now, I started another thread earlier and explained in details what happened with me when I installed Ubuntu on my PC with the above configuration and different scenario for the partitions [[http://ubuntuforums.org/showthread.php?p=8209672#post8209672]](http://ubuntuforums.org/showthread.php?p=8209672#post8209672]).
Now, I don't want to go back to that thread, this is totally different.

My question is: HOW TO INSTALL UBUNTU ON MY PC WITH THE ABOVE SCENARIO?
To be more specific, HOW TO INSTALL Ubuntu on partition (D:) which belongs to Disc2(500GB) and leave Disc1(partition C and E) completely "untouched" and leave it for Windows ONLY also leave both partitions (F:) and (G:) untouched?????

I have lots of free space so I just need to install Ubuntu onto one of my partitions (D:) and leave ALL the others for Windows.

Kindly make sure to explain in details when you answer me question. I want to know what should I do?

a) Shall I use wubi/live CD and run the program under windows? if yes, what shall I do exactly?

b) Shall I put the Ubuntu's CD and restart my PC then boot from the CD and follow the instructions? if yes, what shall I do?
c) when it says:"Where do you want to put Ubuntu 9.10?", what I'm suppose to choose? "Use the entire disc"? or "Use the largest continuous space"? or "Specify partitions manually (advanced)"????

c) if I choose "Specify partitions manually (advanced)", How to make the partitions? last time I've done that, I lost 200GB from my 2nd HD and neither Windows was able to read that partition nor Ubuntu, that's why I had to delete partitions and get Windows back to normal (fixed MBR). 

I've done lots of search and couldn't find the answer for my questions and couldn't find similar scenario.
What I found was about 1 HD only and how to shrink drive C to create more space for Ubuntu or how to install it on another partition on the same disc but never found a topic/thread talking about the above scenario!

Thank you so much and sorry to write too much but I believe the more info I provide, the better answer/solution I get.

AJ

---

### Post by seshomaru samma on 2009-11-01
you should use the live CD
i believe that it comes with an application called gparted which might be called partition editor or something (most probabaly  System->Administration->Partition Editor) 
look for it through the menues and study teh way ubuntu sees your discs . this is important cause ubuntu doesnt use C, D and E, but names like SDA1, SDA2 etc, make sure you know what each partition is called in ubuntu.
next start you installation
when it asks where you want to put ubuntu - choose "manual" 
this will allow you to put ubuntu wherever you want.
don't forget -you will need to create a swap partition for ubuntu

hope this helps

---

### Post by PorkyPie on 2009-11-01
Yes Gpated comes with the livecd at System -> Administration -> gParted.

---

### Post by Cozze on 2009-11-01
Hi,

If you follow this link you'll come to a nicely explained "how to". I followed it and it works nicely with me.

enjoy, Cozze

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by mapes12 on 2009-11-01
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by amjjawad on 2009-11-01
> **seshomaru samma said:**
> you should use the live CD
i believe that it comes with an application called gparted which might be called partition editor or something (most probabaly  System->Administration->Partition Editor) 
look for it through the menues and study teh way ubuntu sees your discs . this is important cause ubuntu doesnt use C, D and E, but names like SDA1, SDA2 etc, make sure you know what each partition is called in ubuntu.
next start you installation
when it asks where you want to put ubuntu - choose "manual" 
this will allow you to put ubuntu wherever you want.
don't forget -you will need to create a swap partition for ubuntu

hope this helps

I formatted and I don't have Ubuntu anymore and I need to install it again. I asked these Qs to avoid the problems I've got 1st time I installed it :(

---

### Post by amjjawad on 2009-11-01
> **Cozze said:**
> Hi,

If you follow this link you'll come to a nicely explained "how to". I followed it and it works nicely with me.

enjoy, Cozze

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

My friend, you didn't read my entire thread, did you? the link that you provide DOES NOT explain or talk about my scenario at all :(
I checked it many times before I started my thread and couldn't find any answers to my Qs!

Sorry, but this is not what I'm looking for!

---

### Post by seshomaru samma on 2009-11-01
> I formatted and I don't have Ubuntu anymore and I need to install it again. I asked these Qs to avoid the problems I've got 1st time I installed it
Do you have a live Ubuntu CD?
1. boot from a live cd
2. open the partition manager
3.note the partition names as ubuntu names them differently
4. start installation
5. when its time to decide where to install ubuntu choose "manual"
6. choose the correct partition (if you want us to tell you which one then boot from the ubuntu live cd , open a terminal and paste the output of "sudo fdisk -l" in here)
7. make sure you created two partitions for ubuntu (you need a small swap partition, it can be a logican one)

if you follow these instructions you will not encounter the problems you had before

---

### Post by amjjawad on 2009-11-01
> **seshomaru samma said:**
> Do you have a live Ubuntu CD?
1. boot from a live cd
2. open the partition manager
3.note the partition names as ubuntu names them differently
4. start installation
5. when its time to decide where to install ubuntu choose "manual"
6. choose the correct partition (if you want us to tell you which one then boot from the ubuntu live cd , open a terminal and paste the output of "sudo fdisk -l" in here)
7. make sure you created two partitions for ubuntu (you need a small swap partition, it can be a logican one)

if you follow these instructions you will not encounter the problems you had before

The one you download from "http://www.ubuntu.com/getubuntu/download"? if yes, then I do have that one for sure.

Believe me, I've done ALL what you have mentioned above and I lost 200GB partition and was unable to access it neither from Windows nor from Ubuntu + I was unable to access Disc1 with all its partitions from Ubuntu at all + During Ubuntu installation, it didn't let me choose a data partition and/or format it as FAT32

As I said, I started this thread coz:
1- I installed Ubuntu and had problems
2- Couldn't find similar scenario in any thread/topic/site coz all of them are talking about ONE DISC with ONE partition and how to shrink that partition and create another one for Ubuntu, that's all what I found.

Thanks!

---

### Post by amjjawad on 2009-11-01
To make your life easier, I want someone to explain "in details" HOW to create partition using "Manual" from Ubuntu partitioning menu during the installation coz this is my weak point and this is where I had problems!

Thanks :)

---

### Post by PorkyPie on 2009-11-01
> **amjjawad said:**
> To make your life easier, I want someone to explain "in details" HOW to create partition using "Manual" from Ubuntu partitioning menu during the installation coz this is my weak point and this is where I had problems!

Thanks :)

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_prepare_disk_space&size=_original]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_create_third_partition")
This should help.

Edit: I've replaced the link

---

### Post by seshomaru samma on 2009-11-01
amjjawd
the reason you "lost" your partition is because you did not manually edited your partition during installation. 
you have a disc with two partitions - Windows and Data
you have another with two empty partitions and an NTFS data
you need to install ubuntu on one of the empty partitions
because you will install it as ext3, it will seem like you can't see it from windows. this has a simple solution - there are xt3 drivers for windows googleit. now it will also seem like you lost all the NTFS partitions from the linux side, but don't worry they are still there, you just need to mount them. [here]("http://www.psychocats.net/ubuntu/mountwindows") is howto . Please read it carefully, preferably several times, aks any questions here.

---

### Post by amjjawad on 2009-11-01
> **seshomaru samma said:**
> amjjawd
the reason you "lost" your partition is because you did not manually edited your partition during installation. 
you have a disc with two partitions - Windows and Data
you have another with two empty partitions and an NTFS data
you need to install ubuntu on one of the empty partitions
because you will install it as ext3, it will seem like you can't see it from windows. this has a simple solution - there are xt3 drivers for windows googleit. now it will also seem like you lost all the NTFS partitions from the linux side, but don't worry they are still there, you just need to mount them. [here]("http://www.psychocats.net/ubuntu/mountwindows") is howto . Please read it carefully, preferably several times, aks any questions here.
My friend, I'll do my best to "re-explain" my problem again and sorry if I missed something before:

I DID use the manual option during installation and I created 4 partitions using Windows before the installation so maybe here's where my problem has come from?!

I don't need to read "Ubuntu's" partitions from Windows, I know I can't read ext3 and/or ext4 from Windows, I need to read "Windows's" partitions from Ubuntu and I was unable to do so first time I installed Ubuntu.

Regarding the lost partition, I got it back, sorry if I didn't make myself clear but as I said, I'm trying to avoid the same problem before I go ahead and install Ubuntu for the 2nd time, that's all :)

As for mounting Windows, that's after installation not before ;)
I need to make sure everything will go smoothly "before and during" Ubuntu installation, then I'll worry about "after" that :D

Thanks!

---

### Post by seshomaru samma on 2009-11-01
let me try to be more detailed:
before you make partitions in ubuntu you need to understand that linux names partitions differently
now you have a good understanding of your discs under windows , but you need to see how linux sees them, for this boot from the live cd (which you used for installation) , but before you install , go to System->Administration->Partition Editor and note the names of the partitions in Ubuntu, most probably hda1 hda2 on the first disc and hdb1 hdb2 hdb3 on the second disc . Identify which partition is D (under windows) and write it down.
start the installation when it gets to the partition part (see [this shot]("http://ubuntuforums.org/showpost.php?p=8212230&postcount=4")) choose manual. delete the D partition. Create a swap partition (should be double your RAM size ) and a main partition for Ubuntu . 
After installation - follow the link in my previous post for mounting NTFS partition and you should be good to go

---

### Post by seshomaru samma on 2009-11-01
I think my last two posts should answer your question , to recap:

partition manually with ubuntu (not windows)
seeing ntfs (windows) from ubuntu is a question of mounting properly (not related to installation), i have provided an excellent link for it
good luck
it might seem very difficult at first but after a while it become very smooth!...

---

### Post by amjjawad on 2009-11-01
> **PorkyPie said:**
> [http://www.basicconfig.com/ubuntu_desktop_manual_partition_prepare_disk_space&size=_original]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_create_third_partition")
This should help.

Edit: I've replaced the link
I think this is where I should start and what should I do :)

I'll read it carefully and hope this is what I'm looking for!

Thanks a lot :)

---

### Post by gn2 on 2009-11-01
> **amjjawad said:**
> ~ I created 4 partitions using Windows before the installation so maybe here's where my problem has come from?! ~

When creating dual boots, I find it's best to use a Windows partitioning tool to resize the Windows partitions down leaving unused (unallocated) space, then use the Linux installer's partitioning phase to create the desired Linux partitions in the unused space.

---

### Post by amjjawad on 2009-11-01
I have TWO HDDS (160GB+500GB) so I don't have to worry about the space ;) thanks for the advice though!

And YES, I should leave unallocated space and use it only during the installation after I choose "manual" option :)

---

### Post by amjjawad on 2009-11-01
> **seshomaru samma said:**
> I think my last two posts should answer your question , to recap:

partition manually with ubuntu (not windows)
seeing ntfs (windows) from ubuntu is a question of mounting properly (not related to installation), i have provided an excellent link for it
good luck
it might seem very difficult at first but after a while it become very smooth!...
I'm going to start the installation now, wish me luck :)

BTW, I love "very difficult" stuff ;) the more things become harder, the better!

Thanks a lot for everything :)

---

### Post by PorkyPie on 2009-11-01
> **amjjawad said:**
> I think this is where I should start and what should I do :)

I'll read it carefully and hope this is what I'm looking for!

Thanks a lot :)

You're welcome. Hope that works for you.

---

### Post by amjjawad on 2009-11-01
Hi again :)

I'd like to THANK ALL those who helped me with advices, links, tips, etc; you guys were very helpful indeed, so thank you so much!

Nothing better than trying it by yourself so I installed Ubuntu and I think everything is fine now. What I did was:

1- While I was on Vista, I put the Live CD for Ubuntu and I ran Wubi/Autorun

2- I chose partition D/sdb1 so that Ubuntu can be installed there

3- Rebooted my PC to finish the installation

4- First problem was: I had some hard time to install Ubuntu on partition (D) which is "sdb1" bcoz it was formatted already and I wanted to see what will happen. So the best option was to delete partition (D)/sdb1 and use the unallocated space to create new partition.

5- Second problem was: You can't create more than 4 primary partitions so had to revert and start all over again. I had to choose "Logical" partitions.

6- Third problem is: As per this site ([http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)), using Wubi will make it possible to install/uninstall Ubuntu just like any other program under Windows but once I formatted the partition (D)/sdb1 which I chose it before using Wubi, I lost the advantage of uninstalling Ubuntu from Windows.

7- I have Dual Booting for both Vista and Ubuntu with more experience :P this is my 2nd day with Ubuntu and it's not bad at all.


Now, as usual, I have some Qs:

a) Is there any problem to use "Logical" partitions instead of "Primary"? I didn't search the net yet and not sure what's the difference between them but I'm asking whether using "Logical" for Ubuntu is bad idea or not?

b) How can I get the best of Wubi? what I understood from this link ([http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)) is that Ubuntu must be installed IN THE SAME partition where Windows is installed. IS THAT RIGHT? or I missed something? and if I have to install Ubuntu on the same drive/partition where Windows is installed, is there any problems may occur or it's safe to do so?

As far as I can tell, Wubi made it easier for those who don't want to be bothered with partitioning and have less experience in these stuff. Am I right?
Problem is, some of these sites/links don't explain in details and always assume the users know about that which is WRONG! you need to be simple and easy so everyone can understand it.

Hope I can find some answers for me Qs.

Thank you in advance!

---

### Post by LewRockwell on 2009-11-01
> re: Dual booting (vista 1st then ubuntu 9.10) installation - **_couldn't find any answers!_**> **amjjawad said:**
> **_i didn't search the net yet_**

?

.

---

### Post by amjjawad on 2009-11-01
I mean I didn't search the internet about the difference between "primary" and "logical" partition but that's in general, my question was " Is there any problem to use "Logical" partitions instead of "Primary"? I didn't search the net yet and not sure what's the difference between them but I'm asking whether using "Logical" for Ubuntu is bad idea or not?"

---

### Post by LewRockwell on 2009-11-01
> **amjjawad said:**
> I mean I didn't search the internet about the difference between "primary" and "logical" partition but that's in general, my question was " Is there any problem to use "Logical" partitions instead of "Primary"? I didn't search the net yet and not sure what's the difference between them but I'm asking whether using "Logical" for Ubuntu is bad idea or not?"

while the conditions which facilitated the necessity of "primary" and "logical/extended" partitions have been largely overcome...we'll be dealing with them for years to come...especially regarding legacy equipment

it is important to note that windows prefers a primary partition

linux distributions don't care

here is a link to a multi-boot laptop thread with a partitioning screenshot for your reference:

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

we also have other threads and posts commenting on partitioning, multi-booting, and grub administration

.

---

