---
title: "Cannot Detect Access Point"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by ZBlach on 2005-08-23
I've managed to get ndiswrapper to understand my wireless card, and I've used Gnome Network Configuration tool to set up the card same as I have in m windows installation, but I still can't connect to my Access Point.

how can I remedy this?

-Z

---

### Post by kikito on 2005-08-23
Hello,

Im also having all sorts of issues with my wireless adapter but I think I might be past your point.  maybe I can help you out.  There is a lot of talk about wireless issues in the forums.  did you look at forum posts like:
[http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto](http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper+howto)

if you still cant find a solution maybe I can help (even thought Im still new at this).

when you type:
iwconfig

do you see your essid?  does your Access Point broadcasts your essid.

One of the tricks that worked for me was to go in terminal and type
sudo iwconfig wlan0 key open XXXXXXXXXX
sudo iwconfig wlan0 essid youressid
sudo ifconfig wlan0 up

you can also check if your card sees your acces point with the following command:
iwlist scan

this command will scan for available networks.  if you dont see your network, then its either down or does not broadcast essid.

---

### Post by kikito on 2005-08-23
You can also check the following posts and howtos (if you havent check them already):
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by ZBlach on 2005-08-24
thanks for the quick response.

I've used that site to install the card. my main issue is with setting the essid and the ap. I get no errors when I set them, but right after, when I

iwconfig wlan0

my changes have not taken effect. 
I've tried setting the essid many times, but it remains 'd11b' and my AP remains at 00:00:00:00:00:00. 

The card is there, its detected, its unconfigurable.

-Z

---

