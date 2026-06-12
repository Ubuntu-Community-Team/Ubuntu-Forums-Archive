---
title: "Shouldn't finding a wireless network be easy?"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Nonnormalizable on 2007-09-20
Hi,

I've got a fresh Feisty Kubuntu install and a EDIMAX EW-7128G wireless router, which according to [this thread]("http://ubuntuforums.org/showthread.php?t=156075") works out of the box in Feisty. I can see it as ra1 in Network Settings. I would have expected a "here are all the wireless networks, pick one" type of screen but nothing like that seems to exist. Do I actually have to enter an ESSID number to connect to any network?! Zerconf Service Discovery is totally blank.

Okay, if that's the way to do it, I took the Base Station ID (00:1C:B3:AB:7D:61, is that the right form for a SSID?) from a dialog box on Mac that's connected to the same network and entered that along with the WEP key, to no avail. It complains about the Gateway IP address, but if I change that for ra1 under Routes to 10.0.1.1 (or any of the other numbers associated with the router I can find) it doesn't help at all. Also, bizarrely, I can't launch knetworkmanager from either the K menu or the command line.

Any help? I hope I'm just missing some easy fix!

---

### Post by SpiritIsReality on 2007-09-22
howdy

ya, what little I know, seems like the last kernel update kind of wrecked the knetworkmanager.
they talk about the ssid here
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
it will be set on your wireless page on your router. see manual or webpage for your router
hopefully your wireless card will work out of the box like they say.
I used to get the knetworkmanager but not now. not even with a sudo aptitude reinstall....
K>system settings>network settings
or right click on the mouse lookin icon in the panel, near the volume icon.
or it's command line yeehaa!

[http://kubuntuguide.org/Feisty](http://kubuntuguide.org/Feisty)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Networking&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Networking&titlesearch=Titles)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=WifiDocs&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=WifiDocs&titlesearch=Titles)
I've got ubuntu-desktop and kubuntu-desktop installed, and at login, can click on menu and
choose gnome or kde to start. then I can follow along on whatever guide I can find, gnome(ubuntu)
or kde(kubuntu). I'm thinkin' of installing them on separate partitions but until then, the k....are kde
the rest are generic or gnome. they get along pretty well now.
ya it should and probably will be easy/easier soon, till then , what's a body to do.
now if you're up to it, you could try reading thru some of  this
[http://aboutdebian.com/](http://aboutdebian.com/)
and there's 
[http://linuxcommand.org/](http://linuxcommand.org/)
if you can't find the .bash_profile, don't worry about it, just go with the .bashrc like I did.

trails

---

