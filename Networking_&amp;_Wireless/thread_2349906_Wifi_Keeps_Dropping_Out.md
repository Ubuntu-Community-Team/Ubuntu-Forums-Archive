---
title: "Wifi Keeps Dropping Out"
date: 2017-01-19
forum: Networking &amp; Wireless
---

### Post by july8six on 2017-01-19
**[SIZE=5]Operating System [/SIZE]**
Ubuntu Studio 16.04

[SIZE=5]**System Information**[/SIZE]

[LIST]
[*]**Wireless Adapter:**  Intel    dual Band Wireless Adapter 7260
[*]**Browser:**  Opera [COLOR=#0A0A0A][FONT=Arial]42.0.2393.137[/FONT][/COLOR]& Firefox  50.1.10
[/LIST]

[SIZE=5]**Issue**[/SIZE]
My Intel Wireless Adapter keeps losing Internet connection.  I keep getting a DNS error on my screen. I checked my other devices and only my desktop is having this issue. This issue is also new since installing Ubuntu. I haven't called the company for support yet. How to I maintain a constant Internet connection?

[SIZE=5]**Steps I Have Taken**[/SIZE]
[LIST=1]
[*]Reset the Internet connection.  The Internet works for a while and then it persists.
[*]Changed my DNS settings.  Did not seem to have an effect.
[*]Browsed the web with a VPN.  No effect.
[*]Reset my computer.  No effect.
[/LIST]

[SIZE=5]**Attachments**[/SIZE]
wireless-info.tar.gz

[SIZE=5]**Additional Question**[/SIZE]
Does anyone know a reputable source that is affordable where I can pay for support for my computer? I am having a hard time getting support from companies since I installed Ubuntu. I don't have time to spend days searching for issues to my problems or constantly contacting support for the products I buy and being told I need to upgrade to Windows 10. This is becoming a hassle. I don't want to go back to Windows because of security issues but it seems like Ubuntu is becoming more of a hassle than it is worth and I may have to deal with the security issues.

---

### Post by ajgreeny on 2017-01-19
See the Wireless-Info link in my signature to run the wifi-info script and post back here the results from that. Users more expert in wifi than I will be able to help you more from that.

---

### Post by july8six on 2017-01-20
Thank you for your help.

---

### Post by jeremy31 on 2017-01-20
It appears that wifi power management is enabled, we can disable with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

We may as well set the country code
```

sudo iw reg set US
```
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

Reboot

---

### Post by july8six on 2017-01-24
> **jeremy31 said:**
> It appears that wifi power management is enabled, we can disable with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

We may as well set the country code
```

sudo iw reg set US
```
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

Reboot
Thank you for your help. I thought the steps worked but I am still experiencing the same problem.

---

### Post by Hadaka on 2017-01-24
Hi please open a terminal...ctrl/alt/t... then copy and paste..
```
echo options iwlwifi swcrypto=1 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

*If you continue to have disconnects/dropouts please post a fresh wireless diagnostic report...wireless-info.txt

Thanks.

---

### Post by july8six on 2017-01-26
Attached is the latest wireless-info.txt

---

