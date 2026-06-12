---
title: "Is Wubi really safe to use?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by User_ on 2011-03-18
Hello everyone, first post here. :)
I am thinking of using Wubi in order to install Ubuntu side to side with Windows 7. I've been reading various threads regarding Wubi and most of them were positive, but I've also found some negative ones. So my question is, "Is Wubi really safe to use?". Thanks in advance for any reply given!

---

### Post by false truths on 2011-03-18
The thing about Wubi is, it's not really installing Ubuntu alongside Windows. It's installing Ubuntu inside Windows. The virtual file that Ubuntu gets within Windows is a fixed size with a maximum of 30gb, so you are very limited in what you can do with it. Also, if Windows goes, so does your Wubi install.

So in short, it's extremely convenient for trying out Ubuntu without risking partitioning your hard drive, but it's in no way made for long-term use.

---

### Post by User_ on 2011-03-18
This means that there isn't any chance of messing up my system?

> **false truths said:**
> 
So in short, it's extremely convenient for trying out Ubuntu without risking partitioning your hard drive, **but it's in no way made for long-term use**.

Is that because of the 30gb limit?

---

### Post by TeoBigusGeekus on 2011-03-18
There's always the chance that ubuntu will mess up your system, whether wubi or dual boot. 
That's why you should backup your important files from windows before doing anything.

As for wubi: I've never tried it, but from what I've read it seems to be slower than a full ubuntu installation. The latter will also provide you with more support in these forums as there are much fewer wubi users than full installation users.

---

### Post by User_ on 2011-03-18
Oh, I see.. It seems like a full installation is a better sollution then. But let's say that I burn Ubuntu into a CD and run the installation.. Will it give me the option to dual boot both Ubuntu and Windows?

---

### Post by TeoBigusGeekus on 2011-03-18
It will, but don't use it: it's buggy!

First of all, boot up on windows and defragment the drive upon which you're gonna install ubuntu 5-6 times.

Then, boot up with the live cd and choose install ubuntu. The installer is pretty straightforward (tip: use lowercase letters for your username) apart from the partitioner:
When you reach the partitioner, choose manual configuration.
From your free space, create 3 partitions:
First: ~1-2gb that will be used as swap (something like pseudo memory for when things go bad ramwise - much like the pagefile in windows).
Second: ~10-15gb that will be used as the root partition. Format: ext4, mount point: /. This is where your main installation will take place.
Third: Anything more than 3gb. Format: ext4, mount point: /home. This will be your home partition, where your user settings will be stored. It's useful to have a separate home partition in case of a reinstallation: you can keep all your settings by declaring your old home partition as your new one.

---

### Post by Wobblybob on 2011-03-18
> **User_ said:**
> Oh, I see.. It seems like a full installation is a better sollution then. But let's say that I burn Ubuntu into a CD and run the installation.. Will it give me the option to dual boot both Ubuntu and Windows?

Yes your get to select the size of the two partitions. I've never got WUBI to work for me in the past, gave up and moved completely to Ubuntu after a very short period of dual booting..

---

### Post by Frogs Hair on 2011-03-18
I started with Wubi and know people who use it without any problem . Wibi is intended for trial use and serves that purpose well for the most part.[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Amalka on 2011-03-18
Hi, first post here. :)

I'm a school teacher and have Ubuntu installed on 10 of pupil's computers. It's dual boot Ubuntu/Windows on 8 of them, and Wubi installation on 2.

Well, from my experience, Wubi is about 20% slower than dual boot instalation. 
(Wish I could just erase Windows from systems and have Ubuntu-only computers, but for now I just can't)

---

### Post by mikechant on 2011-03-18
Re TeoBigusGeekus advice above, I would strongly suggest using Windows 7's own facility to shrink the windows partition to free up space for Ubuntu (after doing the defrags), assuming Windows is currently using the whole disc.

Also as far as the recommendation for 10-15Gb for the root partition personally I would go for 15-20Gb unless you have a small disc.

And as far as the swap partition is concerned it needs to be at least as big as your RAM if you want to use use the hibernate feature.

Re Wubi, I've never used it but I've seen quite a few people get issues with it which they would not get with a proper install.

---

### Post by bcbc on 2011-03-18
If you haven't run Ubuntu before and you are curious about it - then Wubi gives you the closest experience to the real thing, without the hassle of partitioning. It's really meant to provide a risk-free way for Windows users to try out Ubuntu and it works well for that purpose. It's also easy to uninstall if you don't like it.

Some users choose to stay with Wubi for their own reasons (maybe they have 4 primary partitions already, they are nervous about partitioning etc.). But most users that like Ubuntu probably move on to a regular install.

Wubi has it's own unique set of problems that lead some people to think that it's flaky, but I would say for most people it installs without a hitch and does what it is intended to do. If you use Wubi, make sure you keep data backups current as you are using a file system within a file on another file system and this is less reliable than a direct install.

---

### Post by deeZee on 2011-03-18
My experience with Wubi was terrific.  It behaves almost exactly like a regular install (i.e. you can install drivers, and packages for media support etc.)  It's a little slower than a regular install, but significantly faster than trying to run Ubuntu from a live CD.  Ironically, it was because my experience with a Wubi install was so positive that I decided to do regular install.

---

### Post by Mr.Dee on 2011-03-18
I've never used Wubi because of your same concern.  I did not research too much into using Wubi after discovering that booting from USB sticks and SD cards worked well and have never damaged my windows machines.

---

