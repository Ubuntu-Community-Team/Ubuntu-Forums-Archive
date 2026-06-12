---
title: "Hp dv2164eu lubuntu 14.04 wireless adapter not recognized"
date: 2016-03-16
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2016-03-16
Hi,
I installed lubuntu on old hp dv2164eu. Lubuntu does not recognize any wireless adapter and I cannot use it. I followed this guide [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported). However, both the commands
```

lsusb

```
and
```

lspci -v

```
do no show any wireless adapter. The notebook has hard switch for wireless adapter, but if I switch it nothing happen.
Thank you

---

### Post by howefield on 2016-03-17
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by erotavlas on 2016-03-19
I investigated a lot without success.
This is the output of lsubs
```

   Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
 Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Flash Drive
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```
while this is the output of lspci
```

   00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
 00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
 00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
 00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
 00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
 00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
 00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
 00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
 00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
 00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
 00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
 00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
 00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
 00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
 00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
 00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
 00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
 00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
 00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
 00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
 00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
 00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)

 00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

 00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
 00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
 00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

 03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
 03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
 03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
 03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
  
```
The notebook should have a broadcom LAN adapter plus an intel pro wireless adapter. Both lsusb and lspci do not recognize my card.
Any suggestions?
Thank you

---

### Post by erotavlas on 2016-03-19
I decided to open the slot of the notebook that contains the wifi adapter and I discovered that my PC has a broadcom 4311 adapter. I followed all the steps here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx), but the adapter does not work.
Moreover, the command 
```
lspci -vvnn | grep -A 9 Network 
```
returns empty result.
What can I do? The adapter worked well up to two week ago under windows xp 32 bit.
Thank you

---

### Post by jeremy31 on 2016-03-19
Is LAN and WLAN enabled in BIOS?

---

### Post by erotavlas on 2016-03-19
There is not bios option. Maybe I could try to update the bios even if it is an hard task under linux since the installer for hp is only for windows.

---

### Post by jeremy31 on 2016-03-19
Have you removed the card and reinstalled it?  Connection may be dirty

---

### Post by erotavlas on 2016-03-19
Yes I tried to remove the card and to reconnet it without success. I know the I'm not using the latest bios. Could help upgrading the bios?

---

### Post by jeremy31 on 2016-03-19
I would see if Ubuntu 12.04 may work as some support for your computer may have been removed from the kernel

---

### Post by erotavlas on 2016-03-19
So could I install the kernel v3.2 or v3.4 of ubuntu 12.04? Are not there any alternatives?

---

### Post by jeremy31 on 2016-03-19
You can install the older kernel, you will have to use grub to boot into the older kernel

---

### Post by erotavlas on 2016-03-20
I tried with first ubuntu 12.04 kernel v.2.6.3x. and it did not work.
Moreover, I replaced the wifi adapter with different model and intel model. Nothing happens. I see the same behaviour with lsusb and lspci. So I'm starting to think that the wifi slot could be broken or not properly recognized by lubuntu.
Any idea?

---

### Post by jeremy31 on 2016-03-20
> **erotavlas said:**
> I tried with first ubuntu 12.04 kernel v.2.6.3x. and it did not work.
Moreover, I replaced the wifi adapter with different model and intel model. Nothing happens. I see the same behaviour with lsusb and lspci. So I'm starting to think that the wifi slot could be broken or not properly recognized by lubuntu.
Any idea?

I am out of ideas.  If Ubuntu's kernel can't find the device, it is impossible to make it work

---

### Post by praseodym on 2016-03-20
Is it a BIOS or an (U)EFI? If BIOS reset it to default settings

---

### Post by erotavlas on 2016-03-20
Yes, I already tried. I will buy an USB wifi device. Thank you at all.

---

### Post by praseodym on 2016-03-20
Check in your BIOS if networking is a) activated or b) if it can be booted before the OS

---

