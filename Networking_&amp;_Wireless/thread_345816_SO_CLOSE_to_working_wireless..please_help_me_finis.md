---
title: "SO CLOSE to working wireless..please help me finish!"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by jk610 on 2007-01-24
After tons of research I finally got ndiswrapper installed and working. Heres what I have so far:


Version: Egy 6.10
Wireless adapter: WUSB54G
Ndiswrapper: 1.34


I open System -> Admin -> Networking 

I see Wireless Connection... ESSID: LINKSYS... ADDRESS: DHCP


So thats good so far I suppose.


iwconfig


lo   no wireless connections

eth0 no wireless connections

eth2    comes up like my wireless but nothing working

sit0   no wireless connection


Now shouldnt a wireless card come up as wlan0? Mines coming up in eth2. Is there anyway to change that?


I also have a ndiswrapper problem. Everytime I run ndiswrapper -l, nothing comes up it just gives another command prompt. If I do:

sudo ndiswrapper -i /home/jk/Desktop/WUSB54Gv4/rt2500.inf

it says:

installing rt2500usb....
couldnt open /home/Desktop/jk/WUSB54Gv4/rt2500.inf: No such file or directory at /usr/sbin/ndiswrapper line 172.


So long story short...my wireless card doesnt come up at wlan0 and my ndiswrapper hates me. :(

---

### Post by jk610 on 2007-01-24
UPDATE:


I reinstalled ndiswrapper now I get:


sudo ndiswrapper -l
rt2500usb   driver present


Nothing about the hardware though. Is this because I may have had it connected during my ubuntu installation? If so, can I fix that without reinstalling? :(

---

