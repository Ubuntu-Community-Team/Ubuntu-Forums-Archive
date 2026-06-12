---
title: "Spoofing wlan0 MAC - not working"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by mesocal on 2008-11-09
So I've been reading every blog and forum I can find but I still don't have a solution for my problem.  

I am able to change my wlan0 MAC using both ways:

sudo ifconfig wlan0 down
sudo macchanger wlan0 --mac=00:13:e8:22:22:22
sudo ifconfig wlan0 up

or

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hr ether 00:13:e8:22:22:22
sudo ifconfig wlan0

and here is where the problem is.  I am unable to connect to any AP after I've spoofed my MAC.  I've doubled checked my router and there is no MAC filter or restrictions. 

Here is some basic info:

Linux bluemint 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

any suggestions?

---

### Post by mesocal on 2008-11-09
any ideas or any suggestions at all?

---

### Post by tylermenezes on 2008-11-09
Does the MAC address show up correctly for ifconfig or iwconfig?

---

