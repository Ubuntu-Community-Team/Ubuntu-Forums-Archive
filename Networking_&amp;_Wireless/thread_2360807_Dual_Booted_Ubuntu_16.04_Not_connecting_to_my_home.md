---
title: "Dual Booted Ubuntu 16.04 Not connecting to my home WiFi Router"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by ayush1810 on 2017-05-08
I dual booted Ubuntu 16.04.2 with my Windows 10 few days back. Nothing went wrong until yesterday when after keeping Ubuntu idle (but running) for a long time, I could no longer connect to my home WiFi connection. I tried ```
sudo service network-manager restart
``` , ```
sudo systemctl restart NetworkManager
``` , ```
rfkill list
``` and few other commands to find out the issue but couldn't. I can connect to my mobile's hotspot and other networks. 

Wireless info script output: [https://pastebin.com/27FJ85vD](https://pastebin.com/27FJ85vD)            
*AYUSH* is the name of my home router which I can't connect to! 

Thank you.

---

### Post by chili555 on 2017-05-08
> AYUSH      <MAC 'AYUSH' [AN2]>  Infra  1     2412 MHz  54 Mbit/s [COLOR="#FF0000"] 27[/COLOR]      &#9602;___  WPA2      no      The figure I highlighted is the signal strength; I assume you are not  500 meters from the router.

The driver in question, rtl8723be, doesn't automatically select the best antenna connector. We need to specify it. Please see: [https://askubuntu.com/questions/883673/rtl8723be-wifi-incredibly-weak/883688#883688](https://askubuntu.com/questions/883673/rtl8723be-wifi-incredibly-weak/883688#883688)

---

### Post by ayush1810 on 2017-05-08
This solved the issue. 
Thank you so much!

---

