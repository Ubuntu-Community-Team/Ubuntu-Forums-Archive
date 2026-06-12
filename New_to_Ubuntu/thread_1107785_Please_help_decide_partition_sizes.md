---
title: "Please help decide partition sizes"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by yeehi on 2009-03-27
The system has 1 HDD 60GB. How big should / and /home and others be on Intrepid? Where is the best resize tutorial? 

Thank you!

---

### Post by freesitebuilder on 2009-03-27
Here's a useful site:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I've allowed 30gb for root (system), 2 for swap, and everything else for /home (I have a separate /home partition). I don't want to do a fresh install every time a new version is released, I prefer to upgrade and do a fresh install less often, so I allowed more than the minimum required for root. I don't store many large files such as videos or music.

I did a fresh install for 8.10 (due to some disk problems), and my root partition is 15% full, so I may have allowed too much!

---

### Post by MrWES on 2009-03-27
> **yeehi said:**
> The system has 1 HDD 60GB. How big should / and /home and others be on Intrepid? Where is the best resize tutorial? 

Thank you!

My recommendation would be:

/  10gb

/swap 1gb

/home  the rest


30gb is a waste for / -- you'll never come close to using that.

Bill

---

### Post by Sef on 2009-03-27
> My recommendation would be:

/  10gb

/swap 1gb

/home  the rest

Go with that.  That is how I do it.

---

### Post by stderr on 2009-03-27
Sounds fine; I might allow an additional 5GB for root, and 1-2GB for swap, but that's not necessary. 

Remember, it's rare that you get these things exactly 'right' first time, and you can always resize partitions later if need be. I remember the first time I did this I was none too sure what size to make things, even after reading up on it, and in the end my final estimates turned out to be way out of whack with what I needed anyway :)

---

### Post by lovinglinux on 2009-03-27
I have 15Gb for root, 3Gb for swap and the rest for home. I'm currently using 35% of the root partition. But my main drive has 160Gb capacity and I also have an additional 80Gb drive. Since you have only 60Gb, then 10Gb for root is a good choice, unless you plan to install huge 3D games.

---

### Post by azmo35 on 2009-03-27
Hi,on my lapy on dual boot max 60GB,i have 40GB for windose and 10Gb for /file system 9GB for /home and 1GB for /swap, and i'm a very big downloader.

---

### Post by hexanol on 2009-03-27
You could also put everything under a single root file-system... if you want.

---

### Post by Paqman on 2009-03-27
> **MrWES said:**
> 
30gb is a waste for / -- you'll never come close to using that.


You might. Remember /tmp will be on that partition. Some tasks (eg: authoring DVDs) create some pretty enormous temp files. I usually recommend 20Gb for / for this reason.

---

### Post by MrWES on 2009-03-27
> **Paqman said:**
> You might. Remember /tmp will be on that partition. Some tasks (eg: authoring DVDs) create some pretty enormous temp files. I usually recommend 20Gb for / for this reason.


That's a very good point. I've come across that problem say doing some dvd to avi work and usually those program default to /tmp for their needs. However, I just edited the prefs to use /home/tmp and I didn't run into any additional issues with space in / .

Bill

---

### Post by odinb on 2009-03-27
Everyone does it their own way, but it seems that most posters here are in approximate agreement (and so are I).

What I usually do is this:

/ 15-20GB depending on what I feel like that day, and whether the disk is huge or not (if the drive is small, like yours with 60GB, 10-15GB might be enough if you do not plan on doing any major video editing or such on the machine.)

/swap should equal RAMsize, but do not think more than 2GB is neccessary.

/home for the rest.

I would not recommend putting everything under the root filesystem, it will be a pain if you later choose to reinstall from scratch, but want to keep your /home intact...

---

### Post by James_Lochhead on 2009-03-27
> **yeehi said:**
> The system has 1 HDD 60GB. How big should / and /home and others be on Intrepid? Where is the best resize tutorial? 

Thank you!

The above posts are okay if you want to use a home partition. 

The advantages of this is that when re-installing you can keep all your personal files e.g. your music and documents on the hard disk (although you have to delete settings files).

The disadvantages of this is that when using a home partition you don't know exactly how much space your root partition will take, therefore you waste space by allocating too much so you don't run out.

Personally I don't use a home partition for the reason mentioned above (plus I use an encrypted LVM so a home partition wouldn't help me re-install anyway).

If you want a home partition you want should partition like this:

Swap partition: If your RAM is small (1GB and below) you should allocate 2x your RAM to this partition. If you have a large RAM 1GBish should be fine, you could even get away with no swap if your RAM is large enough.

Root partition: 10-20GB depending on what you plan on installing. If you want to install lots of stuff make it at least 15GB to be safe.

Home partition: Whatever is left.

If you don't want a home partition:

Swap partition: If your RAM is small (1GB and below) you should allocate 2x your RAM to this partition. If you have a large RAM 1GBish should be fine, you could even get away with no swap if your RAM is large enough.

Root partition: Whatever is left.

---

### Post by Dawei87 on 2009-03-27
i have a question regarding swap size. i have a 3gb ram and i heard from somewhere that your swap should be equal to your ram. i heard it can be smaller too but to be safe i made my swap 3gb. my question is, do i even need swap? so far i have never seen that drive in use, i have two system monitors and it always shows my swap at 0%. is my ram big enough i just dont need swap?

---

### Post by Paqman on 2009-03-27
> **Dawei87 said:**
> is my ram big enough i just dont need swap?

Probably, yes.

The RAM = Swap rule is to give you the option of using hibernation. When you hibernate the contents of your RAM is copied into your swap and stored.

---

### Post by Dawei87 on 2009-03-28
so you are saying i will only need swap if i am to hibernate me computer?

---

### Post by Paqman on 2009-03-28
> **Dawei87 said:**
> so you are saying i will only need swap if i am to hibernate me computer?

Yep. Ubuntu wouldn't normally run out of memory if it had 3GB. I have 2GB and it never, ever gets full (and I do all sorts of weird stuff like putting my browser cache in RAM). Your system just won't need to be offloading anything into swap space with that much memory.

---

### Post by lovinglinux on 2009-03-28
> **James_Lochhead said:**
> The advantages of this is that when re-installing you can keep all your personal files e.g. your music and documents on the hard disk (although you have to delete settings files).

I partially disagree. One of the main reasons I have a separate home partition is exactly to keep the settings files, along with videos, music and documents. So if I need to re-install, I won't have to configure all stuff again. I'm not talking about upgrading, since old config files can also mess things up due to potential incompatibilities.

---

### Post by lovinglinux on 2009-03-28
> **Paqman said:**
> Yep. Ubuntu wouldn't normally run out of memory if it had 3GB. I have 2GB and it never, ever gets full (and I do all sorts of weird stuff like putting my browser cache in RAM). Your system just won't need to be offloading anything into swap space with that much memory.

I must be doing something wrong then, because I have 2Gb of memory and it is currently being used at 94%

26% in use by programs
68% in use by cache

The cache usually occupies a lot of memory space, specially after running Firefox for a while.

---

### Post by Paqman on 2009-03-28
> **lovinglinux said:**
> I must be doing something wrong then, because I have 2Gb of memory and it is currently being used at 94%

26% in use by programs
68% in use by cache

The cache usually occupies a lot of memory space, specially after running Firefox for a while.

Cache is good. You want the system to be using the free memory as cache. Basically Linux will try and use all the free memory (ie: that not being used by programs) for caching.

In your case you're actually using 26% of your memory to do actual work, not 94%. My numbers usually look similar.

---

### Post by lovinglinux on 2009-03-28
> **Paqman said:**
> Cache is good. You want the system to be using the free memory as cache. Basically Linux will try and use all the free memory (ie: that not being used by programs) for caching.

In your case you're actually using 26% of your memory to do actual work, not 94%. My numbers usually look similar.


I see. So if more memory is needed for programs it will drop some cache instead of sending to swap right?

---

### Post by freesitebuilder on 2009-03-28
I forgot to say that the reason I made my / partition much larger than needed was so that my backup drive could cope - if my /home had been larger, I'd have to have changed my backup disk too. And being mean, I coudn't bear the thought of a chunk of unused disk space on my main drive! :)

---

### Post by Paqman on 2009-03-28
> **lovinglinux said:**
> I see. So if more memory is needed for programs it will drop some cache instead of sending to swap right?

Absolutely. The cache is there to make the apps faster, the absolute last thing it should ever do is slow them down. So if an app needs to use memory, the cache goes out the window.

---

### Post by yeehi on 2009-04-01
I was just reading that having a separate partition for /opt

is a good idea, too!

Programs like Adobe, Cedega and Crossover Office, (all statically installed, and therefore usable with other distros, should you ever replace Ubuntu) are put into the /opt folder. 

Since a lot of programs go there, how large do you think that partition should be on my HDD?

Thank you!

:)

---

