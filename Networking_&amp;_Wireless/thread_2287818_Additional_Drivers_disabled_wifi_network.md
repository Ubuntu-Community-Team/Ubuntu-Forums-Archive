---
title: "Additional Drivers disabled wifi network"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by Ka Fish on 2015-07-22
I was exploring System Settings trying to get the update manager to pop up like it did when I had no internet access. I opened Software & Updates, went to the Additional Drivers tab. There I saw something to the effect of No proprietary drivers are in use. There was 1 option I believed would turn it on so I click it. I was surfing the internet to see if anything gets better when it suddenly stopped. I pulled down the network tab & see the Enable Wireless option is gone. I went back to the Additional Drivers tab & whatever I clicked on is no longer there. It just says No additional drivers available. How do I get the WiFi back on?

---

### Post by chili555 on 2015-07-22
Sadly, the Additional Drivers tool installs the wrong driver in a few cases and, as you see, actually disables wireless. Let's start by identifying your device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nnk | grep 0280 -A2
rfkill list all
```Thanks.

---

### Post by Ka Fish on 2015-07-22
[EMAIL="ka@ka-desktop:~$"]ka@ka-desktop:~$[/EMAIL] lspci -nnk | grep 0280 -A2
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wirele
ss Lan Controller [14e4:4320] (rev 03)
            Subsystem: Belkin F5D7000 v1000 Wireless G Desktop Card [1799:7000]
            Kernel driver in use: wl

I'm not sure how to put in that rfkill... nothing happened when I typed it in by it self. I got No such file or directory when I typed it on a line by itself.

---

### Post by chili555 on 2015-07-22
Please try:```
sudo apt-get purge bcmwl-kernel-source
```After it finishes, reboot and tell us if it's working.

---

### Post by Ka Fish on 2015-07-22
Yes, that did it. It's already connected to the wifi before I logged in & the Enable WiFi function is back under Enable Network like it was before. Thank you so much.

---

### Post by chili555 on 2015-07-23
Please use thread tools at the top to mark Solved. Glad it's working!

NOTE TO SEARCHERS: The Additional Drivers tool sometimes installs the *wrong* driver for your Broadcom card. For help on your wireless drivers, please check here: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

