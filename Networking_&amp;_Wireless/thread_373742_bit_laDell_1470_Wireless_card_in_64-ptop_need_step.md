---
title: "bit laDell 1470 Wireless card in 64-ptop: need step-by-step directions"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by Alaras on 2007-03-01
I've tried to do it myself, but I don't know anything about Terminal.  Please, help me do this in Edgy!  I have the drivers extracted to a folder called Drivers, located directly on the Desktop.  I need to know exactly what to type to access the directory, and have ndiswrapper do whatever it does to the files to make my wireless card work (I literally switched to Ubuntu just last night, so I really need to get this done ASAP).

---

### Post by nachotronics on 2007-03-02
You get your wireless card working following **[these steps]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=edgy+dell+1390")**
The driver in that post is the one for any of these cards:

Dell Wireless 1350 WLAN MiniPCI Card, 
Wireless 1350 WLAN PC Card, 
Wireless 1370 WLAN MiniPCI Card, 
Wireless 1390 WLAN ExpressCard, 
Wireless 1390 WLAN MiniCard, 
Wireless 1450 WLAN miniPCI Card, 
Wireless 1470 Dual-Band WLAN miniPCI Card, 
Wireless 1490 Dual-Band WLAN MiniCard, 
Wireless 1500 Draft 802.11n WLAN mini Card

I couldn't get it working with that driver, instead i used the one i'm attaching here.

After getting your wlan working you might want to install network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks

I had to set SSID broadcasting ON in the router for it to work.

Hope this helps.

---

### Post by rajncajn on 2007-03-19
FYI,
I was able to get the procedure to work with the windows 2000 driver at the Dell website. The xp driver evidently contains support for 64 bit also which was quickly dismissed by Ubuntu since my machine is not 64 bit. Afterwards, I was also having a hard time configuring the card to connect. I installed Wifi Radar which is part of the add/remove programs. That made it very easy and it works like a charm.
Hope that helps,
rajncajn
Dell E1505
core duo 1.66

---

