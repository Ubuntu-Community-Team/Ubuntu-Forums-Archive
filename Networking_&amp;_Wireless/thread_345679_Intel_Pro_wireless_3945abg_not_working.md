---
title: "Intel Pro wireless 3945abg not working"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Jen Fraggle on 2007-01-24
I cannot connect with my wireless card.  I have edgy installed but only did this on Monday, this is my first experience of Linux so am not sure of my way around.  Any help to get this working would be great.  I have downloaded a driver but can't understand the installation instructions.

Thanks for any help

Jen

---

### Post by Floppyjoe on 2007-01-24
Welcome to the Ubuntu community. You'll find many great posts about wireless in this forum. the key is to know what to search for. First of all you need to know the chipset of your wireless interface device. This can be found by the command:
```
lspci
``` for pci cards and:
```
lsusb
```for usb dongles.

Next you would need to search to see if it is supported by Ubuntu Linux with installed drivers. If not supported you could try using [[COLOR="Blue"]ndiswrapper[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") on the windows versions of the drivers: There are documents in the wiki section that would be usefull to follow for ndiswrapper installation and use.

Edit: I downloaded the Linux driver for your card and it looks to me like there is a fair bit of setup work with the driver. If you read the text files that come with the driver they tell you how to set it up. You will need familiarity with the terminal to be able to enter commands. I wish you good luck in your setup. It does not look easy to me.

---

