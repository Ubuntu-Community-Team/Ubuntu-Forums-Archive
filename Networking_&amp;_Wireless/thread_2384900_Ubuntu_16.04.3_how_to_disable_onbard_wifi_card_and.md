---
title: "Ubuntu 16.04.3 how to disable onbard wifi card and changer interface name to wlan0"
date: 2018-02-13
forum: Networking &amp; Wireless
---

### Post by longvu183 on 2018-02-13
hi everyone i am newbie
my laptop install Ubuntu 16.04 
ifconfig my network card name not show wlan0  
my onbard network card name show wlp7s0 or use usb wifi network card name  wlx8416f919c0a6 Link encap

please help me how to disable onboard wifi card wlp7s0
and rename USB wifi card name  wlx8416f919c0a6 Link encap to wlan0

thank a lot

---

### Post by Hadaka on 2018-02-14
Hi, the renaming of the ethernet interfaces started with Ubuntu 15.04.
Is there a reason you dont like the current lan wifi name ?
and before the change the usb would have been wlan1 not 0.
Please insert the usb wifi module and post the output of..
```
ifconfig
lspci -n |awk '/0280/{print$3}'
```
thanks

---

### Post by chili555 on 2018-02-14
I think there are good and valid reasons for the change to persistent naming and I think most of us should just get used to it. After all, there is nothing magic about wlan0 versus wlp3s0 versus what it was about ten years ago for some wireless interfaces, eth1 or what it was for some other wireless interfaces about 15 years ago, wifi0.

[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

Do I think it will change again in about ten years? Yep, things always change. The book that I purchased in 2001, *Practical Linux,* is mostly obsolete and useless, except as an interesting antique.

I don't understand why some people want wooden wheels on their sleek, black BMWs, either: [http://www.jakesctp.com/images/WAGON%20WHEELS/RUBBER%20WAGON%20WHEEL.jpg](http://www.jakesctp.com/images/WAGON%20WHEELS/RUBBER%20WAGON%20WHEEL.jpg)

I hope that my comments will not be seen as too blunt.

---

