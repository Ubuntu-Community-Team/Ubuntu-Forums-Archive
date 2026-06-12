---
title: "Server v Desktop version"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by colmac on 2010-10-05
Hi , complete novice here.

I'm an experienced Windows user, who happily builds and maintains PC's for friends, family etc, but I've never been able to fathom Linux.

I decided to add a new pc to my small home network (1 PC, 2 laptops), and I have a 3 year old Motherboard/chip combination that I will use.

The main use for the machine will be to sit and hold my data, mostly a combination of various multimedia files, but in particular my 30,000 photograhic images from my hobby. The files would then be available for each of the other machines to access. Once set up, I may not even leave a Keyboard or mouse attached to it.

Anyway after a bit of reading, i decided to choose Ubuntu server edition. I tried to install it, but did not get beyond the partitioning, as I did not understand the questions/options available.

So now I've downloaded the PDF Pocketbook which I'll read, but I have a question first.

Do I really want or need the Server edition for what I want, or is the desktop edition what I need? I've never built/run a server before, and I'm not sure if what I want is actually a "Server" or simply a PC acting as a storage centre.

If I can narrow down what I want, then learning about it might be easier.

Thanks folks for listening. Any help much appreciated.

Colin

---

### Post by Najand on 2010-10-05
You probably need the Desktop edition. Considering you are a Windows user and had been using the GUI all the time, Desktop edition is also easier to use for you.

---

### Post by NightwishFan on 2010-10-05
This link should come in handy:
[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

Generally you would want to use the desktop edition. There is little difference between the two except default configuration and files that come on the cd. For example I use the desktop cd to install, and then later add a server kernel for my needs.

If you want a Graphical Interface (GUI) at all use the Desktop CD to install.

---

### Post by colmac on 2010-10-05
Wow! That was quick.

Thanks for the feedback.

I'll read the desktop edition info.

---

### Post by colmac on 2010-10-05
Installed Desktop edition. Like it a lot.

Still trying to learn. No idea when I go to download Flash and it asks me which version (of 5 I want).

Also haven't found out how to configure my network properly. Cant see the Ubunto PC on my Vista PC yet, but I can see the other way.

Finally need to set up my second disk drive ( a partition of my single logical disk). I then want to add 2 other drives.

---

### Post by colmac on 2010-10-05
Just read I want the APT version of Flash

---

### Post by NightwishFan on 2010-10-05
Flash as in Adobe Flash? Just run:
```
sudo apt-get install flashplugin-installer
```

Or just search "flash" in software center.

---

### Post by Najand on 2010-10-06
> **colmac said:**
> Installed Desktop edition. Like it a lot.

Still trying to learn. No idea when I go to download Flash and it asks me which version (of 5 I want).

Seems someone else helped you with that.
> 
Also haven't found out how to configure my network properly. Cant see the Ubunto PC on my Vista PC yet, but I can see the other way.

1. What is your problem with configuring your network?
2. To able to mount Linux Hard Drives you need a third party tool like EXT2FSD ([http://sourceforge.net/projects/ext2fsd/]("http://sourceforge.net/projects/ext2fsd/")) installed on your Windows.
> 
Finally need to set up my second disk drive ( a partition of my single logical disk). I then want to add 2 other drives.
What do you want to do with that?

---

### Post by colmac on 2010-10-06
Hi Folks thanks for the help so far.

Yes I managed to get Flash installed quite happily. Thanks

I then stopped to read the Pocket Guide to Ubuntu that was reccomend here. I'm at page 90 out of 170 so far. I'll finish it today. I certainly wont have taken it all in, but I will have understood some of the principles.

Its well written and explains most things pretty well.

My plan is to get the network set-up and take some of my HDD's from my main PC and store them on my Ubuntu PC, effectively using the machine as a file store.

I am a hobby photographer and also make lots of animated slide show. As a result, I have thousands of images, videos clips and sound FX etc. Most of them are accessed rarely. When I need them tho I sometimes want to use my laptop, sometimes my desktop.

Having it all stored centrally will also simplyify my main PC. It currently has 5 physical disks as well as external USB ones for back-up. At least 2 of these disks will be moved to the Ubuntu PC.

I'll download EXT2FSD now and install that

Thanks

---

### Post by HereInOz on 2010-10-06
If you want to access your home folder on the Ubuntu machine from your Vista machine, which is what I think you want to do, as in "My Network Places" in Windows, you need to install Samba on the Ubuntu machine.

Some aspects of Samba are already installed, which is why you can see the Vista machine from Ubuntu, but you need all of Samba to make the Ubuntu home folder visible from Vista.

You should also install system-config-samba, which will give you a GUI to configure your Samba shares and make it/them visible from a Windows computer.

It will take a little trial and error, but once you get it right, it is easy.  Be careful of firewalls on the Ubuntu machine - they can stop network sharing in its tracks.  Best disable the firewall until you get it all sorted, then if you want to, re-enable it and configure it to pass the Samba ports through the firewall.

---

### Post by colmac on 2010-10-06
Thanks. Yes, I do want to see all my Ubuntu disks on the Vista machines.

I'll have a look now at Samba. Bit more reading for me.

I'll update later.

---

### Post by colmac on 2010-10-07
Getting there now.

I've added an extra hard disk, I've installed Samba and it seems to work initially. I've created folders  to share on the Ubuntu drive, and I can now quite happily copy files from my Window PC to my Ubunto one.

When I reboot however the  share settings are gone.

I cannot see anywhere to set them as permanent shares. Can someone help please.

Ta

---

### Post by NightwishFan on 2010-10-07
I do not know much about networking, however here is a guide on Samba for Ubuntu.
[https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

---

### Post by colmac on 2010-10-07
BY the way you are right, the Firewall is a pig. I've turned it off for now as you suggested. But if the Share wasn't holding it may not have been a firewall issue

---

