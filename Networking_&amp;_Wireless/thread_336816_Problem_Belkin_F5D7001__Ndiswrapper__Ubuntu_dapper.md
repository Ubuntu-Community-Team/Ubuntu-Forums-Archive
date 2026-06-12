---
title: "Problem Belkin F5D7001 / Ndiswrapper / Ubuntu dapper drake."
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by BeingThere on 2007-01-12
Hi everybody!

I have some problems trying to set it up my wireless card in my desktop computer, I just received by post Ubuntu Dapper Drake and I installed it, I can't set up my internet on it because I have a wireless card that apparently doesn't work.

First of all, I installed ndiswrapper, message with ndiswrapper -l: "the driver is install and the hardware present", then I typed ndiswrapper -m to write configuration file, reboot the machine, but the led of my wireless card was not on. Also, I tried to scan any wireless networks and I couldn't obtain any results.

Any idea about how to sort this? I installed the driver provided by the Belkin Cd-Rom, should I try another one? I'm desperate because I don't want to be stuck in Ubuntu in the beginning anymore!

Thanks to everybody.

---

### Post by spd106 on 2007-01-12
The **ndiswrapper -m** command doesn't always work. Check that you have blacklisted the bcm43xx (if that is applicable), then add ndiswrapper to the /etc/modules file.

You can also load ndiswrapper directly through **sudo modprobe ndiswrapper**

---

### Post by BeingThere on 2007-01-16
Sorted! :) 

Find solution here -> [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=F5D7001](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=F5D7001)

---

