---
title: "Chromebook C720 xubuntu wireless slow/dropout fixed"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by SaberCat on 2014-01-01
I recently installed xubuntu on a C720 using the live CD image from the xubuntu site loaded on a USB memory stick. No problem. I installed it over the existing Chrome OS. The only detail is that when the machine boots, I have to enter Ctrl-l (that's a lower case L) to continue the boot -- not a problem. The only issue I had was that wireless web response was slow and the network link would drop out and reconnect occasionally. I solved this by following instructions I found at site:  [https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet) under the "Driver ath9k or ath5k: disable hardware encryption/decryption" section (right column). The procedure verifies that the host is using the Atheros wireless chipset and that the driver is ath9k. The fix is to create file: /etc/modprobe.d/ath9k.conf and enter the following into it: options ath9k nohwcrypt=1 Then reboot. According to the site, this will disable hardware encryption/decryption. xubuntu will then do the encryption/decryption in the software. This encryption/decryption occurs when using a secured wireless connection that utilizes WPA or WPA2. This fixed the problem. I now have very fast web access and no dropouts.

---

