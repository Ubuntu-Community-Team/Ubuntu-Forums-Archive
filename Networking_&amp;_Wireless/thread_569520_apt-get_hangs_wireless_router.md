---
title: "apt-get hangs wireless router"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by mblackwell8 on 2007-10-07
whenever I try to install software or update my system using apt-get (or synaptic package manager, which presumably works the same way), my wireless router hangs and I need to turn it off and on to get wireless access back. apt-get starts downloading, then slows down and stops. seems to do so at precisely the same point in any given download. seems like i can surf and download anything just fine from the internet, although youtube does seem to cause problems, so perhaps it is something to do with large downloads.

the symptoms are very similar to two previous threads:
[http://ubuntuforums.org/showthread.php?t=560584](http://ubuntuforums.org/showthread.php?t=560584)
[http://ubuntuforums.org/showthread.php?t=517499](http://ubuntuforums.org/showthread.php?t=517499)

the first is unresolved and in the second thread the problem was resolved by changing DSL provider... which is more than I want to do!

i'm a newbie so keep your advice gentle! I have a Netgear RangeMax (WPN824) wireless router and I'm using a fairly stock Feisty installation on a Dell 630m (Intel wireless 2200BG chipset using the IPW2200 driver). I think that I'm using a native driver because lsmod | grep ndiswrapper returns nothing... but when I first set up Ubuntu I blindly followed several howto's to get my environment working.

This problem is driving me crazy and it essentially means that I can't install any software or upgrades...

---

### Post by ajgreeny on 2007-10-07
If possible, make a wired connection to the router and try that to see if it is your wireless that is causing the problem.  If so then perhaps you need to play with the driver config for that.  Otherwise I can't think of anything that would let you connect but then drop you out after a certain time other than your ISP or DSL provider.

---

### Post by mblackwell8 on 2007-10-07
wired connections work just fine... i have a linux box (running ubuntu also) connected by physical cable on my network and I can apt-get on that box to my heart's content.

you're probably right about the wireless driver... perhaps it just falls over under heavy traffic and somehow crashes the router?

---

### Post by mblackwell8 on 2007-10-28
seems to be solved now... although i had to go the heavy iron method: i replaced my netgear wpn824 router with a d-link dir-635 and everything seems to work just fine now.

seems that the netgear router just crashed or hung under heavy traffic load caused by an apt-get download or update manager. i had the latest firmware on the netgear and am using an intel wireless chip (therefore the ipw2200 driver). i also had WPA security running. have exactly the same setup with the d-link and it works fine.

hope this helps someone else

---

### Post by belly917 on 2008-04-23
I know it's been a while since the last post on this thread, but I've decided to post here since I also have this problem.

I have 2 machines that I consistently use linux on and both cause the netgear wireless router to crash.  Here's some info:
[LIST]
[*]I share an internet connection with my landlord, and it's his netgear router in his floor of the house.
[*]The router is configure with WPA-PSK Tkip (used to be WEP still had problems)
[*]My dell laptop has Ubuntu 7.10 installed (currently upgrading to 8.04 via a neighbors wifi) and has an Intel 2200BG Wireless card.
[*]My HTPC runs Ubuntu 6.10 server (mythtv setup) and is wired to a buffalo airstation (wireless bridge that provides 4 ethernet ports for desktop & htpc)
[/LIST]

Both computers cause the router to crash and then my landlord has to reset it.  Meanwhile his wired connection to the router also fails to connect to the internet.

So based on the fact that I have a buffalo airstation handling the wireless connection, I'm fairly certain it's not a driver issue.. it's something that the netgear router can't handle.  Maybe a packet size?  I don't know.  

The consistent pieces seem to be a wireless connections, a netgear router and apt-get/system update.

---

