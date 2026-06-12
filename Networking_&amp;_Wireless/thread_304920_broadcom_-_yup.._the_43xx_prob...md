---
title: "broadcom - yup.. the 43xx prob.."
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by tedrampart on 2006-11-22
I've been trying to get wireless on my HP6110ca laptop working, it has a Broadcom 4311 card in it.

so I followed the instructions of this tutorial this morning:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and it didn't work at all.  I also tried the fwcutter method but it said it was IMPOSSIBLE to do.

so I gave up, and turned off my laptop for awhile to work on my bike instead, came back, and now...the wireless card doesn't show up in the Networking applet?!?!?!

it does however show up when I type: sudo ndiswrapper -l

any ideas on how to get wireless working with this?
thanks

---

### Post by Similar on 2007-01-17
did u modprobe the whole thing?

---

### Post by vmikalinis on 2007-01-17
are you getting a light on the laptop at all?

Mine went on as soon as I used fwcutter.

---

### Post by AntiFlash on 2007-01-17
i tried over and over to use ndiswrapper 1.29 and had it working once.  after another fresh install of edgy, i downloaded ndiswrapper 1.34 and it worked after the first shot.  I used this tutorial: 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)
along with the driver from windose (i dual boot, but the cabextract method detailed in the howto works fine).  the key part for you is probably just the modprobe stuff to ensure that the ndiswrapper module is loading at boot.  that is the best how to that I have found in my searching on ndiswrapper over the past few days.  

you'll get it... : )

---

### Post by Doug11 on 2007-01-17
> **tedrampart said:**
> I've been trying to get wireless on my HP6110ca laptop working, it has a Broadcom 4311 card in it.

so I followed the instructions of this tutorial this morning:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

and it didn't work at all.  I also tried the fwcutter method but it said it was IMPOSSIBLE to do.

so I gave up, and turned off my laptop for awhile to work on my bike instead, came back, and now...the wireless card doesn't show up in the Networking applet?!?!?!

it does however show up when I type: sudo ndiswrapper -l

any ideas on how to get wireless working with this?
thanks

I have always found that this one worked for me.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

