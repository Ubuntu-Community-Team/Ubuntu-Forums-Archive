---
title: "Linux Wireless has me pulling my hair out"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by PeterDenStore on 2007-06-09
Hello All,

First of all I'm new to Linux. My experience thus far has been very unpleasant. I got started with Linux when I heard about this Ubuntu Studio. Which I installed it on my desktop, with no problems at all. I really liked the look and feel of it. But in the end it was removed from the desktop because I found the video editing lacking at best and had no other use for Linux on my desktop.

But thought for surfing the net and reading email Ubuntu would be great. So I decided to install it on my old T30 IBM Thinkpad Running a mpci MSI MP54G5 (Ralink RT61). Which is all I ever do on my laptop. 

Well First I installed 7.04 It saw my wirless network but if I tried to connect with the wireless card the whole system would lock up! After trying the Ralink drivers(which I couldn't get to install) and few other things I have found on this forum and still didn't have the wireless working(I at least got to where it wouldn't lock up). 

So I switched to PCLinuxOS 2007 which didn't work out of the box either but I installed the Ralink drivers(which seem to install real easy unlike Ubuntu) and the wireless was working till I rebooted. Then after trying to install the drivers again I couldn't get PCLinuxOS 2007 to boot anymore. 

So Then I switched to Ubuntu 6.06 after reading on the forums that it would probably be easier to get my wireless working then in 7.04. Well 6.06 is by far the most frustrating one yet.  I can't even get online with my etho now! I can ping sites but can't surf the web! 

If I try to activate the wireless with the System>administrator>Networking.  I get a graph bar like it's doing something but that just sits up there forever and never activates the wireless card. 

I downloaded the ralink drivers(on my desktop then put them on a thumb drive) but yet once again can't get those to install on ubuntu. Plus with not being able to get online with my etho there is no real easy way to try and download drivers and apps to make it work. 

So Like I said my experience thus far has been very unpleasant. I would really like to run Ubuntu on my laptop but I think I have been defeated and have to suffer in Window. 

Thanks,
Peter

---

### Post by Newbie29 on 2007-06-09
Hi,

Lol, what coincidence, I was in the same position you were about a month or 2 back, but then my exams were coming quick, so I dropped trying to get my wireless card a D-Link G630 E1 and installed XP on it again, anyway, I got tired of running XP on this old laptop cause it lagged a lot (I mean, it has a pentium 500 MHz processor, and a 6 GB hard disk...yes people I know its antique... ;)   ). Anyhow, a couple of days back my exams got over, and installed Xubuntu on the laptop again, and thanks to God I got the Wireless card to work.

The reason that your wireless card isn't working is that there is no driver for it on your computer which can run in Linux, and the drivers which come in the CD with the wireless card is for Windows and can't run on Linux, however since its a rt61 Wireless card (like mine.. :) ) life is easier for you since there is Linux driver available for your card here:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

On this site go to the downloads page, and then download the appropriate file pertaining to your particular driver (a rt61 in this case), then unzip the package on your computer, open the unzipped package, go to Module, and follow the instructions given in the README. And thats it....  ENJOY...;) Oh and whatever you do, don't go back to Windows :D  .

---

### Post by PeterDenStore on 2007-06-09
Hey

I tried the SerialMonkey drivers in 7.04 with no luck. I used the Synaptic manager to install. Well this time I can do that because I can get online at all :(...So when I download them from the website and read the readme  I get to the point where you do the make command I get the following error bash: make: command not found. I am CD to the the Mudule directory and everything.  So call me dumb but I can get the drivers installed still! :(

Thanks,
Peter

---

