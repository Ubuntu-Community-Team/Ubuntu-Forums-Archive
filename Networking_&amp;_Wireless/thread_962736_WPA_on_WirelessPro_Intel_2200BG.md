---
title: "WPA on Wireless/Pro Intel 2200BG"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by trantloveazuen on 2008-10-29
Hi! I've instaled Ubuntu 8.04.1 and i am having trouble conecting to my home network :/ Its WPA encrypted and it works fine on my Windows Xp. My wpa_supplicant.conf is the following 

###############################################

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="TranTNetwork"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="password123"
}
###############################################

in order to conect i do:
1- sudo iwconfig eth1 essid TranTNetwork
2- sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -B
3- dhclient eth1

and in 3 after some line i get :

No DHCPOFFERS received.

what can i do to fix this?


Regards

---

### Post by trantloveazuen on 2008-10-29
bump : x

---

### Post by trantloveazuen on 2008-10-29
anyone :/?

---

### Post by trantloveazuen on 2008-10-30
up :x

---

