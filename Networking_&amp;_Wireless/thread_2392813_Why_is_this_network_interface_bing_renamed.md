---
title: "Why is this network interface bing renamed?"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-05-25
I found this in the logs 

```
syslog.1:May 25 07:35:02 thelma kernel: [    1.242706] alx 0000:01:00.0 enp1s0: renamed from eth1
syslog.1:May 25 07:35:02 thelma kernel: [   23.984637] alx 0000:01:00.0 enp1s0: NIC Up: 1 Gbps Full

```

There is a legacy definition for some interfaces in /etc/udev/rules.d/70-persistent-net.rules
But none apply to this particular interface.

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:15:58:1e:f7:f4", ATTR{type}=="1", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:10.0/0000:04:08.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:23:2f:4f", ATTR{dev_id}==
"0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

There are two network interfaces.

```
01:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
```

---

### Post by Doug S on 2018-05-25
Things switched to [Predicable Interface Names]("https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/") a few years ago. (if you don't like the reference I gave, just use the search term "Linux Predicable Interface Names" on a search engine for tons of links.)

---

### Post by rsteinmetz70112 on 2018-05-26
I'm aware of that change. I am asking why this particular obsolete interface persists even now.

---

