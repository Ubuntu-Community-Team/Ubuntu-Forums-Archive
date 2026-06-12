---
title: "Please Help"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by ozone702 on 2007-12-19
My wireless at home keeps wanting to connect to an ip address that doesn't exist as a wireless network.  It keeps replacing my home network ssid with some ip address.  My ssid is hidden and I can connect to it if I manually connect, but once I re-boot my network manager keeps trying to connect to the erroneous ip address.

Where do I go to edit the list of known wireless networks?

---

### Post by spd106 on 2007-12-19
There are instructions on the network manager help docs page at [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

You would probably have better results setting your AP to broadcast it's SSID.

---

### Post by ozone702 on 2007-12-20
YES!!!  I finally got that problem off my back.

Thank you.  I looked over that doc several times but didn't think to look at the end where it tells you how to access the GConf registry.  From there I was able to rid myself of the problem. :lolflag:

Much happiness now... :guitar:

---

