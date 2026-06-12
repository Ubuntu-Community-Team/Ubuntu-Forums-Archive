---
title: "Bluetooth not working on HP laptop but Toshiba is fine"
date: 2018-12-05
forum: Networking &amp; Wireless
---

### Post by meburd on 2018-12-05
I have run all the different commands and installed bluez and blueman through the previous threads. My toshiba connected to my bluetooth JBL Flip 2 and my hp doesn't even see it. I checked all the files and they are the same for the bluetooth.  All the services are running. i have tried to include all you may need.

```
mike@mike-HP-Pavilion-Notebook:~$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
08:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 0a)
mike@mike-HP-Pavilion-Notebook:~$ 

```

```
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 003: ID 04f2:b50c Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
mike@mike-HP-Pavilion-Notebook:~$ bluetoothctl
Agent registered
[CHG] Controller 60:6D:C7:F0:5E:C4 Class: 0x001c010c
[CHG] Controller 60:6D:C7:F0:5E:C4 Powered: yes
[bluetooth]# discoverable
Missing on/off argument
[bluetooth]# discoverable on
Changing discoverable on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller 60:6D:C7:F0:5E:C4 Discovering: yes
[bluetooth]#
```

---

### Post by jeremy31 on 2018-12-06
What are the results for ```
dmesg | egrep -i 'blue|firm'
```

---

