---
title: "Trouble with Broadcom-based wireless card (Belkin F5D7001)"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by temoshi on 2007-04-26
Hi,

I'm a somewhat knowledgable Windows user who is interested in switching to Ubuntu (7.04, Feisty Fawn). I don't have a lot of experience with Linux distributions, so I will try to be as descriptive as possible.

Like the title says, I have a Belkin F5D7001 wireless network card and I'm having some trouble getting it to work with Ubuntu. I did a bit of searching and have been able to determine that my card is Broadcom-based, though I don't entirely understand what that means. I did a forum search and started following [this](http://ubuntuforums.org/showthread.php?t=201902) guide. I blacklisted the default bcm43xx driver (because apparently it doesn't work well) and everything was going smoothly until I got to the part with ndiswrapper. I don't have any other internet connection available, so I need to install it from the Ubuntu installation disc. I stuck in the disc and it opened up to the Synaptic Package Manager, but ndiswrapper is nowhere to be found. I also tried going to the terminal and typing "sudo apt-get install ndiswrapper-utils-1.9", but I get an error saying that it could not be found.

I have the drivers for my card (bcmwl5.inf and bcmwl5.sys) and I understand the rest of the guide, but I can't do anything until I have ndiswrapper installed. Right now, my wireless card isn't even showing up when I go to the connection manager. If anyone could offer me some insight as to what I'm doing wrong, I would really appreciate it.

Thanks,
-temoshi

---

### Post by Dieter1967 on 2007-04-26
It would appear that the Broadcom-based chipset used by various manufacturers is causing all kinds of grief with Ubuntu, as well as Fedora Core 6.

I have Ubuntu 7.04 Feisty Fawn.  I've followed several HOWTO posts, which will get the card to work for a while, but if the computer goes to sleep, when I wake it up, the wireless card completely flakes out.  It won't even allow me to take it off "roaming" mode.

So, I'm doing a FRESH install of Feisty, and trying yet another HOWTO.  From what I understand, my card, the 4318, works better with ndiswrapper.  If you can connect up through a wired connection, that's the best thing to do while working on all of this (you didn't specify if that's how you were working).

I'm pretty new to the whole "Linux" world as well, and from everything that I have been told, Linux and wireless communications are not exactly the best of friends.  No big whoop.  I'll deal with that.  Beats the heck out of seeing yet another Blue Screen Of Death!

Keep chugging away at it, and don't give up.  Let us know how it turns out for you.

---

### Post by regal_dunce on 2007-04-26
Temoshi:  I'm pretty sure that ndiswrapper is included on the Ubuntu install disk.  If apt-get cannot find it, I could be because it's not searching the disk.  I would try opening your sources.list file:

```

sudo gedit /etc/apt/sources.list

```
This file specifies the locations where your "package updater"  i.e. apt-get will look for packages not currently installed on the system.  At the top of my file, I have a line that says:
```

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

```
If you have this line in your file, try uncommenting it (i.e. remove the # character before deb)  If it's not in your file at all, you could probably just copy and paste it in there.  Save the file, then try:

```

sudo apt-get ndiswrapper-utils-1.9

```

and see what happens.  If this doesn't work, is there any way you could plug into a router for a few minutes to download the file?

---

### Post by temoshi on 2007-04-30
Sorry for the delayed response.

regal_dunce: I tired what you said and the CD-ROM drive was listed, but it still wasn't installing ndiswrapper when I tried. So, I got frustrated and did a Google search for "ndiswrapper deb ubuntu" and downloaded the files to my flash drive from [here](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/). I finished the guide I linked to earlier and it seemed like everything was installed correctly. I even got a pretty decent signal:

[IMG]http://i17.photobucket.com/albums/b52/Temoshi/wireless.png[/IMG]

Then I tried to open a page in Firefox, and lo and behold it doesn't work. I really have no idea what's going on here. Any help?

---

### Post by Floppyjoe on 2007-04-30
> **temoshi said:**
> Sorry for the delayed response.

regal_dunce: I tired what you said and the CD-ROM drive was listed, but it still wasn't installing ndiswrapper when I tried. So, I got frustrated and did a Google search for "ndiswrapper deb ubuntu" and downloaded the files to my flash drive from [here](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/). I finished the guide I linked to earlier and it seemed like everything was installed correctly. I even got a pretty decent signal:

[IMG]http://i17.photobucket.com/albums/b52/Temoshi/wireless.png[/IMG]

Then I tried to open a page in Firefox, and lo and behold it doesn't work. I really have no idea what's going on here. Any help?
You may have another problem besides the wireless problem. DNS.
If you can ping ip addresses but not domain names then this is your problem.
The following link may be of help to you:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=15](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=15)

---

### Post by regal_dunce on 2007-05-04
temoshi:  Did floppyjoe's solution work for you?  For my broadcom card, I couldn't get the ndiswrapper version available in the repositories to work, so I got the latest version [ from the ndiswrapper sourceforge link ]("//http://ndiswrapper.sourceforge.net/joomla/") and compiled it.  After that everything works.  It may not be the right solution for you, but it's something to try if all else fails...

---

### Post by temoshi on 2007-05-05
Again, sorry for the delayed response.

I tried the guide that Floppyjoe linked to, and I'm still having problems. The first part of the guide told me to make some changes to the /etc/resolv.conf file. I typed in what it said and tried to save, but apparently the file is read-only and it won't let me save over it either. So, I tried the second part of the guide. I made the changes to the /etc/dhcp3/dhclient.conf file and saved, which worked fine. Then it told me to run a command to restart my network card (or something to that effect). When I did, I got a bunch of error messages and my internet access still wasn't working. Finally, I tried just going to "System -> Administration -> Networking" and changing the settings on the DNS tab manually. Eureka! For a moment, it works. Wanting to make sure it wasn't a one time thing, I restarted and found that it no longer worked. I tried doing everything the same way over again, but I can't replicate the same results. When I open the dhclient.conf file, the changes are still there, but I still can't connect to any websites.

Again, I appreciate all of the help. I'm very enthusiastic about the *idea* of open source software, but so far things have been a bit demoralizing. Hopefully I'll be able to get this working soon.

> **regal_dunce said:**
> temoshi:  Did floppyjoe's solution work for you?  For my broadcom card, I couldn't get the ndiswrapper version available in the repositories to work, so I got the latest version [ from the ndiswrapper sourceforge link ]("//http://ndiswrapper.sourceforge.net/joomla/") and compiled it.  After that everything works.  It may not be the right solution for you, but it's something to try if all else fails...

Honestly, I don't have any idea how to compile software from source code, and I only half understand what that means. Of course, I'd be willing to try this, but I'd need more instruction.

---

### Post by Floppyjoe on 2007-05-05
> **temoshi said:**
> Again, sorry for the delayed response.

I tried the guide that Floppyjoe linked to, and I'm still having problems. The first part of the guide told me to make some changes to the /etc/resolv.conf file. I typed in what it said and tried to save, but apparently the file is read-only and it won't let me save over it either. So, I tried the second part of the guide. I made the changes to the /etc/dhcp3/dhclient.conf file and saved, which worked fine. Then it told me to run a command to restart my network card (or something to that effect). When I did, I got a bunch of error messages and my internet access still wasn't working. Finally, I tried just going to "System -> Administration -> Networking" and changing the settings on the DNS tab manually. Eureka! For a moment, it works. Wanting to make sure it wasn't a one time thing, I restarted and found that it no longer worked. I tried doing everything the same way over again, but I can't replicate the same results. When I open the dhclient.conf file, the changes are still there, but I still can't connect to any websites.

Again, I appreciate all of the help. I'm very enthusiastic about the *idea* of open source software, but so far things have been a bit demoralizing. Hopefully I'll be able to get this working soon.



Honestly, I don't have any idea how to compile software from source code, and I only half understand what that means. Of course, I'd be willing to try this, but I'd need more instruction.

This Link shows how to compile ndiswrapper from source:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

---

### Post by regal_dunce on 2007-05-06
> **temoshi said:**
>  The first part of the guide told me to make some changes to the /etc/resolv.conf file. I typed in what it said and tried to save, but apparently the file is read-only and it won't let me save over it either. 

99.99999% of the time if a file says it's read only and can't be saved, it's because you forgot to type sudo before you opened the file.  Regular users can't edit system files, only superusers.  That's where sudo (super user do) comes in.

---

### Post by der_vegi on 2007-05-06
maybe you can try to install the bcm43xx driver. if it works, it works better than ndiswrapper.
 see [http://ubuntuforums.org/showthread.php?t=434946]("http://ubuntuforums.org/showthread.php?t=434946")

---

### Post by temoshi on 2007-05-08
I tried some of the guides linked to above and starting getting a bunch of error messages that I didn't understand. So, I got pissed off and did a complete reinstall of Ubuntu. Apparently, the guide I was using originally was for Broadcom 4306 cards, while I have a Broadcom 4318. So I started using [this](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318) guide, and still ran into trouble.

I posted the following message in the thread for the new how-to guide I'm using. I'm not sure if I should keep posting here or just stick to that thread (which is over 100 pages long).

> **temoshi said:**
> Hi, everyone.

I'm trying to get my Belkin F5D7001 wireless card (BCM4138) to work with Feisty Fawn. I previously posted a thread [here](http://ubuntuforums.org/showthread.php?p=2541641), but I figured this would be the best place to ask for help.

I had been trying to use some other how-to guides that apparently were for a different model of Broadcom-based cards. I got frustrated and completely reinstalled Ubuntu. Once it was done, I followed this guide to the letter. I extracted the tar.gz file to my desktop and ran the ndiswrapper_setup script like it said.

Looking at what the lines in the terminal window said, I notice:

```
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
```

I have the Ubuntu 7.04 disc in my CD-ROM drive. Does mean that it's not reading the ndiswrapper files from the CD?

Right now, I'm not getting any internet access. No wireless networks show up and it doesn't even appear as though I have a wireless card when I go to the Network manager thing. Any help is **greatly** appreciated.

---

