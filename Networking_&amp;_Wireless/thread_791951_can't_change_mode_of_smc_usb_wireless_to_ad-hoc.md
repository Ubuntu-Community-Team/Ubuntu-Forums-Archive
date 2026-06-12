---
title: "can't change mode of smc usb wireless to ad-hoc"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by habib_seif on 2008-05-12
Hi there,

I have a USB SMC Wireless network adapter which worked fine and connected to my ad-hoc home network using ndiswrapper and its windows driver in ubuntu versions prior to 7.04.

Its model number is 2862, its device id is 0707:ee13 and its chipset is prism(according to information on some web pages).

Unfortunately, I can't get it to work in Gusty or Hardy.
My problem is that I set its ip address via NetworkManager but when I want to change its mode to ad-hoc, ubuntu says resource is busy.

After surfing the net, I decided to stop NetworkManager and network adapter, change its mode to ad-hoc, set its ip address and then set it up. In this case, mode change is done successfully but in changing ip address, ubuntu says: operation not permitted.

By the way, I saw the problem in launchpad as a bug for Gusty but WifiDocs wiki page announces that prism chipsets work out of the box in Hardy!

What's your opinion?
Thanks in advance,
Habib

---

### Post by habib_seif on 2008-05-13
just for about 10 hours, my question went to fifth page, interesting forum!!!
Can anyone help??

---

