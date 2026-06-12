---
title: "ESSID Scanning Doesn't Work Anymore."
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by acascianelli on 2005-11-15
I have the same problem on laptops with different configurations.

1st Laptop
Emachines M5310
Broadcom 802.11g with NDISWrapper 1.2
Ubuntu Breezy 5.10

2nd Laptop
IBM T22
Orinoco Gold 802.11b
Ubuntu Breezy 5.10

At one point, BOTH laptops were able to detect wireless network using a iwlist wlan0 scan command. Now, both laptops cannot. They are still able to connect to a wireless network as long as you provide the ESSID.

The Emachines Linux install is much older, about 2 months. The IBM's install is about 2 weeks old. I have no idea why it worked on both initally and now it stopped...Please help.

---

### Post by mlomker on 2005-11-15
That command only worked for me *once* on Hoary and never again.  That is odd, because tools like wifi-radar have no problem displaying them.  Why don't you use that, gtkwifi, or network-manager?

---

### Post by gila_monster on 2005-11-15
[QUOTE=mlomker]  Why don't you use that, gtkwifi, or network-manager?[/QUOTE]

I have tried both of these, and they'll both work. For what it's worth, I prefer network-manager. 

gila

---

### Post by acascianelli on 2005-11-16
I reinstalled the kernel packages and now its working on my emachines notebook.  I'm going to try the same on the IBM.

---

