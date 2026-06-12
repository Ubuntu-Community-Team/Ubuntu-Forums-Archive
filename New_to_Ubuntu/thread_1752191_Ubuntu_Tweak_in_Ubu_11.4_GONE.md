---
title: "Ubuntu Tweak in Ubu 11.4 GONE"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Not unique on 2011-05-07
I recently upgraded from Ubu 10.10 to 11.4 and had many problems least of all graphical errors with unity etc. but also some apps stopped working or even disappeared, Ubuntu Tweak was one of them and I am a big fan of Ubu Tweak I had so much trouble I just reinstalled Ubu 10.10.
But I wondered if any one else had similar problems?

---

### Post by Rasa1111 on 2011-05-07
I didnt upgrade,  but installed 11.04 on its own partition, side-by-side my 10.10 install..

 But I installed Ubuntu Tweak in my 11.04 no problem. 

If you can manage it..
Try not to do the "upgrade", But do a fresh install. 
Or at least do the "upgrade" from the 11.04 disc, not from update manager.
That often causes many unwanted problems. 

 Anyway,  Tweak works perfectly in my 11.04 install.

Good luck.

---

### Post by Not unique on 2011-05-07
My problem was having all the apps including Ubuntu tweak and when I UPDATED then things went wrong and I had to reinstall several apps including also Transmission and VLC many other people have also had problems and that is what I wanted to see about.

---

### Post by Melophonic on 2011-05-07
Ubuntu Tweak doesn't come in 11.04, so you'll have to do a fresh install! ;)

If you want it, go through this [link!]("http://ubuntu-tweak.com/")
Happy Tweaking! :)

---

### Post by Rasa1111 on 2011-05-07
I think I have read somewhere recently that after an upgrade like that, some apps. would need to be re-installed. 

hmm..
For some reason i thought it was just apps. with PPA's..
But Im not sure. 

 Anyway, after reading many, many failed upgrade stories,
I've always decided against the "upgrade", and just do a fresh install,
and I don't run into all the problems I see with failed 'upgrades'. 

Therefore, I always suggest a clean, fresh install. ;)

So, Everything is working for you again?

---

### Post by beew on 2011-05-07
Upgrade only works if you have a pristine system (no ppa, no proprietary graphic card etc) , it takes several hours so there is a good chance that it may go wrong and it may mess up your existing softwares if they have the wrong versions. It is a lot easier to do a fresh install, take a bout 20 minutes and maybe another half an hour to an hour to reinstall all your softwares. It would be even easier if you have a separate /home partition.

---

### Post by Not unique on 2011-05-07
All the APPs affected where the latest via Ubuntu tweak through there source centre so you may be right about the PPA's except for VLC as I remember.

---

### Post by beew on 2011-05-07
> **Rasa1111 said:**
> 
For some reason i thought it was just apps. with PPA's..
But Im not sure. 


Ubuntu tweak is not in the official repo so the OP must have installed it either with PPA or downloading a .deb. I don't think it will survive upgrade.

Also, if you have installed things from ppas you may get into problems even if you disable the ppas because of version incompatibility and even if the upgrade go through you would actually be downgrading your softwares in many cases.

---

### Post by wilee-nilee on 2011-05-07
Use the authors ppa.
```
sudo add-apt-repository ppa:tualatrix/ppa
```

I have ubuntu tweak running in Oneiric it is the natty linked version.

If you have used the application and upgraded enough times you will know it is rather intuitive it only offers what is available on your setup.

When you upgrade as well all the 3rd party repos are # and need to be reopened in the repo section, from synaptic, or the apt/sources.lists.d

---

### Post by Not unique on 2011-05-07
True the 3ed party  PPA's are disabled so what do you think causes the problems

---

### Post by akand074 on 2011-05-07
> **Not unique said:**
> True the 3ed party  PPA's are disabled so what do you think causes the problems

They always disable by default because external PPAs are designated for certain releases, so when you for example add Ubuntu tweak it'll be written to your sources list as:

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main
```

for example if you added it when in Maverick. This tells the system to send you the version designated for maverick, not Natty. So although the maverick one may still work, to be safe, they disable third party PPAs and expect you to edit and and switch it to Natty. Either way though, like most people said, I definitely recommend a clean install every single time. Matter of fact, I noticed I can fully format my filesystem and do a full clean install and then reinstall all my applications etc. ready to use in a shorter amount of time then an upgrade takes. On top of that I have to spend a lot less time fixing things, cleaning up stuff from the old version after the upgrade. In the future, I definitely recommend you do that (make a separate /home partition for your data so you don't have to wipe/affect those when doing a clean install).

---

### Post by wilee-nilee on 2011-05-07
> **Not unique said:**
> True the 3ed party  PPA's are disabled so what do you think causes the problems

Without reading every word here in the thread, use the ppa, and expect upgrades to remove some 3rd party things, there is a removal gui for you to confirm at least some of the removal, at the very end of the upgrade.

I'm like Rasa1111, I always do fresh installs, but I have at least 4 OS's on the computer now. I like fresh installs it is faster, I know what I need as far as my setup so within about a 1/2 hour of a fresh install I have it setup. I also have images and backups of all the OS's

Here is a link on several methods of making a list of installs, post #2.
[http://ubuntuforums.org/showthread.php?t=1733570](http://ubuntuforums.org/showthread.php?t=1733570)

---

### Post by Not unique on 2011-05-07
Experience has told me to also fresh install as it is cleaner but I never figured out how to format my H-drive in Ubuntu, I also prefer to use synaptic over downloading DEB's or PPA's but that can't always be helped.

---

### Post by jdwhite87 on 2011-05-07
> **Melophonic said:**
> Ubuntu Tweak doesn't come in 11.04, so you'll have to do a fresh install! ;)

If you want it, go through this [link!]("http://ubuntu-tweak.com/")
Happy Tweaking! :)

Thank you for this link!

---

### Post by beew on 2011-05-07
> **Not unique said:**
> Experience has told me to also fresh install as it is cleaner but I never figured out how to format my H-drive in Ubuntu, I also prefer to use synaptic over downloading DEB's or PPA's but that can't always be helped.

You use ppas with Synaptic too. That's why they are nice.

---

### Post by Not unique on 2011-05-07
I guess it's depending on the PPA or the APP it installs (especially if it is alpha or beta) too wether or not you get problems

---

### Post by Paqman on 2011-05-07
> **beew said:**
> Upgrade only works if you have a pristine system (no ppa, no proprietary graphic card etc) 

That's not true. The upgrade process handles proprietary graphics and PPAs just fine.

What it does for PPAs is disable them during the upgrade. After the upgrade is done you'll have to re-enable them. That's a simple as changing the entry in Software Sources from "maverick" to "natty", reloading your sources and reinstalling the package. Easy peasy.

---

### Post by Not unique on 2011-05-07
So why DOES it disable the 3rd party PPA's during update?

---

### Post by satanselbow on 2011-05-07
> **Not unique said:**
> So why DOES it disable the 3rd party PPA's during update?

That one was answered earlier ;)

PPA's are "version specific" ie if you look at the ppa line it will have "maverick" in there somewhere - when you upgrade you no longer have "maverick" - you have "natty" so to be safe the ppa is disabled to prevent any potential configuration problems :D

---

### Post by beew on 2011-05-07
> **Paqman said:**
> That's not true. The upgrade process handles proprietary graphics and PPAs just fine.


Not from many people who have had broken upgrades.


> What it does for PPAs is disable them during the upgrade. After the upgrade is done you'll have to re-enable them. That's a simple as changing the entry in Software Sources from "maverick" to "natty", reloading your sources and reinstalling the package. Easy peasy.
You can do that with a clean install as well if you save your sources (say in your /home partition) There is no advantage upgrading as far as I can tell.

---

### Post by Not unique on 2011-05-07
Nice one Beew saving my PPA sources seems like a good tip.

---

### Post by Paqman on 2011-05-07
> **beew said:**
> Not from many people who have had broken upgrades.


Someone having a bad experience once doesn't mean that the upgrade system can't handle PPAs and proprietary graphics. It can, and to say otherwise is just plain wrong. PPAs *used to* cause problems during upgrades, but that problem was fixed several versions ago by the system simply disabling them during upgrade. It works. I know because i've done it many times.

I'm not saying every upgrade works flawlessly, but neither does every fresh install, as you can see from many posts in this forum.

Just because you personally don't like to upgrade, please don't spread misinformation about it. You're quite entitled to manage your system how you like, but lets stick to the facts when we're advising others.

---

### Post by Not unique on 2011-05-07
Personally I see thousands + more complaints about Ubu 11.4 including plenty about APP problems(APPs need re installing)

---

