---
title: "Serious Back Up Question"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by Dark7man on 2010-11-26
Hey guys,
         I've delayed this for 2 weeks already because I can't stop playing with Ubuntu :D  However, my laptop has to be sent back to HP for warranty (which ends in 2months) repair; Problem=(HDMI output related-[mobo replaced possibly?).

Here's what I want to do... My current setup is a Dual boot with Windows 7 (64bit) partitions, HP Recovery Partition, Ubuntu 10.10 (64bit) Partitions.

I want to basically take a FULL backup image of the harddrive.

I'm happy with the setup I have with my system at the minute, and I'm still half way through the transition from Windoze->Ubuntu...

I need to have a full proof backup, so if for example. I send my laptop away and it get's dropped, or the harddrive 'dies' in some other way, I could buy a new harddrive...fit it, and through some process restore the ENTIRE HD Image, so when I push the power button, everything is just like it was the day I sent it off to be repaired.

Why I ask, is this possible?  I'm curious will this be an issue with my Windows Licence? or what would You guys advise, all the applications and the variety of good, fully featured software in Linux sometimes has me stuck on which to go with!  :popcorn:

Any advice would be great... How would You do this in Linux instead of Windows? :)

Thanks in advance! :guitar:
~D

---

### Post by Grenage on 2010-11-26
You'd need to take the drive out of the computer, because you can't ghost/image a drive that's being actively used.  Clonezilla would do it.

I suppose one could boot from a live CD and ghost/image the laptop drive to an external drive.

> I'm curious will this be an issue with my Windows Licence?

Nope; no problem.

---

### Post by indytim on 2010-11-26
You will need to make images of the partitions for re-installation.  An alternative to Clonezilla is

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

The application that you can use while booted in RescuCD is:

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

Oh, I forgot (as I don't use the option myself), I believe there is a flag option so you could "smallsize" the output filesize to accomodate CDs or DVDs.

I've been using this combination as my backup platform for almost a year.  Have done recoveries in ext3, ext4 and ntfs formats.

IndyTim / DataMan

---

### Post by Savio2010 on 2010-11-26
You may visit his site [http://clonezilla.org/](http://clonezilla.org/)
Try it out

It works fine on my PC.

---

### Post by MorleyPotter on 2010-11-26
DD is a command line option or AIR for a gui, AIR should be in the repo's, dd is already installed.

BE CAREFUL! - You could wipe your drive if you get it the wrong way around.

TIP - Use GParted to identify the drives correctly, should be /dev/sda or similar for your primary drive.

Example - dd if=/dev/sda of=/dev/sdb

if - Input directory
of - output directory

I'd advise you read up on it first though.

EDIT - The principle is exactly the same for the restore, just change your drive paths

---

### Post by Dark7man on 2010-11-26
> **Grenage said:**
> You'd need to take the drive out of the computer, because you can't ghost/image a drive that's being actively used.  Clonezilla would do it.


I suppose one could boot from a live CD and ghost/image the laptop drive to an external drive.

Thats what I was thinking along the lines of a bootdisk/live cd, I have a Paragon Drive Image (FreewareVersion) boot disk, if I were to use that, will I run into problems with my Linux partitioning format? As Paragon was installed in Windows?  Or is "Format" not a factor in drive imaging?

> **Grenage said:**
> I'm curious will this be an issue with my Windows Licence?

Nope; no problem.

Ah cool :)  I was wondering, I remember years ago, I had an old packard bell machine, my harddrive died but when I replaced/upgraded my drive, and tried to restore with the "System Restore CDs" that came with my pc, the software wouldn't let me as it was asking for the serial number of my harddrive-I suspect it was the old one?

Appreciate the help thanks mate! :D

Oh-Forgot to add;
The backup will be stored on an Ext. USB HDD.

---

### Post by mickwombat on 2010-11-26
Make a new partition on the external drive slightly larger than the drive you want to back up.

Clonezilla is excellent and I've used myself for exactly this purpose.  It's a bit clunky, but works really well.  Be careful though and make sure you read everything it says to you, just to make sure you don't choose the wrong option.

You may have some issue with recloning windows onto a new drive, but hopefully not.  When I did it, windows wouldn't boot, but was just simply a case of changing a drive value or something in the ntldr file.....I think.

> Why I ask, is this possible?

Most things are possible in Linux......excluding devices that have a 'i' in front of it. ;)

Good luck

---

### Post by Dark7man on 2010-11-26
First off, thanks for the super quick replies everyone! :)

From reading everyones input would Clonzilla be a good choice, its got a GUI and with this I won't have any major problems if I'd to replace the harddrive?

I am not familiar with the popular software in Linux yet you see :)

---

### Post by Paqman on 2010-11-26
> **MorleyPotter said:**
> DD is a command line option

The problem with using dd for backups is that it wastes a lot of time copying empty space. On big drives with lots of free space you could end up taking a *lot* longer than you need to.

---

### Post by MorleyPotter on 2010-11-26
> **Paqman said:**
> The problem with using dd for backups is that it wastes a lot of time copying empty space. On big drives with lots of free space you could end up taking a *lot* longer than you need to.

Good point, I was thinking there's very little chance of anything going wrong with a DD image though.

---

### Post by Dark7man on 2010-11-26
> **MorleyPotter said:**
> Good point, I was thinking there's very little chance of anything going wrong with a DD image though.

Interesting, so are You saying a DD image, creates quite literally-an exact copy of the source drive?  Just interested to know, how each piece of software works and why... so many different pieces of software for different jobs, just trying to take it all in :)  Apoligies for so many questions...

I'm going to download and do this job with CloneZilla, I'm getting the impression its what would be good for what I need, You guys are all great, very patient I appreciate all Your help :)

That is one of my favorite things in Linux, the community, everyone works together! :)

---

### Post by Grenage on 2010-11-26
> **Dark7man said:**
> Interesting, so are You saying a DD image, creates quite literally-an exact copy of the source drive?

DD makes a sector for sector copy.  It has many uses, but it can be a lot slower than something like clonezilla.

> **Dark7man said:**
> Thats what I was thinking along the lines of a bootdisk/live cd, I have a Paragon Drive Image (FreewareVersion) boot disk, if I were to use that, will I run into problems with my Linux partitioning format? As Paragon was installed in Windows?  Or is "Format" not a factor in drive imaging?

I've not used that software, but if it makes a true image/ghost, partitions or filesystem formats should make no difference.


> **Dark7man said:**
> Ah cool :)  I was wondering, I remember years ago, I had an old packard bell machine, my harddrive died but when I replaced/upgraded my drive, and tried to restore with the "System Restore CDs" that came with my pc, the software wouldn't let me as it was asking for the serial number of my harddrive-I suspect it was the old one?

I've not seen a restore check or ask for hardware serial codes before!

---

### Post by s1wood on 2010-11-27
Make sure you have your Windows product key! 

Susan

---

