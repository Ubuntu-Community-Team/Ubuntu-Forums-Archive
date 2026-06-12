---
title: "Ubuntu 8.04 + Wireless Intel"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by Tonmac on 2008-04-23
Hi, I have a HP Pavilion DV2317US with a intel Wireless Adapter. Last saturday I installed the Ubuntu 8.04 RC in my Notebook. The Wireless Connection was working perfectly. Yesterday, I Update my Ubuntu 8.04 and now it is very difficult to connect using the wireless connection. I don´t now why.
Somebody had the same problem? How was fixed the problem?

---

### Post by dstew on 2008-04-23
Did you get a new kernel with the update (that is, is there a new menu item in the grub boot menu)? If so, try booting with the older kernel. If it works with the older kernel, but not with the new, file a bug report on [Launchpad]("https://launchpad.net/ubuntu").

If there was no kernel upgrade, see if there are any system error messages. To see the error messages, open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
dmesg
```Post any suspicious lines on the forum.

---

### Post by la3875 on 2008-04-23
I had the same happen to me on my Dell Inspiron 600m last evening too. I don't recall if there was a kernel update but on reboot wireless and sound was gone. May try a repair from the install disk when I get home. Very frustrating because all was working smoothly up to that point and I couldn't be happier with the OS.

Here's what I got trying to troubleshoot:


jeff@jeff-laptop:~$ sudo iwconfig
[sudo] password for jeff:
lo no wireless extensions.

eth0 no wireless extensions.

jeff@jeff-laptop:~$ sudo iwconfig eth1
eth1 No such device

jeff@jeff-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network:0
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:11:43:4c:b6:15
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 ip=10.xx.xx.xx latency=32 module=ssb multicast=yes
*-network:1 UNCLAIMED
description: Network controller
product: PRO/Wireless 2915ABG Network Connection
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:02:03.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=32 maxlatency=24 mi

---

### Post by dstew on 2008-04-23
It seems that the driver for the Intel wireless adapters is not working after the upgrade. I think a bug report is the best idea. Look in dmesg for any lines that the driver may report. Look for the product name if you can find it, usually the driver will report that at the start of its messages.

---

