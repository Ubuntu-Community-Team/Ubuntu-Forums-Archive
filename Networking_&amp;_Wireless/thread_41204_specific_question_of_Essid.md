---
title: "specific question of Essid"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by taking_the_music_back on 2005-06-12
First, let me explain my hardware... 

it's a broadcom 802.11 b/g wireless, which I installed the drivers for just fine using NDISwrapper.  

Network tools even has shown my wlan0 as being existant, but I cannot modify anything (such as frequency, wep code, etc.)

This, however, I was able to modify using the commandline..

however... I've realized that the sudo iwconfig command shows one glaring error, in that it keeps showing my essid as "off/any"

I've used the the sudo iwconfig essid xxxx command, but it still shows my essid as being off/any.

I think this is the final piece to the grand puzzle that is my wireless card...

---

### Post by FizDev on 2005-06-12
It did exactly the same thing to me. In the beginning, I was using the driver "bcmwl5.inf" with ndiswrapper but I removed it and changed to "bcmwl5a.inf" and then rebooted... could see the led of my wireless card light up. After that, tried again the "iwconfig wlan0 essid name" and then iwlist wlan0, and there it was!... at least, that's what happened to me.
Hope this helps!

---

