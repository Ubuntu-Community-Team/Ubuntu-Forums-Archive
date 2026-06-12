---
title: "WMP54G with RT61 drivers"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by josno on 2006-09-21
Hi There,

Just installed Dapper (I presume) and am trying to get the above wireless card to work. 
I've made the drivers according to [this guide](https://help.ubuntu.com/community/Rt61WirelessCardsHowTo), but I can't edit rt61sta.dat using ```
$ vi -b rt61sta.dat
```(it's read only), and I can't run ```
$ iwconfig ra0 essid myssid/mode managed
``` as it says "Set failed on device ra0 ; the operation is not permitted". If I do an iwconfig it shows up as having the RT61 drivers, rt61 appears in the modules list. Anyone have any suggestions?

---

### Post by Ralphthedog on 2006-09-21
Try lupine nickt's kindly compiled drivers/RutilT here, my rt61 is working quite nicely(even with WEP) with these.

[http://www.ubuntuforums.org/showthread.php?t=240669&highlight=ralink+drivers](http://www.ubuntuforums.org/showthread.php?t=240669&highlight=ralink+drivers)

---

### Post by josno on 2006-09-22
Thanks for the reply. I finally got them working with a fix posted [here](http://ubuntuforums.org/showpost.php?p=1407529&postcount=135)

---

