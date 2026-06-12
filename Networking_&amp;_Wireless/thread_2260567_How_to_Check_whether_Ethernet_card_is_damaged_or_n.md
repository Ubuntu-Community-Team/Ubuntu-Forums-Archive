---
title: "How to Check whether Ethernet card is damaged or not"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by sumanrocs on 2015-01-12
In my university network local IP is assigned to reach machine in the range 172.22.30.2 - 172.22.31.254 when conected to LAN. My laptop (**HP Pavillion G4 with Ubuntu 14.04 and Windows 8 installed in dual- boot mode**) connects to LAN NIC card glows and some random ip address within the range is assigned.

But now when I connect to LAN, my NIC card glows but the network shows only connecting and it never gets connected in my UBuntu system. I bought a USB to LAN and it works just fine. 

What might be the problem, is my ethernet card damaged?

---

### Post by tgalati4 on 2015-01-12
Does the card work in Windows 8 but not with Ubuntu?

Open a terminal, post the output of:

```
lspci | grep Ethernet
```

---

### Post by sumanrocs on 2015-01-12
lspci | grep Ethernet05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

No same thing happens in Windows 8 too.

---

### Post by Bucky Ball on 2015-01-13
> **sumanrocs said:**
> 
No same thing happens in Windows 8 too.

If the USB is working and the internal card is not working in either Ubuntu or Win8, then that sounds like it may be hardware. Does it work on your connection at home or anywhere else apart from uni?

---

### Post by wyliecoyoteuk on 2015-01-13
It might be auto-negotiation failure. Sometimes happens, especially with Gigabit switches and 10/100 NICs, or vice versa
You might need to lock the speed to 100Mbit

[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

