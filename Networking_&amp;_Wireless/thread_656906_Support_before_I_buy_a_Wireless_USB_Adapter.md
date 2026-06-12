---
title: "Support before I buy a Wireless USB Adapter"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by amunimanghi on 2008-01-03
Hello,

I am planning to buy a wireless USB adapter and want to make sure that it has a Linux driver before I purchase it. 

[Link.](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320107)

Does any one know what driver it uses and if it successfully works? I do have internet access via my Ethernet cable so downloading anything additional before I plug it in is no hassle.
 Thanks in advance.

---

### Post by icheyne on 2008-01-03
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by rustybronco on 2008-01-03
It looks like there are a couple of chipsets used with that device, broadcom 4318 and ralink rt2500 usb?, on the site it lists a download for the ralink drivers, you should be able to compile the drivers for it and or use ndiswrapper, but until you get it you will not know for sure.

also... [http://ubuntuhcl.org/pub/manufacturers.php?category_id=32](http://ubuntuhcl.org/pub/manufacturers.php?category_id=32)

---

### Post by julian67 on 2008-01-03
This one works perfectly with Ubuntu [Safecom SWMULZ-5400]("http://safecom.cn/code/sub/category.asp?prdid=321&subcatid=41")

The driver is included in the kernel, it supports WPA and when you plug it in network manager recognises it immediately.

---

### Post by rustybronco on 2008-01-03
> **julian67 said:**
> This one works perfectly with Ubuntu [Safecom SWMULZ-5400]("http://safecom.cn/code/sub/category.asp?prdid=321&subcatid=41")
 > Support for Microsoft Windows 98SE, Me, 2000, XP, **Linux** and MAC Got to love it.

---

