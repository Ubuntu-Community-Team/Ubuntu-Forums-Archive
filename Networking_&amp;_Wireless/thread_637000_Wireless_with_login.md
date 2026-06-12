---
title: "Wireless with login"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by arkros on 2007-12-10
Hi, this is my first time doing wireless on linux. I have my broadcom 43xx working, and it connects fine with my home router. 

     The wireless network at my school requires an additional connection with login and password,  done through what windows describes is a PPPoE connection, which I manually launch after wireless is established on windows. The IP windows connects to for the PPPoE over wireless is 192.168.0.200 .

     Which software do I use to connect to an "unsecured" wireless connection that needs an additional connection to login? I've tried messing with vpnc to no avail. And if nobody can answer this, can somebody tell me the /dev/'x' for my wireless connection, so I can try some dsl software with the device switched or something. Any insight is appreciated.

---

### Post by zyghom on 2007-12-10
iwconfig should show you wlan card
networkmanager or wicd should help you to connect to secured network

---

