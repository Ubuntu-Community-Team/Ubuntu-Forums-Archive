---
title: "Internet Keeps Dropping but Wifi Remains Connected to Router"
date: 2016-02-14
forum: Networking &amp; Wireless
---

### Post by cheese3 on 2016-02-14
Hi All,

I am only 8 feet away from the router through a wall and my usb wifi continues to have a strong signal.  Unfortunately the internet will randomly drop and will not reconnect even after plugging the usb wifi into other usb slots.  It does this at random.  For example, yesterday I had a fast connection for an hour and a half and then the internet went down for the rest of the day.  Today my internet is working great but I never know if it is going to shut down.  I know it is the computer/usb because the internet works well on my work laptop and room-mate’s apple devices.  

USB wifi is the panda wireless paou6, which I believe is the realtek RT2870 driver.  I've tried reinstalling the driver but can't figure out how to compile the scripts after I download it to my desktop.

Any advice is appreciated!

Thanks!

Edit: Here's some output from reading another thread:

bob@bob-MS-7817:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7817]
    Kernel driver in use: r8169
bob@bob-MS-7817:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

