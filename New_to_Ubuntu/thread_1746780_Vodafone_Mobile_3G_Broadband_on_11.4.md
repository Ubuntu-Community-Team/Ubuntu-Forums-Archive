---
title: "Vodafone Mobile 3G Broadband on 11.4"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Ima2k on 2011-05-02
I have a Vodafone Mobile 3g usb broadband modem (Huawei/ZTE K3565-Z) and I am trying to get it to work on Ubuntu. I've never had it working so I decided I'd try with the new release.

I've gone into edit connections, and I have added it there, however I am stuck on this  page - [http://i.imgur.com/wpwTD.png](http://i.imgur.com/wpwTD.png) . I don't know any of those details or what I should enter.

If I remove the device, it tells me it is no longer connected (it wasn't in the first place), and I haven't found anything else.

Some digging on Google uncovered [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

> Manufactured by ZTE. Perhaps usb_modeswitch necessary (see ZTE MF636+).  CD-Mode has Product-ID 0x2000. Takes long time (1min) for detection 

and: usb_modeswitch target ID's: Vendor=0x19d2 Product=0x0031 But that is all I have found. Thanks


edit - alright ,seems all I had to do was change the APN from vodafone.co.nz to pp.internet

---

