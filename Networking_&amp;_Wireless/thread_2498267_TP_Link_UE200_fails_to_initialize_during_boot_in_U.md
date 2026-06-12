---
title: "TP Link UE200 fails to initialize during boot in Ubuntu Server 20.04"
date: 2024-06-06
forum: Networking &amp; Wireless
---

### Post by eldho1416 on 2024-06-06
Hello,


I had ordered a USB to Lan adapter from TP link ([https://tinyurl.com/kptfvtrp]("http://www.amazon.in/TP-Link-TP-UE200_W-Ethernet-Network-Adapter/dp/B01GNP5UUA/ref=asc_df_B01GNP5UUA/?tag=googleshopdes-21&linkCode=df0&hvadid=396987220938&hvpos=&hvnetw=g&hvrand=10339999942097226910&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1007768&hvtargid=pla-649771983582&psc=1&mcid=046610ab530336d0a92643048eb2a76f&ext_vrnc=hi")) which used to work perfectly fine around 6-8 months ago in Ubuntu Server 20.04 running Raspberry PI 4B (4GB RAM) and I recently tried to connect it to same hardware and OS and it fails to show the interface. It doesn't show up in `lsusb` but if unplug and plug it it works fine what could be the problem? 


```
dmesg
[    2.535403] usb 1-1.3: new full-speed USB device number 5 using xhci_hcd
[    2.615603] usb 1-1.3: device descriptor read/64, error -32
[    2.807586] usb 1-1.3: device descriptor read/64, error -32
[    2.999391] usb 1-1.3: new full-speed USB device number 6 using xhci_hcd
[    3.079588] usb 1-1.3: device descriptor read/64, error -32
[    3.271585] usb 1-1.3: device descriptor read/64, error -32
[    3.991400] usb 1-1.3: new full-speed USB device number 7 using xhci_hcd
[    3.991629] usb 1-1.3: Device not responding to setup address.
[    4.227594] usb 1-1.3: Device not responding to setup address.
[    4.435387] usb 1-1.3: device not accepting address 7, error -71
[    4.519396] usb 1-1.3: new full-speed USB device number 8 using xhci_hcd
[    4.519629] usb 1-1.3: Device not responding to setup address.
[    4.727670] usb 1-1.3: Device not responding to setup address.
[    4.935901] usb 1-1.3: device not accepting address 8, error -71




lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0eef:0005 D-WAV Scientific Co., Ltd
Bus 001 Device 003: ID 0461:0010 Primax Electronics, Ltd HP PR1101U / Primax PMX-KPR1101U Keyboard
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by eldho1416 on 2024-06-07
Update: I tried with ubuntu server 22.04 still same persists persists

---

