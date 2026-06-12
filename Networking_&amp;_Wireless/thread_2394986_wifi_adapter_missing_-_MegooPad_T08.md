---
title: "wifi adapter missing - MegooPad T08"
date: 2018-06-24
forum: Networking &amp; Wireless
---

### Post by mr.slimbrowser on 2018-06-24
Hello, i'm struggling with a Megoopad T08 Mini PC
Currently I'm running a dual boot using Windows 10 and Ubuntu 18.04 LTS. Using Windows the wifi adapter shows up and works fine, it's name in device manager is "Broadcom 802.11abgn Wireless SDIO Adapter" and the hardware-id is "SD\VID_02d0&PID_a94d&FN_1".
Results of the wireless-info script on pastebin: [https://pastebin.com/hQX2e0vj](https://pastebin.com/hQX2e0vj)
The device enp0s20u2 I added to the netplan config is my phone that I currently use to get an internet connection.

I hope my english is not too bad, don't hesitate to ask if something is not understandable :)

TIA
,- Slim

---

### Post by chili555 on 2018-06-25
We see this in your paste:> brcmfmac mmc1:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2If you are able to get an internet connection by ethernet, tethering or some other means, open a terminal and do:```
cd /lib/firmware/brcm
sudo wget https://raw.githubusercontent.com/harryharryharry/x205ta-iso2usb-files/master/brcmfmac43340-sdio.txt
sudo modprobe -r brcmfmac
sudo modprobe brcmfmac
```It might take a reboot.

Any improvement?

---

