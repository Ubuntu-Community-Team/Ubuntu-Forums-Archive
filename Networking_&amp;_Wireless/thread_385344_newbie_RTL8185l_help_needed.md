---
title: "newbie RTL8185l help needed"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by papajack on 2007-03-15
I have been trying for three weeks to get my wifi card to work. I have tried ndiswrapper with the bcmwl5 driver, the driver from the cd both XP and 98. I have also tried madwifi. I have read countless forums and spent many hours in #unbuntu chat. 

I just removed my pci card and the cipset says RTL8185l. What steps do I need to take to get this card to work. Do I install ndiswrapper and load the linux driver for this card, if the card has a linux driver do I need ndiswrapper? When I installed ndiswrapper with bcmwl5 i when I ran ndiswrapper -l it stated it was an invalid driver. When I tried the same install with the drivers from the cd ndiswrapper -l said the driver was present. I have tried countless other menthods, two many to count. Could someone please hrlp me get this figured out. 

Links that I have followed:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://www.ubuntuforums.org/showthread.php?t=340689](http://www.ubuntuforums.org/showthread.php?t=340689)
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by papajack on 2007-03-15
well i figured out how to get my desktop working with a Internet connection. After three weeks of research and very helpful forum replies I decided to run a cat5 cable through my house. But the cord soon became a problem so I installed windows on my computer. This was all done in a couple of hours. Maybe I'll get around to dual booting with Linux in the future, but as of for now I dont think I'm ready for another Linux adventure.

---

### Post by squell on 2008-03-31
There is a bug on launchpad for this device not working in Ubuntu

[https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/176507](https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/176507)

The rtl8185l chipset is works in Fedora 9.... maybe there is a way to include the driver in Hardy before it is released??

---

