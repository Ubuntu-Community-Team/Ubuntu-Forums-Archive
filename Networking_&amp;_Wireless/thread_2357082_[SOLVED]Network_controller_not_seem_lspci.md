---
title: "[SOLVED]Network controller not seem lspci"
date: 2017-03-29
forum: Networking &amp; Wireless
---

### Post by odmrtrk on 2017-03-29
hi guys, i don't connected to wifi and rfkill list empty.
i have asus h110m k motherboard and i was update to kaby lake and i am using ubuntu 16.04

lspci
```
00:00.0 Host bridge: Intel Corporation Device 590f (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 5902 (rev 04)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.7 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #8 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)


```

rfkill list all
```
EMPTY
```

Actually my english is very very bad. i'm sorry for this but There was no place I could ask.

---

### Post by chili555 on 2017-03-29
In these specifications, I don't see that this motherboard has any built-in wireless.

[https://www.asus.com/us/Motherboards/H110M-K/specifications/](https://www.asus.com/us/Motherboards/H110M-K/specifications/)

---

### Post by odmrtrk on 2017-03-29
> **chili555 said:**
> In these specifications, I don't see that this motherboard has any built-in wireless.

[https://www.asus.com/us/Motherboards/H110M-K/specifications/](https://www.asus.com/us/Motherboards/H110M-K/specifications/)

Can not my motherboard connect to the wireless network ?

---

### Post by chili555 on 2017-03-29
The motherboard itself, as it comes from the box, does not include a wireless radio and the necessary antennas. The motherboard does have several PCIe expansion slots and you could buy an additional card to add to it. You could certainly add a USB wireless device, as well. Research carefully as some devices are well supported, plug and play, in Ubuntu and some are very difficult.

If you are considering a USB device, several of us here like this one: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/)

---

