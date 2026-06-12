---
title: "No wireless connections shown in Hardy"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by sadranyc on 2008-05-10
Hi guys I have a pretty big problem, you see I just installed Ubuntu Hardy Heron to a Toshiba Satellite Laptop A135 and everything works just fine out of the box, everything but the wireless connection...

The problem that Network Manager shows "Activate wireless" with a tick, when I open the menu Configure Wireless Network (something like that, you see.. my Ubuntu is in spanish) I get no networks displayed at all. All I see is a blank list.

Help would be really appreciated.

---

### Post by destructaball on 2008-05-18
Yea i had the same problem on my dell 640m, i got it working on the live disk tho, could just be a freak event, either reinstall ubuntu or keep looking for the answer, personally i think its quicker just to reinstall.

---

### Post by brujoand on 2008-05-18
try sudo iwlist eth1/wlan0 scan

Choose eth1 or wlan0 whichever is your network interface.

This will show if the problem is in the network manager or in the drivers.
If its in the network manager, you can just connect manually.

---

