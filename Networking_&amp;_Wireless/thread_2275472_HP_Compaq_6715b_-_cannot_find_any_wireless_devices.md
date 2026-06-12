---
title: "HP Compaq 6715b - cannot find any wireless devices"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by jonnyrobbie on 2015-04-26
Kubuntu 14.04.2 LiveUSB 64bit, notebook HP Compaq 6715b

```

 kubuntu@kubuntu:~$ uname -r
 3.16.0-30-generic
 kubuntu@kubuntu:~$ lsb_release -a
 No LSB modules are available.
 Distributor ID: Ubuntu
 Description:    Ubuntu 14.04.2 LTS
 Release:        14.04
 Codename:       trusty
 kubuntu@kubuntu:~$ lspci -nnk | grep -iA2 net
 10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
         Subsystem: Hewlett-Packard Company Device [103c:30c2]
         Kernel driver in use: tg3
 30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 02)
         Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1371]
         Kernel driver in use: b43-pci-bridge
 kubuntu@kubuntu:~$ rfkill list all
 0: hci0: Bluetooth
         Soft blocked: no
         Hard blocked: no

```

First I even had problems getting blue LED wlan indicator working at all, but then I found somewhere that I could reset BIOS settings and now it's starting with it enables so thats a start.

Wired ethernet connection works just fine. I tried going through this page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) to troubleshoot my problems.

I tried getting the proprietary STA driver either via Driver manager GUI, or via CLI, none of them worked. Then I tried the open source one, but the package 'firmware-b43-installer' was not even found in the repo. However I managed to install the open source one via the offline method, but it ultimatelly didn't work either.

When I press the touch wlan button, it toggles bluetooth on and off, but Wi-Fi stays cold.

I did run apt-get update, but it is a LiveUSB version and I don't want to commit to installation if it won't work.

---

