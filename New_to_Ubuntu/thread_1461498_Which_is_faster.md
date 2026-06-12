---
title: "Which is faster?"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by IainMc on 2010-04-24
I have been trying out Ubuntu installing with Wubi on a dual boot with a fresh installation of Windows XP Pro on a Pentium-3 850 Mhz Dell Latitude Laptop with 256Mb Ram and 20Gb hard drive.

Initially I tried installing Kubuntu on a 6Gb partition and although I managed to run it I found the interface to be very slow, much slower than Windows XP infact (which actually works quite efficiently).

Next I tried Xubuntu (same size partition) and although it was alot faster I kept getting "crash report detected" messages repeatedly.

Next I installed Ubuntu (which i'd already found to work well from a live CD) using a 9Gb partition and I have found this to work far more efficiently than the other two versions (though not a great deal faster than windows). Although I was initially getting the odd "crash report detected", its not as intrusive as with Xubuntu and it doesn't seem to be affecting its function.

I was under the impression Linux outperforms Windows considerably. Also I had thought that Ubuntu requires more hardware resources than Kubuntu?


Any ideas where I am going wrong? Anything to do with the partition size (I'd like to reduce it to 5 or 6 if I can without slowing Ubuntu down)?

I'd prefer to use the KDE desktop if I can though I am reasonably satisfied with how Ubuntu is running.

---

### Post by howefield on 2010-04-24
Wubi installations are not the way to compare.

If you want like for like, Ubuntu/Whatever needs to be on its own partition. Why would you think otherwise ?

---

### Post by Merk42 on 2010-04-24
> **IainMc said:**
> I have been trying out Ubuntu installing with Wubi ...

That's probably part of your problem right there.
An installation via WUBI doesn't perform as well as a regular installation

I don't want to get into desktop environments, GNOME, KDE, Xcfe, LXDE, because then it'll just end up in Recurring Discussion

---

### Post by NightwishFan on 2010-04-24
A modern Linux is much more resource efficient than Xp (WHICH IS OLD!!!) but also has higher memory requirements. Installing on anything less than 384mb will be slow. You will have to use a specialists distro for old machines, such as Puppy Linux.
[http://en.wikipedia.org/wiki/Puppy_linux](http://en.wikipedia.org/wiki/Puppy_linux)

---

### Post by ambient007 on 2010-04-24
It might be worth it to invest in a little more ram if you are able. Not that expensive considering the increase in performance you get going from 256mb to 1Gb for example.

---

### Post by warfacegod on 2010-04-24
More RAM wouldn't go amiss. I've had full installs on a 5 GB partition and everything worked fine.

Although, with the hardware you have being rather dated, you should consider trying a lighter Linux distro. Puppy Linux has been mentioned already. Another is Damn Small Linux or my personal favorite, SliTaz.

Another route would be to use Ubuntu with a lightweight Desktop environment such as LXDE. LXDE can be found in Synaptic Package Manager.

Building a Minimal install is yet another solution. Here's a great thread for that:

[http://ubuntuforums.org/showthread.php?t=1209904]("http://ubuntuforums.org/showthread.php?t=1209904")

Whatever you decide to do (if anything at all), I agree with the others, wubi is not the way to go for comparing Linux with Windows.

---

### Post by snowpine on 2010-04-24
Your specs are a little low compared with the [Ubuntu recommended system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"): 

> The Recommended Minimum System Requirements should allow you to run an installation of Ubuntu well. While you can usually run Ubuntu on hardware of lower (and sometimes much lower) specification, performance will necessarily suffer. Most users (especially those new to Ubuntu) risk frustration if they ignore these suggestions.

Ubuntu Desktop (GUI) Installation

    * 1 GHz x86 processor
    * 512 MiB of system memory (RAM)
    * 5 GB of disk space
    * Graphics card and monitor capable of 1024x768
    * CD-ROM drive
    * Sound support
    * Internet access

I would recommend upgrading your hardware (check your local classifieds for an inexpensive used computer that meets or preferably exceeds the suggestions above) or using a specialized lightweight distro like Puppy Linux.

---

### Post by cuberts on 2010-04-24
> **howefield said:**
> Wubi installations are not the way to compare.

If you want like for like, Ubuntu/Whatever needs to be on its own partition. Why would you think otherwise ?wubi is running ubuntu inside of windows, which is incomparable to running it actually on your harddrive as a separate operating systam

---

### Post by _0R10N on 2010-04-24
I agree with the previous comments. When running wubi, you're running Linux over a Windows. So, undoubtedly, wubi depends on, among a lot of other things, the resources management that the host OS (Windows) does.

Taking that under consideration, there's no point of comparing.

On the other hand, if you hardware isn't on top of the line, running any Linux as host OS will be your best choice.

Kind regards!

_0R10N >>

---

### Post by codemaniac on 2010-04-24
Hi mate i think you should do a fresh install instead of wubi , which only gives you a taste of ubuntu not the real flavour..you can also try the lighter desktop enviroments as you are low on resourse.. A few days back i was reading a thread from a fellow ubuntuite which had a link to a distowatch HOWTO article to a lightweight Xfce install.. That might be a good help to you...

---

### Post by mal1958 on 2010-04-24
> **IainMc said:**
> I have been trying out Ubuntu installing with Wubi on a dual boot with a fresh installation of Windows XP Pro on a Pentium-3 850 Mhz Dell Latitude Laptop with 256Mb Ram and 20Gb hard drive.

Initially I tried installing Kubuntu on a 6Gb partition and although I managed to run it I found the interface to be very slow, much slower than Windows XP infact (which actually works quite efficiently).

Next I tried Xubuntu (same size partition) and although it was alot faster I kept getting "crash report detected" messages repeatedly.

Next I installed Ubuntu (which i'd already found to work well from a live CD) using a 9Gb partition and I have found this to work far more efficiently than the other two versions (though not a great deal faster than windows). Although I was initially getting the odd "crash report detected", its not as intrusive as with Xubuntu and it doesn't seem to be affecting its function.

I was under the impression Linux outperforms Windows considerably. Also I had thought that Ubuntu requires more hardware resources than Kubuntu?


Any ideas where I am going wrong? Anything to do with the partition size (I'd like to reduce it to 5 or 6 if I can without slowing Ubuntu down)?

I'd prefer to use the KDE desktop if I can though I am reasonably satisfied with how Ubuntu is running.


Linux does out perform Windows.  The problem here is that your system is woefully under powered.  I would do the following if you are planning on keeping this box and want to run any OS at an acceptable speed


[LIST=1]
[*][COLOR=Red]Upgrade the HD (you can find 40 - 80 Gig drives at many places that are very cheap nowadays. I would go with at least a pair of 60 giggers to start.[/COLOR]
[*][COLOR=Red]Upgrade your memory to at least 512 meg  (running windows anything is memory hog heaven)[/COLOR]
[*][COLOR=RoyalBlue]Also check your video card (or chipset for onboard video)  that way you will know what to report if you run into problems.  Same for sound.  [/COLOR]
[*]Install windows xp onto the primary drive all by itself.  Leave the second drive alone during the windows install.
[*]Boot from the CD and install the flavor of ubuntu you would like on the second drive by itself and let the system install Grub to let you choose from the two on each boot.
[/LIST]
   Your first order of business is to get a higher capacity HD and more memory.  Windows seems to work great because it is using a swapfile that it reads and writes to/from constantly.  This will wear out your HD eventually.  It also is the main cause of Disk fragmentation since the size of the swapfile is not Static.    Here is a trick that works a lot of time to get a slight bit of omph out of your system.  If you have a 60 gig drive for windows, then install windows there but before you do, use fdisk to partition the first drive,  You would want 55 gigs or so as the main primary partition, and a secondary partition of 5 gigs.  After windows is installed move your swapfile to the 5 gig partition and make it a static 4 gigs in size.  You will note a bit more improvement on the windows side.     The main thing here is, whether you move to a dual boot with Windows/Linux or just keep Windows, you need a higher cap. HD and more memory.  If you can't get a second HD in your system then I would recommend at least a 100 gig HD or better yet a 150 gig.  Partition the sucker into two equal halves and then (if you want) add the little 5 gig partition to the first one for the swapfile.  Then you should be fine with almost any of the flavors of Ubuntu.  I do Recommend 9.10 or (Later when the bulk of the bugs have been squashed) 10.04.

Hope this helps a bit.

Mike

---

### Post by NightwishFan on 2010-04-24
Wubi does not run on top of Windows, it just runs inside a Windows filesystem as a virtual ext partition contained inside a file. The biggest issue is space limitation and the fact it is prone to fragmentation. Other than that it should perform normally.

---

