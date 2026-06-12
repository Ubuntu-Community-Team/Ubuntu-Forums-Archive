---
title: "Tenda w311mi usb wifi adapter"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by kirtan_parmar on 2014-10-29
hello!
I am a complete beginner to linux. I have just installed ubuntu 14.04.1. However I am unable to use my tenda w311mi wifi usb adapter. I tried to use the CD packaged with the product but i couldn't do anything. Please help me.

---

### Post by Frogs Hair on 2014-10-29
Hello and Welcome

If you have a wired connection on the computer the first thing I would do is open Software & Updates and navigate to additional drivers and check for a driver. If there is a proprietary or other driver available you will need a connection to download it. The list in the link is not complete and based on what adapters and wireless cards users have added to the Wiki so far. The product cd is most likely for use with a Windows operating system.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Edit: It looks like there was driver support for certain models after 12.10.  [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

---

### Post by kirtan_parmar on 2014-10-30
hey,
thank you for your reply. when i switched on the pc this morning to do the steps given in the link but the pc somehow is connected to the wifi but i still can't access the internet.The usb adapter is plugged in. Any help would be great.I am typing this from my laptop.

---

### Post by Frogs Hair on 2014-10-30
I reads like the driver was included as the second link stated . Have you entered the network password? For my home network I have to select the network name from the panel indicator drop-down menu and when done a password dialog box opens . In my case the first is the network and the second is the router.

---

### Post by kirtan_parmar on 2014-10-31
thanks for your help. turned out to be a problem with DNS servers. I had to add 8.8.8.8 and 8.8.4.4 as additional DNS servers

---

### Post by jerald_bucud on 2015-03-20
How can you add dns servers?? Got the same problem

---

