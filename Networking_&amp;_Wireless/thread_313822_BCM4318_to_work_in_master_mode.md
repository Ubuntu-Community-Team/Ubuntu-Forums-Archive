---
title: "BCM4318 to work in master mode"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by Archfiend on 2006-12-06
Hi all.

I installed xubuntu on a old pc celeron just 2 days ago.
I'm tryng to install, configure a wireless card to work in master mode, to serve as an Home Acess Point for some laptops.

The wireless card is Asus Wl-138g v2 
[BCM4318 driver in the windows cd bcmwl5.inf and .sys]

First thigs first.
When I connected the card and started ubuntu, the light was on, so he detected the card righ away. but since I wanted to have an AP, I tryed to follow this article:

[http://www.linux.com/print.pl?sid=06/07/10/1729226](http://www.linux.com/print.pl?sid=06/07/10/1729226)

So I runed this command:

wconfig eth1 mode Master (eth1 was my wireless card interface)

and to check the result I run this one:
iwconfig eth1
which return the Mode:Master


The thing is, that when I tryed to run this command:
ifconfig eth1 0.0.0.0 up
it returned:
0.0.0.0:Host name lookup failure

Now, maybe I could resolve this error with this:

[http://www.linuxquestions.org/questions/showthread.php?t=28487](http://www.linuxquestions.org/questions/showthread.php?t=28487)

But, since I am a newby in linux, I just searchd the internet and did the usual thing with ndiswrapper.

But now, having the same light on, when I try to turn the mode to master I get this error:
Set failed on devide wlan0: invalid argument (now the card is wlan0)

I can change to other modes, but not to master mode with the ndiswrapper.


I tryed to unnistal ndiswrapper with the synaptics, but after desinstallation, the xubuntu doesnt detect my wireless card again as it did in the begining.

What I ask is:
1 - is there any way of getting my system to is default state before ndiswrapper was installed, so that the system detects again the driver and I can change the mode to master?

2 - Or, just help me from scratch to have the wireless card installed as an AP, since it can work as an AP in windows. (at least thats what it says in the manual)


Thanks for any help you can give me

---

### Post by FrodoB on 2006-12-06
In ndiswrapper Master mode is not available, because it is not available in the NDIS driver from Windows. See the ndiswrapper FAQ:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Is_master_mode_supported.3F](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#Is_master_mode_supported.3F)

---

### Post by Archfiend on 2006-12-06
I see. Since so, what can I do to have my system detecting the wireless card and beying able to switch it to master mode?

---

### Post by FrodoB on 2006-12-06
If you want to make a Linux Wireless Access Point you are pretty much limited to some specific wireless chipsets. 

I have never done this, but I do know that the popular devices are:

prism2 - Hostap - 802.11b 

Atheros - mAdWiFi - 802.11g

Here is a link to a Hostap implementation:

[http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html](http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html)

You can never be when manufacturers will change chipsets so you have to be careful.

I have some links on the Atheros devices in this post:

[http://ubuntuforums.org/showthread.php?t=313564](http://ubuntuforums.org/showthread.php?t=313564)

If you want prism data then I could find that as well perhaps. Though for new applications you likely want Atheros.  Check out the mAdWiFi site for details:

[http://madwifi.org/](http://madwifi.org/)

---

### Post by Archfiend on 2006-12-06
Ok, so I'll have to test eatch of the mencioned drivers for my card, is that it?

---

### Post by FrodoB on 2006-12-06
No you will have to get a new card, but do the research and determine which one gives you the features that you require. 

Compile the drivers and make sure you understand those before obtaining hardware.

---

### Post by Archfiend on 2006-12-06
ok then, Ill check!!
Thanks for t
all the help :)

---

### Post by FrodoB on 2006-12-06
I think that most of the DWL-520 PCI cards are prism2 based. I have ordered one off of Ebay and when it comes in I will reply to this thread with the results. Revisions A1,A2,B1,B2 are prism, we shall see what I get.

Are you looking for PC Card(PCMCIA) or PCI devices?

---

### Post by trubblemaker on 2006-12-06
you know the native driver actually may be able to handle that as the original code base that was leaked was a router, and that has been how we got the bcm43xx driver,  Check my sig for a howto to set it up

|     so you know I haven't used it to setup a master network
|     but the native driver has a lot of functionality that ndiswrapper 
|     doesn't
V

---

### Post by FrodoB on 2006-12-06
You are right as the WRT54G projects will not work without it. Here is someone who has done it for embedded in a Linksys router as we knew they would have to:

[http://forum.openwrt.org/viewtopic.php?id=5585](http://forum.openwrt.org/viewtopic.php?id=5585)

To find out if it can be done on x86 Linux see:

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

See what the documentation says.

Also:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

---

### Post by FrodoB on 2006-12-07
Also see these instructions for building a Linux Access Point:

[http://www.linux.com/print.pl?sid=06/07/10/1729226](http://www.linux.com/print.pl?sid=06/07/10/1729226)

---

### Post by Archfiend on 2006-12-08
Thanks to everyone!!!

The truth is I bought another card:

Gigabyte AircruiserG GN-WP01GS with RaLink RT2561/RT61 802.11g PCI.

Only detected by xubuntu after I upgraded it to the 6.10 version.

I'll post another thread to get help with it

---

### Post by trubblemaker on 2006-12-08
check the wiki there is an awesome howto on it, but I don't know the page (re: ralink)

---

### Post by Archfiend on 2006-12-08
my new (some hours ago but still no awnser :() thread is:
[http://ubuntuforums.org/showthread.php?t=314974](http://ubuntuforums.org/showthread.php?t=314974)

Any help whould be apreciated!!!

---

