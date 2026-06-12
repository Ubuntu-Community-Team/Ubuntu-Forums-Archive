---
title: "3c59x and wireless not working"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by rahmans on 2008-08-13
Hi,

Thanks for reading my post. I'm quite new to Linux and need your help.

I have a problem with my installation of Ubuntu Linux. I can see my eth0 and wlan0 cards and its mac address but they cannot get an IP address. I've tried:-

sudo ifconfig eth0 up
sudo ifconfig wlan0 up
sudo dhclient eth0 (it states its sleeping)
sudo dhclient wlan0 (it states its sleeping)

sudo lshw -C network (it shows me all my cards and its mac)

When i do a ifconfig it states my ip as 169.254.8.108 and subnet 255.0.0.0. This is incorrect as my router ip starts from 192.168.0.1 (router) etc. I've even added the mac of my eth0 in my router and gave it an static ip and did the same address on linux but it still does not work.

I've even tried to reset my NetGear router, I disabled DHCP and then re-enabled it. Rebooted my linux box and still nothing. 

Please help. The only reason I'm trying to get this to work is to enable me to use samba to share with windows and vice versa.

Thanks in advance

---

### Post by Iowan on 2008-08-13
The 169.254.X.X address sounds like **avahi** providing an address in place of failed DHCP attempt. I'm trying to search for threads where this got solved...

---

