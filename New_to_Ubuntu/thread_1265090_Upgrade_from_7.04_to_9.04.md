---
title: "Upgrade from 7.04 to 9.04"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Lisalives on 2009-09-13
Hi there, 

I'm new to Ubuntu Linux (have downloaded the pocket guide, it's great) and am hoping someone can help with a query.

I have two laptops; an Acer running Windows, which I use all the time, and and an Asus F3T running Ubuntu Linux 7.04 (Feisty Fawn).  I don't have dual systems; each laptop runs only the one OS.  The Linux laptop was given to me, and I'm really keen to start using it, but some things aren't intuitive for me so I've put it off for a year!

My query is - how do I upgrade to 9.04?  I thought it might be best to uninstall then install the new Linux (used to this from Windows) but from what I've read that's not the approach.  I don't want to install all the versions from 7.04 to 9.04.  Reason is that the Linux laptop doesn't have any of my data on it, so I'm happy to wipe it clean and restart, I'm not going to lose anything.  I have Ubuntu 9.04 on a CD, but when I install the CD, it doesn't start automatically, and it looks like some of the installation procedures aren't supported.

As an aside, I have broadband internet access but only use this on my Windows laptop, haven't figured that out on Ubuntu either :)

Thanks in advance
Lisa :D

---

### Post by MelDJ on 2009-09-13
try changing your bios to boot from cd

---

### Post by tgalati4 on 2009-09-13
How much RAM do you have?  You need at least 256 MB to install from the Live CD.  You can get by with a little less if you partition your drive with a swap disk.

You will have to be more specific as to what fails during the installation.

---

### Post by nhasian on 2009-09-13
You can only directly upgrade to Ubuntu 9.04 from Ubuntu 8.10 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Bucky Ball on 2009-09-13
> **nhasian said:**
> You can only directly upgrade to Ubuntu 9.04 from Ubuntu 8.10 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

+1

I would reinstall from a fresh CD personally. Upgrading from one version to the next can take an age and is sometimes problematic (bits left over from the old release). As mentioned, you would have to install 8.10 to do it this way anyhow.

8.04 LTS is the long term support version and currently the most stable.

---

### Post by Lisalives on 2009-09-13
Hey thanks everyone for the suggestions, really appreciate it.

Memory shouldn't be a problem, I have about 90 gig available.

Do you think that I should upgrade to the version of 8 that will let me go to version 9.04 as a two step process?

Is it possible to completely uninstall Linux and just load up 9.04?

Cheers
Lisa:)

---

### Post by jocko on 2009-09-13
> **Lisalives said:**
> Memory shouldn't be a problem, I have about 90 gig available.You may have 90 Gb hard drive space, but I really doubt that you have 90 Gb RAM. You need at least 256 Mb RAM to be able to boot your computer from a live cd.> **Lisalives said:**
> Do you think that I should upgrade to the version of 8 that will let me go to version 9.04 as a two step process?
As you say you don't have any data you want to keep on the computer, it would be very silly to go through the very time-consuming process of upgrading twice.
> **Lisalives said:**
> Is it possible to completely uninstall Linux and just load up 9.04?You can't uninstall an operating system. Just boot from a live cd and use gparted (System-->administration-->gparted or "partition manager") to delete all partitions. Once that is done, start the installer and let it install 9.04.

What happens when you use the live cd? Does it just boot from the hard drive as normally instead of starting from the cd?
Or does it boot from the cd and fail before the desktop loads?
Are there any error messages?
Or does it load the live system completely but fails during the install process?

---

### Post by NexusZA on 2009-09-13
> **jocko said:**
> You may have 90 Gb hard drive space, but I really doubt that you have 90 Gb RAM. You need at least 256 Mb RAM to be able to boot your computer from a live cd.
As you say you don't have any data you want to keep on the computer, it would be very silly to go through the very time-consuming process of upgrading twice.
You can't uninstall an operating system. Just boot from a live cd and use gparted (System-->administration-->gparted or "partition manager") to delete all partitions. Once that is done, start the installer and let it install 9.04.

Lets not confuse the poor woman! You don't need any of the data on the laptop? So this is what you do:

1. Start up your computer and in the first few seconds it will give you information on the screen either on how to change the boot device, boot order or open setup etc. In there you will need to find out how you can change the settings to boot your computer from the 9.04 CD

2. Once you have found that, you can restart your machine with the CD for 9.04 in the drive and it will automatically boot with the CD.

3. On the menu choose to Install not to Try and follow the prompts until you get to the partitioning part. Because you don't want to keep anything choose "Guided: Use entire disk" which will wipe out all the old stuff and put the new stuff on for you. Ubuntu will automatically handle the partitions and all that techy stuff you probably aren't to keen on fiddling with.

4. Keep following the questions and answering then sit back and pretty soon you will be bang up to date with Ubuntu 9.04 Jaunty Jackelope :D

PS: To use your broadband Internet in ubuntu, just plug it in ... thats all ;)

---

### Post by Bucky Ball on 2009-09-13
You might want to go to the second link in my signature 'Never Tried Ubuntu?'. Even though you have you will find plenty of info and links to sort out your issues. 

As mentioned you need to change the boot order in the BIOS to boot from CD. Hit 'F10' to save changes and exit and you should be rolling, should boot from the CD. This and more is explained on the link.

---

### Post by nikhilbhardwaj on 2009-09-13
> **Lisalives said:**
> 
Memory shouldn't be a problem, I have about 90 gig available.

Do you think that I should upgrade to the version of 8 that will let me go to version 9.04 as a two step process?

Lisa:)

i think the memory referred to here is RAM

its not wise to go through a two step upgrade a clean install is better
just boot up from the live cd
and choose to install ubuntu using your entire hard disk
that is the simplest method

if your laptop doesnt boot from a cd directly 
you may need to enter the bios and set the preferences to boot from cd 
you can enter your bios by hitting the <del> key when the computer starts

best of luck with installing ubuntu
i have a feeling that you'll need it

---

### Post by Bucky Ball on 2009-09-13
> **nikhilbhardwaj said:**
> 
you can enter your bios by hitting the <del> key when the computer starts



This is by no means uniform. SOME machines use 'del', my laptop uses F1 and my desktop uses F2. A machine I installed on recently used ESC. Check at the screen as soon as the computer boots, it will tell you how to enter BIOS or sometimes called 'Enter Setup'.

---

### Post by Lisalives on 2009-09-13
Hey team

Thanks everyone for comments/suggestions/feedback, much appreciated.  I will give what you say a go and let you know how I get on.

Thanks NexusZA for not making me feel stupid :D  you're right one of the things that bothers me about Ubuntu is the feeling I could inadvertently screw something up, something that Windows won't let you do really (although I am a bit embarrased about the broadband plugin...!!!).   Thanks Bucky Ball for the link and the advice too.

Okay because this is a beginner forum I'm not going to hold back!  More questions:

1. What is a 'live' CD?  I haven't killed any recently.  When I refer to 9.04 on the disk, I had downloaded it from the website.  When I put the CD into the laptop it would open up, but nothing would automatically run, but maybe that's cos it was patiently waiting for me to do something.  Anyway, I'll try again and pay more attention to all the things I didn't stop to notice before that you've alerted me to.

2. What are your thoughts on what version to get?  I went for 9.04 because it's the latest, and it's supported till next year.  But would I be better off going for 8.10?  Let's face it, I'm probably not going to notice the additional features given I haven't even got off the ground yet!

Really appreciate your time/advice
cheers
Lisa:)

---

### Post by MelDJ on 2009-09-13
> **Lisalives said:**
> Hey team

Thanks everyone for comments/suggestions/feedback, much appreciated.  I will give what you say a go and let you know how I get on.

Thanks NexusZA for not making me feel stupid :D  you're right one of the things that bothers me about Ubuntu is the feeling I could inadvertently screw something up, something that Windows won't let you do really (although I am a bit embarrased about the broadband plugin...!!!).   Thanks Bucky Ball for the link and the advice too.

Okay because this is a beginner forum I'm not going to hold back!  More questions:

1. What is a 'live' CD?  I haven't killed any recently.  When I refer to 9.04 on the disk, I had downloaded it from the website.  When I put the CD into the laptop it would open up, but nothing would automatically run, but maybe that's cos it was patiently waiting for me to do something.  Anyway, I'll try again and pay more attention to all the things I didn't stop to notice before that you've alerted me to.

2. What are your thoughts on what version to get?  I went for 9.04 because it's the latest, and it's supported till next year.  But would I be better off going for 8.10?  Let's face it, I'm probably not going to notice the additional features given I haven't even got off the ground yet!

Really appreciate your time/advice
cheers
Lisa:)

you are better off using 9.04 than 8.10. but if you want long term support till 2011, use 8.04
a live cd is a cd which you can boot into. for example the windows xp cd is not a live cd as it does not let you use windows xp but prompts you to install it first. a live cd lets you try the os then install it. some linux oses only run off live cd like backtrack

---

### Post by jocko on 2009-09-13
> **Lisalives said:**
> 1. What is a 'live' CD?  I haven't killed any recently.  When I refer to 9.04 on the disk, I had downloaded it from the website.  When I put the CD into the laptop it would open up, but nothing would automatically run, but maybe that's cos it was patiently waiting for me to do something.  Anyway, I'll try again and pay more attention to all the things I didn't stop to notice before that you've alerted me to.
A live cd is a cd which lets you run the actual os from the cd before it's installed to the hard drive.
Just put the cd in your cd drive and reboot your computer. That should give you a boot menu that lets you choose between a few different options. The two most important ones are:
1. Try ubuntu without making any changes. This is the "live" system, which lets you try ubuntu without making any changes, but also gives you access to some system tools and lets you start the installer (from a shortcut on the desktop). This way you can browse the web while you are installing ubuntu.
2. Install Ubuntu. This option directly starts the installer in a simpler graphical environment, without giving you access to any applications.

If you don't get the cd boot menu, you may need to set the boot order in your computers bios to make sure your computer tries to boot from the cd (see some of the other posts in this thread for how this is done).

---

### Post by CaptainMark on 2009-09-13
To update the os wouldnt she have to do four upgrades 7.04>7.10>8.04>8.10>9.04? I didnt know you could skip any versions, i clean install will definatley save hassle

---

### Post by armandh on 2009-09-13
lastly don't worry about mucking up the OS
It will ask for your pass word B4 any important change.
It is fairly n00b proof. [and]
It is very easy to install the second time.

---

### Post by LewRockwell on 2009-09-13
backup/clone/save/burn-to-disk/etc

fresh install

plenty of tutorials, threads, and posts with information on:

back-ups
cloning
saving data
burning to disk
wiping partitions and complete hard drives
partitioning
fresh installation

most important to save any valuable data

second most important to confirm new operating system works as desired by utilizing LiveCD of same

.

---

