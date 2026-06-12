---
title: "Can't install the wireless driver in HP Pavilion dv2419us"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by maqtanim on 2013-11-06
I've just installed Ubuntu 13.04 in an old HP Pavilion  dv2419us. The problem is, Ubuntu doesn't detect the wireless card. But  it works fine in Windows 7. 
  The following command returns nothing!
  ```
lspci -vvnn | grep 14e4

```  Any suggestion regarding this?

---

### Post by chili555 on 2013-11-06
It's probably not a Broadcom. Please run and post:```
lspci -nn | grep 0280
```

---

### Post by maqtanim on 2013-11-06
> **chili555 said:**
> It's probably not a Broadcom. Please run and post:```
lspci -nn | grep 0280
```

It shows nothing! My lspci output is

```
~$ lspci
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

---

### Post by chili555 on 2013-11-06
We wonder if it's one of those rare devices that's attached to an internal USB bus:```
lsusb
```

---

### Post by maqtanim on 2013-11-06
> **chili555 said:**
> We wonder if it's one of those rare devices that's attached to an internal USB bus:```
lsusb
```

```
~$ lsusb
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by chili555 on 2013-11-06
I still don't see a wireless device. Can you boot into Windows and gather as much information as you can about it?

---

### Post by maqtanim on 2013-11-06
> **chili555 said:**
> I still don't see a wireless device. Can you boot into Windows and gather as much information as you can about it?

The problem is I actually wiped the windows out. (When I got this machine, the installed Windows was a pirated one, so I preferred to remove that one)

---

### Post by chili555 on 2013-11-06
Is there any setting in the BIOS to enable or disable wireless? Any physical switch on the case? We are quickly running low on options.

---

### Post by maqtanim on 2013-11-06
> **chili555 said:**
> Is there any setting in the BIOS to enable or disable wireless?

Checked that, there is none! :(
> **chili555 said:**
> Any physical switch on the case?
 Yes there is one, and I kept that ON. 
```
:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

 > **chili555 said:**
> We are quickly running low on options.
Dont worry about that. There is always a way out! :)

---

### Post by chili555 on 2013-11-06
> There is always a way out!And by that, do you mean you are on your way out to the store to get a USB wireless??

---

### Post by maqtanim on 2013-11-06
> **chili555 said:**
> And by that, do you mean you are on your way out to the store to get a USB wireless??

No... not really. I wanted say that every problem has a solution. :) Hopefully i'll have one too...

---

### Post by chili555 on 2013-11-07
Please reboot so we have a clean slate and then do:```
dmesg > dmesg.txt

```
Find the file in your user directory and post it here. Give us the link in your reply. Maybe we can see what's amiss here. 

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

