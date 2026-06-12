---
title: "Netgear WG511"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by brittanie on 2010-08-26
Hey, Im very new to Ubuntu. I have a Netgear WG511 wireless card and cant get it to work. Any suggestions?

---

### Post by SpockVulcan on 2010-08-26
System> Administration> Hardware drivers 

Tell me if anything is listed there

---

### Post by brittanie on 2010-08-26
No proprietary drivers in use on this system.

---

### Post by plucky on 2010-08-26
Post output from a terminal of ```
lspci -v
```

and find your card [Here](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) to see if it will work out of the box or you have to use [Ndiswrapper](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page) and the windows driver.

Good Luck

---

### Post by brittanie on 2010-08-26
I discovered that I do indeed need to use ndiswrapper and downloaded the one they have in the software manager, Windows Wireless Drivers. The disc I got with the card never worked right so I downloaded the drivers. Once unzipped, I got a .exe and a .txt file. When I try to add a driver through ndiswrapper, it asks for a .inf file. Did I do something wrong?

---

### Post by brittanie on 2010-08-26
Okay. I found a suitable version of drivers with a .sys and .inf. I installed through ndiswrapper and my SSID shows up under available wireless networks. I enter my password and push connect and get no error. I connect to the network with a little lock icon beside my signal stregnth. The wireless icon in the top left bar just pulses like its looking for the network. Please help someone...Im tired of being hooked to this 4 foot cord!!

---

### Post by brittanie on 2010-08-26
So I got it figured out....for anyone that has the same problem as me, this is not the most preferred fix, but I downloaded the ndiswrapper from the ubuntu software center. I still couldnt connect after prompted for my password. Someone suggested I turn off the WPA/WP2 encryption, and that solved it. This may not work for all, but as I am in the middle of 15 acres at the top of a mountain, I dont think security will be an issue. Good luck...the IRC chat people were very helpful!

---

