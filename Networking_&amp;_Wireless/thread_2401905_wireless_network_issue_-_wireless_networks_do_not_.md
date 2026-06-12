---
title: "wireless network issue - wireless networks do not show"
date: 2018-09-24
forum: Networking &amp; Wireless
---

### Post by samster.ve on 2018-09-24
Hello,

I am using a Lenovo legion Y520 with realtek rtl8821ae product and have just installed 16.04.5, 

when i log in i have no wireless network connection. even when i enable wifi there is no networks that show up.

Ive downloaded the latest driver rtlwifi_new from github page and followed all the commnds to make and install them but nothing shows up in my wireless adapters page on systems and settings

here's the output of sudo lshw -class network:

```
*-network DISABLED      
       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 60:14:b3:70:06:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-34-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:140 ioport:4000(size=256) memory:a4300000-a4303fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: 54:e1:ad:6a:67:b8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation ......... etc 
```

Please help. Ive tried several things and frustrated with zero outcome

---

### Post by jeremy31 on 2018-09-24
Try ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot

---

### Post by samster.ve on 2018-09-24
Jeremy ... you are a magician - thanks so much. It works well now

can you help me understand how this fixed the issue

---

### Post by jeremy31 on 2018-09-24
A few years ago, Lenovo changed how the BIOS reported a hard block on wifi and the kernel maintainers use a quirks table for these devices.  Until a new kernel includes your model in the table you need to have ideapad-laptop blacklisted

---

### Post by samster.ve on 2018-09-24
Thank you

---

