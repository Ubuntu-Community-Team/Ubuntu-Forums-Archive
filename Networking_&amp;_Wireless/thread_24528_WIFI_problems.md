---
title: "WIFI problems"
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by Yessongs on 2005-04-07
I have an Averatec 5500 laptop with 5.04 installed. It picked up my onboard ethernet and listed it as eth0, but my built in wireless does not show up under the network settings. I do have another connection called lo, which is connected, but not getting a signal. How do I get it to work properly? I also have a Microsoft PC wireless card I use as well, it is an MN520 Orinco based card. How do I get it to work?

---

### Post by dataw0lf on 2005-04-07
The 'lo' in ifconfig is your loopback.  It basically allows you to connect to your own computer.  
As far as wireless, check out these links to the Ubuntu Wiki: [Wireless HOWTO](http://www.ubuntulinux.org/wiki/WiFiHowto) and [Supported Wireless Cards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards) .
Announcement: Google is your friend.

---

### Post by Glanz on 2005-04-07
Maybe what it picked up is your onboard network card.Try eth1 via ifup to see what happens.

---

