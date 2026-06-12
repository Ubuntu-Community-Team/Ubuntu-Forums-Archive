---
title: "Qualcomm Atheros AR9285 randomly disconnects"
date: 2017-05-21
forum: Networking &amp; Wireless
---

### Post by lothrail on 2017-05-21
[https://paste.ubuntu.com/24617581/](https://paste.ubuntu.com/24617581/)

What happens it that my wi - fi randomly disconnects and then tries to reconnect(usually successfully). I haven't been able to determine any cause of it.

---

### Post by wildmanne39 on 2017-05-21
There was several things we can do to help it connect better, it looks like your firewall is blocking traffic so you will need to look into that.

Please copy and paste for accuracy one line at a time:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Go into your router settings and in your network name take out the special character which is the dash mark.

Check the settings in your router. WPA2-AES is best; not WPA and WPA2 mixed mode and do not use TKIP. 

Next, if your router is capable of N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Let's set your Country code for your router, please do the following if you live in Poland:
```
sudo iw reg set PL
```
```
sudo sed -i 's/^REG.*=$/&PL/' /etc/default/crda
```
Set your settings in network manager to match the screenshots:
Then do:
```
sudo systemctl restart NetworkManager.service
```
Let us know how it is working please.

---

### Post by lothrail on 2017-05-22
Second day, no drops so I guess it's fixed now. Thank you for your time!

---

### Post by wildmanne39 on 2017-05-22
Your welcome!
Enjoy!:)

---

