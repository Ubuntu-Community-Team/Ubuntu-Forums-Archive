---
title: "Can I upgrade AND keep old version?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-01-12
Hi community.

I have learned from experience that updating/upgrading Ubuntu can be very troublesome & even leave me stranded, without Internet access or other vital functions.

For kernel updates, it is easy to keep the last kernel (or 2) available & select whichever I want at boot time.

This allows me to Google/Synapt on the old kernel, for any needed fixes for the new kernel.

Upgrading (Edgy>Fiesty>Gutsy>Hardy) has been even more traumatic & I am getting to the point where I should consider shifting to Intrepid soon, even though I am deliberately a "late adopter" to give time for younger bloods to iron out the main bugs first.

So question: 
Is there any way I can reasonably treat version upgrades like kernel updates - work properly with the new one (not just on CD) but fall back on the proven old one if & when needed?
If so - how?

I Googled & found mentions of keeping different versions on USB sticks or separate partitions, but the explanations were not basic enough for me!

Thanks for any (simple?) suggestions!

---

### Post by zzHanks on 2009-01-12
Hi.

Yes you can keep the old version, just create a new partition (I think the installer even does it automaticly, but I'm not sure).

Edi: You will have to download the 8.10 ISO

---

### Post by LowSky on 2009-01-12
if you are so concerned stick with Hardy. It carries 3 years of security updates. If you really need the newer applications some can be grabbed from backports or from installing them by hand

---

### Post by deputy on 2009-01-12
If you have another hard drive you could install the newest Ubuntu on that, and then dual boot between the new version and the old one.

---

### Post by mkvnmtr on 2009-01-12
I like the idea of dual booting. Once you have everything like you want you can use the partition for the next upgrade.

---

### Post by louieb on 2009-01-12
Before doing a dist upgrade. I use a [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  and take a partimage backup of my / (root) and /home partitions. 

Then do the upgrade. If things still work fine. If not and don't have time  to mess with fixing then a working system is just a partimage restore away.

---

### Post by 2CV67 on 2009-01-14
Thanks for all those constructive suggestions!

I don't have a separate internal hard drive, so that one is out for me.

I had forgotten about LTS vs other versions, so will try to remember that in future.
I could be tempted to stick with Hardy as an LTS, as I don't need or want cutting-edge screen gimmicks, but maybe that would mean the eventual jump to the next LTS version would be even more traumatic?
I keep hoping that new versions will fix my kernel panics, improve printing & scanning etc too...
So I think I will keep incrementing every 6 months (but not as soon as new versions appear!).

The rescue CD idea is good.

What attracts me most is the idea of dual-booting (triple-booting with XP) off different partitions.
Is this feasible?
Easy for dummies?
I didn't find any articles or threads on this idea yet. (but the forum was down yesterday!)

I won't be doing it for a couple of weeks anyway, so plenty of time to chew over the options:
Do I need to have 2 of everything? (Home? Firefox? Bookmarks? Connexions? Printer drivers? etc etc)
Or can some things safely stay common?
Currently I have a separate /home partition. Do I end up with 2 homes or can I share one?
Will Grub handle booting options OK?
I could image either keeping one partition for "odd" versions & the other for "even" versions, then leapfrogging to always have the latest & the previous versions available (probably).
Or keeping one partition for LTS & the other for non-LTS versions (probably not).
Can I upgrade jumping 2 versions OK (Edgy > Gutsy, Fiesty > Hardy, etc)?

Other considerations?
Ideas?
Warnings?

Is there a "how to" anywhere?

Thanks again!

---

### Post by Archmage on 2009-01-14
> **2CV67 said:**
> What attracts me most is the idea of dual-booting (triple-booting with XP) off different partitions.
Is this feasible?
Easy for dummies?

Put in a CD and install it on a free partition. The installation should upgrade your grub accordignly. That is easy. But if something bad happen you might be without an OS at all. So it might be better if you read how you can restore grub if something bad happen.


> **2CV67 said:**
> I won't be doing it for a couple of weeks anyway, so plenty of time to chew over the options:
Do I need to have 2 of everything? (Home? Firefox? Bookmarks? Connexions? Printer drivers? etc etc)
Or can some things safely stay common?
Currently I have a separate /home partition. Do I end up with 2 homes or can I share one?

I think many will have one sperate /home-partition and than use this one on both of there installs. But this might end in strange things when two different version of a program tries to work with the same configuration.


> **2CV67 said:**
> Or keeping one partition for LTS & the other for non-LTS versions (probably not).
Can I upgrade jumping 2 versions OK (Edgy > Gutsy, Fiesty > Hardy, etc)?

Nope. You can only install to the next version e.g. Dapper to Edgy, Edgy to Feisty, Feisty to Gusty and Gusty to Hardy. The only exception is that you can jump diretcly from one LTS to the other e.g. Dapper to Hardy.


> **2CV67 said:**
> Other considerations?
Ideas?
Warnings?

Keep the Live-CDs from the last three releases. They might be great in case of trouble-shooting (e.g. restrore grub).

---

### Post by newbee70 on 2009-01-14
> **2CV67 said:**
> Thanks for all those constructive suggestions!

I don't have a separate internal hard drive, so that one is out for me.



The rescue CD idea is good.


Other considerations?
Ideas?
Warnings?

Is there a "how to" anywhere?

Thanks again!


have you thought of remastersys?
google it and take a look at it.

---

### Post by 2CV67 on 2009-01-14
> **newbee70 said:**
> have you thought of remastersys?
google it and take a look at it.

I would thank you for that - but the thank controls are not there today!

No - I had never heard of it before, but it looks very handy.

I found [this good guide.]("http://www.dedoimedo.com/computers/remastersys.html")

So I can copy my complete Ubuntu with all personal stuff to CD/DVD/USB then upgrade.
Then use the CD for rescue if the upgrade is problematic?
Can I re-install the old version to the hard drive from the CD if needed?
Overwriting the new version, or to a fresh partition(s)?

Can remastersys (or something else) be used to produce an exact working copy of my current Ubuntu with personal stuff etc, to a fresh partition on my current hard drive, so I have 2 identical versions?
I could then upgrade 1 version & keep the other available until next time & so on...
(Still keeping a copy on CD or USB in case of real disaster).

Thanks for all ideas so far :D

---

### Post by 2CV67 on 2009-01-15
Well, I tried Remastersys & was very inpressed with the whole thing.
I made a DVD of my complete Ubuntu set-up & it worked first time & almost as well as the original.
Just needed to set the wireless WEP key & I was surfing with all my bookmarks & sending & receiving e-mails!

Many thanks, newbee70, for that excellent suggestion!
(What happened to the thanks control??)

If I don't find anything better, this is certainly an acceptable answer to my original question, and it is probably going to be the simplest, most reliable & most economical too.

What I did not try yet, was re-installing from the DVD to the hard drive, in case I ever needed/wanted to do that.
I was (am) afraid of screwing up the existing set-up as I did not find any instructions or description of that phase anywhere.

I saw an "Install" ikon on the desktop, but did not touch it in case of...

Can anybody point me to further information on that part of Remastersys?
Does the "Install" ikon do just that?
Does it install where it wants or expect/allow you to select/choose/create partition(s)?

Just out of curiosity, can it write to a Flash drive instead of a DVD? (It didn't look like it, but presumably there are ways of putting the compressed image on a USB drive & using it from there, are there?)

Thanks again for all suggestions!

---

### Post by 2CV67 on 2009-01-28
"Mission Accomplished" - can't think where I saw that...

Thanks to all the help in this thread (& a few others) I now have what I think is a very good set-up.

I made a Live DVD of my Hardy, using excellent Remastersys.
Thats my life belt if the rest sinks!

I made a new partition with GParted & installed my Hardy there from the DVD.
That's my first-line safety-net if I screw up my main Ubuntu, especially during upgrades.
Lots of people warned me off sharing my /home between these 2 & were probably right.

Then I dared to upgrade my main Hardy to Intrepid.
Usual heart-stopping moments when it started throwing up Error messages & Abortion warnings in the last couple of minutes of the installation. (As usual with upgrading or even fresh installing...).

Doubts & uncertainties about booting & grub [(this thread)]("http://ubuntuforums.org/showthread.php?t=1051844").
Eventually decided to keep Intrepid & XP on the first screen & chainload Hardy.

In future, I intend to upgrade the main version (now Intrepid) every 6 months & upgrade the LTS version (now Hardy) whenever new LTS's are available.

I certainly approached the upgrade with less trepidation now I have all those life-belts & braces!

Thanks for all the good advice!

---

