---
title: "ndiswrapper kills my laptop"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by fugative on 2007-01-06
I have a HP pavilion with built-in wlan. I got everything up and running using ndiswrapper and the gui frontend thingy, hardware worked but I noticed that it was running really slow. Boot was ok until i got to logon and then the ubuntu slab that shows the booting of nautilus etc sat there forever and then when it does finish the apps take an age to load even the internet is sub dial up with page loading although downloads seem to be ok. I uninstalled ndiswrapper and everything was perky again. 
Question (obviously) how can i fix it. I might try the  fwcutter method of installing my broadcom but i wasn't very happy with it before.

I can't be the only one with this issue

---

### Post by haiku99 on 2007-01-06
try uninstalling it then reinstalling w/ this howto, had worked well for me (on an HP laptop FWIW)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by teaker1s on 2007-01-06
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29")

---

### Post by fugative on 2007-01-06
thanks haiku but that's how i had i had it before with the ndisgtk, easy to use sweet app but still had the dragging on the system.

cheers

---

### Post by fugative on 2007-01-10
The problem seemed to cure itself when i relinquished and allowed my laptop to chose eth1 as the wireless interface and not wlan0 as ndiswrapper wanted but when i set up eth1 to go ad-hoc and connect at start-up it started behaving like a intel 166 running XP. 

help!!!

---

