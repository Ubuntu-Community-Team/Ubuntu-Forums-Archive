---
title: "Wireless support query"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by ahaslam on 2007-01-24
Hi, I've never used wireless but I'm giving my laptop to my mother & she wont want wires. I intend to give her a fresh install of Dapper as it offers simplicity & stability. My query regards the support of wireless devices, which I've heard isn't great. Basically, I have my eye on a particular piece of kit & wonder whether it'll work ok & how I'll have to go about setting it up?

Here's what I have in mind: [http://www.misco.co.uk/applications/searchtools/item-Details.asp?EdpNo=114742&affiliate=2019](http://www.misco.co.uk/applications/searchtools/item-Details.asp?EdpNo=114742&affiliate=2019)

Any advice would be greatly appreciated ;)

Tony.

---

### Post by Shatrat on 2007-01-24
I can't see where it lists the model of the actual pcmcia card.
Here is a list of cards from linksys with ratings on how well they work.
Hope this helps.
[http://www.linuxquestions.org/hcl/showcat.php?cat=144&stype=1&si=pcmcia&perpage=30&sort=1&stype=&limit=&cat=144&ppuser=](http://www.linuxquestions.org/hcl/showcat.php?cat=144&stype=1&si=pcmcia&perpage=30&sort=1&stype=&limit=&cat=144&ppuser=)

---

### Post by elst on 2007-01-24
It looks like it use a Web-based interface - the page says "Configuration is a snap with any web browser". This is a fairly standard approach. You switch on the router, plug a machine into one of the wired network ports, and point the browser on the system to the IP address in the documentation (it's usually 192.168.0.1). You then get a Web page that lets you configure the router settings, including wireless. Settings are stored on Flash ROM, so that they are kept between boots. To save hassle, it's worth configuring routers with the right settings in advance, then switching it off and take them to whereever they will live.

EDIT: I would probably just chuck the PC wireless adapter in a spares box, and get something with better Linux support.

---

### Post by ahaslam on 2007-01-24
> **Shatrat said:**
> I can't see where it lists the model of the actual pcmcia card.
Here is a list of cards from linksys with ratings on how well they work.
Hope this helps.
[http://www.linuxquestions.org/hcl/showcat.php?cat=144&stype=1&si=pcmcia&perpage=30&sort=1&stype=&limit=&cat=144&ppuser=](http://www.linuxquestions.org/hcl/showcat.php?cat=144&stype=1&si=pcmcia&perpage=30&sort=1&stype=&limit=&cat=144&ppuser=)
Thanks, it appears to be a WPC54G-V7. So looking at your list should work with a little effort :rolleyes:

[QUOTE=elst]I would probably just chuck the PC wireless adapter in a spares box, and get something with better Linux support.[/QUOTE]
What's your reason for this & what would you suggest as a replacement (as I'm giving the laptop away, I don't want to spend too much on wireless)? 

Tony ;)

---

### Post by elst on 2007-01-24
My main concern would be having an update like a new kernel hose ndiswrapper etc. at some future point, and effectively kill Internet access until you can get there and spend time coaxing the system into working again. I've given away computers before, and then had to act as tech support...

Unfortunately, wireless card vendors change chipsets, sometimes without even changing the model name of the card, so the situation isn't stable. The one brand name I always recommend for networking is Intel - you pay more, but you save yourself time and frustration.

---

### Post by spd106 on 2007-01-24
Basically you would have to get lucky with the cardbus's chipset. Ralink and Atmel cards have free drivers so should be what you aim for, except that some people have had a lot of trouble with them (just search for posts in this forum) and they can be very difficult to find. The next best are Intel cards, but they only come built in to new laptops. Then there's Atheros based cards, which have out of the box support through madwifi. They generally work well, but madwifi is still a work in progress (it has the odd peculiarities).

By far the most likely is a Broadcom based card, at times it's like half the posts on whole of ubuntuforums.org are about Broadcom wifi cards. Check out ndiswrapper and bcm43xx. Try to avoid these cards as much as you can. As you are looking at buying a bundle there's no way you can easily check which card you will be buying. Sometimes the version and rev number can mean a very different card. Have a look at this page though it is getting a bit old [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by ahaslam on 2007-01-24
Thanks for the advise :)

PS. Your link shows  the WPC54G v7.1 to work otb in Dapper (along with older versions with different chipsets), I think I'll take a chance on it  ;)

---

### Post by jml on 2007-01-24
Let me put my two cents worth in as well.  In my opinion the Linksys base station WRT54G is a very Linux friendly Wireless base station.  Setup is via web browser access.  It supports multiple types of encryption and if you need a stronger signal (thick walls, long distances,) you can buy high gain antennas to boost the output. I have used them and they do improve signal strength.  Having said that, I have never been able to get a Linksys PCMCIA card working in Linux.

For wireless cards I have had consistantly good luck with the Cisco Aironet 802.11a/b/g card.  A bit pricy but it has a powerful tranmitter and it has Linux drivers available which are supplied by the manufacturer.  A less expensive choice is the NetGear WG511T card.  Both of these cards are based on the Atheros chip set and have consistantly worked with Ubuntu and other Linux distros.  

I would stay away from any system claiming to be 802.11n compatible.  That is the new wireless standard that promises to increase data transfer rates.  The problem is that the 802.11n specification is only a draft specification.  Its not scheduled to be ratified for about a year.  So any hardware you buy now, may or may not work in the future.  Its also so new, that native Linux support is virtually non-existant.  So buyer beware.

Joe

---

### Post by ahaslam on 2007-01-27
It arrived today.

The good news is that I found it cheaper on ebay & the PCMCIA card is detected.

The bad news is that I have been sent a used, faulty & damaged modem/router which does not work.

I can't believe what some people try & sell as new :twisted:

---

### Post by ahaslam on 2007-01-31
Getting a free wireless router from my ISP now & don't have to alter my contract :)
The PCMCIA card is going back with the router for a refund, so I'll have to purchase another. 
Anyone got any experience with the following cards?

[BELKIN F5D7010]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=141078")
[Netgear WAG511]("http://www.netgear.co.uk/wireless_network_card_wag511.php")

Cheers ;)

---

### Post by spd106 on 2007-01-31
I've got a F5D7010 v1 (Broadcom) it works okay, but it's not fantastic. You probably can't get them anymore so you'll end up with a newer version. Pot luck whether it works well or not.

You've probably been directed there before and I can't say I've bought anything from them, but you could try the linux emporium [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

---

### Post by jml on 2007-01-31
I have not tried this specific Belkin card, but I have tried two other similar models and was not able to get them to work properly.

As for the NetGear, as I mentioned in a previous post, the WG511T is based on the Atheros chip set and is recognized out ofthe box by Ubuntu.  That plus the pair of applications network-manager, and network-manager-gnome work very well with that card.

The card you list has a model number similar to the 511T, but there is no way to know if it uses the same chip set.  Is it possible to contact the vendor selling the card and ask?  According to the mad-wifi web site, 

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

the WAG511 card is supported.  I have never used the madwifi drivers but I'm sure others have.   Hope this helps.

Joe

---

### Post by ahaslam on 2007-01-31
Thanks guys, it really does seem "pot luck whether it works well or not" with the constant chipset changes. Why can't they just design something & then leave it alone?

Cheers ;)

---

### Post by ahaslam on 2007-02-01
As my router never worked, I only plugged in the PCMCIA card to see if it powered on & showed up in dmesg. Before packing back up for a refund I had a little play & came up with this:
[ATTACH]24303[/ATTACH]
Looks like my neighbors devices, as the card seems to work well, I'll look for an identical replacement ;)
[B]
After seeing my neighbors routers, will they see mine in the same way, or can it be hidden? I'm sure they have encrypted connections, as would I, but I don't like the idea of advertising something so blatantly. [/B]

Thanks again ;)

---

### Post by spd106 on 2007-02-01
Yes, you can turn off the ssid broadcast in most wireless access points configuration. Unfortunately this can cause problems when you try to connect. Network Manager currently has trouble since it can't detect what kind of encryption to use (tkip or aes/ccmp).

There's also the argument that [security through obscurity]("http://en.wikipedia.org/wiki/Security_through_obscurity") won't stop anyone determined enough to find a flaw.

---

### Post by ahaslam on 2007-02-01
My concern is that anyone with a little curiosity & patience can easily break common wireless encryption methods. There's even Gentoo-esque how-to using open source app's here: [http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks) When I get both my card & router I'll no doubt try it out on my own network, to see just how easy it is or isn't. 

I'm in no doubt that if someone really wanted to access my connection, they could & would. But why spark the curiosity of those that just want to play?* "What else are you gonna do next Friday night? Play Counter Strike?"*

I was intending on going through this once I get my stuff: [http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

Tony.

PS. The home hub arrived today & it offers oodles of security options. Just waiting for my card to arrive now :rolleyes:

---

### Post by ahaslam on 2007-02-03
Got the card today & it's all working perfectly :)

I've changed the admin password, disabled SSID broadcasting & enabled MAC address filtering. The only thing left to do is switch from WEP to WPA. As WEP is the only encryption offered in 'Network Settings' & 'Network Manager' doesn't support Atheros cards, I'll have to get a coffee & read up ;)

Tony :)

---

### Post by ahaslam on 2007-02-04
Wasted half the afternoon yesterday reading wiki's & ho-to's only to get it working for a few seconds. 

I now have WPA working perfectly in Zenwalk (where the card was not recognized otb), all I had to do was compile madwifi & add 2 lines to rc.local. 

I tried the same thing in Dapper & it wouldn't work at all, it seems to be the version of wpa_supplicant in Dapper that is not fully compatible with certain Atheros cards. So I thought I'd compile the newer version, only to be met with a huge list of errors. 

Tony.

---

### Post by Fitzcarraldo on 2007-02-25
Anthony, have you had any progress since your last post above?

I was thnking of buying a Linksys WPC54g (v7.1) Wireless 802.11g PC Card PCMCIA for use with my Gateway Solo 9300 notebook PC and Dapper Drake 6.6 LTS. Did you manage to get your Linksys card working with Dapper and WPA-PSK? If yes, what did you hve to do in the end to get it working? Thanks in advance for your reply.

---

### Post by ahaslam on 2007-02-25
Yes, just use wpa_supplicant & add to rc.local, don't do anything in the GUI, it will interfere.

;)

---

### Post by Fitzcarraldo on 2007-03-06
I got the Linksys WPC54G v7.1 card working with Dapper Drake 6.06 LTS and my home WPA-PSK network quite easily in the end, using Network Manager and wpasupplicant. The steps I took are explained in details in the following thread:

[http://www.ubuntuforums.org/showthread.php?p=2258765#post2258765](http://www.ubuntuforums.org/showthread.php?p=2258765#post2258765)

---

### Post by ahaslam on 2007-03-07
Nice to see that you got it working your way, though it looks over complicated when it's only wpa_supplicant that's needed. Hats off to you though I gave up with the GUI, I believe GUIs are only of use if they make things easier...

;)

---

### Post by Fitzcarraldo on 2007-03-07
It was actually very straightforward. My above-mentioned thread is very verbose as I was trying to make the process easier for newcomers to ubuntu/Linux (like me) to follow but, actually, if Network Manager and wpasupplicant are already installed (which they were by default on my PC) the method boils down to five straightforward steps:

1. sudo gedit /etc/network/interfaces
and comment out everything other than "lo" entries in that file and save the file.

2. Use gedit to create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file.

3. sudo touch /etc/default/wpasupplicant

4. Reboot PC.

5. Enter wireless network's SSID, Type and Password and click Connect.

It was as simple as that.


If Network Manager and wpasupplicant had not already been installed, one would just need to perform three more steps before the above to install them:

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

(or instead use the GUI Synaptic Package Manager or Automatix2 to install Network Manager, which does all the above).

---

### Post by Fitzcarraldo on 2007-03-07
> **spd106 said:**
> Yes, you can turn off the ssid broadcast in most wireless access points configuration. Unfortunately this can cause problems when you try to connect. Network Manager currently has trouble since it can't detect what kind of encryption to use (tkip or aes/ccmp).

There's also the argument that [security through obscurity]("http://en.wikipedia.org/wiki/Security_through_obscurity") won't stop anyone determined enough to find a flaw.

I have turned off the broadcast of the SSID by my hub, and am using WPA-PSK ("WPA Personal") with TKIP. Network Manager has no problem at all detecting and working with the network.

---

