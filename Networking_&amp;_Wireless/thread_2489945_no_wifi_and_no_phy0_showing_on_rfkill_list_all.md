---
title: "no wifi and no phy0 showing on rfkill list all"
date: 2023-08-15
forum: Networking &amp; Wireless
---

### Post by rorysmith on 2023-08-15
Hi,

I installed ubuntu 22.04 on an ASUS Vivobook Go 14. I cannot see the wifi symbol at all once ubuntu loads up. 

When I do an rfkill list all it looks like this and phy0 does not show at all:
[INDENT]0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[/INDENT]

In the bios menu, I can connect to the wifi so it doesn't seem to be a hardware issue.

I tried multiple solutions without any luck:
1) Changing kernel. Current one is 6.2.0-26-generic
2) Downgraded to Ubuntu 20.04
3) restarting from a suspend
4) reinstalling drivers

I can connect to the internet on the cable and via usb from my phone. But I no longer know what else to try. The wifi appears fine in bios but doesn't seem to exist inside of Ubuntu.

Thanks for any help you can offer me....!

---

### Post by jeremy31 on 2023-08-15
Post results from terminal for  ```
lspci -nnk |grep -iA3 net; lsusb
```

---

### Post by rorysmith on 2023-08-15
$ lspci -nnk |grep -iA3 net; lsusb
pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted
02:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7902]
    Subsystem: AzureWave Device [1a3b:5520]
    Kernel modules: wl
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:1506] (rev c1)
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 13d3:54a1 IMC Networks USB2.0 HD UVC WebCam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 22b8:2e24 Motorola PCS moto g(9) play
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:3579 IMC Networks Wireless_Device
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2023-08-15
There isn't a driver for that wifi on linux at this time

---

### Post by rorysmith on 2023-08-15
Ok, thanks for letting me know. Then I will try to buy an external usb wifi adaptor instead that is compatible with Ubuntu. I read the Nano Tp-link N 150mbps could be an option as drivers can be found.

---

### Post by jeremy31 on 2023-08-15
A poster here has a list of supported USB devices at [https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi) but I would avoid any small dongles or any using rtl8188eu

---

