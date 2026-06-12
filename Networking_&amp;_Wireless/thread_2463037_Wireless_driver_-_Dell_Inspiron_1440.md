---
title: "Wireless driver - Dell Inspiron 1440"
date: 2021-06-01
forum: Networking &amp; Wireless
---

### Post by ipsevenenabibas on 2021-06-01
Hi everyone, im new using linux. Sorry for my bad english im a spanish speaker.
I have a Dell Inspiron 1440 laptop, i installed Linux ubuntu 18.04.5 LTS
I think everything is working fine but i realised that the wireless driver is missing.
i run terminal and i write "nmcli" and the wireless network card is "Broadcom Limited BCM4312 802.11 b/g LP-PHY (Wireless 1397 WLAN Mini-card wifi)"
Can anyone teach me how to install that missing driver? im using the ethernet connection for internet but i need the wireless connection.
Thanks.
Franco.

---

### Post by Tadaen_Sylvermane on 2021-06-01
[https://askubuntu.com/questions/408645/ubuntu-12-04-dell-inspiron-1440-wireless-network-does-not-work-with-wireless-net](https://askubuntu.com/questions/408645/ubuntu-12-04-dell-inspiron-1440-wireless-network-does-not-work-with-wireless-net)


I'd install 20.04 first. No sense starting with an old one. I have that exact laptop. When I hit this issue I just changed the WiFi card. Had an extra Intel one sitting about so it was a matter of minutes. Got bluetooth that way as well.

---

### Post by wildmanne39 on 2021-06-01
Moved to Networking and Wireless Sub-Forum.

---

### Post by chili555 on 2021-06-02
> i run terminal and i write "nmcli" and the wireless network card is "Broadcom Limited BCM4312 802.11 b/g LP-PHY (Wireless 1397 WLAN Mini-card wifi)"Please see: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by morrownr on 2021-06-04
You are getting good advice and you do have options. I like the advice about using 20.04 instead of 18.04 and changing out the wifi card to one with an Intel chipset can be relatively easy and cheap. Another option is to get a USB WiFi adapter:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Yes, I know it is a lot of information,

Good luck.

---

