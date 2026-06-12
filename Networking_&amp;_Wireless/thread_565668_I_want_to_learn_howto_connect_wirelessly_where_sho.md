---
title: "I want to learn howto connect wirelessly where should I begin?"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2007-10-02
I want to learn how to connect with wireless but I can't find any general step by step instructions to test whether my USB wireless will work.  Do you guys know if there's such a guide on the Internet?  So far I've only read specific guides on a certain kind of wireless brand not a all covering guide, which gives the reader general common sense CLI commands to check things from 1 to 100.  And it seems that each brand have their own steps which confuses me a lot. :confused:

Also I have a working Wired NIC on my PC.  Can that be on when I want to test my USB wireless adapter?  If not how should I go about step by step please.

PS.
I'm reading this, but would probably need someone to help me out anyways.  I have a tendency to do everything wrong when following instructions.
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

---

### Post by peabody on 2007-10-02
You're forgetting to tell us the most relevant piece of information: the BRAND AND MAKE of the wireless adapter.

We can't promise to get you up and running after we have that information, but at the very least if someone has gotten that usb adapter to work before, they can probably chime in.

---

### Post by jingo811 on 2007-10-02
**brand:** ASUS WL-161

**specs: **
[LIST]
[*]802.11b
[*]USB 1.1
[*]Data rates: 11  ;  5.5  ;  2  ;  1  Mbps auto select
[*]WEP 64 / 128 bit
[*]RF output power: 15 dBm
[/LIST]

I can't find this in the list, I'm kind of hoping that nobody have this crappy Wireless stick and thus haven't properly tested it yet.
[http://linux-wless.passys.nl/query_hostif.php?hostif=USB](http://linux-wless.passys.nl/query_hostif.php?hostif=USB)




======================================================
======================================================




**My router:** Netgear FM114 P
[http://kbserver.netgear.com/kb_web_files/n101206.asp](http://kbserver.netgear.com/kb_web_files/n101206.asp)

**specs: **
[LIST]
[*]supporting Ethernet Standards 802.3 or 802.11b
[/LIST]

I don't think my router have any WPA support I can only find a WEP configure button in my router webpage.  And I have already upgraded to the latest firmware Version 1.5 Release 14.
[http://kbserver.netgear.com/products/FM114P.asp](http://kbserver.netgear.com/products/FM114P.asp)

---

### Post by jingo811 on 2007-10-02
I'm also thinking about buying this Wireless USB stick because it seems to be supported in the list.  Just in case Asus really doesn't work after doing the proper CLI procedures.
[http://www.webhallen.com/prod.php?id=43294](http://www.webhallen.com/prod.php?id=43294)

But it says 802.11g and WPA.  My router is old and only have 802.11b with WEP only will this not work you think?

Another site have some other info can someone confirm if this match will work for my router or not I'm confused :confused:
[http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oUop7hqltbNlwaaFp6DQoHDrpzyRC944ABd3h](http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oUop7hqltbNlwaaFp6DQoHDrpzyRC944ABd3h)

---

### Post by Lambert on 2007-10-02
> **jingo811 said:**
> I'm also thinking about buying this Wireless USB stick because it seems to be supported in the list.  Just in case Asus really doesn't work after doing the proper CLI procedures.
[http://www.webhallen.com/prod.php?id=43294](http://www.webhallen.com/prod.php?id=43294)

But it says 802.11g and WPA.  My router is old and only have 802.11b with WEP only will this not work you think?

Another site have some other info can someone confirm if this match will work for my router or not I'm confused :confused:
[http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oUop7hqltbNlwaaFp6DQoHDrpzyRC944ABd3h](http://www.dlink.co.uk/?go=gNTyP9CgrdFOIC4AStFCF834mptYKO9ZTdvhLPG3yV3oUop7hqltbNlwaaFp6DQoHDrpzyRC944ABd3h)

I'm not 100% positive but don't believe any router with just 802.11b will support wpa

Also a 802.11g card will not work with that router. Router has to support 802.11g. If you update to 802.11g (both usb device and router) you will get improved speeds plus improved security with wpa. You can find some decent routers fairly cheap.

if you want a place to start with a wealth of information, go to wiki.ubuntu.com and search wifidocs
A lot of reading there and good place to start.

---

### Post by jingo811 on 2007-10-02
Mmm I don't think that I'm going to buy a new router I'm saving up money for Starcraft 2 :)  
Besides I'm experimenting on an old Pentium 3 - 550 MHz PC with an outdated Debian kernel so I'm gonna try my luck with my crappy Asus and Ndiswrapper one more time.  I found it at number 60 all that's left is to read how to proceed with the Ndiswrapper method.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

---

### Post by peabody on 2007-10-02
> **Lambert said:**
> 
Also a 802.11g card will not work with that router. Router has to support 802.11g. If you update to 802.11g (both usb device and router) you will get improved speeds plus improved security with wpa. You can find some decent routers fairly cheap.


Correct me if I'm wrong, but I was under the impression that g hardware was backwards compatible to b hardware, so I'm pretty sure a g stick could be used to connect to a b only router.

a and n networks; now those are completely different.

---

### Post by Lambert on 2007-10-02
> **peabody said:**
> Correct me if I'm wrong, but I was under the impression that g hardware was backwards compatible to b hardware, so I'm pretty sure a g stick could be used to connect to a b only router.

a and n networks; now those are completely different.

You are correct, need to brush up I guess.:oops:

n 2002 and 2003, WLAN products supporting a newer standard called *802.11g* emerged on the market. 802.11g attempts to combine the best of both 802.11a and 802.11b. 802.11g supports bandwidth up to 54 Mbps, and it uses the 2.4 Ghz frequency for greater range. 802.11g is backwards compatible with 802.11b, meaning that 802.11g [access points]("http://compnetworking.about.com/cs/wireless/g/bldef_ap.htm") will work with 802.11b wireless [network adapters]("http://compnetworking.about.com/od/hardwarenetworkgear/g/bldef_adapter.htm") and vice versa.

---

### Post by jingo811 on 2007-10-05
I'm trying to follow the Ndis wrapper instructions from the included INSTALL file on My Debian system.  My Prerequisites doesn't seem to work.  Need help plz.

> Prerequisites 
=============

You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

**  ls /lib/modules/`uname -r`/build**

should have at least 'include' directory and '.config' file.





> mike@Firebats:~/Desktop/src$ **uname -r**
2.6.18-5-486
mike@Firebats:~/Desktop/src$ **ls /lib/modules/`uname -r`/build**
ls: /lib/modules/2.6.18-5-486/build: No such file or directory
mike@Firebats:~/Desktop/src$

---

### Post by jingo811 on 2007-10-06
bump1.
Anybody got any tips for solving this Ndiswrapper Prerequisites obstacle?

---

### Post by kevdog on 2007-10-06
sudo aptitude install linux-headers-`uname -r` build-essential

If you dont have an internet connection on the computer you will need the installation cd. Put it in the drive:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-headers-`uname -r` build-essential

---

### Post by Ituxlinux on 2007-10-06
Try this  [ [COLOR="DeepSkyBlue"]blog[/COLOR]]("http://i-eat-noobs.blogspot.com/") that worked for me.

---

### Post by jingo811 on 2007-10-06
If I install and test my Wireless USB on my working Internet machine with Wired NIC will that cause major conflicts?  Or should I only install and test Wireless on a PC that have no previous Internet setup and connection?

---

### Post by kevdog on 2007-10-06
It wont matter, go with the wired NIC -- this shouldnt cause any problems.

---

### Post by jingo811 on 2007-10-07
I'm sure the Ubuntu blog works flawlessly and I've already downloaded the suggested files into a catalog.  But I'm gonna use this as Plan B.

I want to learn and install my Ndiswrapper as Distro independent as possible besides I'm trying to make it work on my non connected Debian.  Anyways when I tried to install the headers I got a bunch of errors.  What should I do know?

> $ **cat error **
Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Reading task descriptions...
Building tag database...
Couldn't find any package whose name or description matched "linux-headers-&#65533;2.6.18-5-686"
Couldn't find package "build".  However, the following
packages contain "build" in their name:
  linux-kbuild-2.6 linux-kbuild linux-kbuild-2.6.18 build-essential 
Couldn't find package "essential".  However, the following
packages contain "essential" in their name:
  build-essential 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

**PS.**
I followed these steps before bumping into that error message!

> 
sudo aptitude install linux-headers-`uname -r` build-essential

If you dont have an internet connection on the computer you will need the installation cd. Put it in the drive:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-headers-`uname -r` build-essential

---

### Post by kevdog on 2007-10-07
What's your question, I dont understand??

---

### Post by jingo811 on 2007-10-07
The commands you gave me for building that header thingy didn't work.  I got the error message saying it doesn't recognize the file name or something.
Now I don't know how to proceed?

> $ cat error 
Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Reading task descriptions...
Building tag database...
**Couldn't find any package whose name or description matched "linux-headers-&#65533;2.6.18-5-686"**
Couldn't find package "build". However, the following
packages contain "build" in their name:
**linux-kbuild-2.6 linux-kbuild linux-kbuild-2.6.18 build-essential **
Couldn't find package "essential". However, the following
packages contain "essential" in their name:
**build-essential **
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by kevdog on 2007-10-07
Try this first -- tell me if this works:

sudo aptitude install build-essential


Then can you post your kernel version:
uname -r

---

### Post by jingo811 on 2007-10-08
I figured out what the problem was it was me the human factor again :oops: 
Instead of typing this like you suggested
```
sudo aptitude install linux-headers-`uname -[COLOR="Red"]r` b[/COLOR]uild-essential
```

I typed this without spacing
```
sudo aptitude install linux-headers-`uname -[COLOR="#ff0000"]r`b[/COLOR]uild-essential
```

Anyhow overcoming that first obstacle enabled me to play some ball.  And from the looks of things doing 
**$ ndiswrapper -l**
gives me an output of 
**driver present and hardware present**
So it seems like I've managed to get my USB Wireless to be recognized by Debian.

The only thing that's left is to make it connect to the router which I don't have any clues on at this time :confused:
I already managed to
**apt-get install wireless-tools**
But I don't know what to do with it?

---

### Post by kevdog on 2007-10-08
Ok 

lets make sure the ndiswrapper module is loaded

lsmod | grep ndiswrapper

If you haven't done this step, lets load the module at boot
echo ndiswrapper | sudo tee -a /etc/modules

Please post iwlist scan, let me know what network you want to connect to, and if it has any WEP/WPA

---

### Post by jingo811 on 2007-10-09
[IMG]http://i23.tinypic.com/zmi50.png[/IMG]

This is so cool my old 14" monitor from 1994, and my 1997 Pentium 3 - 550 MHz which got its Wired NIC fried some years ago.  Is connecting to the Internet for the very first time this is kind of historical.
It reminds me of R2D2, now I'll just wait some other 10 years for it to gain self-conciousness from SKYNET :)

Tnx for the 2 commands it enabled me to climb the last stretch on this Wifi mountain all by myself.
With no mouse might I add!  That's like climbing with only one arm.

All that's left now is to make things load by itself everytime I reboot so that I don't have to issue 
"$ dhclient wlan0" and stuff manually in order to make things work.

---

### Post by jediscout on 2007-10-09
I have a similar problem with my pretty much outdated Dell True Mobile 1400 WLAN internal 802.11b 
Although I have used the wi-fi with my Windows program, it shouldn't be that hard to get it running in the 6.1 Ubuntu could it?
I also have a Linksys 2.4 ghz g card I would like to install also; but since I got it from somebody else used I'm not sure it works.
Thanks for any suggestions any one can give.

---

### Post by jingo811 on 2007-10-09
Your Ubuntu Dapper 6.10 might not support Wireless as good as Ubuntu Feisty 7.04.  Try that for starters Feisty tend to handle most Wireless automatically but not all.

Also can you confirm from your Dell manuals if this information look familiar?

**Card:** Dell Truemobile 1400 minipci 802.11b
**Chipset:** Broadcom BCM4309

---

### Post by jingo811 on 2007-10-09
It says you're yellow.  But then again mine wasn't even listed :) so I had to do things the hard way. The Ndiswrapper method, hopefully you won't have to go through that hell.
[http://linux-wless.passys.nl/query_part.php?brandname=Dell](http://linux-wless.passys.nl/query_part.php?brandname=Dell)

Someone suggested this Ubuntu Wireless guide that seemed nice, I didn't follow it because I wanted to do it the hard way on my Debian system.
But seems like the blog will address your problems pretty well.
[http://i-eat-noobs.blogspot.com/](http://i-eat-noobs.blogspot.com/)

---

### Post by jediscout on 2007-10-09
> **jingo811 said:**
> 

Also can you confirm from your Dell manuals if this information look familiar?

**Card:** Dell Truemobile 1400 minipci 802.11b
**Chipset:** Broadcom BCM4309

The card sounds right, not for sure on the chipset model except I know it is a Broadcom. I'll have to check later.
I just checked and you're right on the money, which is listed as a/b/g version.

---

