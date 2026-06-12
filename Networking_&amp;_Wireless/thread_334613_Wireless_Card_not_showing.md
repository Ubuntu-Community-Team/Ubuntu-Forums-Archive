---
title: "Wireless Card not showing"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by gloscherrybomb on 2007-01-09
Hi,

I have recently installed Ubuntu and my wireless card didn't work, so I used the ndiswrapper to install the correct drivers, and it said that they have been successfully installed. However, when I go to System-Admin-Networks no wireless connection shows up on the list, only wired and a modem connection.

Help!

---

### Post by teaker1s on 2007-01-09
you may not have a broadcom chipset but this page has good info configuring a card with ndiswrapper it could just be you need to comment out eth1.
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
also if you just want wireless in gnome and no config files then install
[COLOR="Red"]network-manager-gnome[/COLOR]

make sure that gnome panel
system
administration
networking

is not configured if you wish to use network-manager-gnome

---

