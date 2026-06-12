---
title: "*-network UNCLAIMED on ubuntu 24.04"
date: 2024-10-08
forum: Networking &amp; Wireless
---

### Post by adrien34490 on 2024-10-08
Hi everyone,

I received my brand new laptop yestersay, an ASUS Vivobook, and I partitioned my disk to have both Ubuntu and Windows installed and I'm able to boot both when i restart.
However, on the Linux side my Wi-Fi does not work. After navigating a LOT of forum post for the past day and a half, I've run the command sudo lshw -C network and obtained the following result :

sudo lshw -C network :
```
  *-network UNCLAIMED       
       description: Network controller
       product: MEDIATEK Corp.
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:2c:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm cap_list
       configuration: latency=0
       resources: iomemory:620-61f memory:622c100000-622c1fffff memory:60200000-60207fff
  *-network
       description: Wireless interface
       physical id: 14
       bus info: usb@3:1
       logical name: wlx1c61b47b4de0
       serial: 1c:61:b4:7b:4d:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822bu driverversion=6.8.0-45-generic firmware=N/A ip=192.168.1.159 link=yes multicast=yes wireless=IEEE 802.11
```

The Wireless Interface is a device plugged in an USB port that provides WiFi access but it's far from ideal.

I've also followed the instruction on this post : [URL="https://ubuntuforums.org/showthread.php?t=370108"]https://ubuntuforums.org/showthread.php?t=370108
[/URL]
And I've obtained this link : [https://termbin.com/s9du](https://termbin.com/s9du)

I'm really new to Linux and all of this so if you need more info, feel free to ask and I'll do my best to provide it to you.
I really need this to work because this computer is going to be my "work" computer and i need to have access to internet without the usage of an USB device.

Thank you all in advance.

---

