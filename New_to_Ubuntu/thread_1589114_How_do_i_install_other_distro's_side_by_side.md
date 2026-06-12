---
title: "How do i install other distro's side by side?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by juil on 2010-10-05
I didn't know how to search on this topic...
I want to install other distro's (specifically Arch, Debian, #!Crunchbang) on the same machine and have them appear in Grub.
I already have Ubuntu installed. I want to install these distro's to learn linux.

I already know how to get info on configuring GRUB.
If someone could direct me to a link, and even write a small tutorial, I'd really appreciate it.

---

### Post by oldfred on 2010-10-05
Some info on partitioning:
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Old using grub legacy to chainboot, grub2 will boot everything if you want, but shows planning required:
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by devondashla on 2010-10-05
> **juil said:**
> I didn't know how to search on this topic...
I want to install other distro's (specifically Arch, Debian, #!Crunchbang) on the same machine and have them appear in Grub.
I already have Ubuntu installed. I want to install these distro's to learn linux.

I already know how to get info on configuring GRUB.
If someone could direct me to a link, and even write a small tutorial, I'd really appreciate it.

Just install one distro (since you already installed Ubuntu, you have this part done!), then install the second one. But when installing the second, at some point in the installation you will be prompted to partition the drive. If it's Ubuntu based (Mint, Crunchbang, etc.) then you should have a screen with an option to install the 2 OS's side by side. If it is not Ubuntu-Based, just follow the partitioning instructions for that distro, with it's own seperate partitions. Generally, you'll do this in GParted, and you can easily find instructions on google.

Honestly, it's easier to install the second operating system AND THEN Ubuntu. Ubuntu has a simpler and more straight-forward installer than other Distro's.

P.S. I know this is somewhat biased, but I just want to let you know I would not mess with Arch on a dual boot. The Arch Install is already complicated enough.

---

### Post by devondashla on 2010-10-05
P.P.S. I noticed you said you wanted to this to 'Learn Linux'. Just to let you know, you can do this quite well by just USING Linux. I have never dual-booted two distro's in my life, and I am satisfied with my knowledge of tools in Operating Systems, although I will NEVER get into programming.

---

### Post by scrooge_74 on 2010-10-05
Good you want to learn linux, but you may be going a bit to fast on your learning curve and may skid and go off road at that speed.

Take it slow, get the hang of one then install a second one so you can see how things change from one flavor to the next.

Mostly it will be things like, place where things are stored or the flavor of your desktop.

In fact an easier way to test other distros if you have enough power on your hardware is to just install VirtualBox and then you run those other distros from inside. Is going to be easier and faster than messing around installing several distros.

And again take it slow, learn one then jump to another one. Also you could learn them depending on flavors: debian based, Redhat based, Arch based, etc.

---

### Post by jadedcritic on 2010-10-06
I can sympathize with the op's intentions, but much as people have already stated, the method is a bit off.  At least in my experience, there's a difficulty spectrum, and all kinds of issues that popped up when I tried to load multiple distros. ( Mostly because I was trying to share partitions).  I'm sure people will disagree, but I tend go think ubuntu and mint are the easiest ones to learn. So they're ideal places to put a stake in the ground until you're feeling comfortable, and then move up.  I've been lucky, I know some g> uys at work who are fervent Linux users, I can usually ask them questions, and by and large our IT dept has left us alone to do what we want with our laptops unless it becomes a serious issue.

Since I actually tend to spend more time per hour on my work pc, it's been helpful for me to get comfortable .  My current plan is to work my way up. Ladder starts with ubuntu and mint, followed by fedora, then sabayon, then arch, ends in gentoo and slack ware. Figure if I can learn gentoo I can learn anything.  I recommend others do the same.  Just my 2 cents.  Still, it definitely does take patience!

---

### Post by juil on 2010-10-06
Thanks to all of you!
All of your advice is super helpful! I've bookmarked this post already.

scrooge_74, I'm gonna take that advice. I think your right. Take it slow. I want to install Arch Linux next. I know the installation is complex so wish me all the best! I'll need it! 

As for programming, I think I might be interested in knowing just enough to be proficient at Linux.

Open Source is the future and I don't want to be too late!

EDIT: As for loading multiple distro's, that is not my intention. I want to use just one at a time, but have the option to choose which one whenever i feel like it. Does this make sense or is there some lack of knowledge in this statement? Maybe i don't quite understand how GRUB works...

> My current plan is to work my way up. Ladder starts with ubuntu and mint, followed by fedora, then sabayon, then arch, ends in gentoo and slack ware.

This is also my plan....Except never heard of Sabayon. Will look into that. :)

---

### Post by ipatfrmww on 2010-10-06
Once you have all the other distro's installed you may want to use Ubuntu as the default in grub. You can do this easily by using the version of grub you have installed on Ubuntu.
To do this you need make your MBR point to the grub on Ubuntu. Boot into Ubuntu and type this at the terminal:
```
sudo grub-install /dev/sda
```

This will install grub into the MBR of sda (change this if your hard drive has another device name, this would be a good thing to check BEFORE you do it)
Note that you can do this command inside any of the other distro's you have and it should make their version of grub the default boot loader for your hard drive.
You may also find this command useful:
```
sudo update-grub
```
This will re-propagate the list you see on boot-up so that it includes the other distro's

---

### Post by jadedcritic on 2010-10-06
> **juil said:**
> 
This is also my plan....Except never heard of Sabayon. Will look into that. :)

If the rumors are true, Sabayon is basically kid-gloves Gentoo.
[http://tinyurl.com/2eotoo](http://tinyurl.com/2eotoo)

If that's true, (I haven't confirmed it), then it strikes me as a logical way to transition into the higher tier/more difficult distros: Arch/Slackware/Gentoo.

I thought about linux from scratch also, but I'm fairly convinced that if I can handle Gentoo, I can handle anything.

---

### Post by HermanAB on 2010-10-06
Howdy,

Multi-boot is very last century.  The modern method is to install Virtualbox or VMware Player and create a VM for each distro that you want to play with.

---

### Post by juil on 2010-10-06
> Howdy,

Multi-boot is very last century. The modern method is to install Virtualbox or VMware Player and create a VM for each distro that you want to play with.

I've never used Virtualbox but aren't there limitations when it comes to configuring and tweaking the distro your running?

Also, regarding Gentoo, I picked up this comment in youtube. If what he says is true then, maybe it's not worth getting gentoo, unless like he says your a linux hobbyist.

> Gentoo&#65279; is only faster than Arch if you have a piece of s**t computer with old hardware. To the naked eye, Arch is just as fast as Gentoo and is less hassle. Gentoo is not worth the effort and is only for Linux hobbyists and not general computer enthusiasts, if that makes sense.
Gentoo is becoming more and more obsolete as hardware technology increases.

---

### Post by scrooge_74 on 2010-10-06
In regards to limitations on configuring a distro using Virtualbox, not really.

It gives you some options for network cards, usb, audio, video. Is like putting together a compatible hardware PC, when you start installing the Distro takes care of the rest.

I have run as VMs CentOS, Pfsense, Debian stable/testing, Ubuntu (several versions), XP SP3, WinServer 2003, Open Solaris, Win 7, and once even FreeBSD

---

