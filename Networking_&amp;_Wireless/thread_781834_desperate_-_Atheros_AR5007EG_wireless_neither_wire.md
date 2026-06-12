---
title: "desperate - Atheros AR5007EG wireless neither wired NIC works!!!"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by KARLZ on 2008-05-04
:confused:
I'm about to have a week fighting against this... I have read tons of threads, try WICD, NDISWRAPPER everything I've seen...
my issue is as follow:
[LIST]
[*]Neither Wireless or Wired NIC card works
[*]NIC worked once with Ubuntu7.04 but upgraded to 8.04 and Wired NIC died
[*]I can't try most of the recommendations in the forum since **they request to download the build-essentials and I have no Internet at all**
[*]after shutting Ubuntu a message is displayed: **could not get the system bus. Make sure the message bus daemon is running!**
[*]When disabling the HAL driver or simply the driver, the message above dissappers.
[*]there's a message when stars to load about a PnP issue.
[/LIST]

NOTE: the Router is not the issue since I have two computers and handled devices with DHCP which work ok. Also I'm running WinXP. I enabled the Wake-on-LAN feature from there and still dont work.

My equipment is an:
Acer Aspire 5050
AMD 64 AthlonX2 (actually running 32bits Ubuntu version)
ATI Radeon Xpress 1100
Realtek RTL8139/810x Family Fast Ethernet NIC
Atheros AR5007EG Wireless Network Adapter
120GB HDD partitioned for WinXP and Linux Ubuntu 8.04


Does anyone can help me and guide me to a solution??? I'm running out of ideas and I'm a Linux newbie:(

---

### Post by Anabolic_OMEN on 2008-05-04
[http://ubuntuforums.org/showpost.php?p=4831547&postcount=39](http://ubuntuforums.org/showpost.php?p=4831547&postcount=39)
use the search

---

### Post by arjuk1 on 2008-05-04
I found that the driver in this link did it for me:
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by KARLZ on 2008-05-04
:-s
that was my face yesterday... today I tried a different flavor of linux: XUBUNTU 8.04

I want to say to everybody out there that the prev post HELPED a LOT! I downloaded WinXP drivers and followed the process! it works now... I WANT TO SAY THE WORLD IT WORKS!!! I really appreciate it! what happened was that XUBUNTU recognized my wired NIC cards and from there I installed the build-essentials... that was all!! THANKS XUBUNTU and ARJUK1!!!

---

