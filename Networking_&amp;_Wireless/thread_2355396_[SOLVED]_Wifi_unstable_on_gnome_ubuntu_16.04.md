---
title: "[SOLVED] Wifi unstable on gnome ubuntu 16.04"
date: 2017-03-12
forum: Networking &amp; Wireless
---

### Post by tkaramp on 2017-03-12
Hi,

I made a fresh install of Gnome ubuntu 16.04 on my lenovo y410p laptop. Before that I was using Ubuntu 14.04 which was working fine. From the very start I was having a really unstable wifi connection. By unstable I mean that every time I wanted to access something online, it would alternate on having and not having a connection. I had no such problems via ethernet. I've tried to apply some proposed ways of fixing it I saw on other threads but to no avail.

Those are the results of the [COLOR=#000000]wireless script [/COLOR]
[https://paste.ubuntu.com/24164897/](https://paste.ubuntu.com/24164897/)

I would really appreciate your input since I am quite stuck.

Edit: I forgot to mention that I dual boot with windows 10 and there wifi works fine

---

### Post by jeremy31 on 2017-03-12
Can you change encryption on the access point to WPA2-AES, WPA2-PSK, or WPA2 only without plain WPA, WEP, or TKIP.  It might help to move it to channel 9 also

We can disable the wifi power management with
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by tkaramp on 2017-03-12
Wow thanks. That seems to did the trick. Is it possible to explain what was the problem?

---

