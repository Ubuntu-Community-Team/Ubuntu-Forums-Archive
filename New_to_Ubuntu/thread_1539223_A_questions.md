---
title: "A questions"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by TaintedMess on 2010-07-26
Ok after using Ubuntu on a old PC for a few months I'm about ready to install it on my main proper PC but a few questions have occurred to me.

My main PC has 3 Physical drives 2 internal and 1 external under windows 1 of the internal drives is partitioned into 2 drives so under explorer I have 4 drives showing.

My intention is to replace XP which is installed on one of the partitions with Ubuntu.

My question is how will Ubunto handle the remaining partition and the other 2 physical drives will it see them and let me use them or do i need to do something to get access to them?

Also how dose sharing folders work with Ubuntu under windows i have a few folders shared on my home network so i can get at the files from my PS3 and laptop can i still do this with Ubuntu?

Cheers

---

### Post by rolnics on 2010-07-26
> **TaintedMess said:**
> My question is how will Ubunto handle the remaining partition and the other 2 physical drives will it see them and let me use them or do i need to do something to get access to them?

Ubuntu will handle as separate partitions, but it won't display them like windows, instead of drive letters it will display them as sda1 for the 1st partition on the first hard drive like C: in windows and so on. They usually appear under the removal devices section, unless you want them to automatically mount on boot.


> **TaintedMess said:**
> 
Also how dose sharing folders work with Ubuntu under windows i have a few folders shared on my home network so i can get at the files from my PS3 and laptop can i still do this with Ubuntu?

Cheers

I assume you have a router? There is a program called samba in ubuntu that will make sharing available. I'm not sure how the PS3 would be handled.

One last thing, and this is the most important, backup your data before you start installing.

---

### Post by TaintedMess on 2010-07-26
> **rolnics said:**
> Ubuntu will handle as separate partitions, but it won't display them like windows, instead of drive letters it will display them as sda1 for the 1st partition on the first hard drive like C: in windows and so on. They usually appear under the removal devices section, unless you want them to automatically mount on boot.

Cheers for the quick response. 

Sounds relatively simple my biggest concern was that i would have to format the drives which was something i Don't want to do.


> **rolnics said:**
> 
I assume you have a router? There is a program called samba in ubuntu that will make sharing available. I'm not sure how the PS3 would be handled.

Yea I do ill look into samba thanks.  I think the PS3 currently connects through windows media server Its only used for streaming movies through so worst comes to worst ill just need to rig up a connection for the laptop to the TV and do it that way.

> **rolnics said:**
> 
One last thing, and this is the most important, backup your data before you start installing.

Yea that's where the 2 internal drives and the external comes in the second internal has all my music, photos, moves and stuff on it and the external has copy of the most important of those on it.

Would i be better to disconnect these 2 drives during the install process do you think just in case?  I'm not overly bothered about what's on the partitioned drive as one half is the OS (which is currently virus infected so due for nuking any ways) and the other is just programs and drivers for reinstalling windows so not really required once i make the jump to Ubuntu.

---

### Post by -kg- on 2010-07-26
OK, first things first:

> **TaintedMess said:**
> My question is how will Ubunto handle the remaining partition and the other 2 physical drives will it see them and let me use them or do i need to do something to get access to them?

Ubuntu will be able to detect and use NTFS or FAT16/32 partitions.  There should be no problem with that at all.  It is Windows that needs special "drivers" to be able to detect and read Linux partitions.

> **TaintedMess said:**
> Also how dose sharing folders work with Ubuntu under windows i have a few folders shared on my home network so i can get at the files from my PS3 and laptop can i still do this with Ubuntu?

Yes, absolutely.  Linux has been used for years in networking and as servers, and should network with other computers in the network.  Have you tried networking your old computer with your network as it exists?  If not, you should include it in your network and experiment a bit with it.  You should be able to share folders and files the same as with your laptop and PS3.

Obviously, it uses different networking software than Windows (Samba), so you should be familiar with Samba and know how to set it up before making the big switch.  It will save a lot of headaches and delays in accessing your files from the laptop and PS3.  Install Samba on your old computer and experiment with it.  Make sure you know how to set it up and use it beforehand.

> **TaintedMess said:**
> My intention is to replace XP which is installed on one of the partitions with Ubuntu.

First consideration is that you have sufficient room to install Ubuntu and install the software that you'll need.  How large is your XP partition?  My personal thoughts are that you will need *at least* 10-15GB for your installation.  More would be nice.  If you have at least that...

I will assume that you know that you can't install Ubuntu in the existing XP partition, unless you're planning on installing via Wubi.  My suggestion is that, when you're absolutely ready (and absolutely sure that you want to replace XP and not dual boot), that you first boot to the Live CD desktop, select "System/Administration/GParted (or Partition Editor)", and delete the XP partition.  Read the information on the page(s) at the link in my signature block.

Then, when you elect to install Ubuntu, select either "Install to largest contiguous free space", or if you want to install a separate "/home" partition or other special installation, select "Manual Partitioning".  Using "Manual partitioning," you will have to create and format your own partitions, and mark their mount points.  Again, for more information on creating and formatting partitions, read the information on the page(s) at the link in my signature block.

Since you have another partition on sda (your primary hard drive), you definitely don't want to select "Install using entire hard drive," since that will erase your other partition, and you don't want "Install side by side," since there won't be anything to install side by side with.  I'm not sure, since I've never installed that way (I always use Manual partitioning), but "Side by side" likely will be grayed out, anyway.

> One last thing, and this is the most important, backup your data before you start installing.

+1 !!

If you read through the pages at the link in my signature block, it will say this over and over.  Partitioning is fairly safe, and what I said to do is the safest method to use, but it is not absolutely safe!  At a minimum, back up your primary hard drive information to the external.  Your secondary also, if you have room.  Then ***_disconnect the external drive before installation_*** so there can be no accidents with it!

I hope this hasn't been TMI, but take it from me, it comes from long, (***very***) hard experience.  If you have any questions, ask! :)

<Edit>

> Sounds relatively simple my biggest concern was that i would have to format the drives which was something i Don't want to do.

From the above, obviously you ***will*** have to do some limited formatting.  You cannot install Linux (Ubuntu) in a Windows partition, unless you install it under Windows using Wubi.  If you replace XP, you will have to minimally have a "/"(root) and /swap partitions in which to install Ubuntu.  The root partition will have to be formatted to ext3/4 and the swap to swap formatting.

Following my instructions will get you through that.

---

### Post by -kg- on 2010-07-26
OK, just read through your second post, so...:

> **TaintedMess said:**
> Sounds relatively simple my biggest concern was that i would have to format the drives which was something i Don't want to do.

Answered in my post above.


> **TaintedMess said:**
> Yea I do ill look into samba thanks.  I think the PS3 currently connects through windows media server Its only used for streaming movies through so worst comes to worst ill just need to rig up a connection for the laptop to the TV and do it that way.

Like I said, check out Samba on the old computer and learn how to set it up before installation on your main squeeze.  That way, it'll almost be seamless.

> **TaintedMess said:**
> Yea that's where the 2 internal drives and the external comes in the second internal has all my music, photos, moves and stuff on it and the external has copy of the most important of those on it.

You should be in like flint, then, but I'd still back up the slave internal to the external first.  Then...

> **TaintedMess said:**
> Would i be better to disconnect these 2 drives during the install process do you think just in case?  I'm not overly bothered about what's on the partitioned drive as one half is the OS (which is currently virus infected so due for nuking any ways) and the other is just programs and drivers for reinstalling windows so not really required once i make the jump to Ubuntu.

Oh!  If the second partition is only a re-installation partition, then that makes the installation infinitely simpler (unless you wanted to create that separate "/home" partition).  You can use the procedure I mentioned above to remove all the partitions from your primary hard drive and install, or you can select the "Use Entire Hard Drive" selection from the partitioning menu in the installer, and it will erase them for you.  For that matter, you can erase them from the manual partitioner.  Just make sure you select the right drive (from what you said, it should be the only drive with two partitions).  It should be "sda".

At any rate, I wouldn't suggest removing the secondary hard drive.  The installer will auto-detect the partition on it and include it in the "fstab" file, which will cause those partitions to show up and be included for mounting.  I ***would*** unplug the external, however.  As rolnics said, when you plug the external in after installation, it will show up under "Removable Media" and be automatically mounted upon hot plugin or rebooting with it connected.

---

### Post by rolnics on 2010-07-26
> **TaintedMess said:**
> Cheers for the quick response. 

Sounds relatively simple my biggest concern was that i would have to format the drives which was something i Don't want to do.


Like -kg- has said installing a new os is always going to involve some formatting. 

> **TaintedMess said:**
> 
Yea I do ill look into samba thanks.  I think the PS3 currently connects through windows media server Its only used for streaming movies through so worst comes to worst ill just need to rig up a connection for the laptop to the TV and do it that way.


Hold on, before you get into samba, if you just want to stream audio/video to your PS3 then there are alternatives. When I mentioned samba as I thought you were looking at data sharing and other forms of sharing including say a printer. If media is the only thing you want to share then take a look at mediatomb. There's a [howto here]("http://ubuntuforums.org/showthread.php?t=650020"), also [this might be worth reading]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/919763.html"), if you have problems.

> **TaintedMess said:**
> 
Yea that's where the 2 internal drives and the external comes in the second internal has all my music, photos, moves and stuff on it and the external has copy of the most important of those on it.

Would i be better to disconnect these 2 drives during the install process do you think just in case?  I'm not overly bothered about what's on the partitioned drive as one half is the OS (which is currently virus infected so due for nuking any ways) and the other is just programs and drivers for reinstalling windows so not really required once i make the jump to Ubuntu.

If I had replied sooner before -kg- ;) Then I was going to suggest you remove the external, along with the internal drives that weren't need for install. But -kg- has a good point that I hadn't thought of....that's why I'm still learning! fstab you'll see this mentioned in linux forums, is a very confusing file to us who are starting out in linux (I include myself in that!) but it tells the linux install everything about the drivers connected and how to treat/use them. 

What I do is boot using the live-cd use gparted to ascertain the drives and their partitions and then go for the install. Or even pre-partition the area I want to use, one thing that I would suggest is go for a separate /home it saves so much hassle later!

---

