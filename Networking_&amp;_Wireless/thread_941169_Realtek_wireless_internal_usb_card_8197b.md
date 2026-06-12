---
title: "Realtek wireless internal usb card 8197b"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by tecknos11 on 2008-10-07
My problem is that I can see the router (AP) but cannot connect. When Linux is restarted I can no longer see the AP and still cannot connect. I cannot connect to the internet using Ethernet either.

I have a Realtek wireless 8197b built in usb card. My laptop is a gateway t1628. I cannot connect to the internet. My computer has both vista and Ubuntu 8.04 on the same drive although I havn't yet got around to booting into windows. 

After doing my research I decided that the easiest way to connect to the internet was thru a wireless connection. I decided the best way was to install the windows drivers thru ndiswrapper as the linux drivers don't work. After installing the drivers everything seems happy except I could only see the network but not connect. 

 I went to realtek's website and got the latest drivers. I installed them thru a usb flashdrive. I first tried vista drivers but they didn't work and the windows xp and 2000 gave me my current complaint. 

Is it a driver problem or am I missing something?

---

### Post by tecknos11 on 2008-10-07
More info

> dmesg

========================================

[ 351.582317] usbcore: Deregistering interface driver ndiswrapper


[ 351.676971] ndiswrapper: Device wlan0 removed


[ 351.691369] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)


[ 351.847281] usb 6-3: Reset high speed usb device using ehci_hcd and address 3


[ 351.983920] ndiswrapper: Driver net8187b (realtek semiconductor corp.,06/25/2008,5.1135.0625.2008) loaded


[ 354.280039] wlan0: Ethernet device 00:16:44:be:24:2c using ndis driver: Net8187b, version: 0x1, ndis version: 0x500, vendor: 'realtek rtl8187 wireless lan usb nic ', 0bda:8189.f.conf


[ 354.280772] wlan0: Encryption modes supported: Wep; tkip with wpa, wpa2, wpa2psk; aes/ccmp with wpa, wpa2, wpa2psk


[ 354.281218] usbcore: Registered new interface driver ndiswrapper


[ 361.120352] addrconf(netdev_change): Wlan0: Link becomes ready


[ 361.150644] net: Registered protocol family 17


[ 365.284891] wlan0: No ipv6 routers present


[ 740.124955] addrconf(netdev_up): Wlan0: Link is not ready


=================================

ifup

=================================

tecknos11@tecknos11-laptop:~$ sudo ifup wlan0


ignoring unknown interface wlan0=wlan0.


=========================

lshw -c network

=========================

tecknos11@tecknos11-laptop:~$ sudo lshw -c network


*-network


description: Ethernet interface


product: Rtl8101e pci express fast ethernet controller


vendor: Realtek semiconductor co., ltd.


Physical id: 0


bus info: Pci@0000:08:00.0


logical name: Eth0


version: 01


serial: 00:03:25:5b:70:05


capacity: 1gb/s


width: 64 bits


clock: 33mhz


capabilities: Pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation


configuration: Autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2lk duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair


*-network


description: Wireless interface


physical id: 2


logical name: Wlan0


serial: 00:16:44:be:24:2c


capabilities: Ethernet physical wireless


configuration: Broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+realtek semiconductor corp. Link=no multicast=yes wireless=ieee 802.11g



---

