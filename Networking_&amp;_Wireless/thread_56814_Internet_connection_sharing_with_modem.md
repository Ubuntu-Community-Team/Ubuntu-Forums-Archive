---
title: "Internet connection sharing with modem"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by Matchless on 2005-08-14
Hi,
   I need to use my Ubuntu box with a dial up modem to share internet on my home lan with another XP and Ubuntu PC. I have had a look at Firestarter, but it does not detect my modem only eth0. At the moment I am sharing from an XP dialup and want to convert to Ubuntu. My modem works on Gnome-ppp and WVdial.
Any help will be appreciated.
Thanks
Matchless

---

### Post by jasmuz on 2005-08-14
Does your LAN work properly ? If so install Guidedog to foward & masquerade your internet connection, and dnsmasq, for DNS resolution and DCHP server for the Ubuntu Machines.

This might help a little: [http://www.ubuntuforums.org/showthread.php?t=25557](http://www.ubuntuforums.org/showthread.php?t=25557)

---

### Post by Matchless on 2005-08-20
Thanks and much appreciated will try guidedog.
Regards
Matchless

---

### Post by Matchless on 2005-08-27
I managed to get firestarter working and have internet sharing working. It seems that ppp0 is only shown in firestarter once it is active, meaning dialled up and connected to the ISP. Its a bit confusing and I expected it to show but as inactive. Maybe some developer will add this further bit of user-friendlyness some time.
Regards
Matchless

---

