---
title: "[SOLVED] Got my wireless card to work with WEP"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by camas on 2008-07-05
I am a real newbie with Ubuntu Linux. I got some local pros from EUGLUG to get my Linksys Broadcom-based wireless card to work, but when I got home I couldn't log onto my WEP-protected access point using WiFi Radar. When I turned WEP off at the access point, however, it worked. After mucking around for a few hours, here's how I got WEP to work. 

I had to go into System, Administration, Network. This opened a Network Settings window. One item in Connections was a wireless connection. To get into this thing to play with it, I had to click Unlock in the lower right part of the window and enter my Admin password. Then click on Wireless Connection and then Properties.

In properties under Network name (ESSID), I clicked the down arrow box and found the correct ESSID among the many listed. (Apparently WiFi Radar is picking up a lot more access points around here than my XP-based Linksys wireless monitor ever did.) Under password type I clicked WEP key (hexadecimal). You may be using an ascii password. At first I mistakenly selected ascii because I didn't see the hexadecimal option. The second time 'round I got it right.

In the Network password box I entered my 10-character hexidecimal WEP key. In the Configuration box, Automatic configuration (DHCP) was already selected. I clicked OK and I was immediately off to the races. 

Since I had already set up the same parameters in WiFi Radar, I didn't need to make any changes there. However, it might be necessary to go back and muck around in WiFi Radar too to get all the parameters in agreement with your access point.

Hope this works for you. I'm looking forward to the day when all this stuff will just happen as Ubuntu is loaded onto a computer. One can dream!

---

### Post by nixscripter on 2008-07-06
I'm glad it worked. You might want to make this a HOWTO thread, or at least mark it as SOLVED (under the Thread Tools menu).

---

