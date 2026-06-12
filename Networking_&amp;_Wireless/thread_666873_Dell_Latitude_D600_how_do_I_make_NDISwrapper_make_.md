---
title: "Dell Latitude D600 how do I make NDISwrapper make my wireless work"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by Sandman1278 on 2008-01-13
I have been looking around a whole bunch of stuff and got the point were I know I need NDIS wrapper installed, I did that but it didn't do anything, I still cannot find any networks, what am I supposed to do? my home network is set up as a WPA personal if that makes any difference, and I'm running KDE 7.1

---

### Post by Perpetual on 2008-01-13
I have a Dell D600 with an Intel Pro Wireless 2200 card and it works out of the box with both Ubuntu and Kubuntu,  What wireless card came with your D600?

---

### Post by Matt Yun on 2008-01-13
I also use a D600 with the ipw2100 module, and connect to WPA wireless networks with no problem.  Gutsy automagically configured everything right from the LiveCD, except for requesting the WPA password.  No need for ndiswrapper here.

---

### Post by figgles on 2008-01-13
What is your wireless card; Is it 802.11g? Does lspci see your card. I prefer NDISwrapper over the madwifi driver but that's not likely the rub here. Have you looked at [http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html) they list 7 different installation experiences -- with SUSE and Fedora, unfortunately, but you can still get a heads-up on issues there.

---

### Post by Sandman1278 on 2008-02-06
i downloaded ndiswrapper but idk what im supposed to do to make anything work, i downlaoded something called KWiFiManager which says my interface eth1 is not connected,  i checked linux-on-laptops nothign there can help me KNetworkManager says I have no active device, even when connected to LAN.  If i go to system settings and then click on Network Settings Eth0 will be connected fine, but eth1 my wireless comes up as disabled, When I go to enable interface, it stays a screen saying enabling inteface for a while, then for a split second it will go to an enabled state then back to being disabled.  I am a total newb to linux, please help

---

### Post by Sandman1278 on 2008-02-12
any ideas?

---

### Post by einnar on 2008-02-22
Try this thread. 
It worked for me.

[URL="http://ubuntuforums.org/showthread.php?t=297092"]
http://ubuntuforums.org/showthread.php?t=297092[/URL]

---

