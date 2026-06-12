---
title: "[SOLVED] New Ubuntu (Dell 910) + Airport Extreme"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by mellburg on 2008-11-01
Please assist - I would assume this is an easy one.  I got an Inspiron 910 and it connected to my Belkin N1 router with no problems and I had internet access.  Then I upgraded to an Airport Extreme to better support the MAC users.  Now the Ubuntu wireless is not working.  I have no security (no password) on the wireless network right now to get everything working first.  The Ubuntu does not seem to see the SSID and even if I manually put it in I have no internet connectivity. I see no other changes to make on the Ubuntu and am not very familiar with the Airport Extreme.  Thanks!

---

### Post by mellburg on 2008-11-02
Using this worked:

sudo iwlist scan

give you a list of essid's then and what interface to use: most often eth1

sudo iwconfig eth1 essid <your essid>
sudo dhclient eth1

But it doesn't last through a reboot.  How do I save this and keep it?  Sorry, newbie.

---

### Post by mellburg on 2008-11-02
Problem Solved.

To save, Administration -> Network -> Unlock -> on General page save to a location name (use diskette icon)

---

