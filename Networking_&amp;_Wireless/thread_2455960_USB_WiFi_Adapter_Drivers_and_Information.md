---
title: "USB WiFi Adapter Drivers and Information"
date: 2020-12-31
forum: Networking &amp; Wireless
---

### Post by morrownr on 2020-12-31
USB WiFi Adapter Drivers and Information


[https://github.com/morrownr](https://github.com/morrownr)


Linux driver for the Realtek RTL8812BU and RTL8822BU Chipsets
Driver Version: v5.8.7.4 (Realtek) (2020-09-22)
Location: [https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)




Linux driver for the Realtek RTL8811CU, RTL8821CU and RTL8831AU Chipsets
Driver Version: v5.8.1.7 (Realtek) (2020-09-29)
Location: [https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)




Linux driver for the Realtek RTL8812AU Chipset
Driver Version: 5.9.3.2 (Realtek) (2020-10-12)
[https://github.com/morrownr/8812au](https://github.com/morrownr/8812au)




Linux driver for the Realtek RTL8814AU Chipset
Driver Version: v5.8.5.1 (Realtek) (2019-10-29)
[https://github.com/morrownr/8814au](https://github.com/morrownr/8814au)




Linux Driver for the RealTek RTL8811AU and RTL8821AU Chipsets
Driver Version: v5.8.2.3 (Realtek) (2020-04-01)
[https://github.com/morrownr/8821au](https://github.com/morrownr/8821au)


Features:


IEEE 802.11 b/g/n/ac WiFi compliant
802.1x, WEP, WPA TKIP and WPA2 AES/Mixed mode for PSK and TLS (Radius)
WPA3-SAE (Personal)
WPS - PIN and PBC Methods
IEEE 802.11b/g/n/ac Client mode
Support wireless security for WEP, WPA TKIP and WPA2 AES PSK
Support site survey scan and manual connect
Support WPA/WPA2 TLS client
Support power saving mode
Soft AP mode
WiFi-Direct
MU-MIMO
Mesh
Wake on WLAN
Supported interface modes:
  IBSS
  Managed
  AP (WiFi Hotspot) (Master mode)
  Monitor
  P2P-client
  P2P-GO
USB mode control (for adapters that have USB 3.0 support)
Log level control
LED control
Power saving control
VHT control (allows 80 MHz channel width in AP mode)


Anyone interested in helping test and maintain these drivers should contact me. 


My main goals are:


- maintain easy-to-understand documentation that is presented in a professional manner
- easy installation for those with less experience
- add features that make the experience better
- upgrade to the most modern version of the driver available in a timely manner


-----


How to determine the chipset inside of your USB WiFi adapter


The easiest way is to start with lsusb command. This utility will show information about the USB
buses in the system and devices connected to them.


Display all USB devices:


$ lsusb


Sample output:


Bus 002 Device 002: ID 05e3:0612 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b812 Realtek Semiconductor Corp.
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




$ lsusb | grep -i realtek
$ lsusb | grep -i ralink
$ lsusb | grep -i atheros
$ lsusb | grep -i mediatek


Sample output:


Bus 001 Device 004: ID 0bda:b812 Realtek Semiconductor Corp.


With the above output we can get more information using the bus and device information:


sudo lsusb -vv -s 001:004


[https://devicehunt.com/search/type/usb/vendor/any/device/any](https://devicehunt.com/search/type/usb/vendor/any/device/any)


-----

Mods: you are welcome to sticky this thread. I will do my best to keep it up to date.

---

