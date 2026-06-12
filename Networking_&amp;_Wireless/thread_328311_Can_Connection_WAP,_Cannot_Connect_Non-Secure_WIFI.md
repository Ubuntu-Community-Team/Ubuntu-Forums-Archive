---
title: "Can Connection WAP, Cannot Connect Non-Secure WIFI"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by xml2k on 2006-12-30
UBUNTU 6.10

I can connect to my wifi router set to  WPA2 Personal, but cannot do so when I set my router to use No Security. I need to be able to connect a non-secure networks for roaming at libraries and coffee shops.

I have tried connecting at two different coffee shops that have free-wifi but could not connect.

Anyone else have this problem.

I am using the Network Manager to connect and have a Motorola WN825G wifi card on a Dell Inspiron 5100 laptop.

I may try the nsidwrapper method if I cannot resolve, since being able to connect to non-secure wireless networks is a requirement.

---

### Post by jml on 2006-12-30
xlm2k, ndiswrapper will not help you.  If your computer already connects to a secured access point, then ndiswrapper will not add anything, and it may actually cause new problems.  What you need to do is to create a new profile, one for unencrypted networks.  If you left click on the network manager icon in the upper right hand corner of the screen, you will see options to connect to other wireless networks.  That should solve your problem. 

Joe

---

