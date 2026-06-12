---
title: "Router advice"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by boregard on 2014-10-14
hello, wanting some feedback on a good cheaper router that would be good to flash dd-wrt or tomato on? been doing some google searches but would like to hear from you guys. thanks in advance

---

### Post by weatherman2 on 2014-10-14
TomatoUSB runs beautifully on all of these in my experience:

Linksys/Cisco E2000 (non-simultaneous dual band - either 2.4GHZ or 5GHZ, not both;  Gigabit ethernet)
Linksys/Cisco E2500 (simultaneous dual band - 2.4GHZ and 5GHZ;  10/100 ethernet only)
Linksys/Cisco E3000 (simultaneous dual band - 2.4GHZ and 5GHZ;  Gigabit ethernet)
Asus RT-N16 (2.4GHZ only;  Gigabit ethernet)

DD-WRT runs great on an Asus RT-N13U/B1 (2.4GHZ only, 10/110 only) + 1 USB port.  No Tomato on this router because it's not a Broadcom chipset.  DD-WRT can be flaky on some non-Broadcom based routers but I used one of these for a year as a firewall and it was rock-solid stable.  Maybe cheap to find second hand, and the USB port is great to make a cheap NAS or use as a USB print server.

I have found all of the Linksys routers above for under $10 USD at local thrift stores.  Your mileage may vary of course.  Make sure you get the right power supply - they are all 12V supplies but the E3000 for example needs a 2A power supply; a 1A may work for testing but not under heavy use. 

I think because of a bug in Linksys routers that causes super slow Comcast performance (on stock Linksys firmware) many people may have ditched their old Linksys routers, thinking they were bad; the latest Tomato and DD-WRT builds should fix the problem however.

---

### Post by kurt18947 on 2014-10-14
One caution about routers with USB ports running stock firmware.  I just bought a Netgear WNDR3400 (I think) on Ebay. $12 including shipping. It is Broadcom based and dd-wrt should work. At least with stock firmware the USB can be used for storage but not to connect a printer. I have a USB flash drive plugged in and it works great. There was a Netgear WNDR3700 which has a second USB port sold a couple hours after I bought mine for what would total around $23. Version can also matter. In my case the Netgear WNDR3400 v1 is supported by dd-wrt. V2 of the same router is a word-in-progress and v3 is not even mentioned.

---

### Post by boregard on 2014-10-14
great info, just what i was after. Thanks Guy's

---

### Post by weatherman2 on 2014-10-14
> **kurt18947 said:**
> One caution about routers with USB ports running stock firmware.  I just bought a Netgear WNDR3400 (I think) on Ebay. $12 including shipping. It is Broadcom based and dd-wrt should work. At least with stock firmware the USB can be used for storage but not to connect a printer. I have a USB flash drive plugged in and it works great. There was a Netgear WNDR3700 which has a second USB port sold a couple hours after I bought mine for what would total around $23. Version can also matter. In my case the Netgear WNDR3400 v1 is supported by dd-wrt. V2 of the same router is a word-in-progress and v3 is not even mentioned.

You're right, many routers with the same marketing name come with more than one version and the different versions may have entirely different hardware inside and not be compatible with these open firmwares.  I always check into that before obtaining a new router.

The routers I mention above do not have multiple versions, however, at least that I'm aware of.

The Asus RT-N13U/B1 (I fixed a typo above) is actually version B1 of the RT-N13U but often referred to as "RT-N13U/B1" in marketing for some reason.  I can confirm that the USB port indeed works for a USB printer under DD-WRT, as I set one up for that specific use.  Perhaps USB hardware in routers varies from router to router - not sure.  I always google for info before investing much in a router.

---

### Post by kurt18947 on 2014-10-15
Good job.  It's wise to investigate any prospective hardware purchase.  A windows user can buy about any piece of hardware and expect it to work at least partially - hardware manufacturers don't have much choice but to support Windows if they want to sell their product.  Linux? Not so much.  I do find it interesting that the 800 lb. Gorillas of the hardware business - Intel and HP - seem to be some of the best when it comes to Linux support.

---

