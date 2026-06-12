---
title: "Got Linksys WUSB54Gv4 working on Edgy Eft!"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by Dizturbanz on 2007-03-17
As a complete newby on Linux (and being an expert user in XP) i wrestled with my Linksys WUSB54Gv4 getting connectied to my wireless LAN.

After two days of trying (and cursing...) and a divorce close by ;-) I succeeded in connecting to network with the WUSB54Gv4 and I would like yo share my pain just to help others be more successful in less time :).

First off all this site helped a lot: [http://moonintheroom.blogspot.com/](http://moonintheroom.blogspot.com/)
so start reading from there.

So the 1st thing that went wrong was on step 4 install the ndiswrapper-utils-1.8. This is what I had to do to get that right:
1) open your synaptic package manager and remove all ndsiwrapper-utils version before 1.8 (it seems that 1.1 and 1.5 are pre-installed)
2) checkmark the ndiswrapper-utils-1.8 en (re)install it
3) now enter the command: **sudo ndiswrapper-utils-1.8**

Continue with step 5 on Moon in the room

In step 9 you have to modify your interfaces file. I had to make some changes there too! This is what I had to change:
wpa-pairwise TKIP
wpa-group TKIP
wpa-proto WPA

For more settings see the thread in [http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

After restarting I got nothing.....yet. UNtil I checked the network icon on the right top of the title bar. Open it and select on the General tab behind the connection setting, wlan0 from the drop down list. And voila the network was connected.

Greetz,
DizTurbanz

---

### Post by qrprat77 on 2007-04-12
Hey, your tricks worked great!
Only weird thing was that I needed to install the latest drivers, not the ones that came on the install cd.
go figger!
Now I'm very happy!!

---

