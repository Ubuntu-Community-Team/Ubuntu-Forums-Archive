---
title: "wifi randomly disappearing on ubuntu 16.04 lts"
date: 2017-05-26
forum: Networking &amp; Wireless
---

### Post by heron1337 on 2017-05-26
yo i have problem with my wifi on ubuntu 16.04.02 lts, internet is randomly disappearing and i cant connect to sites or its loading very very slow, the wifi icon is showing that im connected and everything is ok but its not, like its working for 10mins and randomly i cant load any sites but after 2-5mins internet is back also if i disconnect and connect again, internet is working immediatly... idk whats wrong im on wifi 

i also checked additional drivers update but there is thing like this and i dont know what it is for:
[https://ibb.co/eU4tXa](https://ibb.co/eU4tXa)


wifi adapter:
[https://ibb.co/fAG7sa](https://ibb.co/fAG7sa)

---

### Post by wildmanne39 on 2017-05-26
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by heron1337 on 2017-05-26
> **wildmanne39 said:**
> Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.
[http://paste.ubuntu.com/24668084/](http://paste.ubuntu.com/24668084/)

---

### Post by wildmanne39 on 2017-05-26
Please do the following, just copy and paste for accuracy:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
Check the settings in your router. WPA2-AES (CCMP) is best, not WPA and WPA2 mixed mode and do not use TKIP. 

While in your router settings take out the all special characters in your network name.

Next, if your router is capable of N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

We need to set your Country Code:
```
sudo iw reg set PL
```
```
sudo sed -i 's/^REG.*=$/&PL/' /etc/default/crda
```
Set your settings in network manager to match the screenshots:

---

### Post by heron1337 on 2017-05-26
> **wildmanne39 said:**
> Please do the following, just copy and paste for accuracy:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
Check the settings in your router. WPA2-AES (CCMP) is best, not WPA and WPA2 mixed mode and do not use TKIP. 

While in your router settings take out the all special characters in your network name.

Next, if your router is capable of N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

We need to set your Country Code:
```
sudo iw reg set PL
```
```
sudo sed -i 's/^REG.*=$/&PL/' /etc/default/crda
```
Set your settings in network manager to match the screenshots:

when im trying to change security to wpa2-aes its saying the radious server ip addres 0.0.0.0 is invalid 
[https://ibb.co/fxQyha](https://ibb.co/fxQyha)

and i arleady have channel 1 selected not automatic.
[https://ibb.co/cUy12a](https://ibb.co/cUy12a)

---

### Post by wildmanne39 on 2017-05-26
That setting is only for large networks like enterprise, if you can not set it to wpa2 personal then use wpa2 with PSK instead of AES, but only if you have too.

---

### Post by heron1337 on 2017-05-27
> **wildmanne39 said:**
> That setting is only for large networks like enterprise, if you can not set it to wpa2 personal then use wpa2 with PSK instead of AES, but only if you have too.
kk thanks problem solved anyway

---

### Post by wildmanne39 on 2017-05-27
I am glad it is working now, your welcome and enjoy!:)

---

