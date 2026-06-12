---
title: "I want to backup over my home network, if I can get a network going"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by cjax1 on 2007-06-26
Hi again,

This is the second time I have tried to post this. The first time I got a message that I was logged out when I hit submit new thread. *********mn *$#&&*$%##%^&.

Lets see if it works this time. I'm not typing this again. This is crazy.

I can't believe I have not been able to find anything on this forum about my problem. Is the forum's search feature broke? If I got any results at all it was all irrelevant. I used many different search terms. Never had that problem before.

Anyway, I have also been searching the internet for several days now. Been reading and trying different things but naturally I've got nothing to work. I've been trying to share folders and trying remote desktop connection between my two Ubuntu machines through my router using NFS and nothing has worked. I had no clue it was going to be this damn hard. No tutorial works. I don't even have the links to them now.

But what I want to try to do now is clone or backup my Ubuntu Breezy partition install on my laptop to a partition on the second drive in my desktop running Dapper. I can make the partition on the target drive the same size as the one I'm backing up if need be. I would like to use a live CD on the laptop to do this but I could use another Linux install in another partition like Puppy.

I also don't want something that is going to take hours. I've used dd before to go from one local drive to another but that isn't what I'm looking for. I've never got any real speed out of it. It seems it copies even the unused portions of the drive/partitions. I got dd to work and played around with some variables (don't ask me what they were now) and got it to work a little faster but it still took a long time.

Partimage seemed to be a possibility the the help page says I need boot floppies to backup over a network. My desktop does not have a floppy drive. I mean, get with the times man. There is one on the old laptop.

Even if partimage will work for me I still need to make the connection between the two computers which is baffling me. The only way for me to make a connection on the old laptop is with the wireless card (not an option with any live CD's, except Puppy, but it may eat up too much memory anyway) or my USB/ethernet adaptor. I have a couple live CD's that will configure the adaptor automatically. The Breezy live CD being one.

Is there any other backup programs like partimage that will backup over a network with a live CD only and how?

Would it be easier if I bought an ethernet crossover cable and said screw the network?

Is it possible to put a laptop 2.5 inch hard drive in a usb enclosure then connect it to my desktop to clone/backup and restore? (I can just see a whole new set of problems with that)

Maybe it would be easier to find an adaptor that will allow me to connect the laptop HD internally in my desktop then use partimage to backup/restore?

The only thing keeping the old laptop going is Breezy (it's better than anything else that'll run on it) and now they have cut off support even for synaptic so it will be a pain to install software if I ever need to reinstall. I won't even bother.

I have read about backing up the home directory so after a reinstall you don't have to start from scratch. Does this mean that all the apps I've installed will be restored if I restore my old Home directory after a fresh install? I don't care about anything else. Will all my installed programs be restored? Including any wireless drivers? If so are there any exceptions? Just exactly what does/doesn't that restore? Right now my Home directory is only about 125 MB. That should be no problem to backup over the network. If only I can get the damn computers connected. Or I could even install a CD-RW drive from another old laptop I have (the laptop has CD-ROM now) and burn the Home directory to CD. Make at least two copies.

I know this is long and there's a lot of different questions but if anyone can help me figure out the best way to go about this I would send many many thanks. If it involves backing up a partition over my home network then I will need step by step instructions. How is it I can connect to the internet so easily but I can not get two of my computers to connect over my home network? This is crazy.

My head is spinning.

---

### Post by dmizer on 2007-06-26
okay ... first of all, the forum automatically times out after a certain amount of inactivity on your account.  inactivity means: you haven't clicked on anything.  typing in a post, or a response to a post is not activity on your account.  you can remedy this one of  a few ways ... you can configure firefox to save your password and be sure to put a checkmark next to "remember me" on the signin form, or ... you can try to remember to occasionally click on something like "preview post" or "go advanced" or such.  this is fairly typical behavior for most forums.

if i recall correctly, remote desktop is extremely difficult in breezy, and not much better in dapper.  it can be done, but it's no fun.  here's a howto, but it's old and not maintained: [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

to set up nfs, check the fourth link in my sig. 

here's a good howto on backing up your system: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) it does NOT require you to create a new partition.  it can be easily adapted to make a backup of only your home directory.

you should not have to be concerned about using your router.  i think your problem is simply that you need to know how to configure the network.

i'm currently running wirelessly on knoppix live cd with an ndiswrapper driver, so running wirelessly on a live cd is not impossible.

i don't always have the best success using the forum search function either.  often times, i get better results by using google's advanced search feature: [http://www.google.com/advanced_search?hl=en](http://www.google.com/advanced_search?hl=en) with the domain field filled in as "www.ubuntuforums.com"

also, if you are looking for a how to, you can try browsing the tips and tricks section.  also try searching with the word "howto" as most how to titles have the word "howto" in them.  so search parameters like ... howto backup and restore will return results on the howto i posted earlier for backing up your system.

think i've covered most everything.  if you run into trouble, post in the howto threads and people will be happy to help.  otherwise post here.

---

### Post by cjax1 on 2007-06-26
OK, many many thanks for your reply.

Thanks for the search tip. It just seems like it's this forum I have the most trouble with getting signed out. Maybe other forums do the same but this one has a shorter time out maybe. I wrote this reply a little after 10AM here, now it's a little after 1PM. I hit the post reply button and I got a message saying the forums are off line. This is absolutely nuts. I know this stuff happens but I never never never had this much trouble with any other forums. Ever. Usually they are taken off line late at night, unless it wasn't something expected, or it's late at night where they are. But still, I never had so many problems just trying to post something on a forum. Thankfully I don't have to that often. I am very sorry for all my ranting. I love Ubuntu and this community, I think it's the best, but the forums have some technical issues for sure. From now on I'm writing everything in a text editor, as I'm doing now, then when I'm ready to post I'll copy and paste it. Then I won't loose EVERYTHING I've written when the forums don't work. Maybe this will help someone else.

I was wondering dmizer what version of Knoppix live CD are you using? Does it have ndiswrapper included or did you have to remake the CD? I have an older version but I'm pretty sure it doesn't have ndiswrapper pre-installed.

I was playing with remote desktop again last night on both computers. On the laptop I typed the code supposedly to access my desktop and the laptop actually tries to access itself. I thought there was a file or something that I had to make sure that 127.0.0.1 was not binded to something or other and now I can't find the info. If you have any ideas on that I'd appreciate it but I'm not going to dwell on that too much right now.

I appreciate the links. Especially the How to: Backup and restore your system. That looks great. I bookmarked it. I'll get into it more tonight. I think I'll try it on my desktop and do an actual restore to see if it works for me. I don't care if I hose my desktop install, I can redo that. But not Breezy. At least without pulling my hair completely out. I just kind of skimmed through it for now but it looks like to restore my system, lets say I put in a new HD, I would still have to run the Breezy install disc first, then do my restore from my backup to restore my system to where it is now? Or can EVERYTHING be restored from the backup itself without running the install disc? That's what it looked like to me. Am I right or wrong?

I'll have to work out the details but this is giving me new hope.

OK, it's down to business. I'll work on it again tonight. Now I may just try the shared folders again to transfer my backup off the laptop. I may need help with that but I think I'll save that for a new thread.

I may post back here if I have any more questions about the Howto. Thanks again.
:D

---

### Post by dmizer on 2007-06-26
> **cjax1 said:**
> I was wondering dmizer what version of Knoppix live CD are you using? Does it have ndiswrapper included or did you have to remake the CD? I have an older version but I'm pretty sure it doesn't have ndiswrapper pre-installed.
i'm using the most recent version.  but ndiswrapper has been a part of knoppix for a very long time.  i know i made use of it in 3.8 or so.

> **cjax1 said:**
> I just kind of skimmed through it for now but it looks like to restore my system, lets say I put in a new HD, I would still have to run the Breezy install disc first, then do my restore from my backup to restore my system to where it is now? Or can EVERYTHING be restored from the backup itself without running the install disc? That's what it looked like to me. Am I right or wrong?
that howto is for a complete backup and restore of your entire system, so yes ... everything.  upon using the restore, you will have a fully functional os, so no you do not need the breezy cd.  but you can adapt the howto for just backing up your home directory.   following the howto, the command would look like this:
```
tar cvpjf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /[COLOR="Red"]home/cjax[/COLOR]
```
then to restore:
```
tar xvpfz backup.tgz -C /[COLOR="Red"]home/cjax[/COLOR]
```
and then there is no need to follow the link for restoring grub.

---

### Post by cjax1 on 2007-06-26
Thank you. You've been a big help. I'm going to start working on this later tonight. So I'm going to take my time on this to test out everything to make sure I don't screw something up.

---

