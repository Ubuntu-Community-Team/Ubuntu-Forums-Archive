---
title: "belkin F5D7051 wireless usb adapter still not being recognised"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by buzzleumas on 2007-07-30
i have a belkin f5d7051 wireless usb adapter 

i have loaded ndiswrapper and copied the two .sys files usb8023k.sys and rndismpk.sys into the /etc/ndiswrapper/bcmrndis folder and have achieved the message below

sam@sam-desktop:/etc/udev/rules.d$ ndiswrapper -l
Installed ndis drivers:
bcmrndis        driver present, hardware present

am still getting this error message when i try to run

sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


i have also tried adding this argument 

BUS==&#8221;usb&#8221;, SYSFS{idProduct}==&#8221;7051&#8221;, SYSFS{idVendor}==&#8221;050d&#8221;, PROGRAM=&#8221;/bin/sh -c &#8216;echo 1 > /sys/%p/device/bConfigurationValue&#8217;&#8221;

to a file called 99-custom.rules in the udev/rules.d folder 

I cannot see where i have gone wrong or what i am missing this has been done from various forum posts as a linux beginner a large amount of this was undertaken with very little understanding

any help greatly appreciated

---

### Post by cypher2k on 2007-09-02
buzzleumas,

After having as much joy as you have had regarding a device based on the weird standard that is RNDIS (damn you MS, just ******* die already....). If you check out the two links below you will see that someone has modified the pre-existing RNDIS support in Linux and allowed it to support RNDIS USB wifi devices. 

[http://ubuntuforums.org/showthread.php?p=3296140#post3296140](http://ubuntuforums.org/showthread.php?p=3296140#post3296140) 

[http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

See how you get on :). Needs a bit of work for one to get it installed, but should be better than the ball ache that getting these devices working with ndiswrapper can be. :)

---

