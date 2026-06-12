---
title: "It...just...doesn't work!!"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by Keiji on 2007-06-04
Okay, so I have 3 computers: a desktop with Windows Vista Home Premium, a desktop with Ubuntu 7.04, and a laptop with Ubuntu 6.10.

Now, on my Vista computer, I shared the "Public" folder, and can access it fine with my username and password from my Ubuntu desktop. However, I cannot access it from my laptop. Even when using the smbclient command from the terminal and typing exactly the same thing, it will not work on the laptop. All the computers have the same workgroup.

Also, I have a (supposedly) shared folder on my Ubuntu desktop. I could access this fine from my laptop, but then after setting up my Vista shared folder, I can no longer access my Ubuntu desktop's shared folder at all. So, I cannot transfer files between my laptop and other computers at all over the network, which is extremely annoying.

Any help?

I don't want to upgrade my laptop to 7.04, because it seems to have a big problem with screen resolutions. That's the other thing that's annoying me and I can't be arsed to post a new topic about it: even though my Ubuntu desktop is attached to a 1280x1024 resolution TFT screen, it just won't use that resolution at all, no matter how much I mess with xorg.conf. Which makes it inferior to my laptop, which is ridiculous.

---

### Post by willskills on 2007-06-04
Do you have user and samba accounts set up exactly the same?

---

### Post by renzokuken on 2007-06-04
not great with this but one tip......

....use Samba to share between Vista dn Ubuntu, and NFS to share between Ubuntu and Ubuntu

---

### Post by AlanR8 on 2007-06-04
I thought I responded to this earlier today but I see my response is not listed. Hmm...must have got distracted. I had similar problems when I first started with Kubuntu, not Ubuntu. 

I have an XP Pro box on the network and now have three Kubuntu boxes including my Sony Vaio Laptop that connects wirelessly with no problems. Initially, I could see the Doze box from the K boxes but not the other way round. Indeed, if I logged on to my router the K boxes just were not there!

The purists will doubtless not agree with my fix but I just downloaded Webmin which presents a graphical interface for almost all the settings on your computer and network. BUT, be warned, you can get in a mess if you fiddle with things...you have been warned!

Once downloaded and installed, it presents as a web interface in the browser of your choice, go down to the "Servers" tab on the left and select "Samba Windows File Sharing". You'll find a host of tools to sort your network out and even buttons at the bottom of the screen to stop and restart your Samba server. It automatically makes all the changes required in the various .conf files. It took a bit of fiddling but after a couple of hours all the machines talked to each other and all get on well.

The command line is a wonderful thing but why have to remember commands when there's a web interface designed to make your life easy?

---

### Post by Keiji on 2007-06-12
> **willskills said:**
> Do you have user and samba accounts set up exactly the same?

Yes, on both my laptop and my desktop, almost all my settings are the same, username and password are the same, the workgroup is the same, pretty much the only differing thing is the distro version.

> **renzokuken said:**
> not great with this but one tip......

....use Samba to share between Vista dn Ubuntu, and NFS to share between Ubuntu and Ubuntu

I will try that.

> **AlanR8 said:**
> The purists will doubtless not agree with my fix but I just downloaded Webmin which presents a graphical interface for almost all the settings on your computer and network. BUT, be warned, you can get in a mess if you fiddle with things...you have been warned!

Once downloaded and installed, it presents as a web interface in the browser of your choice, go down to the "Servers" tab on the left and select "Samba Windows File Sharing". You'll find a host of tools to sort your network out and even buttons at the bottom of the screen to stop and restart your Samba server. It automatically makes all the changes required in the various .conf files. It took a bit of fiddling but after a couple of hours all the machines talked to each other and all get on well.

The command line is a wonderful thing but why have to remember commands when there's a web interface designed to make your life easy?

Hmm, I may try that too. While config files are nice, I like to know everything I can possibly change about a config, whereas you usually see some settings in config files which if they aren't present are interpreted as their default value, and are never mentioned. So obviously GUIs fix that problem, besides being easier to use. :P

Also, I have another problem now. While trying to access my Vista comp from my Ubuntu desktop through Nautilus, it works, but if I try and copy a file there, it gives an error, and I have to then click Retry and reload the folder to see that the file is indeed there (so what was the error for?) I've decided to just use smbclient at the terminal for transferring files now.

Anyway, thanks for your replies, and I'll try out your suggestions when I get to it. :)

---

### Post by Keiji on 2007-07-17
Well, it turns out I fixed all my problems (networking and screen resolution) simply by downgrading my Ubuntu desktop from 7.04 to 6.10, like my laptop. Now both my Ubuntu and my Vista desktops can access my laptop's networked folder.

Is anyone else having trouble with 7.04? I'm kinda wondering where the dev team is trying to take this, since I've noticed a lot of stupid things in 7.04 quite reminiscent of Microsoft's move to Windows XP (like the whole "let's go find a program that we haven't installed to open this file in even though the user of this computer probably doesn't want that anyway" idea). Looks like I'll be sticking with 6.10 for a while :P

---

