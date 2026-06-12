---
title: "Wireless not working on Ubuntu 14.04, Lenovo Z580, Broadcom 14e4:4727"
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by lukapez on 2014-06-05
[FONT=arial]Hello everyone. This is my third time having problems with wireless in Ubuntu, but first time in **14.04**. After an update about a month ago it just stopped working; I can see available networks (or just the one remembered, I don't know) but when I try to connect it fails. I use cable but I will need wireless soon, so I need help.
My laptop uses Broadcom **bcm4313**, and the pci.id is the [COLOR=#000000]**14e4:4727**. I have tried to take the steps that helped before and the ones mentioned here but everything I've done so far failed.
I've also downloaded the wifi help script, and here is the output.

Thank you.[/COLOR][/FONT]

---

### Post by varunendra on 2014-06-06
Which one is your Access-Point in the detected ones? Try setting the encryption type to pure WPA2-PSK with AES (CCMP) in it, and channel either 1 or 11.

Even if it used to work with the existing settings, it makes sense to try optimizing it now to see if it helps. Alternatively, you may try compiling a newer version of the driver and see if it works. The default one in 14.04 seems to be causing problems for many people having this particular card.

If changing the encryption type and channel in the router/ap doesn't help, I suggest you download and run a newer version of the wireless_script mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) and post its report.

By the way, your /etc/modprobe.d/blacklist.conf file contains unnecessary repetition of blacklist entries of b43 and ssb. I suggest you get rid of the repetitions and leave only one instance of them. You don't need to repeat the blacklist commands whatever guide you are following. :)

---

