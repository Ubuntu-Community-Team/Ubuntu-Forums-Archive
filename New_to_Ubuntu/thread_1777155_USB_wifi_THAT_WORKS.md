---
title: "USB wifi THAT WORKS"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Joel0829 on 2011-06-07
PLEASE BE GENTLE, I am new to LINUX/UBUNTU and learning so pardon the dumb question(s).  So far I have bought (and returned) three USB wireless sticks for my UBUNTU system.  Have tried NETGEAR (N300), BELKIN and LINKSYS. 

I've copied the INF and Sys files to the UBUNTU system and even have been able to get the USB WIFI to install w/o errors via the SYSTEM/ADMINISTRATION/WINDOWS WIRELESS DRIVERS:  bcmwlhigh6 and netr28u are both installed (hardware present: No).

This is getting frustrating.

1) is there a USB WIFI stick that will work "out of the box?"
2) if not, which one will work with some effort by a novice?

Please and thank you.

Joel

---

### Post by frankbooth on 2011-06-07
There's a community documentation of wifi cards here:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Maybe it can guide you into the right direction when choosing a card.

---

### Post by whatthefunk on 2011-06-07
Is plug and play turned on on your system?  You can usually check BIOS to see if it is.

---

### Post by gandaran on 2011-06-07
> **Joel0829 said:**
> PLEASE BE GENTLE, I am new to LINUX/UBUNTU and learning so pardon the dumb question(s).  So far I have bought (and returned) three USB wireless sticks for my UBUNTU system.  Have tried NETGEAR (N300), BELKIN and LINKSYS. 

I've copied the INF and Sys files to the UBUNTU system and even have been able to get the USB WIFI to install w/o errors via the SYSTEM/ADMINISTRATION/WINDOWS WIRELESS DRIVERS:  bcmwlhigh6 and netr28u are both installed (hardware present: No).

This is getting frustrating.

1) is there a USB WIFI stick that will work "out of the box?"
2) if not, which one will work with some effort by a novice?

Please and thank you.

Joel
most wireless adapters work out of the box like atheros and realtek chipsets, broadcom chipsets don't but just need to install the right broadcom drivers, theres no need to go the windows drivers way, if you post the output of typing in terminal
```
lsusb
```
shows what chip the adapter has and we can recommend what driver to install.

---

### Post by desnaike on 2011-06-07
I went with the 74.00 dollar kit works out of the box on U/K/Xubuntu,Mandriva,Opensuse,Puppy,Mepis,PClinuxos.

[http://www.simplewifi.com/usb-wifi-adapters-en/alfa-1000-mw/](http://www.simplewifi.com/usb-wifi-adapters-en/alfa-1000-mw/)

Good luck.

---

### Post by wolfen69 on 2011-06-07
[This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017&Tpk=enuwi-g2") one does, but it is out of stock right now at newegg. But I'm sure others sell it.

---

### Post by cpres32699 on 2011-06-07
I just installed a Netgear WNDA3100 on my brother-in-law's HP desktop running 10.10 using the directions from the following website:

[http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html](http://www.iheartubuntu.com/2010/10/netgear-wnda3100-usb-in-ubuntu.html)

I had to use the second driver they mentioned from the article and had to run the install/uninstall twice to get the driver to stick after a reboot. Otherwise it was painless and works great.

---

### Post by Idaho Dan on 2011-06-07
I've been using a Netgear WG111v2.
Nothing to do, it just works.

---

### Post by Dlambert on 2011-06-07
In my experience, you have to have the card plugged in (USB) before the computer boots.

---

### Post by walt.smith1960 on 2011-06-07
What version of Ubuntu are you using?  I have two WiFi adapters that were NOT plug & play in 10.10.  They could be made to work but they required firmware and/or installer software. Both are plug & play in Ubuntu 11.04 using either Unity or classic desktops. Both are N150 (150 mb./sec) devices, not dual frequency 300 Mb./sec.

Netgear WNA1100 -uses an Atheros ATH9K chipset which seems to have a pretty good reputation in the Ubuntu world
[http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=netgear+WNA1100&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=14454394448619283361&sa=X&ei=G0HuTe2rNMGRgQeA2JSVDw&ved=0CB0Q8wIwAA](http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=netgear+WNA1100&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=14454394448619283361&sa=X&ei=G0HuTe2rNMGRgQeA2JSVDw&ved=0CB0Q8wIwAA)

TrendNet TEW-649UB - uses a RealTek 8192SU chipset.  Nice and small for laptops & netbooks.  [http://www.google.com/search?q=trendnet+tew-649ub&tbs=shop%3A1&aq=0&oq=TrendNet+TEW-649]("http://www.google.com/search?q=trendnet+tew-649ub&tbs=shop%3A1&aq=0&oq=TrendNet+TEW-649")

I would remove all traces of NDISwrapper if you choose either of these devices.  NDISwrapper/windows drivers  are not required with either device.  I'd be concerned about conflicts.

Here is an oldie but has been a goody for me. TrendNet TEW-424UB ver. 3.1.  It's based on the RealTek 8187**B** chipset which has been plug & play with every Ubuntu distro since  9.04, or maybe even 8.10.  I've read of problems with RealTek 8187 chipsets. I don't know if there are 8187 and 8187B or not but this adapter although limited to G speeds (54 mb./sec) has been very reliable.  It has worked without any tinkering on any machine I've used it with.

---

### Post by Joel0829 on 2011-06-09
After returning almost every WIFI USB adapter Staples had I bought from Staples online the BELKIN f5d8053. Arrived today, put the adapter in the USB and wallla, Abragadabra - it worked from the get - go.  

Finally.

Thanks everyone for your input. 
:popcorn:

---

