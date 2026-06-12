---
title: "Upgrading to 11.04 when it comes out?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-03
Hi,

I am new to Ubuntu Linux and forums.

What happens when 11.04 comes out?  How do I upgrade?  Is it a major ordeal like Windows?  

I am using 10.10 now.

---

### Post by beew on 2011-03-03
A fresh install would be my recommendation. Upgrade takes hours while a fresh install takes 15-20 minutes. If you have separate / and /home partition just keep the configuration during install and you get to keep all your data and setting, only the / partition would be overwrite.

I will be testing 11.04 on external drives but I wouldn't be upgrading to 11.04. My 10.10 installation is perfect, everything just works and I have never had such a smooth computing environment and 10.10  will only be 6 months old by April!  Why the rush? My software is very up to date thanks to PPAs. I will keep it til 11.10 or maybe even 12.04 when official support expires.

---

### Post by davidmchenry79 on 2011-03-03
Beew - 
        Great post - answered a question I've had on my mind for the last two days and I've only had 10.10 for three weeks! Thanks for reminding me that if it's fixed, don't break it!!

---

### Post by migrate from windows on 2011-03-03
Yes u guys r right! Just settled with 10.10 things are smoothing out. But my doubt is how long the updates will be available ? (are support and updates the same?)

---

### Post by beew on 2011-03-03
> **migrate from windows said:**
> Yes u guys r right! Just settled with 10.10 things are smoothing out. But my doubt is how long the updates will be available ? (are support and updates the same?)

Official support (from Canonical) will last til 2012 April. These are security patches, kernel updates and some bug fixes but there has not been any major feature updates since official release (the official repos are frozen) so if you rely only on official source many of your software would be very outdated and old in 6 months and hence the incentive to upgrade the OS (along with the software). 

But you can keep your software up to date without upgrading the OS with PPAs, that is what I do. Some people argue that PPAs introduce instability but I think it is a hell lot more stable than upgrading a whole system every 6 months especially when there are major changes like the new Unity desktop. I expect 11.04 to be quite buggy when it comes out and it will take may be a month or two to get things patched (as it is always the case with new releases, but especially when there are major changes)

I figure the Maverick PPAS would probably dry up by early 2012 when the maintainers turn their attentions to newer releases and when there is too much incompatibility between the new software and the old OS (kind of like the stage where  9.10 is in now) So I figure I can run a very up to date system while avoiding OS upgrade probably til around Feb 2012, at which point I could wait for 12.04 LTS.

In the moment I will be enjoying my 10.10 for another one whole year.

---

### Post by Hedgehog1 on 2011-03-03
+1 for all 4 posters who will leave 10.10 alone and let the 11.04 release settle down.

With a new release every 6 months, you can skip every other one and still be current.

***The Hedge***

**Good advice, beew**

---

### Post by migrate from windows on 2011-03-03
Well replied beew .... I guess I should concentrate on enjoying 10.10 rather than worrying about updates or support for another year.

---

### Post by Th3W1z4rD on 2011-03-03
I followed the instructions on [here]("http://www.ubuntu.com/testing/natty/alpha1") to upgrade from 10.10 it only took 20 minutes on my 3MB/down connection. I loved 10.10 but I also like messing around with experimental builds. I'm running experimental builds on my phone, my tablet, and my computer. If you're comfortable with 10.10 then stick with it. 11.04 definitely caught me off guard with some of the new features but I got use to it real quick and it seems fairly stable for me. I have gotten updates everyday since my upgrade(3 days ago)and it keeps getting better and better.

Of course you can always stick to the tried and true "if ain't broke don't fix it" mantra. ;)

---

### Post by beew on 2011-03-03
> **Th3W1z4rD said:**
> I followed the instructions on [here]("http://www.ubuntu.com/testing/natty/alpha1") to upgrade from 10.10 it only took 20 minutes on my 3MB/down connection. I loved 10.10 but I also like messing around with experimental builds. I'm running experimental builds on my phone, my tablet, and my computer. If you're comfortable with 10.10 then stick with it. 11.04 definitely caught me off guard with some of the new features but I got use to it real quick and it seems fairly stable for me. I have gotten updates everyday since my upgrade(3 days ago)and it keeps getting better and better.

Of course you can always stick to the tried and true "if ain't broke don't fix it" mantra. ;)


I would be testing 11.04 but not on my work machine, moreover it is only an alpha, it would be very premature to upgrade now (as a matter of fact I have tested it a bit yesterday on a live usb and many things don't work and Compiz constantly crashes on me, Unity is not very usable at this stage unless you only want to take some pretty screenshots, not to mention many things are not even in the repo yet)

---

### Post by Th3W1z4rD on 2011-03-03
> **beew said:**
> I would be testing 11.04 but not on my work machine, moreover it is only an alpha, it would be very premature to upgrade now (as a matter of fact I have tested it a bit yesterday on a live usb and many things don't work and Compiz constantly crashes on me)

I completely agree with you. If its a machine you need to make sure stays absolutely rock solid stable than stick with 10.10. I dual-boot between Ubuntu 11.04 and Windows 7 so if Ubuntu starts giving me a headache I can always run back to the safety of my Windows install(which I only use for Visual Basic every now and then anyway)

The 11.04 release is nice but there have been hiccups...as is expected from an Alpha release. I just love seeing an ubuntu release progress its amazing how far this release has come since I installed.

@OP - You should probably stick with 10.10...well at least until 11.04 hits beta ;)

---

### Post by mastablasta on 2011-03-03
> **Learning Linux 2011 said:**
>  
What happens when 11.04 comes out? How do I upgrade? Is it a major ordeal like Windows? 
 

 
you can easilly upgrade through software manager, however it pays off to run the liveCDd first to see if everything is working as it should. 
 
If you have a separate home partition you can also just replace the instalation with new version.
 
as for the when to uprade - you could go with LTS edition and then upgrade every  2 years. But sometimes LTS doesn't work with newer hardware, while newer version have the drivers for it in their kernel.
 
 
another option is to use a roling distribution (for example linux mint debian) where your system is constantly upgraded. thoguh these usually require a bit more user knowledge in case something doesn't wokrk as it should.

---

### Post by Learning Linux 2011 on 2011-03-03
Thank you for your posts, but you might be missing what I originally wanted.

I'm not so much interested in whether I should upgrade or not, I am mostly interested in how it is actually done technically.

Do you have to wipe the drive and reinstall?  Or do you do it through a software upgrade/update? Or something else?

---

### Post by Th3W1z4rD on 2011-03-03
> **Learning Linux 2011 said:**
> Thank you for your posts, but you might be missing what I originally wanted.

I'm not so much interested in whether I should upgrade or not, I am mostly interested in how it is actually done technically.

Do you have to wipe the drive and reinstall?  Or do you do it through a software upgrade/update? Or something else?

No wipe necessary. It updates thru update manager. If you already have 10.10 you can follow [this]("http://www.ubuntu.com/testing/natty/alpha1"). 

Also I answered you earlier in this thread.

---

### Post by rosswmcgee on 2011-03-14
> **Th3W1z4rD said:**
> No wipe necessary. It updates thru update manager. If you already have 10.10 you can follow [this]("http://www.ubuntu.com/testing/natty/alpha1"). 

Also I answered you earlier in this thread.
I did the upgrade to Natty  11.04 this way and it worked fine and went quickly. So far 

I have had only one problem, but I am not sure the upgrade caused it. My desk top panel disappeared, but I was able to restore it. That has happened before in previous
Ubuntus.

---

### Post by scouser73 on 2011-03-15
> **Learning Linux 2011 said:**
> Hi,

I am new to Ubuntu Linux and forums.

What happens when 11.04 comes out?  How do I upgrade?  Is it a major ordeal like Windows?  

I am using 10.10 now.

You can upgrade to 11.04 through Update Manager or you can do a clean install of 11.04.

---

### Post by AnimalMagic on 2011-03-15
> **Learning Linux 2011 said:**
> Thank you for your posts, but you might be missing what I originally wanted.

I'm not so much interested in whether I should upgrade or not, I am mostly interested in how it is actually done technically.

Do you have to wipe the drive and reinstall?  Or do you do it through a software upgrade/update? Or something else?

I have alternative drives and swap them when upgrading. Keep your /home separate and you can just copy it across. Makes for easy backup, just swap the drives over... :-)

I have seen issues with upgrading, and many people recommend a fresh install.

---

### Post by mastablasta on 2011-03-15
well to me frsh install did the trick. that is until certian updates messed it up again. so... it seems i might as well use the upgrade in the update manger.
 
also why upgrade? with newer version usually come newer drivers. In my case sound became unstable again, certain issues dont' work, so yes i can't wait 3 months after 11.04 is out to try and upgrade to it.

---

### Post by Dutch70 on 2011-03-15
> **Learning Linux 2011 said:**
> Thank you for your posts, but you might be missing what I originally wanted.

I'm not so much interested in whether I should upgrade or not, I am mostly interested in how it is actually done technically.

Do you have to wipe the drive and reinstall?  Or do you do it through a software upgrade/update? Or something else?

You never did say whether you had separate "/" & /home partitions. If you do, then a re-install is the way to go. As was mentioned earlier in the post, you keep your files as well as your settings with a separate /home. Upgrades from my experience are a total PIA by comparison.

---

