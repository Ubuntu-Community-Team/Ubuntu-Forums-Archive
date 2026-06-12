---
title: "wusb11 problem"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by orrins on 2007-06-13
Hello ,
](*,)](*,)I am runnig dapper after having no luck getting a internet connection with feisty. I am new to linux. I tried most every post fix. I am running linux on a separate drive, so I boot to that drive on startup. I can find my adapter in device manager, but I have no option in the networking config. only my built in ethernet card and dial up. I have tried iwconfig but it cannot find any wireless devices. I am using a linksys wusb11 v4 adapter and a dlink dir655 router. Also I am running dsl. Any help would be greatly appreciated.

---

### Post by spd106 on 2007-06-15
It's likely that you will need ndiswrapper.
This card is listed as working on the ndiswrapper site [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/#l](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/#l)
though I don't know where you can get a 64bit driver from, try the Linksys website.

This page will help you install and configure ndiswrapper, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Good luck

---

