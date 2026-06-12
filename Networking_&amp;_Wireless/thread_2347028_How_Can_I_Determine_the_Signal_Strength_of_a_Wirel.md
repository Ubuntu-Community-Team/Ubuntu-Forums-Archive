---
title: "How Can I Determine the Signal Strength of a Wireless Connection?"
date: 2016-12-20
forum: Networking &amp; Wireless
---

### Post by matteoraggi on 2016-12-20
Hi, I would like to check the wifi signal strenght trough terminal, how to...?

---

### Post by SeijiSensei on 2016-12-20
sudo iwlist scan

It will report a lot of data about each visible access point including signal strength and a "quality" rating.

---

### Post by DuckHook on 2016-12-20
You might also find useful the ncurses app *wavemon*:```
sudo apt install wavemon
```

---

### Post by chili555 on 2016-12-20
You might also try:```
sudo nmcli dev wifi list
```

```
*  SSID        MODE   CHAN  RATE       SIGNAL  BARS  SECURITY 
   GBR1        Infra  11    54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2     
*  GBR5        Infra  149   54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2     
   nx2.4       Infra  1     54 Mbit/s  54      &#9602;&#9604;__  WPA2     
   MAHB Wi-Fi  Infra  6     54 Mbit/s  37      &#9602;&#9604;__  WPA2     
   Portal      Infra  11    54 Mbit/s  32      &#9602;&#9604;__  WPA2     
   MAHB Wi-Fi  Infra  11    54 Mbit/s  27      &#9602;___  WPA2     
   nx5g        Infra  36    54 Mbit/s  24      &#9602;___  WPA2     
```The asterisk * indicates the SSID to which I'm currently connected.

---

