---
title: "Wifi not working on ubuntu minimal install 16.04"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by onlineaddy on 2016-06-16
Hi
I downloaded ubuntu minimal ISO 16.04
The installation went smoothly. I configured the wifi (hidden ESSID and the password) and the Base system downloaded all the needed files.
After reboot however I cannot connect to wifi. I'm in command line which I'm not very advanced in. I tried the following:

ifconfig wlp2s0 up

ping 8.8.8.8 (tells me network is unreachable)

iwconfig (lists enp1s0 with no wireless extensions and wlp2s0 with:

IEEE 802.11bgn ESSID: "123"
Mode: managed 
Access point: not-associated
Encryption key: off
Power management: off

I think I need to change the last two lines, but how do I add the wifi password and turn on the power management? Thanks.

---

### Post by onlineaddy on 2016-06-18
no clues?

---

### Post by praseodym on 2016-06-18
Please run the wireless-script from the sticky thread and show the outputs.

---

