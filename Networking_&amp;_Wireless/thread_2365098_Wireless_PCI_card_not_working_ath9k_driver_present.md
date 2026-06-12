---
title: "Wireless PCI card not working ath9k driver present but no wireless options showing"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by beijco on 2017-07-02
I have recently built a new computer and installed ubuntu 16.04. The wireless pci card i have used is a qualcomm atheros and uses the ath9k driver however no wif options show in the menu. here is the results of lspci : ```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1450
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1452
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1453
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
01:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43bc (rev 02)
01:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43b8 (rev 02)
01:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b3 (rev 02)
02:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
02:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
02:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
02:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b4 (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
07:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
09:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 699f (rev c7)
09:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aae0
11:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 145a
11:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1456
11:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 145c
12:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1455
12:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
12:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Device 1457
```

---

### Post by jeremy31 on 2017-07-02
Welcome to the forums, please see the wireless script link in my signature and post the results

---

### Post by beijco on 2017-07-02
[http://paste.ubuntu.com/25006319/](http://paste.ubuntu.com/25006319/)

---

### Post by beijco on 2017-07-02
Thank you for the quick response

---

### Post by beijco on 2017-07-03
result of dmesg | grep ath :
> [    2.935856]  [<ffffffff85c831ef>] warn_slowpath_fmt+0x5f/0x80[   19.428870] ath: EEPROM regdomain: 0x69
[   19.428871] ath: EEPROM indicates we should expect a direct regpair map
[   19.428872] ath: Country alpha2 being used: 00
[   19.428872] ath: Regpair used: 0x69
[   19.428900] ath: phy0: dma_mapping_error() on RX init
[   19.429032] ath9k 0000:07:00.0: Failed to initialize device
[   19.429084] ath9k: probe of 0000:07:00.0 failed with error -12
[   19.552861] usbcore: registered new interface driver ath3k




---

### Post by jeremy31 on 2017-07-03
Let's see if it works with power management disabled for wifi
```
sudo sed -i 's/2/3/' /etc/NetworkManager/conf.d/*
```

Did wireless work during the install?

---

### Post by beijco on 2017-07-04
No wireless didn't work during install I have tried 2 different pci cards this one also has bluethooth built in that connects via USB on the motherboard and the Bluetooth works

---

### Post by jeremy31 on 2017-07-04
Are there any IOMMU settings in the BIOS of this computer?

---

### Post by beijco on 2017-07-04
Not as far as I can see could it be called something else

---

### Post by beijco on 2017-07-04
Sr-iov ?

---

### Post by beijco on 2017-07-04
It keeps saying failed to initialize ath9k when booting

---

### Post by jeremy31 on 2017-07-04
I am not sure.  Have you tried Ubuntu 16.04 or 16.04.1 to see if the wireless works.  Actually a bug report against package linux should be made, see [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)
Something must be crashing the ath9k module

> **beijco said:**
> It keeps saying failed to initialize ath9k when booting
I have a few different Atheros wifi cards that use ath9k and have never seen that error which is why I thought of IOMMU unless there are other PCI settings in BIOS

---

### Post by praseodym on 2017-07-06
[https://ubuntuforums.org/showthread.php?t=2363730&p=13663053#post13663053](https://ubuntuforums.org/showthread.php?t=2363730&p=13663053#post13663053)

Check this one for IOMMU

---

