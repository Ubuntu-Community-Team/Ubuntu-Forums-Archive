---
title: "Intermittent internet connection Lubuntu 17.04"
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by matt174 on 2017-07-04
I have no hard drive in my Acer E3-111. I am running with a live USB of Lubuntu 17.04. I can always ping the router and the other computers on the network. Relevant output from lspci:
```

02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

If I plug the computer via ethernet directly to the router, it doesn't work. If I plug it directly into the modem itself, it does work. I have updated network-manager and run sudo service network-manager restart after all changes.

Several things I've tried have seemed to work, but then later the internet is again unavailable. For example:

Changing /etc/network/interfaces from iface lo inet loopback to iface lo inet dhcp
Checking the Fn key for the wireless card
Updating network-manager

One thing I've noticed is that every time the computer restarts, it reverts to iface lo inet loopback

I've also tried changing nameservers, but I don't understand what I'm doing.

Thanks for the help
Matt F

---

### Post by slickymaster on 2017-07-04
*Thread moved to **Networking & Wireless**.*

---

