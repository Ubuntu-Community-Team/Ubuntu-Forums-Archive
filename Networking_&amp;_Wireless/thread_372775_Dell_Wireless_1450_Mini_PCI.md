---
title: "Dell Wireless 1450 Mini PCI"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by Meson on 2007-02-28
Ok, I know this topic has probably been covered many times but I'm having no luck on my own.  I installed NdisWrapper and set it up with the wireless driver I used for XP.  I have a WPA2 PSK network.  I configured my ssid (which is set to hidden in the router) and entered the PSK (I tried both ASCII and Hex - which is correct?).  Either way it says the device is found but the network status icon shows the interface as disconnected.

Obviously I'm missing something because I've followed guide after guide to no end.

Thanks, and sorry for the repeated topic.

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

