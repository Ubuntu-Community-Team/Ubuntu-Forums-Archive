---
title: "Atheros XB63"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by wilerk on 2007-11-16
Hi all,

I'm pretty new with Linux so please bare with me.

I have Ubuntu 7.10 installed and I am hoping you could help me getting my wireless up and running.

I have an Acer Aspire 5610Z and when I want to download the driver at for winXP acer wants me to download the driver for the Atheros XB63 ver 5.3.0.35. 

In the beginning Ubuntu said I had some restricted drivers and this was for my Atheros. Now when following all the HOWTOs I could find for both madwifi and Ndiswrapper I still can't get it to work.

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

lspci:

05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

sudo modprobe wlan_scan_sta doesn't give me any errors.

I don't know what to do any more.

Thanks in advance,

Xander

---

### Post by wilerk on 2007-11-17
Bump, anybody here with the same problem?

---

### Post by wilerk on 2007-11-18
So it seems that XB63 is nothing but a AR5006eg and following the steps in the post below work!

[http://ubuntuforums.org/showthread.php?t=512828&page=23](http://ubuntuforums.org/showthread.php?t=512828&page=23)

---

