---
title: "Authentication of network connection failed"
date: 2020-09-25
forum: Networking &amp; Wireless
---

### Post by aughey on 2020-09-25
20.04 connects for a few seconds then ceases to work completely presenting me with Authentication of network connection failed messages and a triangle with a questionmark. I have windows 10 on the same desktop via a seperate HDD and using the same exact equipment is how I posted this question. The machine uses an edimax card

 SSID:    PLUSNET-6P897H
Protocol:    Wi-Fi 4 (802.11n)
Security type:    WPA2-Personal
Network band:    2.4 GHz
Network channel:    1
Link-local IPv6 address:    fe80::a1b0:7013:2511:ff6d%4
IPv4 address:    192.168.1.2
IPv4 DNS servers:    192.168.1.254
Manufacturer:    Edimax Technology Co., Ltd
Description:    Edimax 802.11n Wireless PCI Card
Driver version:    5.0.57.0
Physical address (MAC):    80-1F-02-C9-0B-E8

---

### Post by grahammechanical on 2020-09-25
I may be wrong but my understanding of "Authentication of the network connection failed" message is that Network Manager cannot connect to the router. I would check:

1) Is the router switched on?
2) Does Network Manager have the password for the router and is the encryption the correct type.
As you are using Windows there is 3) Is WiFi switched off in Windows? 

Regards

---

### Post by aughey on 2020-09-26
The router is never switched off. 20.04 connects initially then gets painfully slow then fails with the authentication message and the triangle with the question mark or three dots. Windows 10 is solid as a rock connecting first time every time no problems. Its the same Edimax PCI card and Plusnet router for both OSes. I still have the CD which came with the edimax PCI card but I dont know if there are any linux drivers on it. Could this be a poor signal issue? I was previously with Talktalk and my desktop had no problems connecting. I recently changed to Plusnet and this has suddenly become an issue

---

### Post by aughey on 2020-09-26
I see the Plusnets Hub Zero is made with Broadcom wifi chips

---

### Post by aughey on 2020-09-30
I installed a copy of Linux Mint Cinnamon 20 on a spare HDD in my desktop. It also failed (at first) to get it online. However it was equipped with a gauage which tells you the strength of the signal from your router. Mine was showing 33% or less/ My Edimax PCI card has a short aerial attached to a cable which was just long enough to place on a window ledge. The signal strength doubled to around 66%. I rebooted into ubuntu and hey presto it was now surfing normally. Hopefully when I| get my hands on a hub one I found for sale on ebay it will improve this again. Touch wood, Problem solved!

---

