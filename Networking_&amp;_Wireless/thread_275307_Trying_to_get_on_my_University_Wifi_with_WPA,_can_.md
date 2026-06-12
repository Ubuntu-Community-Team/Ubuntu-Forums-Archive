---
title: "Trying to get on my University Wifi with WPA, can anyone help?"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by CheeseEatingBulldog on 2006-10-11
Hello all,

I have been an Ubuntu user for about a year and half now and have it on both my desktop and laptop (and none of that dual booting malarky either). 

Anyway, I have a problem, on my vaio I am using a Linksys Wireless -B adapter (model WPC11 ver. 4) (pcmcia), which runs fine at home when connecting to my router. However, at my uni they have as most nowadays a wifi network, but they only support windows hardware/software. Not to be discouraged I have been trying to get WPA_supplicant up and running with no success. The reason being that WPA_supplicant can only use one of 6 or so drivers, which I don't use.

So, can I change drivers? Do I use ndiswrapper on the windows driver? How do I change drivers? How can I see which driver is being used (forgot)? Will the ndiswrapper driver still work the same way as my current setup? (go to system->network and select ssid) or will it be CLI when using ndiswrapper?

It is driving me crazy, as I can't get onto internet there with the laptop, and thus have to set it up at home and then try at uni when I am there. It can't be that hard can it?

Thanks in advance.

-->edit

I ran LSMOD in a terminal and I think the driver that is currently being used is r818x (ieee80211_rtl).

---

