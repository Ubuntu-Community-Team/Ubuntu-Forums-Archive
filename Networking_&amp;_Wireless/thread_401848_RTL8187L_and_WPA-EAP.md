---
title: "RTL8187L and WPA-EAP?"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by mongo on 2007-04-05
Hello,
  I'm having some serious issues with my Alfa USB wlan card (Realtek 8187L based). I tried every possible thing I could find, needless to say without success. :confused: 
I'm running the latest drivers from realtek's site (rtl8187_linux_26.1010) patched for 2.6.20 kernel (rtl8187_2.6.20v2.patch), using the latest kernel (2.6.20.4). 
The driver loads without errors or warnings and I can scan and connect to any unencrypted network. 
I need WPA-EAP though so that I can connect to my school's network. 
I also tried ndiswrapper with every possible windows driver for my card I could find, without luck. wpa_supplicant is up2date (0.5.7), ndiswrapper also (1.39, utils 1.9). 
I'm attaching wpa_supplicant configuration file, debug and log messages that could be useful for debugging. Any help would be highly appreciated.

Best regards, mongo.

---

