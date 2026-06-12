---
title: "VCP download HELP!"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by Miss Karen on 2008-03-19
Hi guys

My uni has a wireless network, which is pretty neat. However, they are telling me that I need a VCP to connect to it, which I can download from the net. Where? Anyone? Please?

 :D

---

### Post by sowelie on 2008-03-19
I'm confused, a Virtual Com Port???  Are you running Gutsy (7.10)? If so can you see the wireless network in your list?

---

### Post by Miss Karen on 2008-03-19
Errrr...maybe I got the acronym wrong...something to do with a personal networky thing...

I can see the network in my list, but it won't connect to the internet until I have this last bit. Apparently...

---

### Post by sowelie on 2008-03-19
So when you try to connect for it does it ask for some sort of password?  I am guessing you don't have the key required to connect.  You'll have to contact your Universities IT department I would imagine.  Maybe you were thinking of WEP key?

---

### Post by Miss Karen on 2008-03-19
I've talked to the uni's IT guys, they went all confused but said I had to have a VNP...VCP...something like that...maybe it was VPC...anyway it was something to enable me to connect to the net.

---

### Post by sowelie on 2008-03-19
Maybe it was VPN?  Are you inside of the college at the moment? They might be confused, VPN is Virtual Private Networking, which allows you to connect to the network from remote locations.

---

### Post by AgentZ86 on 2008-03-19
> **Miss Karen said:**
> I've talked to the uni's IT guys, they went all confused but said I had to have a VNP...VCP...something like that...maybe it was VPC...anyway it was something to enable me to connect to the net.

I've not heard of anything that you would need to download from the net to access a wireless router/accesspoint etc.

Perhaps they mean some sort of VPN client or something, if you could ask them again specifically what is needed to connect. ? or perhaps ask them what type of wireless connection is needed to connect ?

---

### Post by Miss Karen on 2008-03-19
VPN! That's it! Thanks guys...any ideas on where to download from?

---

### Post by sowelie on 2008-03-19
Well, you only need a VPN client if you are not at the actual campus.  But, it depends on what sort of VPN they have.  You'll have to get more details out of them.  Most likely it's a Microsoft PPTP VPN. If that's the case you can use this article:

[http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/]("http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/")

That shows you how to easily install a PPTP VPN client with GUI.

---

### Post by Miss Karen on 2008-03-19
Looks great, guys, but no internet on my ubuntu laptop, so I have to download it onto my USB, then install on Ubuntu...help?

---

### Post by AgentZ86 on 2008-03-21
> **Miss Karen said:**
> Looks great, guys, but no internet on my ubuntu laptop, so I have to download it onto my USB, then install on Ubuntu...help?

Are you planning to get the files downloaded from another ubuntu computer accessing the internet, ? or on a windows computer accessing the internet  ?

Ubuntu has a nice blog on this:
[http://onlyubuntu.blogspot.com/2007/04/create-backup-of-installed-packages.html](http://onlyubuntu.blogspot.com/2007/04/create-backup-of-installed-packages.html)

But for windows I'm not sure where the repositories are in order to burn the CD/DVD with the packages you want ?

Basically it can be put on a memory stick/flash drive etc. and installed with add/remove just like all the other programs, but in the add/remove section you have to select installable from CD rom, so I'm not sure how to do it from the flash drive, I think you have to add your own repository for installation etc. or if it's a .deb package I think once you download it to flash you can just click on it and it will ask you if you want to open with gdebi or some installer or something. 

Also if you just type vpn in the add/remove search there are some programs there, however if you don't have internet I'm not sure how to get them to a CD for you I'm researching a bit now

I'll post back
Also do you have a DVD burner available perhaps to burn the whole repository to DVD

How are you accessing the internet now on a windows or ubuntu computer

---

### Post by AgentZ86 on 2008-03-21
I installed APTtoCD and also the VPN package and was going to create a CD for your with this package on it, but when I attempted to create the CD I did not see the VPN package in my list of packages so I'm not sure this will help or not.

I'll post back after some more research

---

### Post by AgentZ86 on 2008-03-21
Well, I think all you have to do is go to Applications/Add/Remove and then search the list for VPN, and once you select to install the once that says VPN Connection Manager (PPP generic) the once with 4 stars then it will ask for the Ubuntu 7.10 CD

If that one is not listed then I'm not sure how to update the repository without downloading it from the net to a CD

I hope this helps,

---

### Post by Miss Karen on 2008-03-23
Thankyou so much for all your help mate :D

To answer your question, I post here from a Windows computer  - and I never got the Ubuntu 7.10 CD, because my laptop came with it pre-loaded.

I'm just kind of desperate to get this VPN up and running so that I can patch into the uni network and install packages for my DVD player (sigh, one thing after another!) :D

The uni tech guys said that all I needed was the VPN, and they could set it up from there. Mind you, I'm not sure they'd ever seen Ubuntu before...:confused:

---

### Post by AgentZ86 on 2008-03-23
> **Miss Karen said:**
> Thankyou so much for all your help mate :D

To answer your question, I post here from a Windows computer  - and I never got the Ubuntu 7.10 CD, because my laptop came with it pre-loaded.

I'm just kind of desperate to get this VPN up and running so that I can patch into the uni network and install packages for my DVD player (sigh, one thing after another!) :D

The uni tech guys said that all I needed was the VPN, and they could set it up from there. Mind you, I'm not sure they'd ever seen Ubuntu before...:confused:


Here is a place to download the VPN:
[http://launchpadlibrarian.net/6716221/pptp-linux_1.7.0-2ubuntu2_i386.deb]("http://launchpadlibrarian.net/6716221/pptp-linux_1.7.0-2ubuntu2_i386.deb")

Then just click on the package from your Ubuntu system and the firefox windows will come up asking if you want to install with Gdebi, just select OK for yes. and it will install it.

Then to access the VPN setting just click the Ubuntu network icon in the upper right of most Ubuntu installs, and you will now see a VPN configuration menu item.

I hope this helps.

P.S it was RealPSL who really posted the download, I asked this in another post to get this answer for you.
Other post is here:
[http://ubuntuforums.org/showthread.php?t=733053]("http://ubuntuforums.org/showthread.php?t=733053")

---

