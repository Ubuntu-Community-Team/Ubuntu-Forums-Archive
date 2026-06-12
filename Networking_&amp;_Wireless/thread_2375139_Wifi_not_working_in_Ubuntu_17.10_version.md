---
title: "Wifi not working in Ubuntu 17.10 version"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by sh1ju on 2017-10-22
Hi,
I upgraded my Ubuntu 17.04 to 17.10.After upgradation  Wifi stopped working .I am using Lenova ThinkPad E450 laptop.My network information is uploaded to [https://files.acrobat.com/a/preview/3197c0dd-b35a-4d8d-b49c-75f6add91bbe](https://files.acrobat.com/a/preview/3197c0dd-b35a-4d8d-b49c-75f6add91bbe)

---

### Post by praseodym on 2017-10-22
Change to pure WPA2-AES (CCMP) encryption in your router, not mixe mode WPA/WPA2. You may find free channels using the tool "LinSSID"

---

### Post by sh1ju on 2017-10-22
There is no issues in Ubuntu 17.04.After moving to 17.10 ,wifi stopped working

---

### Post by folloppingmattress on 2017-10-22
I'm having problems with network access on my new 17.10 install as well (Ethernet).
Is WiFi your only network connection or does wired LAN work ?

Temporary fix for me is to restart Network Manager service, then it works until the next reboot.
sudo service NetworkManager restart

---

### Post by kzoogene on 2017-12-17
I have an Alienware laptop that wifi worked under 16.04.  When I switched to 17.10 the lan works OK but the wifi will not start up.  I had to move to make room for the Christmas Tree and now the cable will not reach..... help?  ;)  I tried restart of Network Manager but to no avail.

---

### Post by praseodym on 2017-12-18
There is a bug in 17.04 and 17.10. Please run
```

echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

