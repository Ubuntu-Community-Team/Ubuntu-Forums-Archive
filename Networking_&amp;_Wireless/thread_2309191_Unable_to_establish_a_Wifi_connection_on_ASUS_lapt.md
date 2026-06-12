---
title: "Unable to establish a Wifi connection on ASUS laptop"
date: 2016-01-08
forum: Networking &amp; Wireless
---

### Post by janosch2 on 2016-01-08
I'm having some problems with my WiFi connection since a few weeks:

After I boot up my laptop, it tries to establish a connection with my network. Most often this doesn't work - the laptop just keeps trying to connect over and over again without results. However sometimes - actually pretty rarely - it works without me doing anything. Once the laptop is connected I don't experience any issues.

I also have Windows 10 installed alongside and the internet connection works perfectly.

Here's what I've tried so far based on other posts:

[LIST]
[*]disable and re-enable WiFi via top bar 
[*]running [FONT=courier new]echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf[/FONT] which actually worked but only for a day or two 
[*]running[FONT=courier new] sudo rfkill unblock all[/FONT] 
[*]entering sleep mode and wake up 
[/LIST]

Here's my setup:

[LIST]
[*]Ubuntu version: 14.04 LTS 
[*]Laptop: ASUS UX305FA 
[/LIST]

Your help is highly appreciated :)

---

