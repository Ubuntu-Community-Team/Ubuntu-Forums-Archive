---
title: "No Internet"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-08-13
Hello all, after logging on i connected to a wireless network then a notification popped saying network discovery disabled.... I had this annoying popup before and what i do is to uninstall avahi-daemon and it went away but when i open firefox it seems i have no internet connection it always says problem loading the page. What I did is to boot in windows and tried the connection at it works perfectly. After a couple of restarts there is still no internet in ubuntu. I'm at windows atm, thanks in advance

---

### Post by anewguy on 2010-08-13
Did you actually connect to a wireless connection, or were you attempting to connect and got the message?  Has this wireless on this PC ever worked before in Ubuntu?

- open a terminal window (Applications/Accessories/Terminal)

- try again

- immediately after the failuure type:

dmesg | tail <press enter> and post the output back here

lspci <press enter> and post the output back here

lsusb <press enter> and post the output back here

lshw -C network <press enter> and post the output back here


Dave ;)

---

### Post by cbbnewbie on 2010-08-14
yes the connection worked fine before i can connect to it but when the notification popsup (network service discovery disabled) i cannot use the internet although i am connected. My remedy for that before is to uninstall avahi-daemon then restart and evrything is fine again its just now the i cant still use the internet in linux. I'm in windows now


here is dmesg | tail

[  117.200074] usb 1-1: new full speed USB device using uhci_hcd and address 5
[  117.367691] usb 1-1: configuration #1 chosen from 1 choice
[  117.508086] usb 1-1: reset full speed USB device using uhci_hcd and address 5
[  117.738254] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,06/13/2008,5.1313.0613.2008) loaded
[  124.488242] wlan0: ethernet device 00:1a:ef:0d:08:49 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8187.F.conf
[  124.488340] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  124.558599] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  139.642580] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  139.691031] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  140.505559] wlan0: IPv6 duplicate address fe80::21a:efff:fe0d:849 detected!


00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)



Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 004: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub







 *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: eth0
       version: 08
       serial: 00:20:e0:6e:13:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:10 memory:f8fff000-f8ffffff ioport:ecc0(size=64) memory:f8e00000-f8efffff memory:f9000000-f90fffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:ef:0d:08:49
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.55+Realtek Semiconductor Corp. ip=192.168.1.100 multicast=yes wireless=IEEE 802.11g

---

### Post by cbbnewbie on 2010-08-15
hello please help :D

---

### Post by cbbnewbie on 2010-08-16
anyone?

---

### Post by cbbnewbie on 2010-08-16
i dont know what happened but it now works perfectly :D

---

