---
title: "Wireless Card Purchase Advice"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by monkeywork on 2006-12-04
Hi,

Current network 802.11G (Linksys Router) - Ubuntu PC is running on wired network however I will need to move the machine to a part of the house that wiring isn't easily done.  Was wondering what's the most linux friendly PCI wireless card - or what the general favorite is around here.  I basically want to keep the amount of effort involved in setting it up the same as what was required for my wired nic (aka none).

Thanks
MKWK

---

### Post by FrodoB on 2006-12-04
For PCI you want an Atheros card.

---

### Post by FrodoB on 2006-12-04
For PCI the best bet for, works out of the box, is an Atheros based card.

Usually something that says 108Mbps, or better yet contains the Atheros or Atheros Super-G name on it.

Here are some example Atheros devices:

DWL-G510: (Atheros)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368)

DWL-G520: (Atheros)
[http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869](http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0)


Netgear WG311T: (Atheros)
[http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx](http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx)
[http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=8-1/qid=1165274426/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics](http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=8-1/qid=1165274426/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics)
[http://www.newegg.com/Product/Product.asp?Item=N82E16833122134](http://www.newegg.com/Product/Product.asp?Item=N82E16833122134)


D-Link DWL-G650: (Atheros)
[http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6](http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367)

If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.

Warning! Atheros USB devices do not just work in Linux. For USB devices there are not a lot of works out of the box cards that I can recommend, but there are several good ones if you are willing to compile drivers. Here are devices that I have tested myself with good results:


USB Devices:

Belkin F5D7050 ver 3000 has a Ralink rt73 device in it and you can compile drivers on Ubuntu. Here are the instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")

Another USB Belkin Device is the F5D7050 ver 4000 which uses the ZyDas zd1211b which has a non-functional drivers in Dapper and Edgy, working instructions are at:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

The F5D7050 ver 3000 is available at Newegg for $19.99 plus shipping at the moment.

[http://www.newegg.com/Product/Product.asp?Item=N82E16833314011](http://www.newegg.com/Product/Product.asp?Item=N82E16833314011)

at least that is what it was when I purchased it a few weeks back.

Zonet ZEW2500P works out of the box. This device is about $25 at NewEgg:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833130111](http://www.newegg.com/Product/Product.asp?Item=N82E16833130111)

It does have a slow startup, it takes about 12-15 seconds for the device to start working after a bootup or insertion of the device in Edgy. I suspose it is dowloading and starting firmware.

It uses a Ralink rt2570 series chipset and kernel module.

It works well with WEP, I cannot comment upon WPA as I have not yet tried it.

These USB devices are usually available at Wal-mart and Best Buy in the USA. Pricing is around $36-$45 dollars, but if they are near by you can take them back, at least at Wal-mart.


If you just want it to work out of the box with pci, pc card, or pcmcia with Ubuntu then Atheros is the way to go.

---

