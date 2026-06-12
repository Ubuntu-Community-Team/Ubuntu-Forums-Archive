---
title: "wnda3100v2 netgear wifi dongle not working for wifi p2p connection"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by pandi_selvi on 2014-09-13
Hi,
I am using netgear wifidongle wnda3100v2. i want to use it for wifi p2p communication. i have installed ndiswrapper driver and bcm43xx driver also. The dongle is detected and i can see it by using lsusb. wlan0 interface is also created. i can use it as for normal wifi connection. using this dongle,  i can see the list of available networks. but i want to use it for p2p communication. i  have downloaded latest wpa_supplicant and run wpa_supplicant binary. it shows like:
~$ cd /home/aricent/Downloads/wpa_supplicant/wpa_supplicant/
~/Downloads/wpa_supplicant/wpa_supplicant$ sudo ./wpa_supplicant -Dnl80211 -iwlan0 -c/etc/p2p.conf -B
Successfully initialized wpa_supplicant
nl80211: Could not configure driver to use managed mode
wlan0: Failed to initialize driver interface
$ 

i have checked for iw list command. it returns nothing. 
should i install anyother driver or firmware?? Please help me to solve this issue. Thanks in advance.

---

