---
title: "Erratic Wireless Connectivity"
date: 2005-06-14
forum: Networking &amp; Wireless
---

### Post by sphoid on 2005-06-14
I am using a usb dwl-122 wireless adapter on a gateway laptop with Hoary 5.04. I have been having issues getting the wireless adapter to work consistently. I have used wlanctl-ng with the hotplug script I got from the HOWTO on this very forum for my dwl-122. That actually worked fine for a few days but today I started having problems. 

Just for good measure, I switched to ndiswrapper and grabbed the latest windows driver off the dlink site. I tried both INF files that came with the WHQL driver. The configuration goes perfectly smooth using either method and I am able to connect almost instantly. Now heres the problem: If I leave the connection sit, its fine, i can ping my router all day. The second I create any network traffic, either opening a web browser or attempting to download a file, my connection dies. I am still connected however all of my traffic times out. I have a terminal with ping running along side my browser window so i can see the exact moment it occurs. I can deactivate the adapter and reactivate it and sometimes it will come back to life but as soon as I create any sort of traffic again the same thing happens.

I have pulled the adapter out and reinserted it. I have rebooted hundreds of times alternating between ndiswrapper and wlanctl-ng, I have tried the modprobe prism2_usb prism2_doreset=1 trick. I have tested the adapter on my windows machine with no problems and not even a week ago, this adapter was working flawlessly on my suse 9.2 pro installation on the very same laptop. 

Additionally, another symptom that occurs in gnome when this problem occurs is the keyboard lags alot. When i am typing in the terminal it will lag for a second after a type something, and then it will repeat the last key i typed multiple times (kind of like thissssssssssssss). That goes away too when i reset the adapter. This is very frustrating... does anyone here have any ideas?

---

### Post by sphoid on 2005-06-16
bump.

Anyone?

---

