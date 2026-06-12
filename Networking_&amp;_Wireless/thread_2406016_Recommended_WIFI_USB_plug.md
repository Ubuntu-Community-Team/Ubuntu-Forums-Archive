---
title: "Recommended WIFI USB plug?"
date: 2018-11-14
forum: Networking &amp; Wireless
---

### Post by timswait on 2018-11-14
I need to get a desktop PC onto WiFi (using tethering from my phone - for some reason USB tethering doesn't work on this phone, it did on my old one, but WiFi tethering does work). So I got a very cheap (about £5 on ebay) tiny USB WiFi receiver. It's hardly any bigger than the USB plug. However it didn't work plug and play, it turned out to have a Ralink MT7601U chipset which isn't natively supported so I followed these instructions to try to set it up [https://askubuntu.com/questions/457061/ralink-mt7601u-148f7601-wi-fi-adapter-installation#554278]("https://askubuntu.com/questions/457061/ralink-mt7601u-148f7601-wi-fi-adapter-installation#554278")
Got to the last line of the instructions ```
sudo modprobe mt7601Usta
``` and when I entered that the computer froze completely, not even the mouse would work. Had to hard shutdown it, but it wouldn't restart without hanging. When I took the USB WiFi plug out then it would boot up (phew!) but then I tried plugging it in again and it instantly froze completely again.
So can anyone offer any suggestions for (a) making this work or (b) recommend a similar one that's natively supported and doesn't need me to install any drivers?
Thank you.

---

### Post by chili555 on 2018-11-14
I haven't seen any mt7601u device work successfully in many years. I think it's a dead end.

Please check here: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

### Post by makhtc on 2018-11-17
Using Tp-link from 2 years and still going strong.

---

### Post by timswait on 2018-11-22
makhtc: what model TP-Link are you using? Was it plug and play or did you have to build and install drivers? Are there any of these things that do work plug and play?

---

### Post by jeremy31 on 2018-11-22
I have a TP Link TL WN722N 150 Mbps version 1 that works well, plug and play for quite a while with Ubuntu

---

### Post by timswait on 2018-11-22
Thank you Jeremy. If possible I'd prefer one of the tiny ones, I don't need a big antenna on it. Does anyone know of a little one that's plug and play?

---

### Post by jeremy31 on 2018-11-22
You could try the WN723N but the small size will limit the distance between you and router.  The kernel module is still in staging

[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-adapter-gnu-linux-tpe-n150usb](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-adapter-gnu-linux-tpe-n150usb) uses the same chipset as the WN722N so that would work

---

### Post by timswait on 2018-11-22
Distance to the router (my phone!) is no issue at all. How about WN725N, do you know if that's also the same chipset? It seems easier to get hold of.

---

### Post by jeremy31 on 2018-11-22
The WN725N seems to be supported by the r8188eu module [https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2)

---

### Post by timswait on 2018-11-22
Cracking, I'll give it a try and report back.
Cheers

---

### Post by him610 on 2018-11-22
Works out of the box:

Edimax EW-7811Un 150Mbps 11n Wi-Fi USB Adapter, Nano Size Lets You Plug it and Forget it, Ideal for Raspberry Pi / Pi2, Supports Windows, Mac OS, Linux (Black/Gold) [https://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1")

TP-Link TL-WN823N N300 Mini USB Wireless WiFi network Adapter for pc, Ideal for Raspberry Pi
[https://www.amazon.com/gp/product/B0088TKTY2/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B0088TKTY2/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1")

---

### Post by scottbomb on 2018-11-23
I use the Alfa Atheros AR9271. It worked out of the box for me. I used it previously on a Raspberry Pi and it's now connected to a full-sized box running 16.04.

---

### Post by timswait on 2018-11-27
The TP-Link WN725N I just bought does indeed work perfectly, plug and play, no messing about, the instant I plugged it in WiFi networks appeared in the network manager, great! :-) Problem solved, I'm posting this through it!

---

