---
title: "WiFi not able to scan."
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by malakar.subhendu on 2015-02-08
My Broadcomm WiFi used to work fine (although it was slow, don't know why). Yesterday there was an abrupt shutdown (battery drained completely) and after that the WiFi adapter is not able to scan any network. I have Deepin 2014 also as a third OS and it was able to scan and connect to my WiFi router. 
I think the abrupt shutdown had made some changes to some config file. I have attached the output of the "wireless_script"

---

### Post by praseodym on 2015-02-08
Hi,

> ```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```
The card is off, maybe due to the cable connection?! Also two drivers are loaded:
```

echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv brcmsmac b43
sudo modprobe -v brcmsmac
```
Install this firmware file because of a bug in the file **linux-firmware-nonfree** in 14.04 and 14.10:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
If you configure the static interface wlan0 in the "interfaces" file you need to change "false" to "true" in the file **/etc/NetworkManager/NetworkManager.conf**. If you do not wish to do so, reset the file to default
```

echo "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot.

---

### Post by malakar.subhendu on 2015-02-08
Thanks, 
That solved my problem.
Can you tell me what was the problem exactly?

---

### Post by praseodym on 2015-02-09
Maybe a combo of 2 drivers and/or missing firmware

---

