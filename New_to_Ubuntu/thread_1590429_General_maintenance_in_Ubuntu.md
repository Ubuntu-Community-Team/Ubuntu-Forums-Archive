---
title: "General maintenance in Ubuntu"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by CommuneOfLoon on 2010-10-07
As a Windows XP user, I had a pretty regular maintenance regimen for the OS; weekly running disk defrag, disk cleanup, CCleaner, Super Anti-Spyware, MS Security, etc with the occasional disk check thrown in. 

Is this kind of maintenance necessary for Ubuntu?  What should I be doing and how frequently to keep my computer running well? Is it necessary to keep a buffer of free space for the computer to run smoothly? 

Thanks.

---

### Post by aeronutt on 2010-10-07
I switched from XP to Ubuntu about 2 years ago. Not nearly as much maintenance needed in Linux/Ubuntu. Update when needed, and every blue moon, I clean up my installs:

[http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html)
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

But this is mostly to clean up disk space and make myself feel good. :)

---

### Post by NightwishFan on 2010-10-07
Not much at all my friend. Ubuntu and other GNU/Linux systems have scripts that handle maintenance. Your best bet is to stay out of their way. I wrote a small article with some tips on my blog here:
[http://vbrummond.blogspot.com/2010/09/tips-for-ubuntu-administrators.html](http://vbrummond.blogspot.com/2010/09/tips-for-ubuntu-administrators.html)

Also take a look at BleachBit, it can be installed from the software center.
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

For the tweaker in you, check out Ubuntu tweak, but be careful what you do. Though it seems like a very safe application.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by CommuneOfLoon on 2010-10-07
I'll look into that stuff, thank you.

---

### Post by rburkartjo on 2010-10-08
i agree with night bleachbit and ubuntu tweak are a must have for ubuntu users imho

---

### Post by Paddy Landau on 2010-10-08
I disagree. Unless you are tight on disk space, there's nothing you need do. Linux seems to be excellent at cleaning up after itself.

I used to use a cleanup script on a regular basis (also after coming from Windows), but I no longer bother.

I have read comments from some people who had problems after using bleachbit.

I think that ex-Windows users (me included) have a certain level of comfort with these cleanup routines, and it's scary to let go. But Linux doesn't need them.

---

### Post by warfacegod on 2010-10-08
I'm going to split down the middle on this. Ubuntu is generally rather good at cleaning up after itself but there are some flaws as well. For example, all the updates leave their packages in your cache by default. This can grow quite large after a only a few months and can get to be well over 1 GB fairly quickly. I once saw 6 *extra* kernels left over through the course of a years or so. That's several hundred MB alone. Removing applications, even with purge,  always leaves leftover folders in various parts of the filesystem. Unfortunately, there is nothing to be done about that but hunt them down manually. This isn't to say that Ubuntu is as sloppy as Windows. By comparison, it's an obsessive compulsive neat freak.

Is cleanup/maintenance as critical as in Windows? Not in the least. Is it necessary at all? Yes. The average user could easily get away with running say Ubuntu Tweak's cleanup once a year. Could you get away with *never* doing it? Most likely.

---

### Post by Locke_99GS on 2010-10-08
> **CommuneOfLoon said:**
> Is it necessary to keep a buffer of free space for the computer to run smoothly? 

You must have free space available to log in. Don't let / become 100% full.

---

### Post by warfacegod on 2010-10-08
> **Locke_99GS said:**
> You must have free space available to log in. Don't let / become 100% full.

By default, Ubuntu sets a 5% system reserve on all partitions. Because of this, you can't ever get an HDD to 100% unless you start messing with tune2fs.

---

### Post by bouncingwilf on 2010-10-08
System-> administration-> computer janitor once in a while should do it


Bouncingwilf

---

### Post by warfacegod on 2010-10-08
:shock: Please don't use Computer Janitor, it is buggy as hell and should never have been included with Ubuntu. Every time I do a fresh install, I open it and see what it wants to remove. I usually see my video driver, Firefox, and current kernel at the top of the list. C.J. is the very first thing I deep six from any install.

---

### Post by Locke_99GS on 2010-10-08
> **warfacegod said:**
> By default, Ubuntu sets a 5% system reserve on all partitions. Because of this, you can't ever get an HDD to 100% unless you start messing with tune2fs.

And when you fill your partition to 95%, then what? It acts as though it were full. Regardless of what the fs does with itself, it will reach a userspace reported usage of 100%.

When df / measures 100% in use, you'll get piles of seemingly random errors preventing you from logging in. It's a userspace problem, not a kernelspace problem. There is no room available to create and append the files needed to log in.

And to empirically show you, create a small partition, say, 4 gig and give it / and any random fs. Install whatever version of whatever distro you want to it. Boot it, and start filling it up with crap (movies, music, installed apps, whatever) Once it is full relog, or reboot it.

---

### Post by Paddy Landau on 2010-10-08
> **warfacegod said:**
> For example, ... This can grow quite large after a only a few months and can get to be well over 1 GB fairly quickly. I once saw 6 *extra* kernels left over through the course of a years or so. That's several hundred MB alone.
On an old computer, that is a problem. On a new computer, where you already have more than 100Gb, it's really not something to worry about. The days of expensive storage have gone.

---

### Post by NightwishFan on 2010-10-08
Computer Janitor cleans up all processes available for cleanup similar to deborphan, only it is a bit more conservative. If you see such packages on the list it is because of the state of your dependencies made it so.

---

### Post by Paddy Landau on 2010-10-08
> **NightwishFan said:**
> If you see such [Computer Janitor] packages on the list it is because of the state of your dependencies made it so.
I have to agree with warfacegod.

I don't mess with my dependencies; I just use Synaptic to install and uninstall. Even so, Computer Janitor prompts me to uninstall the oddest things.

If we have to mess around with our dependencies to get Computer Janitor to work, then it's not suitable for an OS that is aiming at the average user.

---

### Post by HermanAB on 2010-10-08
Howdy,

Usually, you don't have to do anything at all.  In my experience, most Linux problems are caused by updates gone wrong.

I run my servers with a hands-off policy, with no maintenance and no updates.  Once they are installed and running, I leave them alone and let them run till the hardware fails in three to five years, then I fix it and install a new version of Linux.

Desktop and laptop machines likewise gets no updates and are re-installed once a year with the latest version of Linux.

The result is a trouble free, zero maintenance, low cost system.

---

### Post by NightwishFan on 2010-10-08
Perhaps. I agree it is not for a newbie to mess with I suppose. I would like to see CJ have more of a purpose in administration in the future though, or perhaps merged with the software center.

---

### Post by warfacegod on 2010-10-08
> **NightwishFan said:**
> Computer Janitor cleans up all processes available for cleanup similar to deborphan, only it is a bit more conservative. If you see such packages on the list it is because of the state of your dependencies made it so.

On a fresh install, with only updates and the nvidia driver installed, there should be no dependency issues. I once allowed it to do want it wanted, as an experiment, and it removed the actual video driver, firefox, and several other things that I don't recall, not the leftover packages. It effectively made that install useless.


[QUOTE=Locke_99GS]
And when you fill your partition to 95%, then what? It acts as though it were full. Regardless of what the fs does with itself, it will reach a userspace reported usage of 100%.[/QUOTE]

Then what is the point of having the 5% system reserve at all? With or without it, if the end result is the same, then a default reserve is pointless.

---

### Post by Locke_99GS on 2010-10-08
> **warfacegod said:**
> Then what is the point of having the 5% system reserve at all? With or without it, if the end result is the same, then a default reserve is pointless.

I hadn't heard of a 5% fs reserve, not saying it isn't true. It makes a bit of sense, giving the fs itself room to function internally. 

My point is that in userspace, it will indeed report 100% usage, and that this causes login problems (especially loading the gui)

---

### Post by warfacegod on 2010-10-08
From the Ubuntu Documentation: [https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

> Formatting. A new drive rarely will format to the advertised size. Manufacturers normally promote unformatted capacities. Expect to lose approximately 5-7% of the advertised capacity. Additionally, by default Ubuntu reserves 5% for system use. This can be altered with the tune2fs command and is discussed later. 

> tune2fs. Reduce the space reserved for system use. By default, Ubuntu reserves 5% of linux partitions for use by the operating system. Some commands and applications do not accurately reflect reserved system space (gparted/baobab). Nautilus and the df command accurately display available usable space by accounting for reserved system space.

    *

      The amount of partition space reserved for this can be altered with tune2fs. Replace X with the percentage of disk space you wish to reserve and XX with the device designation.

      ```
sudo tune2fs -m X /dev/sdXX
```

      Example: sudo tune2fs -m 4 /dev/sda1 Note: There is a reason Ubuntu reserves this space. Carefully consider if you want to change this setting before doing so. 

[http://manpages.ubuntu.com/manpages/hardy/man8/tune2fs.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/tune2fs.8.html)

---

### Post by Locke_99GS on 2010-10-08
In which case, the OS does a sloppy job of cleaning up after itself. df / can easily be filled to 100%.

---

### Post by warfacegod on 2010-10-08
I've been looking into the system reserve and I can't find anything that specifically says "it is for this". I only found a few vague references to fragmentation and to certain things still being able to run in the background in case disaster strikes. A lot of people are under the impression, myself included, that it's there to act, at least partly, as a buffer to prevent the HDD from being totally filled hence preventing the idiocy that invariably ensues.

---

### Post by CommuneOfLoon on 2010-10-08
> **Paddy Landau said:**
> On an old computer, that is a problem. On a new computer, where you already have more than 100Gb, it's really not something to worry about. The days of expensive storage have gone.

I do have a fairly old computer (Dell Inspiron 6000) with only about 55gb storage :(

So, in terms of Computer Janitor, should I ever use it? To give you an idea of my level of experience, I have no idea what a dependency is.

---

### Post by NightwishFan on 2010-10-08
If you really want to save space, check out Bleachbit, it removes a small amount of stuff that adds up. (Not too much of that in Linux). If you have a fast internet connection, delete the cache of downloaded packages (multiple gigs on my machine)
```
sudo apt-get autoclean
```

---

### Post by lbrty on 2010-10-08
Everyone has different preferences on how/why/why not to run maintenance on ones machine. In my opinion, I think Computer Janitor is useless and I have removed it from my machine.

I do the following once a month.

**Delete Residual Config packages**
Synaptic Package Manager
Status
Click Residual config (if it does not appear, you do not have any residual packages)
Mark for Complete Removal
Apply

Can be installed under Ubuntu Software Center
Run BleachBit (root)
Run GConf Cleaner

---

### Post by barney385 on 2010-10-08
Thanks.

This is good info.

---

### Post by cgroza on 2010-10-08
> 
I run my servers with a hands-off policy, with no maintenance and no updates.  Once they
 

Even if Linux is more secure than windows , exploits are still found and crackers try to make use of them.Each update usually fixes a bug or a security hole.

---

### Post by Jesus_Valdez on 2010-10-08
What about 

```
sudo apt-get autoremove
sudo apt-get autoclean
```

I do that everytime I'm bored.

---

