---
title: "Recommend me a linux distro..."
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Mountaingod on 2009-11-13
...that uses minimal resources, but more importantly comes as a 'bare-bones' setup, leaving the user to add programs & utilities as required.

Sorry if this is in the wrong place, I was looking for a 'general discussion' section, but the only one here is for 'non-technical discussions'!

The distro needs to be lightweight because it's going on an old laptop with 768mb ram, 2.6ghz Celeron processor, and 20gb disk space. My second requirement comes out of my most recent battle with Xubuntu (which I'm now about ready to ditch).

I've just failed to get FreeNX and/or OpenSSH Server to work on said laptop with said Xubuntu, despite following the relevant (and up-to-date) instructions. This one problem reopened my queue of existing-problems-waiting-to-be-solved which, when put together, tie my hands should I attempt anything more complex than "internet and word processing".

A case in point is installation and uninstallation. It's all very nice to have a package manager list programs, check dependencies, download and install in one action - but within this totally opaque and automated process I'm not told what files are being put where, whether the OS is being modified and how, or how to pry it all back out should I need to.

This is one of the most basic and fundamental functions an OS performs, but with Ubuntu I'm left not knowing what's there and what isn't - essentially, I can't trust my own computer to 'tell it to me straight'. I used to reinstall Ubuntu fresh every time rather than uninstall single programs, because otherwise I'd always find bits of whatever I thought I'd uninstalled scattered throughout the filesystem.

When Windows used to do the same thing, I learnt where I had to look and what precautions I had to take to keep a good grounding in the state of my system. Nowadays M$ has improved in some ways but diminished in others. Installing is better (installed files go where you tell them, config goes in the registry), but opaqueness and 'hiding things from the user' have become much worse. Vista's interface is so simplified it actually tells you very little, beyond "here's the internet", "here's your pictures", etc.

Unfortunately, Ubuntu is taking this path too, presumably to bring less IT-focused people into the fold. I noticed many of the programs listed in the 'Applications' menu aren't even referred to by the name of the program - again, great if the user just want to point-and-click their way to a 'Movie Player', but incredibly irritating if they actually want to have a hand in the composition of their system.

Rant aside, I've decided I need something I can rely on not to ship with loads of stuff I have to remove and replace, given the aforementioned install/uninstall fiasco. I intend to learn Linux starting with the basics. A customised system was my original reason for making the switch anyway.

Thanks for your help.

---

### Post by snowpine on 2009-11-13
Hi Mountaingod, 

Ubuntu *can* be a "bare bones" distro if you start with the minimal CD:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This is how "minimalist" Ubuntu remixes (like CrunchBang) do it.

If you're looking to move outside the Ubuntu/Debian realm (sounds like you have some philosophical problems with the apt package manager), you might check out Arch. Give this a read and see if you agree with the philosophy:

[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

> Arch Linux keeps the inherent complexities of a GNU/Linux system intact, while keeping them well organized and transparent. Arch Linux developers and users believe that trying to hide the complexities of a system actually results in an even more complex system, and is therefore to be avoided. 

---

### Post by sisco311 on 2009-11-13
Ubuntu minimal: [http://psychocats.net/ubuntu/minimal]("http://psychocats.net/ubuntu/minimal")  

ArchLinux: [http://wiki.archlinux.org/index.php/Beginners'_Guide]("http://wiki.archlinux.org/index.php/Beginners'_Guide")

EDIT:
oops, too late. :)

---

### Post by winotree on 2009-11-13
For starters there's [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) if you're wanting to stay with Ubuntu.

On the other hand here's something that I'd do **if** I had a second [back-up] computer [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)  

I'm sure you'll get many responses on this topic -- best of everything to you in your efforts!  ;)

---

### Post by Hospadar on 2009-11-13
I would skip linux from scratch.  In my opinion it doesn't get you anything you can't get much more easily from a distribution.

I've installed systems starting with ubuntu server before, that's worked well for me.  Server is basically the same thing, it just has a lot less stuff installed by default (i.e. no GUI).

That said, I think the system you've described would run stock ubuntu just fine.  I've run systems with the same ram and a 1Ghz cpu that do OK.  

If you want something really fast though, you could look at doing a server-style install with debian or ubuntu, then installing lxde on top of that (it's a nice, very lightweight desktop environment).  If you want something *really* fast, you could go with puppy or dsl, but on your hardware I don't think that's necesary.

I personally prefer trading the extra performance I might squeeze out of a lighter setup for all the convenient extra features of a complete environment like gnome.

---

### Post by Simian Man on 2009-11-13
Arch sounds pretty much perfect for you, and Slackware or Zenwalk might be a good choice as well.

Linux from Scratch is more complicated than you probably want since you will be installing from source.

Ubuntu minimal would be much more bare-bones than full-fledged Ubuntu but, because of the way the packages work, will never be as minimalist as other distros like Arch.

---

### Post by ukripper on 2009-11-13
I'd recommend Arch or Sidux (with KDE-lite instead of XFCE), both are rolling distros. In ubuntu realm - If you want really light weight DE try LXDE on UBUNTU - [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by durand on 2009-11-13
I'd recommend crunchbang however, I would not class 768mb ram, 2.6ghz Celeron processor, and 20gb disk space as an old computer...

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

If you're up for a bit of learning, you could try gentoo. Its a very nice linux distribution but you would need to work for it :)

[http://gentoo.org](http://gentoo.org)

---

### Post by kaivalagi on 2009-11-13
I'd recommend Arch, I switched to it from Ubu 9.10 after having enough of 6 monthly headaches with the updates...it is rolling release based so no mammoth updates twice a year...

The Arch wiki is great too, users have put some serious effort into it

---

### Post by anewguy on 2009-11-13
I wish *I had* a computer that "old"!  :)

Dave :)

---

### Post by DGortze380 on 2009-11-13
Arch lets you build totally from scratch.

---

### Post by LunaticHiatus on 2009-11-13
I don't care for arch, and its roling (broken) release. I vote ubuntu minimal. I was surprised no one suggested Debian netinstall as well. Its lighter then minimal ubuntu and you wouldn't be leaving your comfort zone.

---

### Post by Mustard on 2009-11-13
'Linux from scratch' was a fun exercise for me in building a system from bare bones. :)

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Its not an easy process, but its an interesting one.


Another opton, which I just noticed was mentioned in the previous post, is a debian network install CD.  It can give you the option to start from a very minimal system as well.  Debian package management makes it quite simple to expand on that minimal install.

---

### Post by fooman on 2009-11-13
masonux is a nice, minimal install distro....based on ubuntu 9.04 and using lxde.  doesn't come with much else but firefox and pidgin by default,  but you can add whatever else you like through the normal means (apt-get,  synaptic).

[http://sites.google.com/site/masonux/downloads](http://sites.google.com/site/masonux/downloads)

---

### Post by andrew.46 on 2009-11-13
Hi Mountaingod,

I am a little surprised that nobody has given Slackware 13.0 a big push yet. I run it as my primary distro with multiple variants of Ubuntu as virtual machines and I suspect it meets most of the criteria you mention. I attach a couple of screenshots of Slackware 13.0 running with xfce to tempt you :).

All the best,

Andrew

---

### Post by NickJones on 2009-11-13
I'm running Ubuntu 9.10 on a laptop with lower specs than yours, and I have no problems.

---

### Post by rubendrr on 2009-11-13
If it's control you want, try Gentoo ([www.gentoo.org](www.gentoo.org))! Disclaimer: You may lose half a summer (well, could have, three months ago) while learning how to get everything working exactly the way you want it to. That's what happened to me, at least! And then an upgrade I unwiselly applied screwed it up...
Anyway, if you do go the gentoo way, be prepared to compile everything - this is NOT a binary-based distro!
Or you could try (as many have said) Arch. I really like its simplicity, not to mention the fact that the rolling release model really thrives!
Also, check out frugalware (frugalware.org). Also minimalist, though not quite as much as arch, and also uses pacman, the arch package manager!

Personally, I've tried these three, and also slackware, debian, mandriva, pclos, fedora, etc, and I haven't found a distro I really dislike.

---

### Post by winotree on 2009-11-13
Here's something I'm looking at over the weekend [http://u-lite.org/](http://u-lite.org/) which you may find interesting.  There's a lot out there!  Have fun!

---

### Post by Mountaingod on 2009-11-14
This is all great stuff, thanks a lot for your help! Ubuntu has given me far from nothing - it was the right choice when I wanted a user-friendly entrance to Linux. It's just the more I've begun to customise, the more its 'user-friendliness' has gotten in the way.

I've looked at Slackware, but as some have said elements of it require more knowledge than I currently have. From what's been said, Arch's philosophy does seem to match what I'm after. I'll shop around though, a 'minimalist' form of ubuntu may be sufficient.

Thanks again, this remains the most helpful support forum I've used.

---

### Post by Norm24 on 2009-11-14
Puppy Linux.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by andrew.46 on 2009-11-14
Hi Mountaingod,

> **Mountaingod said:**
> I've looked at Slackware, but as some have said elements of it require more knowledge than I currently have. 

That was true in my case as well, but Slackware is an excellent teacher :).

Andrew

---

### Post by Ji Ruo on 2009-11-14
I wonder if some of your problems have come from using XFCE as the desktop. Ostensibly, it's the desktop for underpowered systems, but in practice I have found 1) no real difference in performance between the GNOME and XFCE desktop and 2) greatly increased difficulty in finding and getting advice on how to get things done.

My laptop that I'm typing this on was abandoned and it's lower spec than yours - 800Mhz Celeron, 256Mb ram, same size hard drive. I'm running Ubuntu 9.04, with ext4 as the file system (default now on Karmic, but available as an option during the Jaunty install) with which I did notice a performance improvement over ext3.

To speed it up, I did remove some programs from the startup sequence (in Gnome this is done by System>Preferences>Startup Applications). I unchecked - Bluetooth manager, Check for new hardware drivers, Evolution alarm notifier, Update Notifier. They can be replaced at startup if I ever needed them again, by rechecking the boxes. I also changed Update manager to only check manually for updates. You can also install bum - boot up manager, which is a gui for modifying the init.d and runlevel files and allows even more control.

This system runs firefox with add-ons and open office, no problem. More than a couple of applications open would be a struggle, but that's always going to be the case with this hardware.

So my solution would be to try GNOME, though Linux From Scratch would be educational (I will probably try it sometime).

With regard to what is going where, I personally see this as more of a problem with not being able to find the information on how Ubuntu works internally. Ideally we would have some information available on how all of the different programs work together, in one place and in a format that is understandable to non-experts. This would be difficult but not insurmountable.

---

### Post by winotree on 2009-11-17
Not sure if you're still looking but thought that you might find this interesting.  [http://linuxondesktop.blogspot.com/2007/03/13-applications-to-install-on-ubuntu.html](http://linuxondesktop.blogspot.com/2007/03/13-applications-to-install-on-ubuntu.html)  The information is a bit dated but most, if not all the apps are still available.

---

