---
title: "DWA-171 Installation Problems"
date: 2019-02-26
forum: Networking &amp; Wireless
---

### Post by jason147 on 2019-02-26
Hi All,

I have recently done a fresh install of Ubuntu 16.04. I have updated all programs and have tried installing my wireless Internet driver multiple times to no avail. I am currently using a D-Link DWA-171 wireless adapter it is using Realtek 8812AU. The installations went fine and managed to install the drivers but when i run usb-devices it shows the adapter is plugged in but there is no driver assigned to it. Is there any way to fix this? I am more than happy to assist with any troubleshooting that needs to happen.

Another thing to note is that when I run lsusb or usb-devices it shows up but when running lshw -C network it does not show the wireless adapter. I have included some code snippets to help out

lshw -C network
  ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 03
       serial: 00:26:18:c0:c5:3f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enx02674f474a44
       serial: 02:67:4f:47:4a:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.103 link=yes multicast=yes

```


usb-devices
```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2001 ProdID=3314 Rev=02.00
S:  Manufacturer=Realtek
S:  Product=802.11n WLAN Adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
```

lsusb
```
Bus 001 Device 006: ID 2001:3314 D-Link Corp. 
Bus 001 Device 002: ID 12d1:108a Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c24e Logitech, Inc. G500s Laser Gaming Mouse
Bus 004 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lsusb -v
[URL="https://pastebin.com/2sHuASLp"]https://pastebin.com/2sHuASLp


[/URL]

---

### Post by chili555 on 2019-02-27
What is the exact response to the terminal command:```
sudo modprobe rtl8812au
```

---

