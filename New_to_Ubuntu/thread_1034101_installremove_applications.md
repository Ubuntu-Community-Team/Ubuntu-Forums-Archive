---
title: "install/remove applications"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Chito on 2009-01-08
Is there a limit of how many applications can you install at one time?
Everytime I install some applications from the APPLICATIONS>ADD/REMOVE after I install the applications, if I log out and shut down my computer, the next time I turn on my computer again, Ubuntu wont work. it doesn't even gives me the option to log on. So I have to reinstall Ubuntu all over again. So far I have not download any application at all, and my computer is working fine. but missing a lot of things like I can't watch videos, but if I download the JavaPackage I'll be able to watch videos. 

First time I tried to install some application were 164items to dowmload it took about 8minutes which is pretty fast. but like I said,I shut down my computer and the next day, ubuntu was not working. So I reinstall ubuntu 8.10 again. 

The computer that I have is a Dell Optiplex 240, yeah I know a little old. You guys think it might be just the computer? Does anyone had this problem. The computer is also connected to a wireless router, to install the software I download Wine so my computer can read the CD-ROM since the software was meant for Windows. 

Anyone can help.

---

### Post by HotShotDJ on 2009-01-08
It is never wise to try to install more than a few applications at once.  Although the applications available through the official repositories have been well tested (less so for Universe and Multiverse repositories) the sheer amount of available software makes it impossible to test every possible system configuration -- in other words, unexpected interactions among installed applications can, and do, occur.  Of course, with third-party sources, all bets are off.

You can minimize this risk by only installing one or two packages at a time (remember, one or two packages can potential pull in a bunch of dependencies with them!).  Test out your system to make sure things are working as expected, and then install the next one or two packages.  By doing this, if something DOES go wrong, you'll have a better idea of what caused the problem and you may be able to fix it without doing a complete reinstall.

---

### Post by computermacgyver on 2009-01-08
And if you have only installed a few programs then you can use the boot menu and select Single/Recovery mode and use "sudo apt-get remove (package name)" to remove the program causing the problem. This is no theoretical limit to the number of packages you can install aside from hard disk space limitations, etc.

---

### Post by Chito on 2009-01-08
> **HotShotDJ said:**
> It is never wise to try to install more than a few applications at once.  Although the applications available through the official repositories have been well tested (less so for Universe and Multiverse repositories) the sheer amount of available software makes it impossible to test every possible system configuration -- in other words, unexpected interactions among installed applications can, and do, occur.  Of course, with third-party sources, all bets are off.

You can minimize this risk by only installing one or two packages at a time (remember, one or two packages can potential pull in a bunch of dependencies with them!).  Test out your system to make sure things are working as expected, and then install the next one or two packages.  By doing this, if something DOES go wrong, you'll have a better idea of what caused the problem and you may be able to fix it without doing a complete reinstall.


To be quite honest, I knew this might be the problem, but I wanted to make sure. well now I know Thanks a lot. and God Bless you.

---

### Post by Chito on 2009-01-08
> **computermacgyver said:**
> And if you have only installed a few programs then you can use the boot menu and select Single/Recovery mode and use "sudo apt-get remove (package name)" to remove the program causing the problem. This is no theoretical limit to the number of packages you can install aside from hard disk space limitations, etc.

This look like a really good solution too. can you explained to me a little bir more.

Boot Menu you talking about F12 when your computer starts and then select single recovery mode and type in "sudo apt-get remove (package name)" and that is it.

---

### Post by hyper_ch on 2009-01-08
there's nothing wrong with installing lots of applications at the same time.

However you need to check if some applications will remove other stuff that you need.

---

### Post by kalidoss on 2009-03-10
I copied the certain *.deb files from my laptop to
the directory /var/cache/apt/archives of my desktop machine.

However, I use of the command
sudo apt-get install <package>
was not successful.
I could install certain packages using
dpkg -i <package>

But the problem is that for dependent packages,
I have to install individually.

Is there a way to tell the system that the required 
packages are already available in /var/cache/apt/archives?

Kalidoss

---

