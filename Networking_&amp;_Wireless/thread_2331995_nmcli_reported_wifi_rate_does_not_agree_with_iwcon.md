---
title: "nmcli reported wifi rate does not agree with iwconfig"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by utu2 on 2016-07-27
Using 64-bit Peppermint 7 derivative of Ubuntu 16.04-1 LTS
on Dell 1545 Laptop with Broadcom wifi , Ubuntu 1.2.0 version of NetworkManager,
and Ubuntu version 6.30.223.271-2 of Broadcom-sta-dkms driver..

My Broadcom wifi rate often exceeds 50 Mbps using Verizon FiOS broadband, and iwconfig agrees with Testmy.net reported rate.
nmcli dev wifi presents handsome display of data representing my wifi & neighbors', but shows all rates never exceeding 54 Mbps.

---

### Post by chili555 on 2016-07-27
The numbers come from different places, mean different things and, in some cases, mean nothing. The nmcli command showing your access point and that of your neighbors comes from:```
sudo iwlist scan
```All of these access points are telling you that they can do at least G speeds and, if you have the password and if you connect, they may be able to negotiate more; i.e. N or AC speeds. Every scan sees the same 54 Mbps speeds unless your neighbor has an 802.11B router!

Testmy.net tell you what the *actual* speed is, considering all of the factors including signal strength to the router, ISP speed, etc.

*iwconfig* tells you what the hardware, driver and firmware, if any, think the speed could be under laboratory conditions; no RFI, only one device connected, one inch from the router, perfectly configured MTU, etc. Myself, I don't sit one inch from the router and kick Mrs. Chili off the network when I want to answer a forum post, so *iwconfig* is a rather meaningless figure.

In short, the differences you see are normal and trivial.

---

