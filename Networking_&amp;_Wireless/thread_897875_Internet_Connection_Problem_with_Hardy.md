---
title: "Internet Connection Problem with Hardy"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by gsongpvamu on 2008-08-22
I have been using Gusty for a while, never have problem with internet connection. Well, when I upgrade to Hardy, I can not connect internet with a big chance (usually I can finally get my internet back with serval rebootings).

I use dell laptop vostro 1510, and it is behind a router. I set the configuration in network to "enable roaming mode". When I can not get the connection, I have tried all of the methods I can find in the forum, unfortunately none of them works yet. I list them here

1. sudo dhclient -r
   sudo dhclient eth0

2. sudo /etc/init.d/networking restart

3. ifdown eth0 && ifup eth0

4. Append/add following codes in etc/network/interfaces
   auto eth0
   iface eth0 inet dhcp 

The information of my hardware:

broadcom Corporation BCM4312 802.11b/g (rev 01)
realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

Anyone has similar problems? Suggestions to resolve the problem are highly appreciated. Thanks!

---

