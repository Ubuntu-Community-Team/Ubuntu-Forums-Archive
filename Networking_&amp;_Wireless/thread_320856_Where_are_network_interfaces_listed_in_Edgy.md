---
title: "Where are network interfaces listed in Edgy"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by abhaysahai on 2006-12-18
Hi,
My Dlink 502T USB connection was working with Dapper, I did an internet upgrade to Edgy ( on the same connection) and Edgy would not recognize my USB connection. I have to use Ethernet cable to connect. 
I tried checking the configurations files, but could not find the file where the USB mac address is mapped to one of the interfaces. 
The files /etc/network/interfaces lists many interfaces, but most are not present. 

Please tell me the file which maps the USB/ Ethernet MAC address to the interface so that I can again connect to intenet using the USB port. 

Regards,
Abhay

---

### Post by hal10000 on 2006-12-18
Please post the output from the commands [COLOR="Red"]lsusb[/COLOR] and [COLOR="Red"]iwconfig[/COLOR]. Do you know the chipset of your wlan-device?

---

