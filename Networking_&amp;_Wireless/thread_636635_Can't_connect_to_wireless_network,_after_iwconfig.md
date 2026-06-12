---
title: "Can't connect to wireless network, after iwconfig"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by LGNR on 2007-12-10
Hi, I'm trying to connect my laptop, which is using a ndiswrapper USB Wireless Card (AWL3025v2) to my router a 2WIRE Homeportal 1701HG. The card is correctly listed in lsusb with the ndiswrapper driver, and it appears in iwconfig list. When I do ```
iwlist scanning 
``` there appears the information of my router, the SSID, the mac address, key (if on or off), etc. Then I do ```
sudo iwconfig wlan0 essid "2WIRE107" mode managed key off
``` (in this case, which is the last I tested, I disabled wireless encryption) and, after that iwconfig, there appears that I have no ESSID and that the AP is Not Associated. This all happens altough I'm correctly putting the info on iwconfig. It is Xubuntu 7.10
Thanks in advance for you advices.
LGNR

---

### Post by LGNR on 2007-12-10
After doing ```
sudo dhclient
``` nothing possitive happens yet...

---

### Post by vertago1 on 2008-05-03
I moved my post to a newer thread: [http://ubuntuforums.org/showthread.php?p=4875430#post4875430]("http://ubuntuforums.org/showthread.php?p=4875430#post4875430")

---

