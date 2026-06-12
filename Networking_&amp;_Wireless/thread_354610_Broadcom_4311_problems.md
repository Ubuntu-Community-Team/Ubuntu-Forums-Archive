---
title: "Broadcom 4311 problems"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by ziadoz on 2007-02-06
I'm not having much luck getting my wireless card to work on my Compaq Presario V5214 laptop. It has a Dell 1390 miniPCI wireless card, which apparently is a Broadcom 4311 (PCI ID: 14E4:4311). I've been using ndiswrapper 1.35, and this seems to install the drivers correctly. 

The only problem is once I'm done the wireless light goes out, meaning the wireless card is turned off I guess. Is there anyway I can turn it on? Or am I using the wrong method to get this card working? I've tried numerous sets of drivers, most of which seem to say they are installed correctly and the device is present.

Thanks in advance.

---

### Post by EttanA on 2007-02-06
Have you tried the guide in my signature? I had the same problem, the light not being on at all. After I tried the guide, the light started working again, so it might be that. I have a Broadcom 4310. But if your light was on, then off after installation, I don't know what it could be, but you could give it a shot.

Oh, and I also tried the ndiswrapper style first, downloading a driver from a page, cabextracting etc, and it said that both driver and hardware were present, but it still didn't work.

---

### Post by ziadoz on 2007-02-06
I tried fwcutter and the wifi light it on though. Device doesn't find any results in the scan though (in terminal, network manager or wifi-radar). I'm doing this all on a live CD, would this make any difference to if it was fully installed?

---

### Post by liljoe76 on 2007-02-06
well this is the only thing that worked for my 4311
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)
unfortunately my nvidia drivers kill the wireless randomly irq#233 :( hopefully ndiswrapper/feisty's kernal will kill this bug sometime soon..

---

### Post by ddo on 2007-02-06
I just finish setup successfully my Dell D820 by following this Howto:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)
I use ndiswrapper-1.28 as the other versions do not work.
 My Wifi card in Dell DW1390. I download the driver from Support.Dell.com selecting Latitude D820 network download.
 I extract the Driver folder ( bcmwl5.inf and bcmwl5.sys) on a Windows machine and move them over.

---

