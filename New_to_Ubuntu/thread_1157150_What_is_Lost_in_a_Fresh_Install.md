---
title: "What is Lost in a Fresh Install?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by XubuRoxMySox on 2009-05-12
I'm using Ubuntu Intrepid today, but want to switch to Kubuntu 9.04.

I took the advice of some kind veterans that frequent this forum just to help newbies ([COLOR="Purple"]**thank you**[/COLOR], by the way - the *volunteer* tech support is awesome here!) and set up my hard drive partitions like this (80 gig hard drive):

10 Gigs for "**Primary**" (Ubuntu),
5 gigs for **Swap** (more than is necessary but who knows when I add RAM someday), and the rest is **/home**.

When my Kubuntu CD arrives (soon I hope! I can't wait to try out the mysteriously beautiful KDE stuff), I'll do a fresh install. I don't want to keep Firefox and Thunderbird and Abiword for now (I want to try the K-browser and K-mail and K-whatever else just for fun), but it'd be nice to preserve my bookmarks and e-mail settings, pictures, documents, and the pretty fancy fonts I've been collecting. I can always put all that on a CD, but I'm told it isn't necessary if I don't format my **/home** partition. But I have a couple of questions:

1.) - Are *programs* lost in a fresh install if I don't format the /home partition? Again, I don't care if the programs disappear.

2.) - Will those unformatted settings and e-mail info info be automatically imported into K-mail, Konquerer and K-whatever else or is there a way to do it manually?

3.) Files I created under the old file format (EXT3) - will they still be "EXT3" or will they be "transposed" to the key of EXT4? Not that it matters, just curious - I know EXT4 is "backwards compatible," but I want to go *forward* in every possible way.

Thanks in advance,
Robin
(newbie Ubuntu fanboy)

---

### Post by lvleph on 2009-05-12
Yes, programs are lost in a fresh install. Home partition holds your settings mostly. Yes, all settings are typically automagically imported. However, with new programs things do change and therefore things may not all be imported. 

To save a list of installed programs
```

dpkg --get-selections > installed-software

```
To reinstall
```

dpkg --set-selections < installed-software

```

I have yet to use the reinstall command, so...

---

### Post by Didius Falco on 2009-05-12
> **dixiedancer said:**
> I'm using Ubuntu Intrepid today, but want to switch to Kubuntu 9.04.

I took the advice of some kind veterans that frequent this forum just to help newbies ([COLOR=Purple]**thank you**[/COLOR], by the way - the *volunteer* tech support is awesome here!) and set up my hard drive partitions like this (80 gig hard drive):

10 Gigs for "**Primary**" (Ubuntu),
5 gigs for **Swap** (more than is necessary but who knows when I add RAM someday), and the rest is **/home**.

When my Kubuntu CD arrives (soon I hope! I can't wait to try out the mysteriously beautiful KDE stuff), I'll do a fresh install. I don't want to keep Firefox and Thunderbird and Abiword for now (I want to try the K-browser and K-mail and K-whatever else just for fun), but it'd be nice to preserve my bookmarks and e-mail settings, pictures, documents, and the pretty fancy fonts I've been collecting. I can always put all that on a CD, but I'm told it isn't necessary if I don't format my **/home** partition. But I have a couple of questions:

1.) - Are *programs* lost in a fresh install if I don't format the /home partition? Again, I don't care if the programs disappear.

2.) - Will those unformatted settings and e-mail info info be automatically imported into K-mail, Konquerer and K-whatever else or is there a way to do it manually?

3.) Files I created under the old file format (EXT3) - will they still be "EXT3" or will they be "transposed" to the key of EXT4? Not that it matters, just curious - I know EXT4 is "backwards compatible," but I want to go *forward* in every possible way.

Thanks in advance,
Robin
(newbie Ubuntu fanboy)

Hi Robin,

1. Yes, all the programs will be lost in a fresh install.

2. They won't be automagically imported, but each program should assist you in doing that.

3. The files themselves neither know nor care if they are on ext3 or ext4. The operations on those files will be faster because of the improvements over ext3.

One other point - if your current /Home partition is in ext3, you won't get the full advantage of ext4. There is a way to convert the filesystem in place, but I'd recommend backing the files up Just In Case. I've not run across any stories about converting just the separate /Home partition, so I can't say if it's easy, hard, or even possible. You could probably do that from the 9.04 Live CD but you should look for more definitive information before attempting it.  

I hope this helps. Please post back what you find out about the separate /Home conversion to ext4 - it'd be nice to know for the next person that asks about it.

I hope this has helped...

Regards,

Didius

---

### Post by lvleph on 2009-05-12
> **Didius Falco said:**
> 

2. They won't be automagically imported, but each program should assist you in doing that.


Is KDE so different from gnome that it doesn't automatically import all settings (yes I know the don't manage the programs, but the programs referred to are made for KDE). I know when I last did a fresh install almost all my programs had the same settings including thunderbird, firefox, terminal (which makes sense), virtualbox, and the various other programs I use. I can't actually think of one that didn't, I just know there was at least one that I had issue with.

---

### Post by SuperSonic4 on 2009-05-12
> **dixiedancer said:**
> 1.) - Are *programs* lost in a fresh install if I don't format the /home partition? Again, I don't care if the programs disappear.

Yes, they are lost. Program data is stored in /usr (with some in /opt - ie: optional like amarok in my case) whereas settings are stored in /home 

> 2.) - Will those unformatted settings and e-mail info info be automatically imported into K-mail, Konquerer and K-whatever else or is there a way to do it manually?

2. don't forget Dolphin ;). They aren't usually transferred immediately but I think ~/.mozilla and ~/.vlc are.

> 
3.) Files I created under the old file format (EXT3) - will they still be "EXT3" or will they be "transposed" to the key of EXT4? Not that it matters, just curious - I know EXT4 is "backwards compatible," but I want to go *forward* in every possible way.

3. I wouldn't know but I don't think you get all the benefit, rather it would be better to back up whatever you wanted to keep and then reformat /home

---

### Post by XubuRoxMySox on 2009-05-12
> **Didius Falco said:**
> 
One other point - if your current /Home partition is in ext3, you won't get the full advantage of ext4. There is a way to convert the filesystem in place, but I'd recommend backing the files up Just In case. I've not run across any stories about converting just the separate /Home partition, so I can't say if it's easy, hard, or even possible. You could probably do that from the 9.04 Live CD but you should look for more definitive information before attempting it.  


Hi Didius,

In that case I'll put 'em all on a CD and mark the /home directory for formatting. That'll make it EXT4, correct? Then my documents and pictures and whatnot will all be "converted" when I put them back on the hard drive, right?

Thanks,
Robin

---

### Post by Didius Falco on 2009-05-12
> **lvleph said:**
> Is KDE so different from gnome that it doesn't automatically import all settings (yes I know the don't manage the programs, but the programs referred to are made for KDE). I know when I last did a fresh install almost all my programs had the same settings including thunderbird, firefox, terminal (which makes sense), virtualbox, and the various other programs I use. I can't actually think of one that didn't, I just know there was at least one that I had issue with.

dixiedancer is moving from Gnome apps to KDE ones, so it wouldn't be importing the old settings to the newer version of the same app, it would be Firefox to Konquerer, etc. Maybe the fresh install will act differently, but  when I loaded KDE into my Gnome setup, nothing was imported automagically.

AAMOF, when I installed 9.04, it didn't even offer to import any settings, it just flew on by that. I found that a bit of a relief, because during the beta, that gave me tons of grief. It caused more than one install attempt to fail.

Regards,

Didius

---

### Post by Didius Falco on 2009-05-12
> **dixiedancer said:**
> Hi Didius,

In that case I'll put 'em all on a CD and mark the /home directory for formatting. That'll make it EXT4, correct? Then my documents and pictures and whatnot will all be "converted" when I put them back on the hard drive, right?

Thanks,
Robin

They sure would, dixiedancer. Not a bad idea to have a separate backup of that stuff anyway. CDs are pretty cheap nowadays, and it's a good idea to get in the habit of backing up.

After you get everything set up the way you want it, you should take a look at RemasterSys, linked in my Sig. It will make a bootable, installable backup of your system to either CD or DVD if you need more room. That way, you always have a way to reset to your preferred configuration. It makes backing up a breeze.

Regards,

Didius

---

### Post by abhiroopb on 2009-05-12
You can use the following guide to re-install programs:

[http://ubuntuextreme.blogspot.com/2008/12/problem-you-want-quick-and-effecient.html](http://ubuntuextreme.blogspot.com/2008/12/problem-you-want-quick-and-effecient.html)

---

### Post by presence1960 on 2009-05-12
> **dixiedancer said:**
> I'm using Ubuntu Intrepid today, but want to switch to Kubuntu 9.04.

I took the advice of some kind veterans that frequent this forum just to help newbies ([COLOR="Purple"]**thank you**[/COLOR], by the way - the *volunteer* tech support is awesome here!) and set up my hard drive partitions like this (80 gig hard drive):

10 Gigs for "**Primary**" (Ubuntu),
5 gigs for **Swap** (more than is necessary but who knows when I add RAM someday), and the rest is **/home**.

When my Kubuntu CD arrives (soon I hope! I can't wait to try out the mysteriously beautiful KDE stuff), I'll do a fresh install. I don't want to keep Firefox and Thunderbird and Abiword for now (I want to try the K-browser and K-mail and K-whatever else just for fun), but it'd be nice to preserve my bookmarks and e-mail settings, pictures, documents, and the pretty fancy fonts I've been collecting. I can always put all that on a CD, but I'm told it isn't necessary if I don't format my **/home** partition. But I have a couple of questions:

1.) - Are *programs* lost in a fresh install if I don't format the /home partition? Again, I don't care if the programs disappear.

2.) - Will those unformatted settings and e-mail info info be automatically imported into K-mail, Konquerer and K-whatever else or is there a way to do it manually?

3.) Files I created under the old file format (EXT3) - will they still be "EXT3" or will they be "transposed" to the key of EXT4? Not that it matters, just curious - I know EXT4 is "backwards compatible," but I want to go *forward* in every possible way.

Thanks in advance,
Robin
(newbie Ubuntu fanboy)

you may want to be picky about which config files you leave in your /home folder when you install kubuntu, unless you are going to keep all those settings the same. When I tried Kubuntu I learned the hard way because there were a lot of settings in my /home I particularly didn't want with Kubuntu. I learned from experience when switching to a different desktop (Gnome to KDE) to just copy my personal data over  to /home from my /home backup and configure everything from scratch. I had applet settings and such from the gnome panels that I didn't want in Kubuntu.

To save your firefox and thunderbird settings & bookmarks back up your . mozilla and .mozilla-thunderbird folders located in your /home. These have everything in them including your profile, bookmarks, settings etc.

---

### Post by abhiroopb on 2009-05-12
Btw I don't think you need 5gb of swap! I have 2.5 and I've never even hit 1gb :)

---

### Post by XubuRoxMySox on 2009-05-12
[SIZE="7"][COLOR="Purple"]Thank you[/COLOR][/SIZE] one and all for the very valuable help!

I think I'll just back up the documents and pictures and fonts, abandon the settings and reformat the /home file beacause:

1.) - I'm changing from EXT3 to EXT4, and

2.) - I'm changing from Gnome (actually from [LXDE]("http://lxde.org") which is pretty, lightweight, and speedy - I might come back to it but I just want to play with K-stuff for awhile to see what all the fuss is about over KDE). I don't think the old settings are going to be compatible anyway, and I want to make the most of the new EXT4 benefits.

I'm sure the info in this thread will be very helpful to others, though, and to me too the next time I upgrade.

Y'all are awesome! Again, [SIZE="6"][COLOR="Purple"]thank you![/COLOR][/SIZE]

A newbie Ubuntu fanboy who is really grateful for your help, ):P

Robin

---

### Post by lvleph on 2009-05-12
Woops I guess I missed that the OP was moving from Ubuntu to Kubuntu.

---

### Post by XubuRoxMySox on 2009-05-12
> **lvleph said:**
> Woops I guess I missed that the OP was moving from Ubuntu to Kubuntu.

[FONT="Comic Sans MS"]LOL, no matter, your advice is still quite valuable for anyone who is doing a fresh install rather than an upgrade. I appreciate it!

-Robin[/FONT]

---

