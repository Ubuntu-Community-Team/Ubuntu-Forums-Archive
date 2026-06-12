---
title: "no wireless connectivity"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by wrylypioneer on 2008-08-29
I am very new to Ubuntu and am having a hard time with my wireless connection.

i have provided the results of a couple commands below:

any help would be much appreciated... thank you


nano/etc/network/interfaces

 

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

iface wlan0 inet dhcp
wpa-psk 5617577d5c22057e74f42b61e1ae1963ead48f9a8d1b5ba9845766181d7feccb
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid wrylywireless

auto wlan0

and this is the result of my sudo lshw -C network   command

wrylypioneer@wrylypioneer-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:24:9a:79
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:58:a2:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
wrylypioneer@wrylypioneer-laptop:~$

---

### Post by Sam Lars on 2008-08-29
It looks like you're using b43 as a driver, I would suggest at least trying Ndiswrapper with the Windows drivers for your card.

---

