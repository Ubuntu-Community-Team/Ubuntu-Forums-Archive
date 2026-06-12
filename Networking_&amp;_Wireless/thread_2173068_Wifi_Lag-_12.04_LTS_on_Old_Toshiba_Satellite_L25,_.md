---
title: "Wifi Lag- 12.04 LTS on Old Toshiba Satellite L25, Atheros AR5BMB5"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by eDTQXEx on 2013-09-07
Hi folks,
So I picked up an old but serviceable Toshiba Satellite L25-s1193 laptop at a thrift shop for ten bucks. The computer works great. I installed 12.04 on it earlier today and it went off without a hitch.
It recognizes wifi networks and connects to them just fine, and has great range.
Here's the problem-
when trying to browse the web on wifi only the connection stalls...and stalls..and stalls...
It WILL load pages, the simpler the better; the problem is especially pronounced on sites that require some sort of authentication (Gmail, Amazon, etc.) the connection will time out on these sites.

Browsing with an ethernet cable is zippy and trouble free.
The network card in this dinosaur is an Atheros AR5BMB5.
Any help anyone can give me would be GREATLY appreciated.
THANKS!

---

### Post by wildmanne39 on 2013-09-07
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Thanks

---

