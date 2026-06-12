---
title: "Long term support?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-07
Just a kind of general question, I was looking at the offical Ubuntu documentation and I noticed that distros listed as XX.04 are all long term support and but XX.10 are not, why is this? Also I downloaded and installed Ubuntu 10.10 as that  was what was first offered on the download site (in my assumption just the newest) but now I'm wondering if I should of gotten 10.04 as long term support is offered. How easy is it to switch to 10.04 or should I wait for the new release (I'd assume 11.04) either way would I have to go through all the set up process again? Perhaps a link that could help me understand all this better?

---

### Post by migs73 on 2011-03-07
The next LTS will be 12.04 the LTS's are every two years, supported for three. 
If 10.10 works for you, I wouldn't worry too much about going to the LTS versions unless you have good reasons to do so.
I am not aware of any way to go back to the previous release, so a fresh install with 10.04 would probably be required.
Have a look at some of the guides for partitioning your drive when installing Ubuntu, this could keep your personal data (/home) separate from the OS (/) thus allowing you to install a different version without losing your settings or data.

---

### Post by turtle153 on 2011-03-07
Releases like Maverick 10.10 are supported for 1.5 years, while LTS are supported for 3 years. You you don't want to go through a release upgrade, the idea is to stick to using LTS. If you're planning on getting the latest release, you should do exactly that. Either way doesn't matter.

---

### Post by DGINSD on 2011-03-07
So as of right now if 10.10 is working well for me (and for the most part it is, no hibernate with the lid is the only thing I've found) I should stick with it till the next release of a LTS version and stay on that "track"?                                                                                                                                      MIGS73, I'm interested in learning more about how to partitoin as you stated that sounds great however I'm not too experienced with the ins and out of partitioning. This install of ubuntu along side my windows XP is my first stab at partitioning and I'm pretty damn proud of myself for not screwing it up. Where can I read up on how to set up that way? It may not even be possible to do on my machine I only have an 80G HDD and after the dual boot set up I have a grand total of about 30G of free space left (time to spend some money I think)

---

### Post by coffeecat on 2011-03-07
> **DGINSD said:**
> I'm interested in learning more about how to partitoin

There is a mass of good community documentation. This for partitioning:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by CharlesA on 2011-03-07
Upgrading isn't mandatory. :)

You can run of Maverick until it reaches EoL in (about) 15 months if you wish.

---

### Post by DGINSD on 2011-03-08
> **coffeecat said:**
> There is a mass of good community documentation. This for partitioning:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I read through a lot of the guides and they were very helpful, but there wasn't anything on how to deal with partitioning after a OS (such as Ubuntu) is already installed and also a way in which to set things up like MIGS73 said, where I could upgrade my Ubuntu without losing my settings and personal files. Is this something that can be done after the fact in essence changing the way my partitions are set up to fit that model or would I have to start from scratch? Links on how to do that would be great and helpful.

For what its worth the Ubuntu explanation on partitioning was far more helpful and easier to understand than what I read from Microsoft's info pages. They didn't explain it very well and it just confused me.

---

### Post by migs73 on 2011-03-08
There is community documentation on how to do this here;
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Doesn't look that easy though! I did mine with a fresh install and I don't dual boot. 
It might be worthwhile leaving it till you have to upgrade, and do it all with a fresh install.

My only advice about partitioning would be BACK UP ALL YOUR IMPORTANT DATA before you do anything.

Mike

---

### Post by 3rdalbum on 2011-03-08
If you're new to Ubuntu, I'd suggest keeping up-to-date and using whatever the latest version of Ubuntu is. This isn't Windows XP where you stay on the same version of the OS for ten years; this is Linux where there are always new additions and refinements.

---

### Post by DGINSD on 2011-03-08
> **3rdalbum said:**
> If you're new to Ubuntu, I'd suggest keeping up-to-date and using whatever the latest version of Ubuntu is. This isn't Windows XP where you stay on the same version of the OS for ten years; this is Linux where there are always new additions and refinements.

Yeah thats pretty much what I want to do I just want a way thats
practical to move on to the next and newest release without having to go through the trouble of reloading my wireless card drivers re doing all my personal settings ect. ect. ect. I mean if thats what must be done so be it just seems there should be an easier way.

---

### Post by kaldor on 2011-03-08
> **DGINSD said:**
> Yeah thats pretty much what I want to do I just want a way thats
practical to move on to the next and newest release without having to go through the trouble of reloading my wireless card drivers re doing all my personal settings ect. ect. ect. I mean if thats what must be done so be it just seems there should be an easier way.

Simply use whatever works best, and always use a LiveCD on new releases to make sure it all seems okay. Also, backup often and always do a clean install when you upgrade.

If you like 10.10 right now, use it until you stop getting security updates in about a year and a half. If you don't want these issues, use an LTS after your 10.10 becomes unsupported. By then, 12.04 will be the current LTS. Then you can get by for 3 years.

---

### Post by DGINSD on 2011-03-08
I just used Gparted to shrink down my windows partition so I could add to my linux extended partition but Gparted has the extended partition locked as well as the swap partition even if I use if from a live disc boot. How can I extend both my extended and logical partitions? 

I'm guessing my best way to set up a separate home partition is wait till I do my next upgrade and back up my home folder and wipe all but my windows partition and set everything up from scratch. How much space should be used to install Ubuntu assuming my home folder is on its own partition.

Seems to me if this is the best way to set your system up for future upgrades, live CDs should be arranged to install this way by default.

---

