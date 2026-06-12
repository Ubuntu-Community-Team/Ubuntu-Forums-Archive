---
title: "Unstable wifi connection Lenovo Z510 with Intel Corporation Wireless 7260"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by bananan on 2013-12-28
Hi all,
I've got similar problem on my Lenovo Z510 with Intel Corporation Wireless 7260.
Here are logs from lspci:
```
borys@z510:~$ lspci -nnk | grep -iA2 net08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Lenovo Device [17aa:3803]
	Kernel driver in use: r8169
09:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
	Kernel driver in use: iwlwifi
```
My system is Ubuntu Gnome 13.10 with kernel 3.11.0-14-generic. Network indicator shows that laptop is constantly connected with WiFi but it isn't possible to open any page in browser etc. Connection is working properly for about 10 minutes and then this issue occurs. Then I have to turn WiFi off and on again - after that laptop connects to my WiFi network and everything is fine for about 10 minutes.
I've introduced workaround with added option iwlwifi 11n_disable=1 to iwlwifi.conf file in /etc/modprobe.d/. After this system asks me for password to my WiFi network but doesn't "lost" connection.
All those things happens on battery. When computer is running on AC everything seems to work fine.
Does anyone have any new solutions for this issue?

---

### Post by chili555 on 2013-12-28
> **bananan said:**
> 
```
borys@z510:~$ lspci -nnk | grep -iA2 net
09:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
	Kernel driver in use: iwlwifi
```

All those things happens on battery. When computer is running on AC everything seems to work fine.
First of all, you might look into the updated firmware for your device; check post #24 here: [http://ubuntuforums.org/showthread.php?t=2189035&page=3&highlight=7260](http://ubuntuforums.org/showthread.php?t=2189035&page=3&highlight=7260) 

Second, your issue is probably related to power saving. I suggest you try changing your conf file to:```
options iwlwifi 11n_disable=1 power_level=5
```Reboot and let us hear your report.

---

### Post by codemaniac on 2013-12-28
Hello bananan,

First of all welcome to the Ubuntufourms. I have moved your post to a new thread. Enjoy. ;)

Best Regards,
CM.

---

### Post by bananan on 2013-12-28
> **codemaniac said:**
> Hello bananan,

First of all welcome to the Ubuntufourms. I have moved your post to a new thread. Enjoy. ;)

Best Regards,
CM.

Hi,
After posting I thought it was wrong thread for my issue (different system version and WiFi card in topic) but I was unable to remove my post so I've left it as it was.
Thanks for moving to another thread. ;)
Sorry for that offtopic, again. ;)

chili555, I've changed firmware for now - let's what will happen.

---

### Post by bananan on 2013-12-29
> **bananan said:**
> chili555, I've changed firmware for now - let's what will happen.

It looks like everything works fine after updating firmware to 22.1.7.0 version.
Thanks for help!

---

