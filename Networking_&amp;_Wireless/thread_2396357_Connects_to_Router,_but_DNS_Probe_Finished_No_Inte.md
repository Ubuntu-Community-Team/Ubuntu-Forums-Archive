---
title: "Connects to Router, but DNS Probe Finished No Internet"
date: 2018-07-14
forum: Networking &amp; Wireless
---

### Post by gregory7 on 2018-07-14
It is 18.04 and it works perfectly at home, but now I've gone on holiday and it doesn't connect to the router, though this other computer and two phones connect fine. So why? And how can I get it to connect? I've tried two browsers, same problem.

---

### Post by gregory7 on 2018-07-14
i tried to get a wireless-info text file to run but nothing happened

---

### Post by jeremy31 on 2018-07-14
Can you connect to wifi using a phone and use USB tethering to the computer?

---

### Post by gregory7 on 2018-07-14
I even started the computer with a live USB and connected again to the router there. Still no luck - so what is the conclusion? Even if it is a new install it cannot connect to a router which three devices are easily connecting to? I was going to re-install... saved myself the trouble!!

---

### Post by gregory7 on 2018-07-14
> **jeremy31 said:**
> Can you connect to wifi using a phone and use USB tethering to the computer?

Nope, I tried that too

---

### Post by jeremy31 on 2018-07-14
Go into Network Manager settings, IPv4 and see if putting 8.8.8.8 in additional DNS helps

---

### Post by gregory7 on 2018-07-14
I should say that I am in China, so any google sites don't work unless I have a vpn, and it doesn't connect at the moment, not surprisingly

---

### Post by gregory7 on 2018-07-14
> **jeremy31 said:**
> Go into Network Manager settings, IPv4 and see if putting 8.8.8.8 in additional DNS helps

maybe another site which is not blocked such as bing or baidu?

---

### Post by jeremy31 on 2018-07-14
What shows in terminal for ```
iwconfig; ifconfig
```

---

### Post by gregory7 on 2018-07-14
> **jeremy31 said:**
> What shows in terminal for ```
iwconfig; ifconfig
```

See attachement

---

### Post by jeremy31 on 2018-07-14
This will turn power management off and restart networking
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by gregory7 on 2018-07-14
> **jeremy31 said:**
> This will turn power management off and restart networking
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

I gave that a go, but still the same result, no connection - server not found etc. :(

---

### Post by gregory7 on 2018-07-14
I now get an activation of network connection failed when i restart, I don't know if that is important

---

### Post by gregory7 on 2018-07-14
Ah, the internet works!!

---

### Post by gregory7 on 2018-07-14
I needed to restart - i thought it wouldn't need it - i got that message but it works! yay! Yr wonderful - I love you and your many children to come!! :D

---

