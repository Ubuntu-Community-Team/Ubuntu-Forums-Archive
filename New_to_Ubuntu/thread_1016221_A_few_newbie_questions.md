---
title: "A few newbie questions"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by BrettUK on 2008-12-19
Hi all,

First I would like to say I am a complete novice when it comes to Linux/Ubuntu so if some of my questions are a little obvious or even silly please understand I have been a windows user for many years and the thought of using anything else frightens the bloody life out of me, but on the plus side I enjoy playing around, breaking things and putting them back together (operating systems I mean) 

My wife has just purchased a Dell Mini 12 for me with Ubuntu 8.04, wont be delivered until after xmas but I’m looking forward to getting my hands on it. 

The questions I have are 

Is this the official Ubuntu Forum?

Are there many differences in 8.04 and the latest 8.10 

What is the best browser to use?

What Anti-virus and firewall’s should I be using (On this point I seem to be reading conflicting info on the web, people saying you don’t need Anti-virus for Ubuntu but for my own Pease of mind I would like a firewall and AV running on it)

I don’t have a CD drive on the Mini laptop so can I re-build it, should I need to via a USB devise /flash drive

How easy is it to upgrade from 8.04 to 8.10 (Should I completely remove 8.04 before installing the latest version)

Hown do you install drivers, is it just an exe file or do you need to assign them to the device. (I know this question sounds odd but from what I have read on the forum installing drivers can cause problems.

Maybe I am running before I can walk with this, hay I have not got the laptop yet but I like to be prepared before I start

Thanks for the help in advance and the continued support I most probably will need

Thanks

BrettUK

---

### Post by donkyhotay on 2008-12-19
In answer to some of your questions... Yes this these are the official ubuntu forums. Firewall is preconfigured. Antivirus you don't need to worry about but if you want one get clamAV. Drivers are generally automatically installed. If a driver isn't installed find out what the hardware is and post it here and we'll help you get it installed. I don't find much difference between 8.04 and 8.10 except for cosmetic. I upgraded from 8.04 to 8.10 and didn't run into any major problems (less then a clean install at least) and the upgrade process is pretty easy. This is one of the main reasons I use ubuntu, I started with fedora but when a new version came out I had to pretty much reinstall everything from CD.

---

### Post by Daveth on 2008-12-19
Welcome to the ubuntu forum (the official one- the only one?)

You will find lots of helpful information here

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Browser - I have always been an Opera user, falling back to Firefox when the need arises. I always go for a clean install at upgrade, but it helps immensely if you have a separate /home partition in which all your personal data and the config files sit, as you just wipe the old version and stick on the new. And as many times as you like, and whatever distribution you like. Many drivers are already built into the system, so things just work and, when they don't, you can usually find some guides how to fix them.
Hope you enjoy your new laptop, and happy Christmas.

---

### Post by donkyhotay on 2008-12-19
Oh yeah, browser is just a matter of personal preference. Except for IE and safari you can use almost any browser you want! I personally use firefox just because it's what I used back when I used to run windows.

---

### Post by hyper_ch on 2008-12-19
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by jerome1232 on 2008-12-19
> **BrettUK said:**
> 
Is this the official Ubuntu Forum? Yes

> Are there many differences in 8.04 and the latest 8.10 Well 8.04 is a LTS release meaning it will get security patches 'till Aprill of 2011. For the most part it is the more tested and stable of the two.  8.10 is more bleeding edge has newer versions of software and is only supported 'till October of 2010.

> What is the best browser to use?

 This is very subjective by nature, by best do you mean most secure, most features, most custimizable... 

The masses flock to Opera or Firefox. I find both of them to be great browsers in General.  

> What Anti-virus and firewall&#8217;s should I be using (On this point I seem to be reading conflicting info on the web, people saying you don&#8217;t need Anti-virus for Ubuntu but for my own Pease of mind I would like a firewall and AV running on it)

Ubuntu comes with iptables for a firewall, it's configured to allow all traffic by default but there's also no services listening for connections by default in Ubuntu (so incoming traffic is droped anyways). If you want to configure iptables look at gufw or ufw as easy to use front ends. I have no recomendations for anti-virus as it's just not needed on an up-to-date desktop system.

> I don&#8217;t have a CD drive on the Mini laptop so can I re-build it, should I need to via a USB devise /flash drive I know you can install from a flash disk, I don't have experience with this though so I can't help with that.

> How easy is it to upgrade from 8.04 to 8.10 (Should I completely remove 8.04 before installing the latest version)

 You can update through ubuntu's package manager with out reinstalling. I've never had any problems doing it that way.

> Hown do you install drivers, is it just an exe file or do you need to assign them to the device. (I know this question sounds odd but from what I have read on the forum installing drivers can cause problems.)

For the most part drivers come with the system and are used when needed. The most common execption would probably be if you have an ATI/NVIDIA graphics cards and those can be install using Ubuntu's package manager.

> Maybe I am running before I can walk with this, hay I have not got the laptop yet but I like to be prepared before I start
Best way to learn is to dive in head first :)

---

### Post by albinootje on 2008-12-19
> **BrettUK said:**
> 
Are there many differences in 8.04 and the latest 8.10

I recommend sticking with 8.04, it's a LongTermSupport release, and the changes in 8.10 are not that interesting to switch en masse to 8.10 
> 
What is the best browser to use?

Firefox is my choice since years (Mozilla before that, Netscape before that :), one reason is the amount of extensions/add-ons available. I like having Galeon and Epiphany-browser around just in case, but those both don't have those extensions, and i really want adblock-plus and no-script (by the way, i don't recommend no-script to new users, it can be a hassle to get used to, but i like it very much!)

> 
What Anti-virus and firewall’s should I be using (On this point I seem to be reading conflicting info on the web, people saying you don’t need Anti-virus for Ubuntu but for my own Pease of mind I would like a firewall and AV running on it)

In my opinion you will eventually find more peace of mind if you go read and practise some basic Linux security things, rather than (fooling yourself by) installing some anti-virus software which is meant to protect MS-Windows-users.

---

### Post by Kellemora on 2008-12-19
Hi Brett

You will be surprised at how fast you will pick up using Ubuntu!  I'm 61 years old and converted my entire business office to Ubuntu after only using it for one month.  I've only got 3 months under my belt so far, so I'm a noob too, still, hi hi.....

I'm sure you will ENJOY your Christmas Present!

> Are there many differences in 8.04 and the latest 8.10

I use 8.04 nicknamed Hardy Heron because it is the stable LTS release.  It will be supported for 6 months after Intrepid is dead and buried.

> What is the best browser to use?

I use Firefox myself, but it's really a matter of preference as to which one you like the best.  Opera is considered the BEST and I use it a lot too!

> What Anti-virus and firewall’s should I be using

You don't need an anti-virus program.  It's nearly impossible to infect a Linux machine!
In fact, even when I was running Windows I didn't use an anti-virus program because they caused more problems than a virus did!  I would use a virus checking program like SpyBot, but didn't let the monitor run.

I use a stand alone firewall, but Ubuntu has a built in firewall turned on by default.

> I don’t have a CD drive on the Mini laptop so can I re-build it, should I need to via a USB devise /flash drive

I'm running a Backpack CD/DVD burner via USB.  The bios on most of my machines will let me select it as the boot device if need be.  Don't know if this is true for all types of computers or not.

> How easy is it to upgrade from 8.04 to 8.10 (Should I completely remove 8.04 before installing the latest version)

I suggest you stick with the stable LTS version, unless you require the latest for some reason.
Most of the problem question posted here are 8.10 users and those who upgraded instead of reinstalled.
Does that answer your question?

> Hown do you install drivers, is it just an exe file or do you need to assign them to the device. (I know this question sounds odd but from what I have read on the forum installing drivers can cause problems.

Most common device drivers are part of the Kernel!  So unless you have something new you are adding, and since you are getting a new computer with 8.04 already installed on it, it should already have all the drivers for it to work properly.
Normally, loading a new driver is just a command line instruction.

> Maybe I am running before I can walk with this, hay I have not got the laptop yet but I like to be prepared before I start

I'm sure you will have a dozen more questions on day one of using your new computer after it arrives.
Just remember, It's NOT the Doze, so it don't work like the Doze!  Most things are much more Logical too!
And dig this, there are over 25,000 FREE programs waiting for you to try out in Synaptic Package Manager that are already tested out and work perfect with Ubuntu.
Thousands of Windows programs have Better than equivalents written for Linux and stored in repositories, again, all FREE.  There are a few programs you can purchase, but even so, the Source Code is FREE and you can compile from that after you gain some experience, so then it's still FREE.

TTUL
Gary

---

### Post by albinootje on 2008-12-20
> **Kellemora said:**
> 
I use a stand alone firewall, but Ubuntu has a built in firewall turned on by default.

That is not correct. Ubuntu does not turn on a built in firewall by default.

Try :
```

sudo ufw status
sudo iptables -L -n

```
After a fresh Ubuntu desktop installation.

---

