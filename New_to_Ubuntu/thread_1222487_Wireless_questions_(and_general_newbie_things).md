---
title: "Wireless questions (and general newbie things)"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by admiralspark on 2009-07-24
Hello all!
After a grueling 8 hours of trying to install Ubuntu (9.04), I have finally succeeded (one of my ISO burners is junk, I learned at the end). I am running Ubuntu through the Wubi setup on a Compaq Presario that has served as my trusty and faithful servant for the past 4 years. I am a Windows XP fanatic of sorts, who is gaining interest in Linux as something new to use and attempt to master. 

Before I get started, the reason I'm using the Wubi setup is because I need to retain the functionality of Windows and didn't want to repartition the drive (and have to reinstall Windows and all of the junk I've collected for it). 93 gigs of my 100gb hdd is the windows partition ;-)

Another side note, my previous experience with linux is limited to Knoppix, so this is a step up from the Lite OS.

Anywho, the meat and potatoes: Everything is working great EXCEPT, of course, my Broadcom 802.11 g :(. As I type this, I am using the hardwired connection, but that's kind of a pain for me since I tend to move alot with the laptop. I have read through the guide "**HOW TO: Configure wireless cards with Broadcom chipsets", **and that would work great except I don't have Ndiswrapper installed. When I went to look for an installation guide, I found half a dozen different ways to install it and none of them in real layman's terms. As long as it's laid out step by step, I think I could handle it with no problem, but most of the guides use terminology and installed apps that I don't know/have/understand. If somebody could point me in the right direction?

---

### Post by esalnoj on 2009-07-25
Firstly, [HTML]http://sourceforge.net[/HTML] is your friend.

Go there, search ndiswrapper, and download the .tar.gz

Move the file to Desktop, then run the following in terminal (applications->accessories->terminal)

```
cd Desktop
tar zxvf ndiswrapper-1.55.tar.gz
```

Close terminal, then open the new folder on your desktop.
Follow the directions in "INSTALL" in terminal.

Be sure you copy the wireless card .inf file from your XP into ubuntu before starting.

Remember: cd is "change where I am in folder paths"

---

### Post by spcwingo on 2009-07-25
You could also install ndisgtk (gui for ndiswrapper) through synaptic while hard-wired.  ;)

---

### Post by admiralspark on 2009-07-26
Thank you both for the quick responses! I happen to be in XP at the moment, but I will jump over and try it now!

---

### Post by mapes12 on 2009-07-26
Have you tried fwcutter? It's searchable in synaptic. IMHO ndiswrapper should be a fix of last resort.

What adapter do you have - Go Applications>Accessories>Terminal and enter```
lspci
```Post the output back here.

---

### Post by admiralspark on 2009-07-26
Well, according to the SourceForge documentation, some updated drivers should work. Of course, when I went to install the windows driver, I got this after running "ndiswrapper -i bcmwl5a.inf":

> defaultuser@ubuntu:~$ cd Desktop
defaultuser@ubuntu:~/Desktop$ ndiswrapper -i bcmwl5a.inf
couldn't create /etc/ndiswrapper/bcmwl5a: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.

Both bcmwl5a.inf and bcmwl5.sys are on my desktop (the new, "working versions" and the originals installed under windows), as is Ndiswrapper. Am I missing a *.bin file? I have the windows .exe for the installation on the desktop, I'm going to try and install that through windows as it is just an update, maybe that will solve my problems.

By the way, I am running a Compaq Presario V5000 with the Broadcom Corp BCM4318 AirForce One 54g 802.11g Wireless LAN Controller (rev02) and using the following site for links: [URL="http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318"]http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Broadcom_BCM4318
[/URL]

---

### Post by Liolikas on 2009-07-26
sudo ndiswrapper -i bcmwl5a.inf

---

### Post by mapes12 on 2009-07-26
This may help you out:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by admiralspark on 2009-07-26
Well, here's my update:
The sudo command worked, of course. That file is installed in my system. However, I've had an interesting past few hours. 

I clicked on that last link, and went into my Hardware Drivers tab. On that, I at first found only one driver: "Software modem", the Smartlink modem daemon. I activated that and lo and behold, the wireless card light lit up when I restarted! So, I went about trying to set up the connection, but Ubuntu wouldn't recognise the card was running. So, I went back to that page. 

I realized then that I hadn't even been using the right driver as a new one had popped up: Broadcom B43 Wireless driver. So, I activated that...or attempted to. It will only show "this driver was just disabled, but is still in use". So there's dilemma #1. Of course, the light says off now no matter what combination of active/inactive I do with the two drivers. 

Clicking on the Network Connections tab up top, I get "device not managed" under Wireless Networks. 

I should also point out that I reversed the blacklisting of the b43 drivers and all as was called for in the Ndiswrapper instructions. 

I'm at a loss as to what to try next. Any ideas?

---

### Post by admiralspark on 2009-07-26
IT'S FIXED!
I'm so very happy, I managed to get it working when I followed this link: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

I'm psyched to finally have this going; it's the one major problem that I had with Knoppix before, and now I can begin to explore Ubuntu!

Once again, thanks to EVERYONE who helped me along the way, I couldn't have made it this far without the suggestions. 

-Admiralspark

---

