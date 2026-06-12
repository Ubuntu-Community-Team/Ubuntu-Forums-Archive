---
title: "BIG hard drive space problem"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by NolanVE on 2010-06-24
Alright, I'm a complete noob to this and just downloaded Ubuntu yesterday because Windows was being... Windows. 

Anyways, the Disk Usage Analyzer says I have 168.4 GB out of my 250GB hard drive while the file system basically says I have 0 Bytes for some reason and anytime I try to download anything it doesn't work...

Help?

---

### Post by warfacegod on 2010-06-24
How did you install Ubuntu (if you did, could be live after all)? Wubi (Ubuntu inside Windows), dual boot (Ubuntu next to Windows) or no Windows at all?

---

### Post by NolanVE on 2010-06-24
> **warfacegod said:**
> How did you install Ubuntu (if you did, could be live after all)? Wubi (Ubuntu inside Windows), dual boot (Ubuntu next to Windows) or no Windows at all?


Yeah, I think I used Wubi and I have a dual boot to Windows but Windows is practically unusable right now for some reason...

---

### Post by warfacegod on 2010-06-24
My knowledge of wubi is limited to knowing that it is not intended to be a permanent install. It's really just for trying Ubuntu and that's it.

Your best long term option here is to get Windows working better so that you can resize it and create a separate partition for Ubuntu. Or even better, in my opinion, do away with Windows entirely.

If this appeals to you, let us know and we'll get you set up.

---

### Post by NolanVE on 2010-06-24
Yeah, I would love to just get rid of Windows entirely and just stick with Ubuntu.

---

### Post by Paqman on 2010-06-24
> **NolanVE said:**
> Windows is practically unusable right now for some reason...

Did this start before or after you installed Ubuntu?

---

### Post by NolanVE on 2010-06-24
It worked once after I installed ubuntu, now it doesn't the last time I checked.

---

### Post by warfacegod on 2010-06-24
> **Paqman said:**
> Did this start before or after you installed Ubuntu?

> ...because Windows was being... Windows.

Looks like before, hoss.

---

### Post by NolanVE on 2010-06-24
Yeah, Windows was messing up before Ubuntu, after I downloaded Ubuntu, it worked once and now it's pretty much dead.

Soo, Is there away I can get rid of Windows completely and Just have Ubuntu on my computer like wa rface said? 

I'm also assuming that will fix my hard drive issue.

---

### Post by Paqman on 2010-06-24
> **NolanVE said:**
> 
Soo, Is there away I can get rid of Windows completely and Just have Ubuntu on my computer like wa rface said? 


Sure, boot up into the LiveCD and install it, telling it to wipe the whole hard drive in the process.

---

### Post by warfacegod on 2010-06-24
You'll want to make certain you have a backup of *all* of your important data files. Videos, docs., music. Get everything because this will destroy what is on your HDD. If you don't have any backups, you should be able to get your files using the LiveCD.

01. Boot into LiveCD and select Try Ubuntu.

02. Go to: System> Admin.> Gparted> delete all partitions (Have a backup First!). Click Apply.

03. Now right click the unallocated space and select New. Make this partition 10 - 15 GB. Set it to be formatted as ext4. It's your choice on size but this one will be for your OS so it doesn't need to be all that big.

04. Repeat step 03. but this time make the size very big. Basically, size it so that there are only a few GB left. Mark this also as ext4.

05. Click Apply.

Back with more instructions shortly.

---

### Post by NolanVE on 2010-06-24
> **Paqman said:**
> Sure, boot up into the LiveCD and install it, telling it to wipe the whole hard drive in the process.

nvm

---

### Post by warfacegod on 2010-06-24
> **NolanVE said:**
> Once again, Complete noob here.

Not exactly too familiar on how to boot up into "LiveCD" xD

Put CD in tray. Restart computer.

---

### Post by Paqman on 2010-06-24
> **warfacegod said:**
> Put CD in tray. Restart computer.

If this doesn't seem to work you might need to tell your machine to boot from the CD instead of the hard drive. Look out for little messages about how to get into boot settings or BIOS when you first power on, and then make sure it's set to boot from the CD first.

---

### Post by NolanVE on 2010-06-24
Alright so my CD with the ubuntu-10-1.04-desktop-i386.iso is what needs to be put in the tray and restarted?

just want to make sure before I restart haha

Thanks for dealing with my complete noobness right now btw.

---

### Post by warfacegod on 2010-06-24
Okay continuing from post #11.

I forgot to mention that the first two partitions are going to be "Primary Partitions"

The remaining unallocated space is going to be swap. This should only be equal to or somewhat greater in size than the amount of RAM you have.

06. Still like step 03. except this time it will be an *Extended* partition. Click Apply.

07. Yet another partition. Right click the Extended partition you just created and create a *Logical* partition as big as will fit inside the Extended partition. Format this one as linux-swap. Click apply.

---

### Post by warfacegod on 2010-06-24
Now once all of that is done comes the install process. Assuming Gparted "Completed All Operations Successfully", close it.

08. Double click the "Install Ubuntu" on the desktop. It will take a moment to load. Once it does, you'll want to set your keyboard layout, timezone, language. Most of the time the Default selection is fine but make sure you are getting what you want.

09. Now you are going to want to select "Specify Partition Manually".

10. Right click sda1 and select "Change". In the Window that pops up, select "Use as ext4..." Be certain that the check box for formating is UNCHECKED. Mark as /

11. Select sda2. The steps are the same as in step 10. but this time Mark as /home

12. The remaining sda whichever one has the *highest* number (I *think* it should be sda4) select "Use as linux swap". You may need to mark as /swap as well. I can't remember for sure, it's been so long since I even bothered to have a swap partition.

13. Be certain none of the partitions have a check to be formatted. formatting would be redundant since we've already done it with Gparted. Now click Continue.

14. You should be able to take it from here. It will ask for username and password and what not. I recommend Selecting "Ask for my password during loggin" *Not* the "...and to decrypt my home folder" option.

---

### Post by Paqman on 2010-06-24
Btw, warfacegod's instructions for setting up partitoins manually are all good, but if you want you can just tell the installer to do all the partitioning for you. 

When you get to the partitioning step in installation just select the option for Ubuntu to "use the whole drive". It'll wipe Windows and automatically set up the partitions it needs. It's a pretty basic setup, but totally usable.

---

### Post by warfacegod on 2010-06-24
> **Paqman said:**
> Btw, warfacegod's instructions for setting up partitoins manually are all good, but if you want you can just tell the installer to do all the partitioning for you. 

When you get to the partitioning step in installation just select the option for Ubuntu to "use the whole drive". It'll wipe Windows and automatically set up the partitions it needs. It's a pretty basic setup, but totally usable.

And if there are issues with the OS in the future, all of the data *and* settings will be safe and cozy if they're sitting on a separate /home partition.

---

### Post by Paqman on 2010-06-24
> **warfacegod said:**
> And if there are issues with the OS in the future, all of the data *and* settings will be safe and cozy if they're sitting on a separate /home partition.

Indeed, I always use a separate /home partition. But it's not essential and if you're finding the partitioning process at all confusing, i'd just skip it for now. You can always come back to it later.

---

### Post by RavensKrag on 2010-06-24
No offense, but your partitioning suggestion looks a little off.  Why is the swap partition in an extended partition? Also, the swap should be the first partition on the drive, so that it is placed on the fastest sector of the disk.  Or so I have heard.  If there are already 2 or more partitions on a disk, then the entire linux installation would be better off in the extended partition, IMO.  Still, the extended partition should be completely unnecessary if NolanVE plans to wipe windows off of his hard drive.

Thus, the partition order would be
swap
root filesystem (\)
\home

Also, I believe that it would be simpler to use the ubuntu installer to partition the drive, as I believe it uses gparted as a backend anyway.  It would cut down on steps and make the process a little simpler.


An additional note to the novice linux user: if you ever have to reinstall ubuntu, simply reinstall using same CD, but keep all the partitions in place and only reformat the partition which holds the root filesystem.  As the other two have already said, having your \home directory on a separate partition is very useful for this reason.  Also, this makes upgrading to new versions of Ubuntu easier.

---

### Post by warfacegod on 2010-06-24
That is absolutely backwards, swap should always be at the end of the drive and / should be in the front. Having / at the end would greatly increase HDD seek time and make the entire OS slower. Boot time is also likely to suffer with / at the end. Swap should always be the least used partition, hence in the back. 

As for it being in an Extended/Logical partition, if left to it's own devices, that's exactly how the Ubuntu installer would create it.

> Also, I believe that it would be simpler to use the ubuntu installer to partition the drive, as I believe it uses gparted as a backend anyway. It would cut down on steps and make the process a little simpler.


This is true but the Gparted front end is much easier to use and understand than the front end that Ubiquity uses. It is also faster to use Gparted because the system will only need to have Gparted in RAM and not Ubiquity as well. In a Live environment, RAM is already at a premium because the OS itself is sitting in RAM and not on the hard drive.

---

### Post by NolanVE on 2010-06-24
Alright I put the CD in the tray and restarted. My Boot order is set to boot from the CD Rom so thats not the problem. Gah.

---

### Post by warfacegod on 2010-06-24
> **NolanVE said:**
> Alright I put the CD in the tray and restarted. My Boot order is set to boot from the CD Rom so thats not the problem. Gah.

I assume this is the same disc you used to install via Wubi?

---

### Post by NolanVE on 2010-06-24
Yes, I put the Iso file on the disc and I remember restarting it before and it didn't do anything so I had end up doing it on Wubi in windows.

---

### Post by warfacegod on 2010-06-24
> **NolanVE said:**
> Yes, I put the Iso file on the disc and I remember restarting it before and it didn't do anything so I had end up doing it on Wubi in windows.

Did you burn the disc as an .iso or simply put the file onto the disc? There's a difference. Burning the file to the disc won't work, it needs to be done as an.iso burn.

---

### Post by NolanVE on 2010-06-24
Hmm, im pretty sure I did with an iso burner. Let me try burning it on Brasero.

---

### Post by OneMixDJ on 2010-06-24
> **RavensKrag said:**
> 
Thus, the partition order would be
swap
root filesystem (\)
\home


Sorry, but I've never had to install any distro this way; nor have I seen any true benefit to it. 

Swap is always located to the rear in my installs and I've never had a problem; even with my old machines.

---

### Post by Paqman on 2010-06-24
> **NolanVE said:**
> Yes, I put the Iso file on the disc and I remember restarting it before and it didn't do anything so I had end up doing it on Wubi in windows.

When you open the disk and look at the files, what do you see? One big .iso file, or a bunch of folders? 

If it's the former, you didn't quite burn it right. You need to burn the .iso as an image, not as data. You can get instructions how to do that [here]("http://www.ubuntu.com/desktop/get-ubuntu/download").

> **RavensKrag said:**
> No offense, but your partitioning suggestion looks a little off.  Why is the swap partition in an extended partition? Also, the swap should be the first partition on the drive,

> **warfacegod said:**
> That is absolutely backwards, swap should always be at the end of the drive and / should be in the front.

Guys, you're off topic arguing over confusing trivialities, which is no use to the OP. If you want to debate this issue, i'd suggest you start a thread elsewhere.

---

### Post by warfacegod on 2010-06-24
> Guys, you're off topic arguing over confusing trivialities, which is no use to the OP. If you want to debate this issue, i'd suggest you start a thread elsewhere.

You don't think it's confusing for the OP to have someone suggest something different than what has already been put forth without answering it and explaining why it isn't a good idea?

---

### Post by Paqman on 2010-06-24
> **warfacegod said:**
> You don't think it's confusing for the OP to have someone suggest something different than what has already been put forth without answering it and explaining why it isn't a good idea?

Both of you are wrong, it makes no real difference on a modern drive where you put it.

---

### Post by NolanVE on 2010-06-24
nm

---

### Post by warfacegod on 2010-06-24
Almost but not quite. sda1 should be 10 - 15 GB

sda2 should be the really big one

---

### Post by NolanVE on 2010-06-24
[IMG]http://i47.tinypic.com/20s9jph.png[/IMG]

Thats more like it?

---

### Post by warfacegod on 2010-06-24
Yup! Now the Extended/Logical partition for swap and your in good shape.

---

### Post by NolanVE on 2010-06-24
Alright, I'm kind of confused about the size of the Extended partition, I make it the same amount as my RAM? The logicial partition is just what is left?

---

### Post by warfacegod on 2010-06-24
The extended should be as big or bigger than you RAM. The Logical partition will be made inside the Extended partition filling the space you created in the Extended partition. To make your life simple, use the rest of the unallocated space for Extended.

---

### Post by NolanVE on 2010-06-24
> **warfacegod said:**
> The extended should be as big or bigger than you RAM. The Logical partition will be made inside the Extended partition filling the space you created in the Extended partition. To make your life simple, use the rest of the unallocated space for Extended.


Alright by "filling the space you created" you mean just use however much  space is left for the partition?

---

### Post by warfacegod on 2010-06-24
> **NolanVE said:**
> Alright by "filling the space you created" you mean just use however much  space is left for the partition?

It should look something like this. Right click the unallocated space> New Extended> right click that Extended partition> New Logical partition> Use as linux-swap

---

### Post by NolanVE on 2010-06-24
Alright it's installing, Thanks a lot  warface! (and everyone else that had input)

---

### Post by warfacegod on 2010-06-24
Sure thing!:biggrin:

Let us know how it goes.

---

