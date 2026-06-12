---
title: "wireless wpa roaming and Dapper"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by pikaia on 2008-10-26
Hey.

I just installed Dapper on an old Thinkpad.  I've been using Ubuntu since Feisty and am happy with it.  But this is my first foray into Dapper.  It runs very very well on this old 500Mhz cpu, but the network manager is giving me troubles.  I can connect to my neighbors unsecure WEP network, but I can't get it to use WPA or utilize the wireless roaming feature I'm used to in later versions.  

I've also tried wicd.  It installs but I can't get it to start I go to Internet->Wicd manager and nothing.  I enter wicd-client into terminal and I get a message about the wicd.wpath error.  I've uninstalled and reinstalled several times to no avail.  

Is there something I'm missing?  My home network is WPA encrypted and I'd like to use it instead of the neighbors, so any help would be great.  Plus this is going to be a Christmas gift for my uncle. 

THanks.

---

### Post by pikaia on 2008-10-26
To clarify a bit.  I've been using Ubuntu since Feisty, but this is my first foray into Dapper.  I'd like the network manager (either network-manager-gnome or wicd) to display the available wireless networks with a click on the panel applet or even in the System->Admin->Network, as well as have full functionality with WPA networks, since my home network is WPA.  I have an atheros card that works fine and is noticed by the OS, but the manager does NOT let me connect to my WPA network.  The Network manager doesn't give an option for WPA, only WEP key (ascii and hexidecimal) even after update and upgrade.  

wicd installs but it won't load the gui to give me access to my networks.

wicd in terminal gives the error that it can't find module wpath.py.  I've I've tried accessing this file through terminal, but it doesn't exist and I don't see anywhere to download it.

Any help would really be appreciated.  I just want full functionality out of my Dapper install.  I need to stick with Dapper because this is an old laptop and the later versions are just too bloated for 500mhz and 288RAM.

Thanks again.

---

### Post by pikaia on 2008-10-26
Ok, I figured it out using the instructions from this site.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Thanks anyway, hopefully this'll help others.

---

