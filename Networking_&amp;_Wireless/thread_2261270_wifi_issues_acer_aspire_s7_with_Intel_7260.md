---
title: "wifi issues acer aspire s7 with Intel 7260"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by tomay2 on 2015-01-17
Hello, I am having intermittent wifi issues with Ubuntu 14.04 on an Acer Aspire s7 and Intel Corporation Dual Band Wireless-N 7260. The connection is weak, and I get frequent disruptions and diconnections.  I understand this is a common issue with this setup. 

I've attached results from running the wireless script recommended by varunendra and referenced here:
[http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)

[ATTACH]259327[/ATTACH]

---

### Post by praseodym on 2015-01-18
Change the encryption mode in your router to pure WPA2-AES (CCMP), not mixed mode WPA/WPA2. Additionally, you could deactivate the power management:
```

sudo iwconfig wlan0 power off
```

---

