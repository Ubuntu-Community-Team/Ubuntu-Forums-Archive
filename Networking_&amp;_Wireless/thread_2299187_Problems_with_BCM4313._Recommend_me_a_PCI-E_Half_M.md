---
title: "Problems with BCM4313. Recommend me a PCI-E Half Mini wireless card."
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by pipe1984 on 2015-10-16
Hi.


Could someone recommend me a PCI-E Half Mini wireless card that has no issues with Ubuntu.
I have a DM1-4310ss laptop HP with BCM4313 wireless card, I have several problems: slow connectivity, stops working sporadically, etc.


There are several workaround but does not stop working well, especially with the F11 button to activate / deactivate.


Recommend me a PCI-E Half Mini wireless card that works well and has no problems with Ubuntu?


If possible double radio, 2.4 and 5 GHz .


I have seen on ebay for example : INTEL WiFi Link 5100 512AN_HMW A / G / N by  4.56€.

Thanks
Regards.

---

### Post by chili555 on 2015-10-16
Are you aware that some and, perhaps all, HP laptops are limited in the BIOS to only accept certain wireless cards?

[http://joshuawise.com/wireless-whitelist](http://joshuawise.com/wireless-whitelist)
> As the authors of this article discovered unintentionally, recent HP laptops (including the HP tc1100 tablet PC and the HP zv5460us desktop replacement) have a wireless whitelist built into the BIOS similar to that found by Matthew Garrett on IBM Thinkpads. In an attempt to replace the built in Broadcom wireless card in Chris' laptop with an Atheros card, we came across this evil firmware hack on our own.

---

### Post by FlashCrash on 2015-10-16
Chili-
Trying to set up a Ubuntu stick w/persistence. Does the same apply to the BCM4312? Read your previous instructions regarding the "UNCLAIMED" network howto but since I am running 14.04 I get different answers when I plug in the 
"lspci -nn | grep 0280" and the "sudo apt-get remove--purge bcmwl-kernel-source". It says it can't find the stuff.....
I'm a newbie, any help appreciated...

---

### Post by praseodym on 2015-10-16
Which Ubuntu version? Which driver? Please show
```
lsb_release -a
uname -a
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
iwlist chan
sudo iwlist scan
dmesg | egrep 'wl|brcm|b43'
```

---

### Post by FlashCrash on 2015-10-16
Ubuntu 14.04, trusty tahr (?), PCI I have in my old eMachines laptop is the Broadcom BCM 4312, don't know anything about the drivers in Ubuntu. I have to jump over to the stick to try the code you sent.....be back in a bit

---

### Post by pipe1984 on 2015-10-19
> **chili555 said:**
> Are you aware that some and, perhaps all, HP laptops are limited in the BIOS to only accept certain wireless cards?

[http://joshuawise.com/wireless-whitelist](http://joshuawise.com/wireless-whitelist)


thanks for the reply.

there is a list of compatible wireless card?

Apart from that , I should install or make my BCM4313 work best ?

Thanks again-

---

### Post by chili555 on 2015-10-20
> **pipe1984 said:**
> thanks for the reply.

there is a list of compatible wireless card?

Apart from that , I should install or make my BCM4313 work best ?

Thanks again-praseodym or I will be glad to help. Please provide the data he requests and we'll proceed. Broadcoms can usually be made to work well.

---

