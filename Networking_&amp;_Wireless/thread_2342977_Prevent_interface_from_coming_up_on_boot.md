---
title: "Prevent interface from coming up on boot"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by postcount on 2016-11-11
I have a wireless network interface, **wlp2s0**, that I do not want "up" at any time.  What is the proper way (in Ubuntu 16.04) to prevent it from being brought up during boot?

---

### Post by wildmanne39 on 2016-11-11
Please post the output of:
```
lspci -nnk | grep -iA2 net
```

---

### Post by postcount on 2016-11-12
```

02:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
    Subsystem: ASUSTeK Computer Inc. RT2790 Wireless 802.11n 1T/2R PCIe [1043:130f]
    Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
--
04:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Gigabyte Technology Co., Ltd GN-WP01GS [1458:e934]
    Kernel driver in use: rt61pci

```

---

### Post by SeijiSensei on 2016-11-12
I use Kubuntu, and the NetworkManager client has a box in the General tab for "Automatically connect to this network when it is available".  If you have an equivalent option in vanilla Ubuntu, see if unchecking that works for you.

---

### Post by wildmanne39 on 2016-11-12
You should be able to uncheck the automatically connect to this network but you can also blacklist the driver since you say you never want to use it.

To blacklist do the following it is your choice how you want to do it of cource.
```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by postcount on 2016-11-13
Thank you for the replies.  Wild Man's suggestion of blacklisting the driver will do the trick, and I appreciate the help.

---

### Post by wildmanne39 on 2016-11-13
Your welcome!

---

