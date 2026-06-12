---
title: "Intel Centrino Ultimate-N 6300 on Ubuntu 12.04: spotty wifi, requires reboot"
date: 2017-01-23
forum: Networking &amp; Wireless
---

### Post by jwestern on 2017-01-23
Hello,

I am having a recurring problem whereby my wifi connection conks out on my laptop, after having no problems for ~days. If I restart my laptop, the issue goes away. This solution can last days, or a few minutes - there doesn't seem to be any regularity. I recently restarted and have no issues at the moment, and I'm taking this opportunity to post.

I've attached the output of the wireless info script provided by this forum. Is anything amiss? 

Thank you.

---

### Post by Hadaka on 2017-01-24
Hi, please open a terminal..ctrl/alt/t...then copy and paste..
```
echo options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

you have 2 connections with the same ssid  2.4 ghz happy home and 5. ghz happy home, and both have a space in the ssid name
```
happy home:      Infra, <MAC 'happy home' [AC10]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 49 WPA2
 *happy home:     Infra, <MAC 'happy home' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
```
Your connection is most likely trying to roam from one to the other and causing conflict and drops.
I would suggest changing the ssid to something like...  Happy_Home  and Happy_Home_5g  
Thanks.

---

### Post by jwestern on 2017-01-28
Thanks for your response.

I did as you suggest. What will that added line to iwlwifi.conf do? And based on what you've seen, should I be using the 2.4 GHz or 5 GHz connection?

---

