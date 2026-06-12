---
title: "wlan0 disappears on reboot"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by trondo on 2005-05-26
A couple of days ago, I decided to try Ubuntu 5.04 on my Dell Latitude D600. I installed the driver for the Dell Truemobile 1350 with ndiswrapper following the instructions [on this page](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Ubuntu?PHPSESSID=d0103be3cb07e5da5fd68e156796a5d9). And I have done *ndiswrapper -m*. The install works without errors of any kind, and the wlan appears in the Network Settings. But it disappears when I reboot, so I have to do *modprobe ndiswrapper* to make it reappear.

Does anybody have a solution to the problem?  ](*,) 

PS: Apart from this, Ubuntu seems to be a very good alternative to Fedora Core 3 that I have been using recently.

---

### Post by f.prisson on 2005-05-26
Simply add the module in```
/etc/modules
``` and it will be autoloaded on each reboot.

---

