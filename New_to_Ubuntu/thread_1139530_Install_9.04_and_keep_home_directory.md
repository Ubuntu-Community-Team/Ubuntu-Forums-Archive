---
title: "Install 9.04 and keep home directory"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by akkad on 2009-04-27
i have a dual boot system ubuntu/windows, am looking to install 9.04 with a new fresh installation(not upgrade), is it possible to have a fresh installation and also keep my current home directory and also without affecting the windows installation ??? one note here that i installed ubuntu after windows so ubuntu is handling boot loading.

any suggestions?

---

### Post by kpkeerthi on 2009-04-27
Is your /home on a separate partition?

---

### Post by akkad on 2009-04-27
> **kpkeerthi said:**
> Is your /home on a separate partition?

nope :(

---

### Post by kpkeerthi on 2009-04-27
Well then, unfortunately, the only option is to backup the contents of /home/<user> to an external media and then restore them back after you complete your install.

---

### Post by akkad on 2009-04-27
> **kpkeerthi said:**
> Well then, unfortunately, the only option is to backup the contents of /home/<user> to an external media and then restore them back after you complete your install.

maaaaaaaaaaaannnnn :(, you know what i guest ubuntu should take this in consideration, or in fact ubuntu should utilise the feature of linux that a user data/config are all in one place un like windows which you dont know where the files are, so it can be a good option if a user can transfer the user directory from older to new ubuntu version.

---

### Post by alphacrucis2 on 2009-04-27
> **kpkeerthi said:**
> Well then, unfortunately, the only option is to backup the contents of /home/<user> to an external media and then restore them back after you complete your install.

Is that actually true? What happens if you do a manual install selecting the existing partition and tell it not to format. I vaguely recall I did that on one of my machines and it worked ok.

---

### Post by akkad on 2009-04-27
> **alphacrucis2 said:**
> Is that actually true? What happens if you do a manual install selecting the existing partition and tell it not to format. I vaguely recall I did that on one of my machines and it worked ok.

man can you assure this 100%? if i will lose my data i will sue you :D

---

### Post by alphacrucis2 on 2009-04-27
> **akkad said:**
> man can you assure this 100%? if i will lose my data i will sue you :D

No way. Back your data up first before trying anything like this. If it works it will at least save doing the restore:lolflag:

---

### Post by nothingspecial on 2009-04-27
Why not put your /home on a seperate partition. <snip>

---

### Post by akkad on 2009-04-27
> **nothingspecial said:**
> Why not put your /home on a seperate partition. <snip>

i dont know but i refered to this issue before where a lot of people didnt recommend this as a kind of that all packages/application and even ubuntu in some cases consider the default home directory is on the same / root partition.

---

### Post by alphacrucis2 on 2009-04-27
> **akkad said:**
> i dont know but i refered to this issue before where a lot of people didnt recommend this as a kind of that all packages/application and even ubuntu in some cases consider the default home directory is on the same / root partition.

That shouldn't normally be a problem as the applications ought not care what partition a file is in. They should be accessing it via the directory structure.

---

### Post by kpkeerthi on 2009-04-27
> **alphacrucis2 said:**
> Is that actually true? What happens if you do a manual install selecting the existing partition and tell it not to format. I vaguely recall I did that on one of my machines and it worked ok.

How would that work if / and /home were on the same partition? You need a room for the new OS. Correct?

---

### Post by alphacrucis2 on 2009-04-27
> **kpkeerthi said:**
> How would that work if / and /home were on the same partition? You need a room for the new OS. Correct?

It should just overwrite any existing files of the same name and directory  of any files it is installing. Nothing magical.

---

### Post by kpkeerthi on 2009-04-27
> **alphacrucis2 said:**
> It should just overwrite any existing files of the same name and directory  of any files it is installing. Nothing magical.

I wouldn't do that as it would leave a lot of junk files behind and you would have no idea what/where they are. But that's just me.

---

### Post by scheuri on 2009-04-27
Hi all

**Situation**
You have ONE partition (with ubuntu - the os - and your home) and you would like to install a new ubuntu.

**Solution to situation**
You HAVE to make a backup of all your data and then install ubuntu freshly and formatting the whole part where you want to install ubuntu.
This time I suggest you make two partitions. One for Ubuntu (/) and one for your home-drive (/home). So next time you can easier upgrade.

**Reason:**
If you install the nwe ubuntu and tell it just to overwrite the data (without letting it format the partition, as mentioned by alphacrucis2) it can screw up the whole installation. Ubuntu 904 ships with new software which can be larger or smaller. Just "installing" it over the exisiting partition will keep the rest of the partition (which is not overwritten by the new installation). But do you know where that will stop? Do you know where Ubuntu 9.04 will leave the rest of your data alone? You have no clue how much data the new insallation will overwrite and how much it will not.
It is a very very very very very very unsafe thing to do.

**IMPORTANT:**
Always make backups of your data, no matter when and how you upgrade!

Now, you said that Ubuntu should take that into consideration.
Windows does not and usually you buy computers where the whole disk is ONE partition. So...same situation everywhere. If you are savy enough to install windows, you already should have taken that into consideration.

But you are right...there should be some sort of tool tip or warning mentioning to make a seperate /home.

Good luck
cheers
scheuri

---

### Post by alphacrucis2 on 2009-04-27
> **scheuri said:**
> Hi all

**Situation**
You have ONE partition (with ubuntu - the os - and your home) and you would like to install a new ubuntu.

**Solution to situation**
You HAVE to make a backup of all your data and then install ubuntu freshly and formatting the whole part where you want to install ubuntu.
This time I suggest you make two partitions. One for Ubuntu (/) and one for your home-drive (/home). So next time you can easier upgrade.

**Reason:**
If you install the nwe ubuntu and tell it just to overwrite the data (without letting it format the partition, as mentioned by alphacrucis2) it can screw up the whole installation. Ubuntu 904 ships with new software which can be larger or smaller. Just "installing" it over the exisiting partition will keep the rest of the partition (which is not overwritten by the new installation). But do you know where that will stop? Do you know where Ubuntu 9.04 will leave the rest of your data alone? You have no clue how much data the new insallation will overwrite and how much it will not.
It is a very very very very very very unsafe thing to do.



I don't agree. An install is just writing files to disk just like any other program does. As long as the file system software on the install CD it is using, is not faulty then it shouldn't cause any problems to files that aren't specifically being replaced. This has prompted me to try this on my test machine tomorrow as it has nothing to do till the alpha1 of Karmic comes out.
 

> **IMPORTANT:**
Always make backups of your data, no matter when and how you upgrade!

That goes without saying whether you are upgrading or not. A disk can fail at any time.

---

### Post by kpkeerthi on 2009-04-27
@akkad:
If you currently have only one partition where both / and /home exist, the safest option is to backup the contents of your /home. And then copy them over to your new /home.

---

### Post by alphacrucis2 on 2009-04-27
> **kpkeerthi said:**
> I wouldn't do that as it would leave a lot of junk files behind and you would have no idea what/where they are. But that's just me.

Yes. That is a good point against it.

---

### Post by scheuri on 2009-04-27
> **alphacrucis2 said:**
> I don't agree. An install is just writing files to disk just like any other program does. As long as the file system software on the install CD it is using, is not faulty then it shouldn't cause any problems to files that aren't specifically being replaced. This has prompted me to try this on my test machine tomorrow as it has nothing to do till the alpha1 of Karmic comes out.

I am sorry, but I guess you do misunderstand (or I do for that matter).

He said he is NOT wanting to upgrade. Like using apt-get or a cd-rom and say "I am on intrepid, please make it jaunty with the update manager".
He wants to REINSTALL the whole thing and make a fresh install.

With a normal upgrade, you are right. Package1 will be replaced by a newer version shipped by Jaunty...no big deal.
With a new fresh installation, you just say to jaunty "hey, there is a big partition, install yourself, but do not format it before you do".

Let me make a comparison:
You have a CD worth of 8 Minuntes of Music (partition of, lets say, 8 GB). Four minutes are your main music piece (the OS) and 4 minutes is your specific music piece (your /home folder). Partitionwise or CD-wise there is no difference for these music samples. They are on the same CD.
Now, what he wants to do is...exchanging the first 4 minutes with a software (installer of jaunty) by telling it "use as much space as you want, just dont delete the data on the CD".
Where do you end up? You do not know? Exactly....:)
Maybe Jaunty needs 4 minutes and 30 seconds...so 30 seconds of the private sample are lost.

Point is...the jaunty installer does NOT care what software is already installed and will not take that into account even if you tell it NOT to format the partition you do install it on.
It does NOT upgrade the packages, it just starts to overwrite from the beginning and uses as much space as it needs and then stops and leaves the rest of the partition alone.
How much that will be and what kind of influence on the new installation that might have you have NO clue...

I do not know if I can explain it clearly in english...but...well.
Cheers
scheuri

---

### Post by presence1960 on 2009-04-27
> **alphacrucis2 said:**
> Is that actually true? What happens if you do a manual install selecting the existing partition and tell it not to format. I vaguely recall I did that on one of my machines and it worked ok.

That will only work if your /home partition is already a separate partition from the / partition. I beleieve the OP already said that is not the case. Therefore the OP must back up his data in /home and can set up a separate /home partition either thru the Manual partitioning option of the install or can set ithe partitions prior to the install with Ubuntu Live CD or gparted Live CD. Then do the install utilizing the manual option of the partitioner, making sure to set the mount point for the home partition to /home. Then migrate his/her data to the new separate /home partition.

---

### Post by MrWES on 2009-04-27
> **akkad said:**
> maaaaaaaaaaaannnnn :(, you know what i guest ubuntu should take this in consideration, or in fact ubuntu should utilise the feature of linux that a user data/config are all in one place un like windows which you dont know where the files are, so it can be a good option if a user can transfer the user directory from older to new ubuntu version.

Hrmm...what happens when you do a 'fresh' install of Windows and you format your partition? You lose your data, no? Unless you back it up. Use the upgrade feature, it works.

Bill

---

### Post by kpkeerthi on 2009-04-27
> **scheuri said:**
> 

Point is...the jaunty installer does NOT care what software is already installed and will not take that into account even if you tell it NOT to format the partition you do install it on.
It does NOT upgrade the packages, it just starts to overwrite from the beginning and uses as much space as it needs and then stops and leaves the rest of the partition alone.
How much that will be and what kind of influence on the new installation that might have you have NO clue...


And also... 
Assuming you currently have package x, y an z installed and you just let the installer overwrite the files on the same partition and this time the installer installs just x. What would happen to the files and binaries that came with y and z? You would have the files that the package manager has no clue about. Too bad.

---

### Post by alphacrucis2 on 2009-04-27
> **presence1960 said:**
> That will only work if your /home partition is already a separate partition from the / partition. I beleieve the OP already said that is not the case. Therefore the OP must back up his data in /home and can set up a separate /home partition either thru the Manual partitioning option of the install or can set ithe partitions prior to the install with Ubuntu Live CD or gparted Live CD. Then do the install utilizing the manual option of the partitioner, making sure to set the mount point for the home partition to /home. Then migrate his/her data to the new separate /home partition.


Except that I recall successfully doing this - I might be misremembering though. Will try again on my test machine tomorrow. The only issue I see is that it may leave orphan junk files around. Will attempt to install Jaunty from live CD using manual partitioning - no formatting over the top of an existing install on one partition. Obviously you can't change the file system type doing this. Will report what happens.

---

### Post by alphacrucis2 on 2009-04-27
> **kpkeerthi said:**
> And also... 
Assuming you currently have package x, y an z installed and you just let the installer overwrite the files on the same partition and this time the installer installs just x. What would happen to the files and binaries that came with y and z? You would have the files that the package manager has no clue about. Too bad.

Yes. Those packages you had installed that aren't included in the liveCD would have to be reinstalled manually even though the files would still be there.

---

### Post by akkad on 2009-04-27
i am thankful for your discussion, i can collect a lot of hints from your words and at last may be come up with a good solution for my problem, and by the way am not comparing windows to ubuntu, i just mentioned windows just to make sure that the ubuntu installation will not affect windows, and by the way windows is installed on a partition with 5GB only, this is because i installed my favorite game C&C Generals (i know its old :D) where i tried all the ways to run this game on ubuntu but i couldn't and am really waiting for the day that either this game will be able to run on ubuntu (which will avoid me from setting up this annoying 5GB partition behind) or new installable C&C Generals release that steal my attraction.

---

### Post by SentientFluid on 2009-04-27
> **alphacrucis2 said:**
> I don't agree. An install is just writing files to disk just like any other program does. As long as the file system software on the install CD it is using, is not faulty then it shouldn't cause any problems to files that aren't specifically being replaced. 

Actually you're incorrect. The install doesn't just try and locate the files to replace them with new ones. That's what an upgrade should do.  An install starts writing at the beginning and finishes where ever it finishes.

Let's assume that all the data on your hard drive is written in a linear fashion (ie first files ever written are at the beginning of the drive and the last files written, which should be files you added after install, are written closer to the end).

If the old OS, which would have to be the first files, took up 3GB of hard drive space, then your data would start at say 3.1GB.  What happens if the new OS takes up 5GB of space?  Well it overwrites any of your data from 3.1GB to 5GB so you lose 2GB of data.

And that's a very simplistic view and assumes that everything is written in a linear fashion on the disc.  We all know data isn't written like that!  Some of your user data could very well be at the front of the disc and so even more would be overwritten!

So to the OP, back up before doing anything, even an upgrade.

---

### Post by SentientFluid on 2009-04-27
> **kpkeerthi said:**
> And also... 
Assuming you currently have package x, y an z installed and you just let the installer overwrite the files on the same partition and this time the installer installs just x. What would happen to the files and binaries that came with y and z? You would have the files that the package manager has no clue about. Too bad.

The installer isn't reading the drive to see what files are already on it. Whatever doesn't get overwritten will just be ignored.

---

