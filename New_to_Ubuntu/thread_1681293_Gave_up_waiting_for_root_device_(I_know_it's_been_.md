---
title: "Gave up waiting for root device (I know it's been posted before, but...)"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by zander x on 2011-02-03
Hello.

I know the following problem has been posted, but I'm not sure how to go about fixing it:

Gave up waiting for root device
...
ALERT! /dev/mapper/lrb-root does not exist. Dropping to a shell.

The reasons why I am reposting this:

*Every 10 failed boots, one will work (strange)
*This is my *FOURTH* fresh install of Ubuntu 10.04 Server
*The CD version of Ubuntu doesn't work 100% of the time, and even in Terminal, I get errors.
*This is on a Dell Powerserver 2650, so this is on a SCSI drive. When I had the same OS on a IDE drive on a P3, there was no problem.

Since this server takes a long time (2 minutes plus) to fully boot, just before this screen, I can catch a quick "error disk not found" before it drops me into Busybox. I think I've read enough to understand the problem and have tried some solutions, but to no avail. Can anyone help?

---

### Post by zander x on 2011-02-04
> **zander x said:**
> Hello.

I know the following problem has been posted, but I'm not sure how to go about fixing it:

Gave up waiting for root device
...
ALERT! /dev/mapper/lrb-root does not exist. Dropping to a shell.

The reasons why I am reposting this:

*Every 10 failed boots, one will work (strange)
*This is my *FOURTH* fresh install of Ubuntu 10.04 Server
*The CD version of Ubuntu doesn't work 100% of the time, and even in Terminal, I get errors.
*This is on a Dell Powerserver 2650, so this is on a SCSI drive. When I had the same OS on a IDE drive on a P3, there was no problem.

Since this server takes a long time (2 minutes plus) to fully boot, just before this screen, I can catch a quick "error disk not found" before it drops me into Busybox. I think I've read enough to understand the problem and have tried some solutions, but to no avail. Can anyone help?

Also, I cannot save any changes to grub. I get "error: cannot find a device for /".

The following solutions also do not work:

[http://ubuntuforums.org/showthread.php?t=1611213&highlight=gave+up+waiting+for+root+device](http://ubuntuforums.org/showthread.php?t=1611213&highlight=gave+up+waiting+for+root+device)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

It seems like a lot of people are dual booting or getting some sort of menu to edit. I don't have that luxury. Once I get into a terminal session with a live cd, a lot of these commands fail. And for some reason, my file system -- my 73 gig drive -- is referred to as a 233 meg drive. What is going on?

---

### Post by Hedgehog1 on 2011-02-04
> **zander x said:**
> *This is on a Dell Powerserver 2650, so this is on a SCSI drive. When I had the same OS on a IDE drive on a P3, there was no problem.

> **zander x said:**
> And for some reason, my file system -- my 73 gig drive -- is referred to as a 233 meg drive. What is going on?

zander x,

Please boot up on the live CD, and then nab a screen shot of your gparted screen.

This will give us a decent glimpse of why your SCSI drive is reading 233 megs rather than 73 gigs.

That fact that it boots 1 out of 10 times is also telling, but lets see the gparted screen shot first, please...

:KS

---

### Post by Hedgehog1 on 2011-02-04
Also, please let us know

* is the dual or single xeon model
* single SCSI drive or raid array of SCSI drives

This is the rack mount version, right?


:guitar:

---

### Post by Hedgehog1 on 2011-02-04
More info:

This fellow got his to boot Ubuntu:

[http://www.youtube.com/watch?v=7_n8WaVCdwU]("http://www.youtube.com/watch?v=7_n8WaVCdwU")

His notes under the video list the steps it took to get the drives setup to work (reset of Bios, Raid 0).

](*,)  ](*,)

---

### Post by zander x on 2011-02-04
> **Hedgehog1 said:**
> Also, please let us know

* is the dual or single xeon model
* single SCSI drive or raid array of SCSI drives

This is the rack mount version, right?


:guitar:

This is a dual xeon 3.06 ghz with a single SCSI drive. It has room for 4 more drives but I'm only using one. This is the rack mount version.

After this most recent fresh install, it booted up twice with no problems, then back to the annoying screen.

---

### Post by Hedgehog1 on 2011-02-04
These servers are circa 2002.

They typically have lead a very hard life (on 24/7, then pulled from their racks and stored in some ghastly storage area until they are resold)

A unit like this is near or at its expected end-of-life.

Based on the screen shot and the description of how often the system doesn't boot, I think it is a 60% chance the SCSI drive electronics are failing, and about a 40% chance the SCSI controller is at fault.

There is a valid reason we swap out these things from our own racks every so many years...

I don't know if it is even worth trying to put a SATA controller and drive in that box (assuming the PCI slots are even reachable).

I think it would be throwing good money away on bad.  :frown:

---

### Post by zander x on 2011-02-05
> **Hedgehog1 said:**
> These servers are circa 2002.

They typically have lead a very hard life (on 24/7, then pulled from their racks and stored in some ghastly storage area until they are resold)

A unit like this is near or at its expected end-of-life.

Based on the screen shot and the description of how often the system doesn't boot, I think it is a 60% chance the SCSI drive electronics are failing, and about a 40% chance the SCSI controller is at fault.

There is a valid reason we swap out these things from our own racks every so many years...

I don't know if it is even worth trying to put a SATA controller and drive in that box (assuming the PCI slots are even reachable).

I think it would be throwing good money away on bad.  :frown:

Not to argue with you, but when I had Win XP on there, it booted up perfectly every single time. If there was a problem with the SCSI components, wouldn't the built-in Adaptec application throw up some sort of error? It's obviously old, but I'm not in front of it and won't be until Sunday. Are there any other rabbits in the hat?

Also, very few of the commands listed on any other threads, especially update-grub will work. They all give some sort of mount error. I can't add the "rootdelay" statement because it won't stick. Grr.

---

### Post by Hedgehog1 on 2011-02-05
I have no full sized rabbits, but perhaps one little baby bunny left.

The gparted shows the largest partition as extended (/dev/sda2), with a logical partition in it (/dev/sda5) formatted in 'lvm2'.

My only other idea (when you get to the system on Sunday) is to reinstall but this time don't use the Logical Volume Manager.

Instead, just make it ext4 and lose the extra layer of translation.  This should stop the mount errors ***I hope***

That is about it from my bag of tricks.

---

### Post by Hedgehog1 on 2011-02-05
zander x,

The more I think about this, the stronger I feel you are facing a hardware failure issue.

The fact that the drive is 'their & the right size' sometimes, other times it is 'sorta there but the wrong size and wont write or boot' just feels like SCSI controller/disk failure to me.

I know the adaptec controller is not giving you an error message, and that XP used to run fine on it; but this is just how it 'feels' to me.

I hope I am wrong and it is instead some easy fix I just don't  yet know about.

Hopefully we will both know on Sunday when you get access to the system.

You do have me very curious....

---

### Post by fabricator4 on 2011-02-05
> **Hedgehog1 said:**
> I have no full sized rabbits, but perhaps one little baby bunny left.

The gparted shows the largest partition as extended (/dev/sda2), with a logical partition in it (/dev/sda5) formatted in 'lvm2'.


I'd have to agree with you, but I must be missing something as this looks completely screwy to me.  The 250 MEGAbyte bootable partition has nothing but the bootloader on it?  The LVM2 partition is mounting as root?

I think I'd be reverting to a 60+ GB ext4 boot partion mounting as root, with an appropriately sized swap partition on the end and see if the system starts to behave.

After that, look at the HDD smart data if available and see if it show any sign of an impending crash and burn on the part of the HDD.

Chris.

---

### Post by zander x on 2011-02-06
> **Hedgehog1 said:**
> zander x,

The more I think about this, the stronger I feel you are facing a hardware failure issue.

The fact that the drive is 'their & the right size' sometimes, other times it is 'sorta there but the wrong size and wont write or boot' just feels like SCSI controller/disk failure to me.

I know the adaptec controller is not giving you an error message, and that XP used to run fine on it; but this is just how it 'feels' to me.

I hope I am wrong and it is instead some easy fix I just don't  yet know about.

Hopefully we will both know on Sunday when you get access to the system.

You do have me very curious....

Well, much to my chagrin after spending 5 hours trying to update the BIOS and then 20 minutes on a new copy, the same problem exists, although the computer loads up quite a bit faster and now the directory after "ALERT!" is different. I'll come back and attach screenshots. I've been at it all afternoon and my team is losing the Superbowl. I'm hungry and tired. I even had to make multiple trips to DOS land.

(But once again, when I ran Windows on this same machine earlier... no problems.)

---

### Post by zander x on 2011-02-06
> **fabricator4 said:**
> I'd have to agree with you, but I must be missing something as this looks completely screwy to me.  The 250 MEGAbyte bootable partition has nothing but the bootloader on it?  The LVM2 partition is mounting as root?

I think I'd be reverting to a 60+ GB ext4 boot partion mounting as root, with an appropriately sized swap partition on the end and see if the system starts to behave.

After that, look at the HDD smart data if available and see if it show any sign of an impending crash and burn on the part of the HDD.

Chris.

I'll try that tomorrow night, but I need some step-by-step hold-my-hand instructions.

---

### Post by Hedgehog1 on 2011-02-06
Well - if windows still runs OK on it - I will drop my insistence that it is a hardware issue.

(Ahem) *I humbly withdraw any criticism I may have made about the age of your server* :KS

Of course, we still don't know why it refuses to work...

Oh - Sorry about your team being behind...

---

### Post by zander x on 2011-02-06
> **Hedgehog1 said:**
> Well - if windows still runs OK on it - I will drop my insistence that it is a hardware issue.

(Ahem) *I humbly withdraw any criticism I may have made about the age of your server* :KS

Of course, we still don't know why it refuses to work...

Oh - Sorry about your team being behind...

Here are the "before" and "after" screenshots -- the one with "lrb" is before and the one with all the numbers and such is after. I'm just not ready to chalk it up to hardware yet -- or at least not anything in the case. Now the HD itself, maybe that guy is bad. Je ne sais pas. 

I will say this, I feel like *I'm* about to give up waiting on Ubuntu server to work right and either use desktop or another flavor altogether.

---

### Post by zander x on 2011-02-07
> **zander x said:**
> Here are the "before" and "after" screenshots -- the one with "lrb" is before and the one with all the numbers and such is after. I'm just not ready to chalk it up to hardware yet -- or at least not anything in the case. Now the HD itself, maybe that guy is bad. Je ne sais pas. 

I will say this, I feel like *I'm* about to give up waiting on Ubuntu server to work right and either use desktop or another flavor altogether.

Tonight I tried a few experiments. This time I just tried to turn it on and hope for the best. Nothing. So then I said f it, and installed Ubuntu 10.04 desktop. Unlike every server install thus far, this one was smooth. Great. I ejected the disc and let it reset. DAMN ERROR SCREEN! For some odd reason, typing "exit" with the server version never worked but I tried it this time and it resumed loading and showing all that trace data that Ubuntu Desktop likes to do. Fine by me. Once I installed the 254 updates (or however many it was), I reset again and held my breath. It got to the black screen and then... Ubuntu splash screen! Then I installed LAMP and some of its friends, hit reset, got the black screen and then... Ubuntu splash screen! Then I turned it totally off, unplugged it and even turned it a different direction, plugged it on, turned it on and then... Ubuntu splash screen!

So what is the problem? Was it the PowerEdge 2650 needing to be updated to BIOS revision A21? Is it something in the Ubuntu Server install code? Is it something that is in a Desktop update that isn't in a server update? Am I just getting lucky? I neither know or care.

I read up on the differences between the two versions, and considering that I'm running dual Xeon (32 bit processors) and already have 4 gigs of RAM, I don't think the difference would be major or am I missing something?

Otherwise, it's back to the fun of getting Webmin and BIND configured to make a webserver (pure hell).

---

### Post by Hedgehog1 on 2011-02-07
> **zander x said:**
> 
...
Once I installed the 254 updates (or however many it was), I reset again and held my breath. It got to the black screen and then... Ubuntu splash screen! Then I installed LAMP and some of its friends, hit reset, got the black screen and then... Ubuntu splash screen! Then I turned it totally off, unplugged it and even turned it a different direction, plugged it on, turned it on and then... Ubuntu splash screen!

So what is the problem? Was it the PowerEdge 2650 needing to be updated to BIOS revision A21? Is it something in the Ubuntu Server install code? Is it something that is in a Desktop update that isn't in a server update? Am I just getting lucky? I neither know or care.
...

You ask a series of excellent questions.  I regret I cannot offer a series of excellent answers to match them.

I do know that if the BIOS update was all that was needed, the server install that followed the BIOS update would have worked.

That original YouTube video of the other fellow running Ubuntu on the same machine - he was running Desktop and not Server.  I wonder if that was a lucky choice he made, or something neither of us would have guessed.

The big key here is: [SIZE="3"]You are Up and Running![/SIZE]

:guitar:

Now only another four hours of suffering, and this this will be behind you... Until you add another PowerEdge 2650 server to your rack... :KS

---

### Post by zander x on 2011-02-07
> **Hedgehog1 said:**
> You ask a series of excellent questions.  I regret I cannot offer a series of excellent answers to match them.

I do know that if the BIOS update was all that was needed, the server install that followed the BIOS update would have worked.

That original YouTube video of the other fellow running Ubuntu on the same machine - he was running Desktop and not Server.  I wonder if that was a lucky choice he made, or something neither of us would have guessed.

The big key here is: [SIZE="3"]You are Up and Running![/SIZE]

:guitar:

Now only another four hours of suffering, and this this will be behind you... Until you add another PowerEdge 2650 server to your rack... :KS

I am glad to be up and running! Now adding another PE2650? NOT HAPPENING! I will build a server instead. Like a lot of people, I'm not hot on Dell anymore. 

Now kind sir, can you help me with some networking problems?

---

### Post by Hedgehog1 on 2011-02-08
Those are not my strength (I have fellow geeks at the office who do nothing but network).

May I suggest a new thread?  With just the network issue left, (and I hope it is a 'just'), you should be able to find semi-willing volunteers...

p.s. I, too, have wandered away from Dell.

We use IBM Linux servers at work (where the network nerds are).
I have replaced the home Dell laptops with HP ones.
The desktop I am using as I type is a hand built one - with a 55" 3D TV as the monitor.

:KS

---

