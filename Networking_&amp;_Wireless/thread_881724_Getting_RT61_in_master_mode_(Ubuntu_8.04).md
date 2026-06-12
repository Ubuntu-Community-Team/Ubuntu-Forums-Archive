---
title: "Getting RT61 in master mode? (Ubuntu 8.04)"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Dacobi on 2008-08-06
Hello All

I'm trying to set up an access point using my RT61 based wifi PCI card.
The problem is that when I run "sudo iwconfig wlan0 mode master"
I get this error:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

From what I've read the RT61 should support master mode??

I tried compiling the driver from ralinks site but it failed horribly...

I'm using the default drivers in Ubuntu 8.04, mac80211 and rt61pci and such.

Is it even possible to run this card in master mode??

/Dacobi

---

### Post by Dacobi on 2008-08-06
*bump*

Anyone?

Is master mode possible for the Ralink RT61 Chipset?

---

### Post by alfredska on 2008-11-13
I would like to bump this once more to see if anyone has succeeded in getting the RT61 into master mode?  (and how?!)

---

### Post by razius on 2009-01-07
bump?

---

### Post by n4p1 on 2009-08-24
Its possible I think...
I removed this mpci card from edimax br-6215SRg router/access point and successfully using it in my IBM laptop as a client wifi. But i never try it as a master.

---

### Post by PF-Flyer on 2009-08-26
I'm also interested in getting a wireless PCI card to work. It's a Linksys WPS54Gv4.1, which has a Ralink RT61 chip.
 
SourceForge has RaOdar, which it describes as 
"...a wireless network scanner and graphical configuration utility to easily setup Ralink RT61 based cards."
[http://sourceforge.net/projects/ra0dar/](http://sourceforge.net/projects/ra0dar/)
But I'm a total Linux newbie, and don't know how to install it, :confused: let alone whether the 2006 program would still work with a Ubuntu Studio 8.04.1 Hardy. 
 
I'm used to the plug-and-play experience of Windows, which asks for a disk, or for permission to search the internet for a driver, when new hardware is installed. :redface:
 
I have downloaded the RaLink RT61 driver file, which includes many other files; since the linux machine does not have internet yet through its wireless card (which is not yet working), I downloaded the driver to a USB flash drive, which Ubuntu recognized; 
but none of the files seemed to be programs one could click to install the driver. So from what I've read, it seem you have to go into terminal mode, which sounds like dying in a hospital ER...:frown:
 
The document at the following link claims that the RT61 should work with Ubuntu 8.10:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)
But I installed the more stable Ubuntu Studio 8.04.1, instead of the newer version. I may have to switch. We have done nothing with Ubuntu Studio yet, so it would be no great loss to burn a new install DVD and reinstall 9.1.
 
The following SourceForge web page regarding ndiswrapper claims :o that one should not use ndiswrapper with the RT61 chip, but instead, use the RaLink driver:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WMP54Gv4.1](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WMP54Gv4.1)
It says, 
"Driver: Don't use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink [http://www.ralinktech.com]("http://www.ralinktech.com/") . It compiles for 2.4 and 2.6 kernels." 
But I don't know if this text on the ndiswrapper wiki at SourceForge is outdated; the driver at RaLink has a date of January, 2009. (good argument for dating the wiki entries at SourceForge).
 
Here's the RaLink linux driver page, which lists the driver about half-way down, but the "RT61" is not at the start of the title; it's in parenthesis in the middle of the title:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) 
Here's what it looks like:
RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661) 01/23/2009 1.1.2.3 Doc 
with (RT61 as the first thing inside the parentheses ().
 
Another site lists success installing the same wireless card after what seems a lengthy process:
[http://ubuntuforums.org/showthread.php?t=245558](http://ubuntuforums.org/showthread.php?t=245558)
but it's a 2006 post, and I'd assume that if Ubuntu 8.1 or Ubuntu Studio 9.1 might be compatible (tho' less stable in the case of US9.1?), I'm not sure why a newbie like me would want to go to the trouble of compiling and editing a driver, or tweaking NDISWrapper. I'm taking the Ubuntu Studio plunge because my son and I wanted to do digital recording, :guitar: not because I wanted to become an amateur programer.
 
If any of these links are helpful regarding Ubuntu 8.04 and RT61 in master mode, great. But from all my reading and Googling on the topic, if it seems it will work right away with 8.1 or Ubuntu Studio 9.1, I will probably install the latest version. #-o

---

### Post by xTkAx on 2009-08-26
I'd like to know if there is a howto or a guide to get this working too.  I have the RaLink RT2561/RT61 wireless card and was hoping to use it as a replacement for a router.  

```
sudo iwconfig wlan0 mode master
```gives me:

```

Error for wireless request "Set Mode" (8B06) :
     SET failed on device wlan0 ; Invalid argument.

```I plan on finding a different card (one supported by madwifi) because after searching for a few days, it seems fairly complicated to get this card set up on ubuntu 9.04 in master mode.  But im hearing its possible, so if anyone can point us to a guide or a how to, that would be great.. tia!

:)

---

### Post by PF-Flyer on 2009-08-26
xTkAx: So you're trying to get it to work on ubuntu 9.04 and having trouble?  This is discouraging.  
 
As I write this, I'm upgrading from Ubuntu Studio 8.04 to 9.04, and am doing this because of some research (see my prev. message) that indicated Ubuntu 8.1 and later contained support for the RT61.  Those claims may be in error. 
 
Or perhaps I am not understanding the full meaning of "master mode."  Are you saying you can get the card to work, but that it does not work in master mode, or that it won't work at all?  Please enlighten me, as I'm a newbie and would appreciate any explanations that may help in my education. 
 
We may both be looking for new wireless cards that are compatible.

---

### Post by xTkAx on 2009-08-26
PF-Flyer: i have a pci card, and with the 9.04 install, it seems to work fine, that is, aside from putting the card into master mode.

I never tried to connect to my network with the card so i can't say, my main reason for installing the card was to use my ubuntu machine as a router.  However, i did manage to set up an ad-hoc network in ubuntu with this card quite easily.  It was just a matter of clicking on the network manager and going to "create new wireless network".  the problem is though that ad-hoc is computer to computer, and i am looking to have multiple computers use this machine, with the said wireless card,  as an access point/gateway to the internet.  

So i need to find a way to make the card work in 'master mode' so that i can run the wi-fi card in infrastructure mode.  And therein lies my problem...

---

### Post by PF-Flyer on 2009-08-27
If I can't get the Wireless card to access my wireless DSL modem/router, I may also look into adding an ethernet (wired) router to my existing modem-router, and giving up on going wireless with Ubuntu Studio
-- if the costs for a wired router are lower than the costs for a wireless router I'm SURE would work are higher
-- or if there's no such thing as certainty about wireless network cards with Ubuntu 9.04.

---

### Post by Sylslay on 2009-10-16
Linksys card with rt61 / RaLink RT2600 802.11 MIMO

worked on some other livecd in any mode,,
testeted

modinfo rt61pci give me in karmic that list"

0/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     801A037A3E53BB7E7E9C627
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
:guitar:

---

