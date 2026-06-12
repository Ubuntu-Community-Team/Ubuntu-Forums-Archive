---
title: "Broadcom Model #??? Help!"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by joconnorwi on 2007-04-10
Hey friends! I have a Broadcom card in my HP dv9000, how can I find out what model it is? I'm not sure where to look. I checked device manager already, so far I just know it's a [I]802.11 a/b/g   
WLAN[/I]

That's all I got...:confused:

---

### Post by paullew on 2007-04-11
Run ' lspci | grep -i broadcom ' in a terminal - here's the output from mine.

> $ lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by joconnorwi on 2007-04-11
Oh! Jeez...I'm sorry! I meant in *looks around sheepeshly* windows...tryin to get ready to put ubuntu on this bad boy...:(

---

