---
title: "Wi-Fi connection keeps dropping"
date: 2018-03-18
forum: Networking &amp; Wireless
---

### Post by Zaphan58 on 2018-03-18
Hi all, I have just bought a new Dell Inspiron laptop and installed Ubuntu 17.10 on it. The wi-fi and internet connection do work but every 10 minutes or so the connection drops out. I have followed the sticky and created a wireless-info.txt file which is below.

[https://paste.ubuntu.com/p/NK2tB85qyS/](https://paste.ubuntu.com/p/NK2tB85qyS/)

Any help much appreciated.

---

### Post by Hadaka on 2018-03-18
Hi, as seen in the dmesg output of the wifi report
the wifi is dropping because it is roaming between the 2.4 and 5 GHz connections ..
both connections have identical ssid.

```
SSID                     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
'Cyberdyne Systems T-800' [AC1]>  Infra  6    2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2   yes     * 
'Cyberdyne Systems T-800' [AC17]>  Infra  44  5220 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2   no
```
#Please COPY and Paste commands to avoid error.

Suggest you rename    Cyberdyne-Systems-T-800-2     and Cyberdyne-Systems-T-800-5 [including the space removal]
as Ubuntu wifi has isssues with blank spaces in ssid names.

also please do..
#Set power mgmt. off
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
and..
#Set correct country code.
```
sudo iw reg set GB
sudo sed -i 's/=.*/=GB/' /etc/default/crda
```
Then for BOTH connections,if NOT using IPv6..please set to Ignore..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/[COLOR=#ff0000]**2GHz-**[/COLOR][COLOR=#ff0000]**SSID-NAME-HERE**[/COLOR]
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/[COLOR=#ff0000]**5GHz-SSID-NAME-HERE**[/COLOR]
sudo service network-manager restart
```
Thanks

---

### Post by Zaphan58 on 2018-03-19
Thanks! That looks like it might solve the problem :)

---

