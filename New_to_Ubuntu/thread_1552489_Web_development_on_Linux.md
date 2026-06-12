---
title: "Web development on Linux"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by horseatingweeds on 2010-08-13
I'm looking for some general advice, or perhaps a general idea of what using Linux is like. I'll give my simple questions then some more background. 

[LIST=1]
[*]I was reading about how you can run Ubuntu as a regular program on Windows. Can you run Apache php mysql mail and all that on such an Ubuntu install?
[*]Are there versions of Ubuntu that come packaged with all the web server stuff?
[*]Has anyone experience configuring an Integrated Development Environment with php Development Tools, like Eclipse IDE, on Ubuntu?
[*]How is running Apache on Ubuntu? Is it the precarious and confusing task that it is on windows?
[/LIST]
I'm a web developer (or at least learning to be) and currently my development environment is Win xp running XAMPP. I built this machine last year and bought a copy of XP on Ebay in order to avoid Windows Vista. 

XAMPP, I've found, is very slow. JSON requests are ridiculously slow (Java script requests to the server) like 15 seconds. XAMPP is also very good at convincing me that I'm way to stupid to have any business computing or developing software. 

As an example, I've been spending the better part of the past few days trying to configure Eclipse IDE (and I tried netBeans), mainly trying to get the debuger to work - both xdebug and Zend debug. Instructions to do this are everywhere on the internet, and are all a little different. 

I managed to get xdebug working with NetBeans, but the settings caused timeout errors in PhpMyAdmin making imports not work, and made the XAMPP control panel not work, and caused some other problems. Likewise, settings to get xdebug and Zend debug working with Eclipse also cause weird problems.

I work with Drupal (a php CMS framework) and would like to start contributing to the community, for which I need CVS. I haven't started trying to configure/learn that on Eclipse though. I'm a little exhausted from the debugger. But seriously, configuring all this web server stuff makes programing in php seem easy and makes things like Drupal look simple and ingenious, rather *more* ingenious. 

I've considered a move to Linux in the past, but have felt trapped on Win because of the Adobe Suit and things like Auto CAD. Currently, I don't use CAD that often, focused more on web development, and regardless, I've been reading about VirtualBox which should allow you to run anything on top of a linux OS.

So the overall question I've been pondering is this: "Am I a complete moron, lacking the aptitude to setup an IDE or operate a web server, or is working with Apache on Windows, a setup like XAMPP, inherently difficult?"

---

### Post by corrytonapple on 2010-08-13
I would just try Ubuntu Server. You have nothing to loose if you erase XP.:D

---

### Post by horseatingweeds on 2010-08-13
Not especially helpful corrytonapple. :roll: Regardless, I'm talking about a desktop with an Apache development environment. My production website are on Linux servers but I don't administer them.

---

### Post by Zeike on 2010-08-13
> **horseatingweeds said:**
> Not especially helpful corrytonapple. :roll: Regardless, I'm talking about a desktop with an Apache development environment. My production website are on Linux servers but I don't administer them.

The desktop edition of ubuntu doesn't come with a full LAMP stack (the server edition does), but it is trivial to install with a single command.

Eclipse IDE is available in ubuntu, though I have never used it.

From my experience installing apache in windows is far harder than necessary.  The actual install in ubuntu is more or less automated, you just have to edit the config files to your liking.

As to running ubuntu as a 'regular program' in windows... sort of. This is done by a method called wubi.  See here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) .  I wouldn't really suggest this for anything beyond trying out ubuntu temporarily though.

---

### Post by corrytonapple on 2010-08-13
> **horseatingweeds said:**
> Not especially helpful corrytonapple. :roll: Regardless, I'm talking about a desktop with an Apache development environment. My production website are on Linux servers but I don't administer them.
Probably should have had links. :)Ubuntu server is designed for servers (Obviously). Get it [here]("http://www.ubuntu.com/server/get-ubuntu/download"). For using Ubuntu temporally, you use an application called Wubi. I have no experience with it. You can not use Apache with Wubi well. It is To use it, you have to **install** it. Otherwise, you can't use Apache. And yes, most of my posts are helpful.:)

---

### Post by phillw on 2010-08-13
Hi,

as suggested above and hinted at by yourself; get yourself a dual-boot system that will give the option to start Windows or Ubuntu [Dual Booting](https://help.ubuntu.com/community/WindowsDualBoot) This will be far more managable for you with LAMP and still have a Desktop system to work with (surfing the web etc.).

I recently gave a class on LAMP (The bits you need for Web stuff) installation on a desktop system. The class was logged at [LAMP on a desktop system](http://irclogs.ubuntu.com/2010/07/28/%23ubuntu-classroom.html) It also includes the link to the slides I used.

The LAMP wiki is currently under review, with the draft being at [Phill's draft](https://wiki.ubuntu.com/phillw/draft)

I hope it is of help to you.

Regards,

Phill.

---

### Post by horseatingweeds on 2010-08-13
Ok, that answers a few questions of mine. :D

Is a dual boot the best idea now though? I've been reading about [Virtualbox,]("http://www.virtualbox.org/") and according to them, running a virtual machine is no different that running another system on your network. 

If that's true I'd plan on doing this: Put a virtual Ubuntu on this system for now, as an improved web development environment. My next system I build (I like to keep two, so I have one for work and one for other stuff, and as a backup) I'll put Linux on it, and run Windows or whatever else as virtual machines for testing and using the few programs that Linux doesn't support and for which there are no open source alternatives.

Phillw - awesome link - [Phill's draft]("https://wiki.ubuntu.com/phillw/draft").

---

