---
title: "Horrible wireless experience"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by FreedomIsntFree on 2007-02-24
Hey everyone.  I have been a linux user for probably a good 4 years now  even this simple problem has seemed to stump me.  Here's the deal.  I have recently bought a Gateway MT3705 from Circuit City (I sell PCs there so I got a really good deal on it.)  and I can't seem to get the wireless working in the slightest.  Seems to be a kernel issue so I have searched for workarounds for it for the past few days.  Of course, Ubuntu was my first choice distro wise and all seems to work great with the exception of the wireless.  I have tried Ubuntu, Mepis, and DreamLinux and Ubuntu is actually the only distro that my LAN even works out of the box.  My wireless card seems to be based off the Realtek 8185L chipset.  I have tried Realtek linux drivers, and NDISwrapper.  NDISwrapper says hardware is installed and present and under network settings its showing my wlan0 is active and enabled yet I cannot find any local networks.  Any ideas?  If anyone has gotten this to work, please send me a step-by-step.  I REALLY don't want to boot WinBlows again.

Thanks!

---

### Post by soul814 on 2007-02-25
I'm in the same boat as you and i've been trying to figure this out for 8 hours =]. I've been searching and searching and trying everything and nothing works. I see my wireless connection in iwconfig and iwlist scanning shows me available networks but i just cant seem to connect to it =/

---

### Post by tgalati4 on 2007-02-25
Wireless cards are cheap these days.  Perhaps it's time to change cards to something more compatible.  There's a wiki dealing with out-of-box wireless experiences.

---

### Post by gradedcheese on 2007-02-25
Your nickname, "FreedomIsntFree" is fitting :)  Buy a WiFi card that contains a chipset made by a company that actually provided documentation to the community and, thus, has a real Linux driver supporting it.  Don't settle for a bad wireless experience or this ndiswrapper crap, buy something with a Ralink chipset, most Atheros, Prism, etc.  Avoid companies like Broadcom, Marvell, and Realtek until they get their act together.

That said, if your WiFi is built-in (and that's what it sounds like), we should probably go ahead and troubleshoot it and get it working.  It's not really your fault that Gateway soldered this one to the board, but in the future purposely choose a laptop with Intel wireless (why?  Intel actually stated the ipw_ series of open source projects and actually works with the community).

If you or anyone wants to hear my speech about why WiFi support is the way it is in Linux, I'll be happy to post it :)  It's the exciting story of chip makers, the FCC, and media access control (MAC) implementations.

---

### Post by dmizer on 2007-02-25
according to this thread: [http://www.ubuntuforums.org/showthread.php?t=210958](http://www.ubuntuforums.org/showthread.php?t=210958) this card can work in edgy with ndiswrapper if you make sure to blacklist the native rtl8185 module.

there is also a bug open on this ... the consensis is that this is a kernel issue because the problem is not platform specific. [https://launchpad.net/ubuntu/+bug/55905](https://launchpad.net/ubuntu/+bug/55905)

there seems to be some good links and information in the bug report, i'd have a look there if blacklisting the native driver doesn't work.

---

### Post by FreedomIsntFree on 2007-02-25
Well after looking through the bug reports, after weeding through all the people arguing on if it is a kernel bug or not (come on guys, us *nix users are a community, don't argue amongst each other.  We are here to work together to bring down WinBlows >:) )  I found that the person down at the bottom booted Feisty and it works fine.  Think I shall try Feisty and see if that solves the problem.  Will report back after I try it out tonight.  Thanks for the help!

---

### Post by FreedomIsntFree on 2007-02-25
Heh...  Seems Feisty wont even boot.  Frozen at the "Configuring network interfaces" line.

---

### Post by FreedomIsntFree on 2007-02-25
Fixed!  I'm currently booting Kubuntu Edgy and I got some new drivers for my card and used ndiswrapper then ran ifconfig wlan0 up and rebooted.  Don't know why that wasn't working before.  Might be the fact I was running regular Ubuntu before but that shouldn't be the case sicne the really only difference is KDE and Gnome.  It is still not showing the correct signal strength but that can be pushed aside for now since I now have it up and running.  Still wondering why Feisty Herd 4 would'nt boot thought...

---

