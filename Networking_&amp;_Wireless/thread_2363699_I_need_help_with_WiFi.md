---
title: "I need help with WiFi"
date: 2017-06-13
forum: Networking &amp; Wireless
---

### Post by darkanlord on 2017-06-13
Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe

I changed yesterday to ubuntu OS, and I noticed that the wifi did not call since the installation, appeared the card plus the wifi did not call, could someone help me?

---

### Post by slickymaster on 2017-06-13
*Thread moved to **Networking & Wireless***

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("https://pastebin.com/") yourself.

---

### Post by darkanlord on 2017-06-13
como eu faço pra ativar o script pelo terminal ?

---

### Post by darkanlord on 2017-06-13
[Https://pastebin.com/6quV6qUH](Https://pastebin.com/6quV6qUH) olha ai

---

### Post by slickymaster on 2017-06-13
Please keep in mind that this is a English spoken forum.

---

### Post by chili555 on 2017-06-13
From your paste:> 0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]This suggests that the switch or key combination is set to turn off the wireless radio. Please find the switch and turn the wireless on.

Your wireless appears to have a working driver.

---

### Post by jeremy31 on 2017-06-13
Your wifi shows it is blocked, is there a switch or button you can use to enable wifi?  Also check settings in BIOS

---

