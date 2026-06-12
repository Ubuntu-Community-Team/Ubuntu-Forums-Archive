---
title: "Wireless G plus desktop card in dapper"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by trainstroker on 2006-12-07
how do i get it to work in dapper. its this or use windows :(

---

### Post by Sam Lars on 2006-12-07
Have you already tried to configure it?  Do you know what kind of card it is?

---

### Post by FrodoB on 2006-12-07
What is the output of:

lspci -v

or if the card is USB then:

lsusb

---

### Post by FrodoB on 2006-12-07
OK, from what I can see on the web this seems likely to be a ZyDas zd1211 or zd1211b chipset. 

If you are using Edgy it may just work out of the box.

You can test this by inserting the device and running:

iwconfig

If you see the adapter as wlan0 then you should try to configure it. 

If not you will want to install the ZyDas zd1211/zd1211b driver. The instructions for a similar device are at:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Once configured this should be a rather reliable device with Linux, if it is indeed a ZyDas device.

---

