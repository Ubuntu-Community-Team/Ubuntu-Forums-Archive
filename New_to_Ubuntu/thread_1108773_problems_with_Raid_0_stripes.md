---
title: "problems with Raid 0 stripes?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by initialfaust on 2009-03-28
I am considering making my PC a dual boot with XP 64 bit and ubuntu 64 bit.  I am new to linux and use my computer for online gaming so i didn't want to jump in headfirst without checking on some things first.  

well i have a pc that was built by my brother-in-law (basicaly i handed him a parts list to maximize video settings and he filled in the blank spots) and it has 2 250 gig hard drives in a raid 0 stripe. my first question is when I install ubuntu will i be able to use the same disk with the raid settings as when i installed XP?  my main concern is starting to install it and having it not recognize the drives because of the stripe.

My second question was i had read a thread about ubuntu automaticaly recognizing Netgear wireless routers and i was wondering if this was still the case?  this is my mess around computer so it is on a wireless adapter to my main PC.  and i have looked at netgears website and from what i gathered they dont make drivers for ubuntu.

Im sure i will think of other questions but it is 3:30 am and i have to be awake in 5 hours so thanks in advance for any help.

---

### Post by Cresho on 2009-03-28
1.  NO!  you will not be able to use linux because onboard Raid is "fake RAID" and not true rait.  you only get 10% boost but that is it!  Ubuntu will see it as 2 hardrives and not striped or mirrored.

2.  Ubuntu does not automatically recognize netgear wireless routers unless you have a recognized wireless pci card or a wireless usb adaptor.

3.  (my filler answer before you ask).  you can use windows drivers to install hardware.  I posted a tutorial long ago and seem to miss it.  but if you run the ubuntu cd, with the wifi adaptor, you can see if it runs without drivers needed.  you will see a network adaptor on your upper left hand corner.  right click or left click to see your network.

---

### Post by initialfaust on 2009-03-28
> **Cresho said:**
> 1.  NO!  you will not be able to use linux because onboard Raid is "fake RAID" and not true rait.  you only get 10% boost but that is it!  Ubuntu will see it as 2 hardrives and not striped or mirrored.

2.  Ubuntu does not automatically recognize netgear wireless routers unless you have a recognized wireless pci card or a wireless usb adaptor.

3.  (my filler answer before you ask).  you can use windows drivers to install hardware.  I posted a tutorial long ago and seem to miss it.  but if you run the ubuntu cd, with the wifi adaptor, you can see if it runs without drivers needed.  you will see a network adaptor on your upper left hand corner.  right click or left click to see your network.


what do you mean it is a fake raid?  do you mean that i wont be able to use linux period or that it will just treat them like seperate drives?  my main concern with the raid setup wasnt that it was functional when running ubuntu.  i just didnt want to go to install ubuntu and have it not recognize the drives at all.  both drives have high rpm's and caches.  the main reason i went with the raid 0 stripe was for loading purposes for the games i use xp for.  So i searched using information i found about my motherboards raid controler and i saw the same thing that you said about linux not recognizing raid setups from the 750SLI chipset.  my main question is should i bother trying to install it onto the raid that it wont recognize or should i just go the easy route and just get another hard drive that would be dedicated to ubuntu?

the wireless usb adapter i have is a netgear MA101.  when i had initialy done the search on this adapters compatability with linux the post i read was about an ma101 usb adapter and the guy said it worked.

---

### Post by Cresho on 2009-03-28
put the cd into the drive.  boot up linux and it will run off the cd.  In this environment, you are not installing, it is not doing but running off the cd.  You can then see if your raid works and if you see one striped drive.  you can also see if you can work your wifi, audio, printer, scanner....basically all is installed minus your video driver because the kernel identifies them if so.

Boot up the cd..there is no problems.  This is how I found out about the raid issue I had with my gigabyte motherboard.  10% increase is not worth it so I split my drives up.

True raid is a pci-e card hooked up to a couple of 10000 20mbplus cache drives.  You practically get 100% or 90% performance boot over the horrible, illogical 10% off the motherboard fake raid.

Boot the cd...youll be fine.   just don't click on install unless you want to.

---

### Post by initialfaust on 2009-03-29
i'm making the CD now.  im going to check to see if the hardware works.  i was curious about if it does and i go to install it.  will i have to create the partition for it before i install or is it like the windows cd where i can create the partition while installing?  if it works i might just reformat my PC and create the partition for ubuntu before hand.  if not im probably just going to throw in one of the hard drives i have laying around for ubuntu specificaly.  that way i wont have to screw with the partitioning.

---

### Post by initialfaust on 2009-03-29
ok so i made the disk and booted up.  it did see the setup as two seperate drives.  aside from that i found out that the driver for my video card wasnt automatic which wouldnt have been a problem but i also couldnt seem to get my wireless router to work.  it found the network and it seemed like i had to set it up problem was i didnt have my ip on hand to fully check it out.  it seems like im going to go with my third hard drive specificaly for ubuntu option.

---

### Post by ramjet_1953 on 2009-03-29
This may be worth a read:

[http://reformedmusings.wordpress.com/2008/12/27/ubuntu-810-intrepid-and-nvidia-raid/](http://reformedmusings.wordpress.com/2008/12/27/ubuntu-810-intrepid-and-nvidia-raid/)

Regards,
Roger :)

---

### Post by initialfaust on 2009-03-29
thanks for the info.  i think i am going to just use the third hard drive.  it would be better than having to partition the other two.  i do have one question though.  last night after i made that one post i copied down all of my information for my wireless router and loaded ubuntu from the cd to see if i could get my adapter to work.  i managed to get it so that it was connected to the internet and it found the drivers for my video card and stuff like that but i didnt bother trying to get them because it wasnt actualy installed.  my question is this. even though the wireless router was functioning and i was connected to the internet when i tried to use the firefox it was treating it as if i was offline.  was this because i was running off the disk or was there some other problem?

---

### Post by Cresho on 2009-03-29
Glad you decided to keep ubuntu at least on a third drive.  It is a really nice operating system.  It is difficult at first but this is the only way I feel you can get off the windows addiction.  I haven't booted into windows in like...Can't remember.

When I did my first installation of ubuntu, I was browsing the net, chatting in pidgin while it was installing.  I was also finishing up a homework assignment in openoffice and saving the info onto a thumbdrive while installation was occuring.  If you manage to read your single raid drive, ubuntu cd can become an awsome backup utility.  after mounting the windows partition, you can backup all pictures, docs, music or what ever on an external drive with the live cd....  very powerfull.

here..look at this.

[http://www.category5.tv/content/view/412/148/](http://www.category5.tv/content/view/412/148/)

Hope this helps.

---

### Post by initialfaust on 2009-03-29
i have an external harddrive that i backup all important information to.  i still dont understand why my wireless internet was connected yet firefox was treating it as if i was offline.  is that just because I booted off the cd or should i still be able to use firefox which would mean something else was wrong?

---

