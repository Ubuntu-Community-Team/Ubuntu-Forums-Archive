---
title: "RTL8187L on Ubuntu 8.04 using WEP"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by kniwor on 2008-08-23
Hello everyone, 

I am not a linux expert, installed ubuntu 8.04 x86 on my computer yesterday, and having problems using wifi.

Motherboard is P5B-Deluxe wifi which has Realtek RTL8187L on USB to the best of my knowledge.lsusb shows the device allright.

There is a driver preloaded wlan0 is shown in the list of adapters, "iwlist wlan0 scan" shows the networks in the area(not all), but cannot connect to any. It does NOT show WEP networks. Everything works fine under windows XP. I want it to work for WEP enabled wireless networks.

Note: Router is a D-link one, no more info available, this is my college network so changing router configuration etc.. is out of question, I just have the key.

---

### Post by kniwor on 2008-08-24
I just woke up and did an "iwlist wlan0 scan" only to discover than the WEP connection was detected this time, I tried connecting to it using network-admin and it was sucessful, but the ping to google.com has 82% packet loss, the internet is pathetic... and gives "Destination Host unreachable" after a while.

I tried to install drivers on Realtek website, but too many erros compiling the code (while building modules), so cannot proceed any further.

---

