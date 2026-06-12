---
title: "Ubuntu 10.10 wireless connection"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by lubigbright on 2010-12-22
Hi, y'all !

I am using Ubuntu 10.10 Maverick Meerkat and my wireless connection can be established smoothly, but it is really slow! It takes more than 1min to open Yahoo.com.
Even when the Yahoo webpage is open, it will show "The connection has timed out. The server at [www.yahoo.com](www.yahoo.com) is taking too long to respond" and become unavailable.

Here is the connection information:

Interface:   802.11 WiFi(wlan0)
Harware Address: 70:F1:A1:... (omitted)
Driver: rt2800pci
Speed: 54 Mb/s
Security: None

the connection is "active" and 100%

Is there any problem with the Wireless setting? I have the settings as follows:

<Wireless>
SSID:  XXX Wireless
Mode: Ad-hoc
Band: Automatic

<IPv4 Settings>
Method: Automatic(DHCP)

<IPv6 Settings>
Method: Automatic
(ticked) Require IPv6 addressing for this connection to complete

I am using an HP desktop and the wireless works perfectly fine with Windows 7.  But I prefer to Ubuntu. Can somebody help? 

Thanks heaps in advance!

---

### Post by TeoBigusGeekus on 2010-12-22
Disable ipv6 and see if you notice any difference.

---

### Post by wannacme16 on 2010-12-22
I know when I hook up my wireless connection it automatically defaults to Ad-hoc and in order to access any web pages, last-fm, etc. I have to go in and change from Ad-hoc to infrastructure, IPv4 settings to Automatic (DHCP), IPv6 settings Ignore, wireless security set to my type being that of WPA & WPA 2 Personal. This works for me because the default settings show connection but in reality I cant access anything Internet related. Hope this helps, I'm not tech savvy but I tinker till I find what work's for me. Again hope this helps.

---

