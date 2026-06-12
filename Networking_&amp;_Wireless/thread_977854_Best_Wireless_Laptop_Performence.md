---
title: "Best Wireless Laptop Performence?"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by gijoe3k on 2008-11-10
Hey Guys and Gals

So I am thinking about getting a Mini-PCI wireless card for my ThinkPad 600x. I’m really concerned about getting hibernation/suspend working on this laptop. Do all of the wireless mini-pci cards work well with hibernation/suspend, should I be concerned about this?

Snooping around the forums it seems that the Atheros chipset seems to be the best option for an Ubuntu setup. The Intel cards seem to work for the most part but some need the “ndiswrapper” option,  but that doesn’t sound like the best choice for any situation. 

I found this card on ebay:
[http://cgi.ebay.com/802-11b-g-MINI-PCI-Wireless-Card-4-IBM-ThinkPad-600X_W0QQitemZ250299686110QQihZ015QQcategoryZ31534QQcmdZViewItemQQ_trksidZp1742.m153.l1262](http://cgi.ebay.com/802-11b-g-MINI-PCI-Wireless-Card-4-IBM-ThinkPad-600X_W0QQitemZ250299686110QQihZ015QQcategoryZ31534QQcmdZViewItemQQ_trksidZp1742.m153.l1262)

It has the “AR5005G” chipset, I found this link under the WikiUbuntu:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink?highlight=%28AR5005G%29](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink?highlight=%28AR5005G%29)

In short, what is the best chipset that works great with Ubuntu? Which chipset works great when coming up from hibernation/suspend? Any input would be greatly appreciated, thank you in advance! :grin:

gijoe3k

---

### Post by hahahan on 2008-11-10
gijoe3k,

Don't know if it helps you but I think there is not much difference in behaviour of various wifi-devices regarding hibernate/suspending.
In my case with three differend devices, they are all up when the laptop awakes from hibernate or suspend, but the network is down. I have to run /etc/init.d/networking restart or reconfigure a device manualy.

Just an thought: I would consider to choose a usb device and even better one with a external antenna connector. In case signal strength is low you will be able to choose a better position (usb extention cable) or improve reception by use of a better antenna.

GreetZ Han

---

