---
title: "Odd Wifi Connect Problem"
date: 2018-03-28
forum: Networking &amp; Wireless
---

### Post by LVDave on 2018-03-28
I have a Dell Latitude E5410 running KUbuntu 14.04, with a Broadcom 802.11n wifi adapter. I use the laptop pretty regularly on the road, usually at a Starbucks. The odd problem is network manager makes the RF connection TO the "google starbucks" access point, but the connection times out. Sometimes it will actually connect on the second (or third try--or fourth try), or after I toggle the "wifi kill switch" on the front of the laptop. Today none of these tricks worked, so I swapped out the Linux harddrive to a Win7 drive I carry (for reasons), and I connected first time to the access point. What appears to be happening is the dhcp client is either not asking for an address or isn't receiving it. I've watched the connection with wireshark and I don't see any dhcp oriented transactions. Not sure where to go with this..

---

### Post by praseodym on 2018-03-29
Which device and driver? Please run the wireless-script from the sticky thread and show the outputs

---

