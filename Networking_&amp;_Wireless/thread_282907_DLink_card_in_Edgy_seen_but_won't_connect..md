---
title: "DLink card in Edgy seen but won't connect."
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by Monkus on 2006-10-23
Just thought I would run this through this forum. I just upgraded to Edgy, love it, but the wireless is funky. I have a DLink DWL-G650 wifi card with the Atheros chipset. Worked great in Dapper, but cannot connect in Edgy. The thing is this, The card shows up with network monitor, showing 85%-95% signal, but I cannot connect to the internet. It shows up in iwconfig, but not in ifconfig. If I ifup ath0 I get No DHCPOFFERS received. If anyone knows a fix for this, that would be great. Thanks.

---

### Post by Monkus on 2006-10-23
Ok, so now it shows up in ifconfig. This is weird. I did notice that with iwlist scan, it says ath0 is set to Mode: Master and under iwconfig it says ath0 is set to Mode: Managed. I don't know what that means, but it could be of importance.

---

