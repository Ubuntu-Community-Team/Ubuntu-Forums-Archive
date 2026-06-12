---
title: "TP-Link Archer AC1300 T4U Setup"
date: 2020-06-27
forum: Networking &amp; Wireless
---

### Post by sydreamer on 2020-06-27
Hi,

I just finished a fresh installation of Ubuntu 20.04 and have been trying to get my USB Wi-FI Adapter (TP-Link AC1300 T4U v3) to work.

After following a number of guides, I believe I have managed to install the device, but am unable to enable it and use it.

I am currently using my android device as a usb tether to access the internet so I could setup the adapter.

Thank you in advance for the help.

lsusb:[INDENT]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 22b8:2e24 Motorola PCS moto g(7) plus
Bus 002 Device 002: ID 2357:0115 TP-Link 802.11ac NIC
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0d8c:0134 C-Media Electronics, Inc. TONOR TC-777 Audio Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1a2c:4c5e China Resource Semico Co., Ltd USB Keyboard
Bus 004 Device 002: ID 258a:1007 SINOWEALTH Game Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/INDENT]

sudo lshw (network section only, output is quite long):[INDENT]  *-network:0
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:4
       logical name: usb0
       serial: 96:1f:96:ec:26:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.163 link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@2:2
       logical name: wlx00e04c5c08e0
       serial: 00:e0:4c:5c:08:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl88XXau multicast=yes wireless=unassociated




[/INDENT]

---

### Post by CelticWarrior on 2020-06-27
The [TP-LINK AC1300 T4U v3]("https://wikidevi.wi-cat.ru/TP-LINK_Archer_T4U_v3") has a Realtek 8812BU chipset, apparently. Please confirm with 'lsusb'.
That being the case then [https://askubuntu.com/questions/1079377/how-do-i-install-drivers-for-realtek-rtl8812bu](https://askubuntu.com/questions/1079377/how-do-i-install-drivers-for-realtek-rtl8812bu)

---

### Post by sydreamer on 2020-06-27
Managed to solve it through the guide, though I had to navigate the github to find the most recent version.

Thanks for the help.

---

