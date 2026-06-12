---
title: "Need help with bluetooth driver on lenovo miix 2 8"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by login721 on 2017-07-02
[COLOR=#000000]Hello .[/COLOR]
[COLOR=#000000]I'm new to ubuntu . I just installed xubuntu on lenovo miix2-8 .[/COLOR][COLOR=#000000]
The NIC is [/COLOR][COLOR=#000000]Broadcom 802.11abgn Wireless SDIO , [/COLOR][COLOR=#252525][FONT=sans-serif]VID_02D0&PID_4324&FN_1.After manual added [/FONT][/COLOR][COLOR=#000000]brcmfmac43241b4-sdio.txt i can use wifi , but bluetooth still not works. When i click "setup new device" ,blueman assitant shows "No adapter found".

[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#252525][FONT=sans-serif]this is result of lspci:
[/FONT][/COLOR]```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI [8086:0f35] (rev 09)
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 09)
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 09)
```[COLOR=#252525][FONT=sans-serif]


lsusb
[/FONT][/COLOR]```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0fce:7197 Sony Ericsson Mobile Communications AB 
Bus 001 Device 004: ID 056e:6022 Elecom Co., Ltd 
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[COLOR=#252525][FONT=sans-serif]

[/FONT][/COLOR]cat /sys/bus/sdio/devices/*
```
cat: '/sys/bus/sdio/devices/mmc0:0001:1': Is a directory
cat: '/sys/bus/sdio/devices/mmc0:0001:2': Is a directory

```

cat /sys/bus/sdio/devices/*/uevent
```
SDIO_CLASS=00
SDIO_ID=02D0:4324
MODALIAS=sdio:c00v02D0d4324
DRIVER=brcmfmac
SDIO_CLASS=00
SDIO_ID=02D0:4324
MODALIAS=sdio:c00v02D0d4324

```

lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 056e:6022 Elecom Co., Ltd 
Bus 001 Device 006: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: LNV4752:00: GPS
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.174050] [Firmware Info]: PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] not reserved in ACPI motherboard resources
[    1.928614] [Firmware Bug]: No valid trip found
[    4.641575] Bluetooth: Core ver 2.22
[    4.641611] Bluetooth: HCI device and connection manager initialized
[    4.641621] Bluetooth: HCI socket layer initialized
[    4.641626] Bluetooth: L2CAP socket layer initialized
[    4.641639] Bluetooth: SCO socket layer initialized
[    4.658911] Bluetooth: HCI UART driver ver 2.3
[    4.658915] Bluetooth: HCI UART protocol H4 registered
[    4.658916] Bluetooth: HCI UART protocol BCSP registered
[    4.658917] Bluetooth: HCI UART protocol LL registered
[    4.658919] Bluetooth: HCI UART protocol ATH3K registered
[    4.658920] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    4.659017] Bluetooth: HCI UART protocol Intel registered
[    4.677237] Bluetooth: HCI UART protocol Broadcom registered
[    4.677239] Bluetooth: HCI UART protocol QCA registered
[    4.677240] Bluetooth: HCI UART protocol AG6XX registered
[    4.677242] Bluetooth: HCI UART protocol Marvell registered
[    5.416288] brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
[   73.966451] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   73.966454] Bluetooth: BNEP filters: protocol multicast
[   73.966463] Bluetooth: BNEP socket layer initialized


```

Thanks in advance!

---

