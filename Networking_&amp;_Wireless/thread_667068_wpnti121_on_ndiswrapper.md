---
title: "wpnti121 on ndiswrapper"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by dmaksimov on 2008-01-14
i tryed getting my netgear wpnt121 wireless usb adapter to work with ubuntu gusty. well when i added the drivers and rebooted it froze while loading. well i got into the recovery mode and it stopped while it was trying to load the ndiswrapper driver. it said something like invalid irp f56becd0. 0 something like that. i was wondering if anyone could help me.

---

### Post by wieman01 on 2008-01-14
Problem might be that the current version of 'ndiswrapper' which is in the repositories does not support your device or has issues with it. 

User Kevdog has written a nice trouble-shooting guide on 'ndiswrapper' which also explain how to compile the latest version from source. Please take a look at it and post here if you have problems.

[http://ubuntuforums.org/showthread.php?t=574501]("http://ubuntuforums.org/showthread.php?t=574501")

Please also look at my Ralink tutorial (signature) which explains how to use 'ndiswrapper', etc. It's for Ralink based chipsets, however, it should also work for you.

---

