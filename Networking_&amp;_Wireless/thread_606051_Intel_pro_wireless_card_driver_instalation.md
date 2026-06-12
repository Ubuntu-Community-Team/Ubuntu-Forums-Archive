---
title: "Intel pro wireless card driver instalation"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by tashmooclam on 2007-11-07
I decided to "upgade" to a wireless card for my Dell D600 made by Intel. It's the 2200B card.
I did this because Intel has the driver and firmware available for download for Linux OS. 
I do not know how to download and "extract" or do whatever is needed to get this driver on my laptop.
I know what the download file is called, is it possible to use synaptic or terminal "apt-get" to download and install it? 
The driver's called "intel_ipw2200_120" 
Thanks

---

### Post by Whiffle on 2007-11-07
Ubuntu should detect that card just fine w/o doing any additional drivers.  Have you tried it yet?

---

### Post by tashmooclam on 2007-11-07
I don't know if it's being detected, it's not like before when I got prompted to install things for the previous card. 
I am pretty sure the card is "on". After install and restart, I hit the keys which turn on the wireless cards on this laptop.
I went to a Terminal and wrote "iwconfig" and the card shows up.
Otherwise I don't know what to do.

---

### Post by rmills on 2007-11-07
System > Administration > Network

Select the wireless adapter and click the Preferences or Properties button (don't remember and don't have it in front of me).  Set your SSID and WEP/WPA key there or leave it on roaming.

---

### Post by tashmooclam on 2007-11-07
Gentlemen, thank you both for posting.
I made the possible error of installing and switching to a program called Wicd, so the network manager will not really "see" anything any more.
Good news however. I will post about this elsewhere.
In Wicd, under Preferences menu there is a button "WPA Supplicant Driver" 
Under a list which includes "NDiswrapper" and "Wext" (worked with boadcom and bcm43xx-fwcutter), I saw "IPW". 
I selected this and clicked OK.
Then all the wireless networks appeared. 
I think I am cooking with gas. 
If this vastly improves my wireless performance, I will post about the experience. 
Some folks love Wicd, but I may have made things more complicated with it. 
Changing the wireless card on this laptop was very simple and inexpensive.
Now I'll unplug and test the wireless.

---

### Post by tashmooclam on 2007-11-07
I'm on wirelessly now.
I would alternately see wireless networks available in Wicd and then would not, and couldn't connect. I had some other steps to do.
I went to System>administration>network, and re-entered the Properties of the wireless.
Now Wicd connected me without my noticing.
Anyway, evidently this will function. 
The test will be if I get more reliable speed with this Intel card and setup. 
I kick myself for being stubborn/cheap. I really should have shucked out the dough for a new Dell, but I thought this was worth a try.

---

