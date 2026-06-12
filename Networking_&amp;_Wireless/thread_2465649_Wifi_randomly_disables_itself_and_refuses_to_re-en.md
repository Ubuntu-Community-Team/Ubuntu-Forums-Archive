---
title: "Wifi randomly disables itself and refuses to re-enable until I restart it?"
date: 2021-08-07
forum: Networking &amp; Wireless
---

### Post by justjeff-999 on 2021-08-07
I have an old PC which I recently uncovered, and I've spent quite a bit of time revamping it and making it usable for other people, however, one issue that bugs me persistently seems to be the fact that at random occasions all the current in-range wifi networks disappear and I am unable to re-enable the wireless searching option until I restart it, despite the networks not being down or anything. I do realise this may count as a driver issue and this computer was made quite a few years ago so I assuming that the drivers aren't geared to handle such recent technology, but I would still like to see if there is anything possible to revamp the desktop pc to decent expectations.

I have tried:
1) Disabling wifi power saving, which improved the perfomance but it didn't actually solve the issue.
2) Restarting the network manager service, which doesn't do anything, no matter what Ubuntu based distro I use.

etc....

I would just like to see if there is anything possible for this PC to at least improve the situation.

_sudo lshw -C network_ output:
```

*-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 02
       serial: 90:e6:ba:ec:1d:d2
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-25-generic latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febe0000-febfffff
  *-usb:1
       description: Wireless interface
       product: 802.11 bg WLAN
       vendor: Ralink
       physical id: 8
       bus info: usb@1:8
       logical name: wlx701a0486ccb7
       version: 0.01
       serial: 70:1a:04:86:cc:b7
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=5.11.0-25-generic firmware=1.7 ip=192.168.0.16
```

Any updated drivers or something? I'd appreciate any guidance or at least a way I can fix this.

---

### Post by morrownr on 2021-08-07
Hi justjeff,

This smells like the adapter may be having problems with the wifi router/access point. That happens with some modern routers. Here is a paste of wifi router advice from my github repo:

-----

Recommended WiFi Router/ Access Point Settings


Note: These are general recommendations, some of which may not apply to your specific situation.


Security: Set WPA2-AES. Do not set WPA2 mixed mode or WPA or TKIP.


Channel width for 2.4G: Set 20 MHz fixed width. Do not use 40 MHz or 20/40 automatic.


Channels for 2.4G: Set channel 1 or 6 or 11 depending on the congestion at your location. Do not set automatic channel selection.


Mode for 2.4G: For best performance, set "N only" if you no longer use B or G capable devices.


Network names: Do not set the 2.4G Network and the 5G Network to the same name. Note: Unfortunately many routers come with both networks set to the same name.


Channels for 5G: Not all devices are capable of using DFS channels. It may be necessary to set a fixed channel in the range of 36 to 48 or 149 to 161 in order for all of your devices to work on 5g. (for US, other countries may vary)


Best location for the wifi router/ access point: Near center of apartment or house, at least a couple of feet away from walls, in an elevated location.


Check congestion: There are apps available for smart phones that allow you to check the congestion levels on wifi channels. The apps generally go by the name of WiFi Analyzer or something similar.


After making and saving changes, reboot the router.

Note: The part about setting 2.4g to "n" only does not apply to you since your adapter is a "bg" only capable adapter.

-----

I suspect the above will help but it could be a situation where a little more modern adapter could help and the good thing about usb wifi adapters is they are easy to move around and use on whatever machine you want. Give this repo a look to see what usb wifi adapters that use in-kernel drivers are available these days. There are many and the repo provides links to many:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Good luck and let us know about your progress.

morrownr

---

