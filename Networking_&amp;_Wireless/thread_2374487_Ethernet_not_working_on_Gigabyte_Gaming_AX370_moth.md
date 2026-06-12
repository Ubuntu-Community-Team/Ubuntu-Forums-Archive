---
title: "Ethernet not working on Gigabyte Gaming AX370 motherboard"
date: 2017-10-16
forum: Networking &amp; Wireless
---

### Post by average6502 on 2017-10-16
I'm on Ubuntu 16.04 and the ethernet port is not working. Something is recognized as being there, but it does nothing, doesn't even light up when I plug in an internet connection. I have a usb ethernet dongle that i have been using that works fine though. 

I know the lan is realtek, but I can't find info about specifically what kind besides 10/100/1000. 

Does anyone know how to get thees working?

---

### Post by ajgreeny on 2017-10-16
Let's see the output of **lspci** in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by average6502 on 2017-10-16
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1450
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 1451
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1454
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1454
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 59)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1460
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1461
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1462
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1463
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1464
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1465
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1466
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1467
03:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43b9 (rev 02)
03:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b5 (rev 02)
03:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b0 (rev 02)
04:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
04:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
04:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
04:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
05:00.0 USB controller: ASMedia Technology Inc. Device 1343
09:00.0 VGA compatible controller: NVIDIA Corporation Device 1b06 (rev a1)
09:00.1 Audio device: NVIDIA Corporation Device 10ef (rev a1)
11:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 145a
11:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1456
11:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 145c
12:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1455
12:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
12:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Device 1457

```

---

### Post by ajgreeny on 2017-10-17
You do not seem to have an ethernet device that is pci connected which is a bit strange.

Can you now please show us the full output of ```
sudo lshw -sanitize -c network
``` which may help find your ethernet device.

---

### Post by average6502 on 2017-10-18
> **ajgreeny said:**
> You do not seem to have an ethernet device that is pci connected which is a bit strange.

Can you now please show us the full output of ```
sudo lshw -sanitize -c network
``` which may help find your ethernet device.


Sorry for the slow response, I appreciate your help. 

```

  *-network               
       description: Ethernet interface
       physical id: 1
       bus info: usb@5:1
       logical name: enx00249b0e4d48
       serial: [REMOVED]
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ax88179_178a duplex=full ip=[REMOVED] link=yes multicast=yes port=MII speed=1Gbit/s

```

I believe this is the usb adapter I am currently using. But that's all.

---

### Post by average6502 on 2017-10-18
I suppose it's possible that the MB is just defective, though I've never heard of one just not having an ethernet port just not show up at all.

---

### Post by jeremy31 on 2017-10-18
Any IOMMU settings in BIOS that you can change?

---

### Post by average6502 on 2017-10-19
All i see is an enable/disable IOMMU, which doesn't seem to affect this problem at all. 

[code]
sudo lshw -sanitize -c network
[\code]

gives the same output regardless.

---

### Post by Tadaen_Sylvermane on 2017-10-19
I've heard of Ethernet ports dying before. It can happen. Likely the case here. How old is the board? If recent enough you can do an RMA most likely.

---

### Post by oldfred on 2017-10-19
Older Gigabyte AMD based systems all needed IOMMU changes, not sure still an issue with newer ones.

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)

---

### Post by average6502 on 2017-10-28
Sorry for the slow reply, but this is like a month old and I've never had the ethernet port work.

---

