---
title: "Wifi Drops after 5-10minutes (Intel 3165, Ubuntu 16.04)"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by bdmcgraw on 2018-02-18
Thank you in advance for the help. 

Wireless output is here:

[https://paste.ubuntu.com/p/BfPBbgmYcm/](https://paste.ubuntu.com/p/BfPBbgmYcm/)

---

### Post by bdmcgraw on 2018-02-19
Update on my end if anyone has any thoughts. 

From searching other 3165 threads, it seems that my country is unset. (equal to 00 when it should equal US)

I have tried the steps in this thread ([https://askubuntu.com/questions/819830/sudo-iw-reg-get-still-shows-country-00-after-updating-etc-default-crda](https://askubuntu.com/questions/819830/sudo-iw-reg-get-still-shows-country-00-after-updating-etc-default-crda)) but haven't been successful.

---

### Post by wildmanne39 on 2018-02-19
There are a few things we can change that should help, first we will turn off power management by doing:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then go into network manager and set IPV6 to ignore.

The main issue I believe is that you have so many networks near you and 7 on the same channel.

Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, in your case I believe I would try 40 if your 2.4 ghz and 5ghz have the same name please change the name of one of them. After making these changes, reboot the router and computer.

00 should be okay for CDRA if you are in the U.S. but you can set it by doing:
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Let us know how it is working now.

Thanks

---

### Post by bdmcgraw on 2018-02-19
Hi, Thank you so much for the help!

Ran
```
[COLOR=#000000][FONT=&quot]sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf[/FONT][/COLOR]
```

Set ipv6 to ignore in network manager
Router was already using WPA2-AES, left unchanged

Set Channel Width to 20mhz in TP-LINK_2.4GHz_6952C9 (was previously set at Auto)
Set Channel Width to 40mhz in TP-LINK_5GHz_6952CA(was previously set at Auto)

ran
```
[COLOR=#000000][FONT=&quot]sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda[/FONT][/COLOR]
```

but I don't think it did anything because 
```
sudo iw reg get
``` still shows 00

However, it has been longer than usual now and no disconnect, so I'm cautiously optimistic. I will check in again tomorrow.

---

### Post by wildmanne39 on 2018-02-19
Did you do the most important part and change your channel in your router to a fixed channel of 40 and make sure your 2.4ghz and 5.0 ghz network names do not have the same name?

I will keep an eye on this thread for your update.

---

### Post by kerry_s on 2018-02-20
try running nm-applet in terminal, you get another wifi applet, click that-> edit connections, select your wifi & edit, under general set the wifi priority, mine was set at 0, i changed it to 1. there are more settings in there you can try, like if you prefer 2.4 or 5ghz, etc... just have a look.

---

### Post by bdmcgraw on 2018-02-21
Solved, thank you everyone

---

