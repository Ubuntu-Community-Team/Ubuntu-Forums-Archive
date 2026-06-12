---
title: "Ubuntu 16.04 wireless problem AR9485"
date: 2016-04-25
forum: Networking &amp; Wireless
---

### Post by ublintu on 2016-04-25
Hi,
I just made a fresh install Ubuntu 16.04 on a Lenovo G500. After the install, when I first connected to the wireless internet, when I typed  password in I had no problem with the connection. When I rebooted, I couldn't connect to the internet again.
I reinstalled ubuntu 16.04 (a few times...) and I always had the same problem. So far the only solution for the problem is, that when I log in to the computer, I can't connect to the internet  > edit connections > edit wi-fi connection > type a wrong password in, save. When I connect to the wireless, it will ask the correct password. When I type in the right one, it's working!
How can I solve this problem? 

lspci -nnk | grep -A2 0280
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Lenovo AR9485 Wireless Network Adapter [17aa:3218]
	Kernel driver in use: ath9k

---

### Post by wpa-psk on 2016-04-26
Try putting 

```
options ath9k nohwcrypt=1
```

into /etc/modprobe.d/ath9k.conf

and setting your country code in /etc/default/crda

Does that help?

---

