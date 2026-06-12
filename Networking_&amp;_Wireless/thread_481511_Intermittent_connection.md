---
title: "Intermittent connection"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by CyberCod on 2007-06-22
I'm running Feisty on a decent machine, it has built-in ethernet and I'm using a Linksys USB wireless card.

The problem is that whenever I leave my machine alone for more than an hour or so, the network settings change.  Either the wireless will disable itself, or the eth0 connection will enable itself, or they'll both be enabled, or both disabled...  In any case, just about every time I sit down at my machine, I have to open up Network Settings to change it back to what it should be so that I can connect.

If anyone can tell me what is going on I'd appreciate it greatly.

---

### Post by CyberCod on 2007-06-22
C'mon, no responses?  I tried asking in the irc channel and got ignored there as well...

and I've tried looking around in previous posts, but I can't figure out a good way to phrase the problem!

---

### Post by dardack on 2007-06-23
I do not know if this will help you.  I don't know what wireless card you have.   I've had issues with my internet connection with Arethose AR 5005G and with WUSB 11 v 2.8.  Both i had to use ndiswrapper and use wicd instead of Network-manager.
If you decide you want to try this (could break your wireless completely)

First go to ndiswrapper ubuntu wiki page ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) and go to section 2.5, to see if your wireless card is supported by ndiswrapper.  
but don't blacklist or install anything just yet.  If it is supposrted, save that wiki to harddrive, open system -> administration -> Synaptic pakage manager (or whatever it is) and search for ndiswrapper, and install the 3 pakages (common, utils, ndisgtk).
Um before uninstalling network manager make sure you download the 1.2.9 testing wicd .deb from wicd.sourceforge.net  (also might want to save the wicd faq page to harddrive).

Than in synaptic search for network-manager uninstall it.  

Than run the wicd .deb file.  Than follow the ndiswrapper instruction, for blacklisting, will have to reboot after blacklist i think.  Anyways, this worked for both my conenction drops, intermittent connections, low signal stregnth, etc.

---

