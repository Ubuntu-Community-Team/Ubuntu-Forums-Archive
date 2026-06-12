---
title: "Wireless randomly disconnecting"
date: 2020-01-31
forum: Networking &amp; Wireless
---

### Post by matanjonas on 2020-01-31
[COLOR=#242729][FONT=Arial]I've had a very annoying issue in the past 10 days or so, the general idea is that wireless connectivity is lost pretty randomly ("Activation of network connection failed"). After this happens, the network icon on the top bar disappears, I cannot restart Wifi by turning it off and on manually, by using[/FONT][/COLOR]

> sudo service network-manager restart

[COLOR=#242729][FONT=Arial]And pretty much the one and only thing that will get wireless working again is restarting the computer. For a while it seemed like this might be related to power management turning wireless off if I remove the AC cable, because the problem would occur primarily when I would be working on the computer away from the cable, but I am now writing this post connected to the power source and it has happened several times while connected, so it's possibly not that.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm running Ubuntu 18.04.3 LTS on an HP laptop. My network info is as follows:[/FONT][/COLOR]
> *-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: d0:bf:9c:10:6b:60
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:5000(size=256) memory:c6200000-c6200fff memory:c6000000-c6003fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlp10s0
       version: 00
       serial: 2c:33:7a:25:cb:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.15.0-76-generic firmware=N/A ip=192.168.14.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 ioport:3000(size=256) memory:c6100000-c6103fff


[COLOR=#242729][FONT=Arial]Things I've tried to solve this issue so far based on various google searches, all have failed:[/FONT][/COLOR]

[LIST]
[*]updating RTL8723BE drivers
[*]changing default-wifi-powersave-on.conf from =3 to =2
[*]Turning off IPV6
[*]Installing WICD and uninstalling network-manager (which terminal wouldn't actually let me do)
[/LIST]
[COLOR=#242729][FONT=Arial]Will appreciate any help on this matter because I'm on the verge of putting a sledgehammer into my laptop and I can't actually afford a new one.[/FONT][/COLOR]

---

### Post by morrownr on 2020-02-04
I don't have a device with that chipset so this probably isn't the answer you are looking for but I am familiar with some products that work well:

Panda 300Mbps Wireless N USB Adapter

[https://www.amazon.com/Panda-300Mbps-Wireless-USB-Adapter/dp/B00EQT0YK2/?creativeASIN=B00EQT0YK2&linkCode=w61&imprToken=v72SMwFhX45oj8oatWErqg&slotNum=0&tag=bestusbwifiadaptersdotcom-20#customerReviews](https://www.amazon.com/Panda-300Mbps-Wireless-USB-Adapter/dp/B00EQT0YK2/?creativeASIN=B00EQT0YK2&linkCode=w61&imprToken=v72SMwFhX45oj8oatWErqg&slotNum=0&tag=bestusbwifiadaptersdotcom-20#customerReviews)

Very low cost. It might help you out here.

Nick

---

### Post by jeremy31 on 2020-02-04
See the wireless script link in my signature and post results

---

### Post by matanjonas on 2020-02-07
I ran the script as you mentioned in your signature, uploading the txt file in the attachments here

---

