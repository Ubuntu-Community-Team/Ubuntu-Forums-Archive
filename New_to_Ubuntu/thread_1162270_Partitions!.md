---
title: "Partitions!"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by gumblina on 2009-05-17
Hi,

Could somebody check my partitions? I installed ubuntu a little while ago and I have a dual boot for XP too, and its working fine, but I'm worried that my partitions are all wrong. It looks a bit messy and I also want more storage on the ubuntu side.
I have 7gigs space in my home folder, but I have a 72gig thing called 'media'. I'm not sure what it is, but I think its part of XP. As you can tell, I barely know what I'm doing, and I don't want to mess with it unless I ruin it completely!

I've attached a screenshot of my partition manager. Any help anyone could give me would be much appreciated :KS

---

### Post by whoop on 2009-05-17
Well you won't get a beauty award but there's technically not really something wrong about that. The 72 Gig thing is a ntfs (or windows) partition. You do not seem to be booting from that (ever) so you can probably see that as a second drive (besides C:) when you are running windows xp.. 

So:
sda1: probably something the manufacturer put on there (maybe its the contents of the windows xp cd, cause it's pretty big. It's most likely some kind of recovery partition (use for troubleshooting (windows)). I can't see how much data is on there cause it isn't mounted in your screenshot, but it's not that important.
sda2: probably windows xp (at least you seem to boot from it)
sda7: your linux home partition
sda6: your linux root partition
sda5: your linux swap partition
sda3: probably a (second) windows partition

To resize partitions (what you will need to do if you want bigger ubuntu), make sure you defrag windows as much as possible (windows partitions really fragment over time and resizing them without defragging can get nasty). So your C: drive and the other one (I can't know what windows will be calling it when you boot). I even boot windows in safe mode when I partition to make sure I have less processes running (so I can defrag even more).

---

### Post by gumblina on 2009-05-17
thanks for the reply! sda3 is my d: drive on xp, i don't know why I didn't get that before! I've defragmented both of them now. I want to resize sda3 and use the spare space for sda7. Is it ok to unmount them so I can resize them? I don't understand how I can unmount sda7 so I can resize it if I am on it, if you know what I mean.

---

### Post by ranch hand on 2009-05-17
You should do any partition manipulation from your live cd.  This is the safe way to do that.

You should not have any problem unmounting anything that way either.

Your first partition is only of use to you if you have the instalation CD for Windows.  It may or may not work if you do have the CD.  If you do not have the CD, you really don't need that partition at all.

Keep in mind when I say that, that I don't think you need the Windows partition either (a little hostility problem that I have).  But I really do not think you need that first partition.  One problem with removing it is that it will change what you need in grub to boot so I would not delete it I would just shrink it down.  It appears to be empty anyway.

Gparted is fairly self explainatory in resizing and moving.

I think you are going to have a problem using sda3 for space for sda7 because 7 is a logical partition in sda4 (extended partition).

What is on sda3?  If we knew that we could move on.

---

### Post by gumblina on 2009-05-17
the first partition was called windows vista loader when I was installing ubuntu, and it comes up on the grub menu too. I don't have vista (i've got a samsung nc10 netbook - it came with xp and I don't think it could even do vista anyway). I'm not sure if its necessary to be able to load xp. 
Tbh I'm quite tempted to get rid of windows entirely. I only kept it because it made me feel a bit safer, like there's a backup to go to. I've had ubuntu for about a month now tho, and I've only gone into xp once or twice since then.
What would be the best way to go about getting rid of it, so I just have ubuntu? I think it would make it less complicated all round to just have one OS on here!

eta: I'm not really sure whats on sda3, it looks like windows system/samsung recovery stuff, so I'm a bit wary of doing anything to it!

---

### Post by whoop on 2009-05-17
> **gumblina said:**
> 
eta: I'm not really sure whats on sda3, it looks like windows system/samsung recovery stuff, so I'm a bit wary of doing anything to it!
Don't you think sda3 is your d: partition in windows?

---

### Post by gumblina on 2009-05-17
it is, but that is all that is on it. i've attached a screenshot. the first two folders have a file called update.exe in them.

---

### Post by whoop on 2009-05-17
> **gumblina said:**
> it is, but that is all that is on it. i've attached a screenshot. the first two folders have a file called update.exe in them.

sheesh, and thats nearly 20gigs? Is it making system snapshots or something.... Simple recovery tools don't require that much space.

---

### Post by gumblina on 2009-05-17
When I first got my netbook and went through the setup process, it included a recovery thing from samsung. It split the drive in two and made c: and d:. every so often it said it was backing everything on c: on to d:. I don't have any of my actual files, e.g. photos, on d: anymore, so all thats left seems to be this recovery program. Really, I don't know what its doing, which isn't great!
I kinda want to get rid of windows now I'm comfortable with using ubuntu (even tho I know naff all about the technical stuff, but I'm trying to learn!).

eta: the samsung recovery folder has four files, which are 4gb each. I don't know what they are tho!

---

### Post by whoop on 2009-05-17
> **gumblina said:**
> When I first got my netbook and went through the setup process, it included a recovery thing from samsung. It split the drive in two and made c: and d:. every so often it said it was backing everything on c: on to d:. I don't have any of my actual files, e.g. photos, on d: anymore, so all thats left seems to be this recovery program. Really, I don't know what its doing, which isn't great!
I kinda want to get rid of windows now I'm comfortable with using ubuntu (even tho I know naff all about the technical stuff, but I'm trying to learn!).

I really wouldn't know what to advice in this case. I don't know this tool or it's importance for windows xp.
If I knew sda3 was useless I would copy everything from D: to C: and completely remove sda3. Then you can comfortably resize ubuntu.

---

### Post by gumblina on 2009-05-17
Thanks for trying to help :) 

I think I'm probably going to get rid of windows completely anyway now, I can't be arsed with dual boot and complicated partitioning stuff when I always use ubuntu now anyway! Hopefully I won't turn my computer into a doorstop in the process :)

---

### Post by whoop on 2009-05-17
> **gumblina said:**
> Thanks for trying to help :) 

I think I'm probably going to get rid of windows completely anyway now, I can't be arsed with dual boot and complicated partitioning stuff when I always use ubuntu now anyway! Hopefully I won't turn my computer into a doorstop in the process :)
Well in that case maybe just start with removing sda3... You'll get allot of diskspace for ubuntu, with a reasonable chance windows xp wasn't even really using it in the first place (and therefore wont miss it)  --> win win (a hate that frase ;) )

---

### Post by ranch hand on 2009-05-17
I don't know what you have on the Windows partition or your Ubuntu partition so it is kind of hare to answer your question.

I would burn any files you want to keep to CDs or other backup media.

Then I would boot from your Live CD and delete all of your partitions, if what you want is just Uuntu (I think is a good choice but I am not you).

I would then create a primary partition of about 30Gb at the start of your drive to use as a saftey net (more later).

I would then use the rest of the drive as 1 Extended partition.  Put a 3-5Gb partition at the very end of that and format it to swap.  Make a partion of 20Gb at the beginning of your extended partion and format it for what ever version you are putting on (judging from your current partitions this would be ext3).  I would then make another partition next to that one of about 40Gb and format it the same.

When you install use the manual partition meathod when you come to the partitioner in install.  Click on the 20Gb partion and hit edit.  the size is fine the format is fine you just need to pick a "mount point" and you want "/" (root).  Click OK (or what ever it is) and that will take you back to the partioner.  Click on the 40Gb partition and do the edit thing.  Pick "/home" for the mount point.

Then finnish your install.  This will give you a root and a home partition.  If you screw up something you can reinstall your root and probably save all your home files (backup highly recommended).  You will have free space between /home and swap for later use.

You can also do another install on that 30Gb Primary partition.  This will give you a simple install that I would use for trying things out on so that you do not screw your "production" installation.  You can also put a backup file on there to save vital stuff from your main OS.

Your free space out to be big enough for 2 more Linux OSs.  You can try out others there and new releases there rather than mess with what you have gotten working right for you.

---

