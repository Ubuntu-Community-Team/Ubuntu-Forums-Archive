---
title: "wireless can not get DHCP work after setting ESSID by iwconfig"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by h113331pp on 2013-10-21
Hi, everyone:
    recently I upgrade my computer from 10.04 to 12.04. ervery thing works fine :D 

but one little thing bothers me - wireless can not get DHCP work after setting ESSID by iwconfig  

I used to use following script to connect wireless when using 10.04:
```
#!/bin/sh

sudo dhclient -r wlan0

sudo ifconfig wlan0 0.0.0.0

sudo iwconfig wlan0 mode managed key off ap off essid off

sudo ifconfig wlan0 down

sudo wpa_cli -i wlan0 terminate

sudo ifconfig wlan0 up

sudo iwconfig wlan0 mode managed essid "sw-wifi"

sudo wpa_supplicant -B -D wext -i wlan0 -c ./sw-wifi_WEP_auth_file

sudo dhclient -v wlan0
```

but since upgrade to 12.04, I have to repace 'sudo iwconfig wlan0 mode managed essid "sw-wifi" ' to 'sudo iwconfig wlan0 mode managed'

or I will never get the DHCP work. although sw-wifi_WEP_auth_file also contains the ESSID name, so wireless still can connect.

my question is, why can't I set the ESSID first? is this step not needed anymore?

---

