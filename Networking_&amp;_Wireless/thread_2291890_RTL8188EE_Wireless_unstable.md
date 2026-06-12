---
title: "RTL8188EE Wireless unstable"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by chris382 on 2015-08-23
I have Ubuntu 14.04 LTS and i am forced to use an ethernet connection for now. I've tried to install new drivers and change settings but nothing has helped so far. When i try to connect it may connect but the connection is very unstable and disconnects after a short time. Then it trys to reconnect while sometimes it may connect and other times it will just say keep trying to reconnect. Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
I had windows 8 in the past and the internet was fine but it got erased for Ubuntu and now the wifi doesn't work.

---

### Post by praseodym on 2015-08-23
Obviously, you want to connect to xfinitywifi. There are 2 networks in your scan with the same ESSID. So, rename one of those (manual of the router) and change to secure WPA2-AES (CCMP) encryption, not WEP (too insecure).

---

### Post by chris382 on 2015-08-23
I've already tried that and don't think it has anything to do with that because every network i connnect to it does the same thing. Thanks Praseodym.

---

### Post by psfal on 2015-09-05
I'm having that identical issue on my HP 450-a24 slimline desktop with the same wireless network adapter and OS. I'm scanning through the threads looking for an answer with no luck yet

---

### Post by psfal on 2015-09-05
I found mention of this issue being resolved by him replacing his linksys router, I too have a linksys router. I've found no other mention of a working solution. My fiance's Lenovo laptop is also running 14.04 and has no issues, nor does my Lenovo laptop running 12.04. I'm wanting a new router anyway, I'll try that out. Here's the link to the other thread: [http://ubuntuforums.org/showthread.php?t=2289993&highlight=RTL8188EE+Wireless+Network+Adapter](http://ubuntuforums.org/showthread.php?t=2289993&highlight=RTL8188EE+Wireless+Network+Adapter)

---

### Post by psfal on 2015-09-06
Update, my connection has been up for about 7 hours after replacing my old Linksys E2500 router with a new Netgear N900, where previously I couldn't go a half hour without losing my connection. I believe this issue is resolved for me, with the additional benefit of having a stronger wifi signal in my garage now :-)

---

