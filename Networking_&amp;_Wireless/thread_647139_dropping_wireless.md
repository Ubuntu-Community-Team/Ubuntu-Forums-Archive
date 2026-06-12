---
title: "dropping wireless"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by xanfantasy on 2007-12-22
I have installed the Broadcomm 43xx drivers and firmware and it works fine all except that every so often it just drops. if I roll over it show the wireless with 0% connection but in the drop down it shows 75% or so.After a while the connection comes back just fine. While connected I have full functionality.

details:
  Ubuntu 7.10 "Gusty"
  Build it myself computer
  Linksys G PCI adapter with Broadcomm 43xx chips
  Westell wireless G router with wpa

I went through the search and only turned up out dated versions of Ubuntu but one thing I was wondering is if either 
[I]
sudo /etc/init.d/networking restart[/I]

or

[I]I had the same issue with a WUSB54GV4 adapter in Dapper and Edgy until I went into /etc/network and remarked # iface eth0 in the interfaces file so it would not look for it. Has not dropped out since. Hope this helps.

gtrtoolman[/I]

Would solve the problem. Any help is appreciated.

Xan Fantasy

---

### Post by xanfantasy on 2008-01-04
So does no one have any suggestions?

---

