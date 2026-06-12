---
title: "suggestions for best Linux compatible wireless"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Bunyak on 2006-11-26
Just wondering... what's the most compatible of the various wireless router/ wireless pcmcia /wireless pci card thingies.  Wanting to go wireless.  2 computers on Linux, 1 on (egad!) windows xp.

:-)

Thanks

---

### Post by FrodoB on 2006-11-26
For PCI the best bet for, works out of the box, is an Atheros based card. 

Usually something that says 108Mbps, or better yet contains the Atheros or Atheros Super-G name on it.  

An example of a very likely working candidate it this card from TigerDirect, shipping is high, but fast here in the USA. 

See:
[http://www.tigerdirect.com/applicati...485096&CatId=0]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0")

If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.

Warning! Atheros USB devices do not just work in Linux. For USB devices there are not a lot of works out of the box cards that I can recommend, but there are several good ones if you are willing to compile drivers. Here are devices that I have tested myself with good results:

Belkin F5D7050 ver 3000 has a Ralink rt73 device in it and you can compile drivers on Ubuntu. Here are the instructions:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")

Another USB Belkin Device is the F5D7050 ver 4000 which uses the ZyDas zd1211b which has a non-functional drivers in Dapper and Edgy, working instructions are at:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

The F5D7050 ver 3000 is available at Newegg for $19.99 plus shipping at the moment.

[http://www.newegg.com/Product/Produc...82E16833314011]("http://www.newegg.com/Product/Product.asp?Item=N82E16833314011")

at least that is what it was when I purchased it a few weeks back.


These USB devices are usually available at Wal-mart and Best Buy in the USA. Pricing is around $36-$45 dollars, but if they are near by you can take them back, at least at Wal-mart.

If you just want it to work out of the box with pci, pc card, or pcmcia with Ubuntu then Atheros is the way to go.                                                                                __________________

---

### Post by Bunyak on 2006-11-26
Thanky muchos-graciously!  Will definitely check out the Atheros thingie.

---

