---
title: "Need Wireless Cad Advice"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by srafx on 2006-11-23
I currently have a card that I can only get to work with the bcm43xx driver, which times out...thats another thread.  

I know about this list: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

But can anyone tell me from personal experience how their card worked?  I would like to buy a card around the price of like 20-40 dollars and would love for it to plug and play in Edgy.

---

### Post by cantormath on 2006-11-23
> **srafx said:**
> I currently have a card that I can only get to work with the bcm43xx driver, which times out...thats another thread.  

I know about this list: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

But can anyone tell me from personal experience how their card worked?  I would like to buy a card around the price of like 20-40 dollars and would love for it to plug and play in Edgy.

Broad com (bcm43xx driver) is evil.  I have done really well with Oronico and atheros.

---

### Post by srafx on 2006-11-23
> **cantormath said:**
> Broad com (bcm43xx driver) is evil.  I have done really well with Oronico and atheros.

Yeah, very evil.  Do you happen to have a link to a page that would have provide install instructions for either one of those drivers?  I currently use network manager and the bcmxx43 with WAP.  

I tried ndiswrapper, but my card just doesnt work, its a little off from any on the list that work.

I'm using a linksys WMP54GS but the important is below, the 4318
and specific: 
08:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by FrodoB on 2006-11-23
What type of device do you want? PC Card (PCMCIA) or USB?

---

### Post by srafx on 2006-11-23
> **FrodoB said:**
> What type of device do you want? PC Card (PCMCIA) or USB?

This is for my desktop so I would either want a pci card or usb.  What ever would be easiest to get up and working (plug and play).  I would love 54mb/s + too. :)

---

### Post by FrodoB on 2006-11-23
For PCI the best bet for, works out of the box, is an Atheros based card. 

Usually something that says 108Mbps, or better yet contains the Atheros or Atheros Super-G name on it.  

An example of a very likely working candidate it this card from TigerDirect, shipping is high, but fast here in the USA. 

See:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0)

If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.

For USB devices there are not a lot of works out of the box cards that I can recommend, but there are several good ones if you are willing to compile drivers. Here are devices that I have tested myself with good results:

Belkin F5D7050 ver 3000 has a Ralink rt73 device in it and you can compile drivers on Ubuntu. Here are the instructions:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")

Another USB Belkin Device is the F5D7050 ver 4000 which uses the ZyDas zd1211b which has a non-functional drivers in Dapper and Edgy, working instructions are at:

[https://help.ubuntu.com/community/Wi...cs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

The F5D7050 ver 3000 is available at Newegg for $19.99 plus shipping at the moment.

[http://www.newegg.com/Product/Produc...82E16833314011]("http://www.newegg.com/Product/Product.asp?Item=N82E16833314011")

at least that is what it was when I purchased it a few weeks back.


These USB devices are usually available at Wal-mart and Best Buy in the USA. Pricing is around $36-$45 dollars, but if they are near by you can take them back, at least at Wal-mart.

If you just want it to work out of the box with Ubuntu then Atheros is the way to go.

---

### Post by srafx on 2006-11-26
> **FrodoB said:**
> For PCI the best bet for, works out of the box, is an Atheros based card. 

Usually something that says 108Mbps, or better yet contains the Atheros or Atheros Super-G name on it.  

An example of a very likely working candidate it this card from TigerDirect, shipping is high, but fast here in the USA. 

See:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485096&CatId=0)

If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.


Great advice!  I went out to Circuit City and found the only one with "Atheros" on the box.  It ended up being a Netgear WG311T:
[http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx](http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx)

Now, when I first plugged it in the card didnt work.  As I found out by searching the forums I needed to install linux-restricted-modules and that brought back the ath0 connection.  I think mine got messed up from installing the nvidia drivers.  I also had to add nv to the blacklist, but that is another problem and another thread :).

If you would first install linux, buy this card, it will auto detect on ath0.  Thanks again for the wonderful advice!

---

