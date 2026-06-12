---
title: "Will this partition scheme work?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Longstreet on 2011-03-26
Noob here, with an Aspire One D255, N455 Atom, 1G RAM, 160G HDD. My plan is to partition the HDD so that I have one 40G partition for Win 7 Starter, one 40G for Ubuntu, and the remainder for NTFS storage so both OS can access. After comparing what Win Disk Management tells me with what GPartEd tells me, I'm not sure what I'm going to be allowed to do.

[IMG]http://i659.photobucket.com/albums/uu314/Longstreet308/Screenshot.png[/IMG]

If I understand this right, I've got sda1 and sda2 as Restore partitions that I won't/can't fool with. sda3 is where Win 7 and the other pre-installs live, in 23.41G. I'll increase that to 40, then create another partition of 40G for Ubuntu, and finally a Storage partition of ~56G (sda4 and sda5?), all out of the ~136G I have on the HDD.

Am I seeing this correctly? Is my partition plan sound?

And what do you suppose the 1.84M unallocated space is?

Thanks for any help. I'm so close to pulling the trigger on this. Just want to make sure I know what I'm doing.

---

### Post by samcot on 2011-03-26
That sounds like a reasonable plan. And you can always change it later.
 
I'm not recommending this, but I deleted my restore and "tools" partitions to free up more space, and I tidied up my partitions with GParted before the install. Of course I created recovery discs for Windows ahead of time (and tested them, too). You don't have to do this, though. I wouldn't hesitate using that little bit of unallocated space you have.  
 
When you get to partioning, do you plan on creating two Linux partitions, one for "/" and the other for swap?

---

### Post by deconstrained on 2011-03-26
A slightly more convenient way of doing it would be to allow a 10-15 GB for Ubuntu root and use the rest as a home partition.

Note, however, that you cannot have more than 4 primary partitions. You need to use extended partitions for Linux if you want to slice up the hard drive any further, or create a logical volume group on the remaining free space for Linux (more flexible and versatile, but more complicated).

---

### Post by Miljet on 2011-03-26
I hope that you understand that you can only have 4 primary partitions, and you are already using 3 of them. After shrinking sda3 (using Vista's disk tools), you will need to create an extended partition using all free space. You can then create logical partitions within the extended partition that you have created. And don't forget to make a swap partition of at least 1G.

---

### Post by Longstreet on 2011-03-26
> **samcot said:**
> That sounds like a reasonable plan. And you can always change it later.
 
I'm not recommending this, but I deleted my restore and "tools" partitions to free up more space, and I tidied up my partitions with GParted before the install. Of course I created recovery discs for Windows ahead of time (and tested them, too). You don't have to do this, though. I wouldn't hesitate using that little bit of unallocated space you have.  
 
When you get to partioning, do you plan on creating two Linux partitions, one for "/" and the other for swap?

If I understand your question correctly, the consensus seems to be that swap should be a separate partition, so that's probably what I'll do.

Acer is sending me a Restore disk. I may just use up that extra space...

Thanks for your help!

---

### Post by Hedgehog1 on 2011-03-26
> **Longstreet said:**
> Noob here, with an Aspire One D255, N455 Atom, 1G RAM, 160G HDD. My plan is to partition the HDD so that I have one 40G partition for Win 7 Starter, one 40G for Ubuntu, and the remainder for NTFS storage so both OS can access. After comparing what Win Disk Management tells me with what GPartEd tells me, I'm not sure what I'm going to be allowed to do.


Longstreet,

You can shrink down the Win7 partition to 40 gigs (please try to use the Windows Disk Manager for it.  If you cannot shrink the partition all the way with windows tools, please defrag the windows partition before you finish the shrink with gparted.

The you will create an extended partition call /dev/sda4 that uses the entire balance of the disk.

Inside the extended /dev/sd4, you can create 3 or 4 partitions:

/dev/sda4
__/dev/sda5 - Ubuntu '/'
__/dev/sda6 - Swap
__/dev/sda7 - Ntfs

OR

/dev/sda4
__/dev/sda5 - Ubuntu '/'
__/dev/sda6 - Swap
__/dev/sda7 - Ubuntu '/home'
__/dev/sda8 - Ntfs

Also - please do not delete the /dev/sda2 partiton - that is the windows boot partition.

***The Hedge***

:KS

---

### Post by Longstreet on 2011-03-26
> **deconstrained said:**
> A slightly more convenient way of doing it would be to allow a 10-15 GB for Ubuntu root and use the rest as a home partition.

Note, however, that you cannot have more than 4 primary partitions. You need to use extended partitions for Linux if you want to slice up the hard drive any further, or create a logical volume group on the remaining free space for Linux (more flexible and versatile, but more complicated).

I've seen the "Root/Home" partition arrangement described. Apparently it makes updates to the OS simpler, right? Not quite sure how to make that happen.

---

### Post by Hedgehog1 on 2011-03-26
Make two EXT4 partitions, a 10 gig for '/', and the rest of ubuntu space a second EXT4 for '/home'

During the manual install, you will do this extra step:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

***The Hedge***

:KS

P.S. Would you like to to post a step-by-step?

---

### Post by Longstreet on 2011-03-26
Wow, y'all are responding faster than I can keep up!

I understand (I think) the primary/extended thing. sda4 would be the final primary, and everything else would have to be inside there as extended. It would look like the second example in Hedgehog's post (thanks for the warning about sda2, btw).

That's a Root and Home arrangement, right? It's done that way so that any future update, if it gets wonky, affects only Root, making it easier to go back to a more stable release, correct?

> You can shrink down the Win7 partition to 40 gigs (please try to use the Windows Disk Manager for it. If you cannot shrink the partition all the way with windows tools, please defrag the windows partition before you finish the shrink with gparted.
That's where the confusion comes from (I neglected to mention this earlier). I've defragged C: 3 times now, and each time I get a similar result. Windows Disk Manager tells me I only have ~60G available to shrink. That just doesn't seem right. I've had this machine for 3 weeks, have only added a few things (Chrome browser, Kindle for PC, and Avast free) and have deleted some of the preinstalled programs. There just doesn't seem any way that I could have already used that much HDD space. The numbers from Win Disk Mgmt are:

Total size before shrink in MB  139213
Size of available shrink space in MB  60265
Total size after shrink in MB  78948

There's not much I need Windows for, but there are a couple of different programs that I had hoped to retain. If, however, Win 7 Starter, which is supposed to be pretty lightweight, is going to hijack almost half of my HDD, I'm wiping the whole thing and going all Ubuntu.

What am I missing, looking at Win Disk Mgmt vs GPartEd?

Thanks again for the help.

---

### Post by Longstreet on 2011-03-26
> **Hedgehog1 said:**
> Make two EXT4 partitions, a 10 gig for '/', and the rest of ubuntu space a second EXT4 for '/home'

During the manual install, you will do this extra step:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

***The Hedge***

:KS

P.S. Would you like to to post a step-by-step?

If it's not too much trouble, that would be great!

---

### Post by samcot on 2011-03-26
The swap partition *must* be separate, as far as I know. It's normally at least the same size as your RAM, and if you want to hibernate, make it twice that size. 
 
You say that you ordered recovery discs, and that's good, but did you make a set, too?

---

### Post by samcot on 2011-03-26
*please do not delete the /dev/sda2 partiton - that is the windows boot partition.*
 
Yes, good of you to mention that! I'm guessing that the /dev/sda1 is a recovery partition? If he cuts down sda3 to 40GB, that doesn't leave a whole lot of room for Windows to grow, but then, once he starts using Ubuntu, maybe that won't be an issue. :-)
[I] 



[/I]

---

### Post by Longstreet on 2011-03-26
> **samcot said:**
> The swap partition *must* be separate, as far as I know. It's normally at least the same size as your RAM, and if you want to hibernate, make it twice that size. 
 
You say that you ordered recovery discs, and that's good, but did you make a set, too?

No, that's why Acer is sending me the disk. I bought a CDR/W DVDROM drive off ebay right after I got my netbook, primarily so I could burn the recovery disk. It was only after I spent the money that I discovered it had to be DVDR/W. I called Acer to complain that their website says it could be either/or, and so they're sending the Recovery Media free of charge.

Is there a difference in the one they send vs the one I would burn?

---

### Post by Hedgehog1 on 2011-03-26
In gparted, create 3 partitions: ***(You will make also make an NTFS parttion)***

1) ext4 '/'
2) Linux swap
3) ext4 '/home'

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Longstreet on 2011-03-26
> **samcot said:**
> *please do not delete the /dev/sda2 partiton - that is the windows boot partition.*
 
Yes, good of you to mention that! I'm guessing that the /dev/sda1 is a recovery partition? If he cuts down sda3 to 40GB, that doesn't leave a whole lot of room for Windows to grow, **but then, once he starts using Ubuntu, maybe that won't be an issue**. :-)
[I] 



[/I]

That's exactly what I'm planning on!

---

### Post by Miljet on 2011-03-26
> There just doesn't seem any way that I could have already used that much HDD space

You probably haven't used that much. Windows has always had a nasty habit of scattering files all over the disk and then telling you that some of them can't be moved. That is probably why you can't shrink the disk as much as you would like. But it is funny how quickly those same files decide they can be moved when gparted tell them it is taking that part of the disk.

---

### Post by Hedgehog1 on 2011-03-26
The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a 'typical' view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

p.s. The '/home' as a separate partition is useful, but optional.

---

### Post by samcot on 2011-03-26
*Is there a difference in the one they send vs the one I would burn?*
 
No, they should be the same, and you got it for free so that's good.

---

### Post by Longstreet on 2011-03-26
Yeah, that's kinda what I figured was going on! I trust GPartEd more than I do Win Disk, just was a bit confused.

Thanks all of you, esp Hedgehog for the step-by-step. It's 2225 here, and I have to go to work tomorrow. I'll try this Monday morning, and let you all know how it went.

---

### Post by deconstrained on 2011-03-27
> **Longstreet said:**
> I've seen the "Root/Home" partition arrangement described. Apparently it makes updates to the OS simpler, right? Not quite sure how to make that happen.
Separate partitions for root and home makes it way easier to switch to a different distro or reinstall Ubuntu all you please without messing up your personal files & settings.

---

### Post by Longstreet on 2011-03-28
Eureka (I think)! I used GParted to shrink the free space to 40G, then partitioned as Hedgehog suggested. Hit install (btw, Ubuntu should REALLY make a note that the username can't have any caps in it), wifi works out of the gate, everything else I've tried so far is working...

My partitions look like this:

[IMG]http://i659.photobucket.com/albums/uu314/Longstreet308/Newinstall.png[/IMG]

Everything look ok?

---

### Post by Hedgehog1 on 2011-03-28
***Well Done Longstreet!!***

I think that is a ***Lovely*** looking install.

Of course, I am a little biased. :D


So... OK if I start ending folks your way with partition questions?  I think you have this down pat now...


***The Hedge***

:KS

---

### Post by Longstreet on 2011-03-29
> **Hedgehog1 said:**
> ***Well Done Longstreet!!***

I think that is a ***Lovely*** looking install.

Of course, I am a little biased. :D


So... OK if I start ending folks your way with partition questions?  I think you have this down pat now...


***The Hedge***

:KS

I don't know if I "have this down pat", but it did go very well! It's one of those things that you don't really understand until you do it. After it was through I thought "THAT'S what that was all about!"

Don't know how much help I can give, but I would be more than happy to do so! If nothing else I can offer encouragement.

Many thanks to Hedgehog, deconstrained, samcot and miljet.

---

