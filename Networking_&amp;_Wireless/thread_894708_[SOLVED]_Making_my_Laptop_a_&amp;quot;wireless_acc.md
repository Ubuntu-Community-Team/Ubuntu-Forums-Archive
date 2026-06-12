---
title: "[SOLVED] Making my Laptop a &amp;quot;wireless access point&amp;quot;"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by AlexBellisBrown on 2008-08-19
Hello everyone, i have a new problem to solve, ive tried, no success, so fingers crossed you guys can help. Let me explain. I have a ipod touch, and i wish to surf the internet using its wifi... etc. I have a laptop with a wireless card. BUT!!! I do not have a wireless access point. I am connected via an Ethernet cable. So, what i wish to do, call it what you will, is make my laptop the access point, i think you can also call it a Ad-Hoc network, but just so everyone knows, i basically want my laptop, to send out a SSID, thus making it a access point. This should be quite simple, though ive tried following numerous internet pages for the last hour, and had no success, can anyone help? Im using Hardy, 8.4.1, (flavor, Ubuntu), and my 2 wifi cards are a ralink and a USB wifi card (both work flawlessly, but just letting you know)

Any ideas appreciated, even past experiences. Thanks!!!! :popcorn::)

---

### Post by jimv on 2008-08-19
WICD (alternative to NetworkManager) makes what you are doing fairly simple.  Just install it, and click New > Adhoc Network, and choose your settings.  It's pretty self-explanatory.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by amedac on 2008-08-20
Do you know some terminal way to do this? I asume i must set up my wlan card in ad-hoc mode, and bridge my lan connection to wlan. Do you know some tutorial for thar?

---

