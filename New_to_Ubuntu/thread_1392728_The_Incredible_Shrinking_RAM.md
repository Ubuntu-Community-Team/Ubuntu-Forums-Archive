---
title: "The Incredible Shrinking RAM"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by MichaelBurns on 2010-01-28
I am running the live CD of jaunty.  I have no hard drive.  I have 1 GB of RAM.  After I have just booted, I open (nautilus) to view my home folder (user name "ubuntu").  At the bottom-left of the window is shown the amount of free space:  475.0 MB.  I assume that this indicates the amount of RAM that is unused.  Of course, as I install programs, this number will decrease; I do understand that.

So, as part of my experimentation, I wanted to install latex.  (I guess the apt-get codename for it would be "texlive", but anyway I have all of the *.deb files saved to my flash drive, so I just dpkg the folder where I keep them.)  However, the first thing that I noticed was that, when I saved the text file to my flash drive that I used to keep a record of this experiment, the free space went down by 0.1 MB to 474.9 MB.  Why?  Then, after installing latex, the free space went down to 219.3 MB.  (Geeze, I really need to strip down that installation!  There must be a gagillion things in latex that I never use.  I never noticed how huge it is.)  Anyway, I did expect some RAM to be used up in the latex install (just not that much).

Then, I connected to the wireless internet by turning it on at the hard switch, and then selecting an available network in the NetworkManager applet.  This cost me another 0.1 MB, leaving me with 219.2 MB.  Why?

Simply opening firefox (from the icon on the task bar) cost a whopping 3.4 MB, leaving me at 215.6 MB.  I realize that programs are loaded into RAM, and I was actually surprised that firefox uses so little.

Next, I performed my habitual firefox preferences ceremony:  changing home page, disabling java and javascript, setting fonts to 16 pt, unchecking form and password saves, setting clear private data stuff, setting cache to 0 MB, setting backspace action to Windows default, etc. etc..  That set me back another 3.5 MB; now I'm down to 210.4 MB.  Why?

Then, just for kicks, I unmounted my flash drive, locked the screen and closed it, attended to chores around the house, came back and remounted the flash drive.  This cost me a whopping 4.4 MB, leaving me with 206.0 MB.  Why?

That ended my official preliminary experiment.  However, I also accidently acquired one last datum.  I ran latex, and probably ran various other programs.  But I never installed anything else, and I never saved anything to the native file system (always to the flash drive).  Then, I closed all programs, locked and closed the screen for the night, and waked up the computer this morning, to find 160.6 MB of free space.  **That's a 45.4 MB loss of space, for no apparent reason!**  Why!?!

I have been running the live CD now for about a month, and I have several times encountered the problem of "out of space" errors when I want to install another program.

So, here's my question(s):
Why do these trivial tasks cause the computer to eat up space (permanently)?  How can I prevent this (or at least greatly reduce it)?  Can someone suggest a different distro where I won't experience this problem?

---

### Post by ruivilela on 2010-01-28
My first guess is that the kernel is doing caching. Open shell and type "free -m". When there is no space it will discard it immediatly. If you are worried with ram consumption, maybe Ubuntu is not the best for you. (kidding)

---

### Post by warfacegod on 2010-01-28
That free space on the bottom left is showing you how much space is left on the flash drive not your RAM.

---

### Post by warfacegod on 2010-01-28
Scratch my last comment. It's wrong.

What is happening, I believe, is that when you install something Live, it installs it into the RAM. It does that because your Live OS is installed in the RAM as well. Basically, it treats your RAM as a hard drive and real RAM at the same time. All those changes you are making, preferences, home page what ever, all go to the RAM. They can't go anywhere else, after all.

---

### Post by warfacegod on 2010-01-28
By the way. It sounds like this whole thing you do is quite a hassle. Whu not buy a cheap HDD?

---

### Post by Enigmapond on 2010-01-28
Really as the minute you power off.....you fliush all those changes, settings, ect. as they're not being saved anywhere and you will go though that every time you boot up..:)

---

### Post by MichaelBurns on 2010-01-28
Thanks for the suggestions, everyone.

My main concern is why my configurations/settings require so much memory.  I do understand that, when I install a program, it must go into RAM.  I do understand that, when I change a setting from default, a config file must be saved to RAM.  What I don't understand is why the config files need to be MB's in size.

Here's a thought:  can I redirect storage to my flash drive?

Regarding the hdd issue:  believe me, I definitely know how much of a hassle it is.  I have gotten into the habit of leaving the laptop on overnight.  I would love to have a new hdd.  I am currently unemployed, and so even $50 on a new hdd is hard to justify (since I can get by with the live cd, which boots from total shut down to logged in in under 5 minutes, and then installing extra programs on the order of a minute each).  You better believe that, the moment I get a steady cash flow, it's all about a new hdd.  (I would rather get a new laptop, but I can't find one that suits me.  I prefer hardware control of volume and wireless.)

---

### Post by warfacegod on 2010-01-28
> **MichaelBurns said:**
> Thanks for the suggestions, everyone.

My main concern is why my configurations/settings require so much memory.  I do understand that, when I install a program, it must go into RAM.  I do understand that, when I change a setting from default, a config file must be saved to RAM.  What I don't understand is why the config files need to be MB's in size.

Here's a thought:  can I redirect storage to my flash drive?

Regarding the hdd issue:  believe me, I definitely know how much of a hassle it is.  I have gotten into the habit of leaving the laptop on overnight.  I would love to have a new hdd.  I am currently unemployed, and so even $50 on a new hdd is hard to justify (since I can get by with the live cd, which boots from total shut down to logged in in under 5 minutes, and then installing extra programs on the order of a minute each).  You better believe that, the moment I get a steady cash flow, it's all about a new hdd.  (I would rather get a new laptop, but I can't find one that suits me.  I prefer hardware control of volume and wireless.)

I know what you mean about cash. I run my own roofing business. It's winter here. Have you considered installing ubuntu into your flash drive?

---

### Post by nothingspecial on 2010-01-28
***EDIT***


On 2nd thoughts this is an unhelpful post in the beginners forum.



***EDIT***

---

### Post by nothingspecial on 2010-01-28
> **MichaelBurns said:**
>   Can someone suggest a different distro where I won't experience this problem?

Puppy linux and DSL (Damn small linux) are designed to run in ram.

They are exactly what you (without a hard drive) are looking for.

---

### Post by Paqman on 2010-01-28
If you've got a 2GB+ USB stick knocking about i'd be inclined to set it up as a LiveUSB with persistence. They're dirt cheap, someone might even have one they can lend you until you can afford a hard drive.

---

### Post by Puppyite on 2010-01-28
> **nothingspecial said:**
> Puppy linux and DSL (Damn small linux) are designed to run in ram.

They are exactly what you (without a hard drive) are looking for.

Puppy Linux loads itself and all [bundled software](http://www.puppylinuxfaq.org/category/9/bundled-software.html) completely in [128MB RAM]( http://www.puppylinuxfaq.org/content/17/57/en/minimum-hardware.html).

Puppy Linux can also be [installed](http://www.puppylinuxfaq.org/content/17/78/en/automated-install-procedure-save-file-431.html) on nearly any type of removable media including USB, SD or multi-session CD+RW or DVD+RW.

I am author of [Puppy Linux FAQ](http://www.puppylinuxfaq.org/) the definitive guide for using and enjoying Puppy Linux. I invite you to visit my site. There is no easier way to get started with Linux than by visiting [www.puppylinuxfaq.org](www.puppylinuxfaq.org)

Regards,
Puppyite

---

### Post by audiomick on 2010-01-28
> **Paqman said:**
> ... set it up as a LiveUSB with persistence.

Here
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

although I saw a post from Herman not long ago in which he said he doesn't know why anyone does that these days. I can't remember his reasons. I will see if I can find it.

found it
[http://ubuntuforums.org/showthread.php?t=1384175](http://ubuntuforums.org/showthread.php?t=1384175)
I am talking about post #5
I think his point was that if you use a USB external drive, you don't need a persistant install.

---

### Post by Paqman on 2010-01-28
> **audiomick said:**
> 
although I saw a post from Herman not long ago in which he said he doesn't know why anyone does that these days. I can't remember his reasons. I will see if I can find it.

Presumably because it's a couple of mouse clicks to set it up on a USB stick.

---

### Post by wirelessmonkey on 2010-01-28
Though I'm not certain where all the space goes, I am certain that you aren't paying attention to your system logs.

---

### Post by MichaelBurns on 2010-01-29
Thanks to nothingspecial and puppyite for the suggestions regarding puppylinux and dsl.  I have tried dsl, but I couldn't figure out how to get wireless to work.  I might try it again.  I will also look into puppy linux.

Also, thanks to warfacegod, paqman, and audiomick (I hope that I didn't forget anyone) for the suggestions regarding usb with persistence.  I noticed that recently when I was browsing around for a solution to a related problem.  I will revisit it.  However, if I recall correctly, my laptop would need to be able to boot from the usb.  My laptop cannot boot from usb.  (My laptop is so old that it still has the option to boot from fdd.)

wirelessmonkey, you are correct.  I have not developed a mature appreciation for the logs.  I am still in the stage of being overwhelmed by all of the differences and self-reliance involved after migrating from Windows a few months ago.  I have tried to look at log files, but at this point, to me they just seem randomly scattered everywhere throughout the filesystem.  I have no idea where to look.  (I'm not complaining or anything; just making excuses.)

---

### Post by audiomick on 2010-01-29
> **MichaelBurns said:**
> .. if I recall correctly, my laptop would need to be able to boot from the usb.

I only flew over that, but I think I read something about booting from CD and saving the persistent stuff to a USB stick. Could be wrong though...

---

### Post by ovid9 on 2010-01-29
> **MichaelBurns said:**
>  However, if I recall correctly, my laptop would need to be able to boot from the usb. My laptop cannot boot from usb. (My laptop is so old that it still has the option to boot from fdd.)
 
You can boot puppy either from a CD or creating a floppy boot disk that THEN allows you to boot off your USB.  
 
I know this is possible because I had a friend do it on an ancient laptop with no ability to boot from USB or an internal CD drive (it was USB as well).  
 
Puppy now works on that machine and she uses it regularly.  So, it can be done, but it just adds some steps.
 
Sorry, I can't fill you in on the steps as she lives 900 miles away and I was "helping" via IM and email.

---

### Post by Bodsda on 2010-01-29
I don't understand the point of a persistent LiveUSB install. Why not just install it normally onto the usb drive?

For minimalistic install I usually go for a stripped down ubuntu + fluxbox implementation.

---

### Post by MichaelBurns on 2010-01-29
> **Bodsda said:**
> I don't understand the point of a persistent LiveUSB install. Why not just install it normally onto the usb drive?My laptop cannot boot from usb.  I actually do have a flash drive with an ubuntu installation (I used unetbootin to set it up from the iso image).  It will not work in my laptop (but it did work in an eeepc).  My laptop's bios doesn't have an option to boot from usb; only cdrom, hdd, fdd, and lan.

---

### Post by ovid9 on 2010-01-29
> **MichaelBurns said:**
> My laptop cannot boot from usb. I actually do have a flash drive with an ubuntu installation (I used unetbootin to set it up from the iso image). It will not work in my laptop (but it did work in an eeepc). My laptop's bios doesn't have an option to boot from usb; only cdrom, hdd, fdd, and lan.
 
So, don't worry about booting from USB.  Either make a CD, or make a boot floppy that then allows you to load it up from the USB.
 
For option #2 this might give you some direction:
 
[http://www.puppylinux.com/hard-puppy.htm](http://www.puppylinux.com/hard-puppy.htm)

---

### Post by wirelessmonkey on 2010-02-05
My point was actually that your system logs are growing in size with each activity. Every update, cron run, system mail, rotate, firewall, etc... are growing the size of your logs. This takes up physical memory, as they aren't written to disc when using a livecd or persistent system.

---

### Post by MichaelBurns on 2010-02-25
I tried the persistent usb, but it didn't work.  Here's basically what I did:

- reformat my usb stick with a single ext3 partition labeled "casper-rw"
- reboot, press F6, type " persistent" (with the space in front of it), and then continue loading OS from the live CD

I first tried this all from command line, using fdisk, mkfs, etc., according to the [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) instructions.  I tried it with ext2 instead of ext3 this first time (the instructions say that this is OK, and even mention that ext2 is probably better for usb sticks).  For the second attempt, I just used GParted for everything, and I made the fs ext3.  I'm a bit confused by the instructions, because they say that you have to use the command line to make the "casper-rw" label, but GParted let me assign a label, and I never needed the command line.

Anyway, in both attempts, I looked in the casper-rw file system, and I saw various folders, such as home, var, and etc, which were apparently automatically created at bootup.  So, "something" is happening, but none of my settings are being saved, and my RAM is still shrinking.

Anyone have a suggestion?  Something that I haven't tried?

---

### Post by egalvan on 2010-02-25
I don't know where Georgetown is, but if it's any size at all, try to find a local Mom&Pop style of computer repair shop,
and ask if they have a 20-30GB laptop drive they can sell cheap.
Usually they have no warranty.
Such "small" drives are usually considered "obsolete"
They may just give it away...

Another place is a local Computer Club, or a high school or college/university computer course...

Another (less likely) source is a BigBoxStore such as Best Buy or CompUSA...
Go to the repair desk and ask if they can find you a small (20-30GB) laptop drive, that a low price is the main factor.

If you are lucky in your quest, then download Darik's Boot And Nuke
dban.org
and wipe the drive clean, then load a Linux.

BTW, PartedMagic is another excellent small distro, oriented towards disk set-up, but rather full-featured none-the-less.

---

### Post by MichaelBurns on 2010-02-26
Thanks for your suggestions, egalvan.  However, I have become obsessed to accomplish a persistent system without a harddrive.  Does anyone else have an idea of what I could try to get the persistence to work?

---

### Post by knurledflanges on 2010-02-26
Did you ever check out "free -m"? It will show you how much ram is being taken up by cache.
I'm not an expert on this, but one thing that it's not clear that you're taking into account is that until there's actually no memory left, it doesn't necessarily matter how much a given app reduces your free space number. Up until that point, if hundreds of Mbs of not very useful stuff gets cached in free memory, that's simply what the memory is there for; it doesn't necessarily hurt performance. If the computer didn't manage the memory in a way where the cached stuff gets cleared out as new programs get loaded or, in the case of a LiveCD session's virtual drive, as new data needs to get written, then that would be a problem. But until it's not doing that, or until there's actually a performance hit of some kind, there is no problem. You may already know this, but I wanted to mention it because for years I didn't understand, until pretty recently when a friend was trying to figure out why certain programs that seem like they should be lightweight were taking up so much memory.
Also, if you haven't tried Puppy yet, you really should. It's very fast on old hardware and it's more or less designed to be booted off CD and save user settings and data on USB sticks.

---

### Post by MichaelBurns on 2010-02-26
> **knurledflanges said:**
> Did you ever check out "free -m"? It will show you how much ram is being taken up by cache.Yes.  What can I do with that information?

> **knurledflanges said:**
> ... until there's actually no memory left, it doesn't necessarily matter how much a given app reduces your free space number.
...
If the computer didn't manage the memory in a way where the cached stuff gets cleared out as new programs get loaded or, in the case of a LiveCD session's virtual drive, as new data needs to get written, then that would be a problem.Well, I don't know about the performance issues related with excessive ram storage, but I presume that at least there is some additional heat produced.  Anyway, I have encountered exactly this problem of running out of space.  In fact, I have experienced several ocassions where the computer becomes more and more unresponsive and then just literally shuts down.

I am in the process of trying to figure out how to build my own ubuntu so that I can kill this issue once and for all, but it's quite daunting and will no doubt take me several months.  In the meantime (and probably a good educational excercise), I want to figure out at least how to redirect storage to my flash drive (instead of my ram for now, or even hdd when I finally get one).  Apparently, the way to do that is to use so-called persistence, but I am open to any other method (within jaunty) that anyone cares to suggest.

I want to be in charge of how my computer operates.  I think that anyone who has migrated from Windows can appreciate that sentiment.  (Or am I the only one???)

> **knurledflanges said:**
> ... if hundreds of Mbs of not very useful stuff gets cached in free memory, that's simply what the memory is there for;I don't know what you mean by caching in this sense, but the purpose of *my* ram is "number crunching" (storing array variables and such), not to store permanent configuration data, and I think that program state information should be expunged from ram after I close the program.  100's of MB of useless crap is 100's of MB worth of crunchable space that I can't use, and that's actually a *big* problem.

> **knurledflanges said:**
> Also, if you haven't tried Puppy yet, you really should. It's very fast on old hardware and it's more or less designed to be booted off CD and save user settings and data on USB sticks.I would be willing to try it, but apparently I don't have access to my cd tray while I'm running off of the live cd.  (I'm hoping that persistence will give me access to the cd tray.)  And then, once I get a hdd so that I can free up my hdd, this whole problem goes away (except in principle).  So, trying puppy is kind of a catch-22.  Not that I'm inclined to try a new distribution anyway; this is the ubuntu forums after all.

Please try to understand, the moment that I decide to go out and spend money on my problem, this whole situation will completely change.

---

### Post by Don1500 on 2010-02-26
I've run puppy for a while off of a 1G pen drive and it worked very well. It saved all of my configs, ran firefox, flash and every other firefox app I needed. Set up was easy and uneventfull. Don't expect to have everything but you'll have what you need.

---

### Post by egalvan on 2010-02-27
> **MichaelBurns said:**
> 
Well, I don't know about the performance issues related with excessive ram storage,
 but **I presume that at least there is some additional heat produced**.

Absolutely no extra heat produced. Dynamic RAM circuitry is never really "OFF", even if it is not "storing data".
 It's always storing a ONE or a ZERO, there are no "intermediate" values...
(note...NOT to be confused with "sleep" or "hibernate" states, in which some of the circuity is grossly under-clocked, or actually shut down... 
in this case, RAM no longer has "valid_data", and needs to be re-loaded.)


> I would be willing to try it, but apparently **I don't have access to my cd tray while I'm running off of the live cd**.

Puppy runs totally in RAM if it finds 256M or more, and frees up the optical drive.

>    So, trying puppy is kind of a catch-22.
  Not that I'm inclined to try a new distribution anyway; this is the ubuntu forums after all.

Yep, it's the Ubuntu forums, but many of us have a liking for other *nixen...
Lots of us run multiple distro's.
Puppy is a perennial favorite for it's small size and excellent performance on smaller RAM.
Mint, Crunchbang and SliTaz are others.

> Please try to understand, the moment that I decide to go out and spend money on my problem, this whole situation will completely change.

For some folks, "time is money"
for other folks, "money is time"

---

### Post by MichaelBurns on 2010-02-27
> **egalvan said:**
> Puppy runs totally in RAM if it finds 256M or more, and frees up the optical drive.How do I get a running puppy into ram?  (That sounds like the beginning of a joke.)  The only way that I know to do it is to boot up with a puppy cd.

> **egalvan said:**
> For some folks, "time is money"
for other folks, "money is time"I don't think that either of those are true for me right now (unemployed), but hopefully soon ...  Anyway, the reason that I'm trying to learn linux is not because I put a monetary value on my time.  I would say that time allows experience and education, and I value those things.

---

### Post by egalvan on 2010-03-02
> **MichaelBurns said:**
> Question:
How do I get a running puppy into ram?

Answer:
You don't. you get a puppy in ram to run... (cheap rim-shot :P)


sorry, could not resist...


 > The only way that I know to do it is to boot up with a puppy cd.

Either a LiveCD or a bootable USB.
I think there may be a floppy-based boot option... floppy disks are long gone from my work-a-day machines, so no experience in this.
The website will have specifics.

---

### Post by shihkster1015 on 2010-03-02
@[egalvan]("http://ubuntuforums.org/member.php?u=521362") lol

I think there's a gadget where you can use a RAM stick as USB, but that requires a constant supply of power. 
Data stored in a RAM dies out once there is no power, so installing puppy on a stick of RAM is impossible. Unless you want to use the gadget i'm talking about and then freeze the RAM to -100C :P

---

### Post by MichaelBurns on 2010-03-02
It seems that either no one is understanding my predicament or I'm just a complete moron.

I have no way to burn a puppy cd because jaunty will not relinquish my cd tray (but I can't figure out why it needs the cdrom once it's loaded into the ram).

I cannot boot from usb on my laptop (actually, I just read something in one of my recent google searches that gives me one more idea to try, but I will do that later).

If either of the above two situations were to change, then I don't need puppy anymore.  So, unless I can load a running puppy into ram from an already booted and running jaunty, then I don't understand how puppy can help me.

---

### Post by bodhi.zazen on 2010-03-02
> **MichaelBurns said:**
> It seems that either no one is understanding my predicament or I'm just a complete moron.

I have no way to burn a puppy cd because jaunty will not relinquish my cd tray (but I can't figure out why it needs the cdrom once it's loaded into the ram).

I cannot boot from usb on my laptop (actually, I just read something in one of my recent google searches that gives me one more idea to try, but I will do that later).

If either of the above two situations were to change, then I don't need puppy anymore.  So, unless I can load a running puppy into ram from an already booted and running jaunty, then I don't understand how puppy can help me.

I believe you are not understanding how the live CD or RAM works in Linux.

In terms of RAM, you need to examine your RAM use with the command free (free -m).

See :

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

The other part of your question, how a live CD works, I do not know the technical answer to, but I can tell you, yes you will run out of space. If you install, then remove an application, the space is not available again.

As an over view , if you are interested, see :

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

In terms of a broader answer to your problem, what people are telling you is that the Ubuntu Live CD is designed to test then install Ubuntu. There are alternate distros better suited to your situation, Puppy, Slax, etc. These distros will , for example, load into RAM and release your CD drive so you can burn CD.

See [http://cyti.latgola.lv/ruuni/](http://cyti.latgola.lv/ruuni/)

So while you may not have the ability to burn a CD, is it possible for you to have a friend burn one for you ? CD burners are not that difficult to find.

---

### Post by MichaelBurns on 2010-03-02
I'm think I'm leaning towards being a moron.  Thanks for being patient and trying to restate the suggestions from a slightly different perspective ;)

> **bodhi.zazen said:**
> The other part of your question, how a live CD works, I do not know the technical answer to, but I can tell you, yes you will run out of space. If you install, then remove an application, the space is not available again.That is actually not true.  For example, I was just recently experimenting with different latex installs.  I would install one, see how much space was taken up, and then remove it.  Then, I would install a different one.  When all was said and done, and I removed the last one, I was only missing a few MB (whereas even the smallest latex installation required 90 MB).

To clarify, I start out with 475MB of free space.  Then, I install some package, and the free space goes down to say 350MB.  Then, I remove the package (remove,autoremove,purge,clean,autoclean), and my free space is at say 470MB.  So, *most* of my free space comes back after removing an installed package (and cleaning up).

> **bodhi.zazen said:**
> So while you may not have the ability to burn a CD, is it possible for you to have a friend burn one for you ? CD burners are not that difficult to find.OK, fine.  (You're assuming that I have friends ;) )  I actually do know people who I could ask to do this for me, but that's not the point.  If I do decide to bother one of the few people I know who might be willing to do this for me, then I don't understand why I would ask them for a puppy disk; why not just ask them for a karmic disk set up with persistence by default?

---

### Post by bodhi.zazen on 2010-03-02
> **MichaelBurns said:**
> That is actually not true.  For example, I was just recently experimenting with different latex installs.  I would install one, see how much space was taken up, and then remove it.  Then, I would install a different one.  When all was said and done, and I removed the last one, I was only missing a few MB (whereas even the smallest latex installation required 90 MB).

To clarify, I start out with 475MB of free space.  Then, I install some package, and the free space goes down to say 350MB.  Then, I remove the package (remove,autoremove,purge,clean,autoclean), and my free space is at say 470MB.  So, *most* of my free space comes back after removing an installed package (and cleaning up).

Exactly, each time you loose some space, and over time it adds up. I do not know how or why the space is lost, but I have observed the phenomena.

> OK, fine.  (You're assuming that I have friends ;) )  I actually do know people who I could ask to do this for me, but that's not the point.  If I do decide to bother one of the few people I know who might be willing to do this for me, then I don't understand why I would ask them for a puppy disk; why not just ask them for a karmic disk set up with persistence by default?Well, you may of course use any distro you choose, but what people are trying to tell you is that there may be better distros (tools) to use for your intended purpose.

I also like this one :

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

And Slax 

The point is that these smaller distros will use less ram and are possibly better suited for your specific needs. So long as they have the features you like you can use most of yoru RAM for applications.

The first one I gave you , 

[http://cyti.latgola.lv/ruuni/](http://cyti.latgola.lv/ruuni/)

Will load fully into RAM and release you CD ROM. This means you can use your CD ROM for other things, music, burning a CD, whatever you like.

I would downlad the newest version, here:

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/AUSTRUMI-1993.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/AUSTRUMI-1993.shtml)

This latter distro uses 44 Mb RAM (with some in buffers). It has a few awkward features so it depends a bit on your tolerance for such things.

---

### Post by MichaelBurns on 2010-03-02
@bodhi.zazen (and everyone else, really):

Thank you for your patience and many helpful suggestions.  After rereading from the very beginning, I think that it is time to mark this thread as "solved".

Conclusion:  either I need to grow a pair of programicles to get down and dirty forcing jaunty to be my slave, or I need to relax one of my strict conditions for how I am using my laptop.

---

### Post by bodhi.zazen on 2010-03-02
Here is a screenshot of Slitaz running in Astrumi running in Virtualbox (downloaded the Slitaz ISO).

Virtualbox is using 512 Mb ram

[[IMG]http://bodhizazen.net/img/Small.JPG[/IMG]]("http://bodhizazen.net/img/Large.JPG")

Click on the image for a larger view :twisted:

---

### Post by Chris Edgell on 2010-03-04
> **bodhi.zazen said:**
> Exactly, each time you loose some space, and over time it adds up. I do not know how or why the space is lost, but I have observed the phenomena.

Why?
Why?
Why?

It reminds me of children asking their parents really hard questions... questions that barely have answers.  "Is heaven very far?"

And now you have received your answer... "We don't know"

Not to demean the answers, the solutions offered, the discussion: leave it to bodhi to answer your queries honestly and directly AND to affirm your observation of the phenomena; I like this a lot.

To all of you others: please forgive me if I seem to be putting something in a nutshell, I mean no offense.

Extraneous comes to mind at times, but many people cannot hone in on the essential question (especially when the answer is "I don't know") and instead offer ways around the need to ask your question.  Although I must acknowledge that Michael asked other questions along the way.  And monkey-what-was-it raised a good point about the LOGS...(sorry, I forgot your name...do you think that's the real answer to where that RAM goes?)

---

### Post by wirelessmonkey on 2010-03-04
wirelessmonkey ;)

And yes, the memory either goes to logs or to processes, it doesn't "just disappear"

---

### Post by Chris Edgell on 2010-03-10
Can I get any comments on this post?

[http://ubuntuforums.org/showpost.php?p=8437208&postcount=8](http://ubuntuforums.org/showpost.php?p=8437208&postcount=8)

---

### Post by Sir Jasper on 2010-03-10
Calling Chris @ # 41,

I expect so, but you would be better to open a new thread (or re-open your link) since your query seems to relate to Drive Space and this thread seems to be about RAM.

My regards

---

