---
title: "ubuntu 18.04.1 - no wi-fi adapter found"
date: 2018-11-13
forum: Networking &amp; Wireless
---

### Post by cybrus10 on 2018-11-13
i just installed ubuntu 
my laptop is hp 

[IMG]https://i.stack.imgur.com/5TQAC.png[/IMG]
and thanks in advance

---

### Post by TheFu on 2018-11-13
FYI, support for 17.10 ended in July.
Best to use either 18.04, an LTS release w/  yrs of support, or 18.10 which has 6+ months of support remaining.

The first step for any hardware not found issue is determining if the OS knows anything about it or not.
**sudo lshw -C network** will show all recognized network devices and the drivers being used.

---

### Post by cybrus10 on 2018-11-13
> **TheFu said:**
> FYI, support for 17.10 ended in July.
Best to use either 18.04, an LTS release w/  yrs of support, or 18.10 which has 6+ months of support remaining.

The first step for any hardware not found issue is determining if the OS knows anything about it or not.
**sudo lshw -C network** will show all recognized network devices and the drivers being used.

am sorry its  ubuntu 18.04.1 

[QUOTE=The first step for any hardware not found issue is determining if the OS knows anything about it or not.
**sudo lshw -C network** will show all recognized network devices and the drivers being used.[/QUOTE]

thanks it said 
description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

---

### Post by TheFu on 2018-11-13
It should have at least 8 lines for every different device.  Post all and please use **code tags** so things line up correctly. Every line is important.

---

### Post by lisati on 2018-11-13
I have a Compaq (HP) laptop on which I recently installed 18.04.1, and faced a similar challenge getting Wi-Fi to work. What eventually worked was to go into BIOS (mine's a pre-UEFI machine), go to the "System Configuration" screen, and change "Action Keys mode" to disabled.

Disclaimer: results may vary, depending on your specific laptop model, and is offered in the hope that it helps save some time googling and trying stuff that does not work.

---

### Post by cybrus10 on 2018-11-13
> **TheFu said:**
> It should have at least 8 lines for every different device.  Post all and please use **code tags** so things line up correctly. Every line is important.

```
-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 15
       serial: 10:62:e5:6a:1c:e8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:4000(size=256) memory:a4104000-a4104fff memory:a4100000-a4103fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:a4000000-a400ffff
```

---

### Post by chili555 on 2018-11-13
May we also see: ```
lspci -nnk | grep 0280 -A3
```

---

### Post by cybrus10 on 2018-11-13
> **chili555 said:**
> May we also see: ```
lspci -nnk | grep 0280 -A3
```

thank you 
```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac
 PCIe Wireless Network Adapter [10ec:c821]
  Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac
 PCIe Wireless Network Adapter [103c:831a]
```

---

### Post by chili555 on 2018-11-13
Here you go: [https://askubuntu.com/questions/1070593/lenovo-thinkpad-e480-no-wifi-adaptor-found-in-ubuntu-18-04/1070645#1070645](https://askubuntu.com/questions/1070593/lenovo-thinkpad-e480-no-wifi-adaptor-found-in-ubuntu-18-04/1070645#1070645)

---

### Post by cybrus10 on 2018-11-13
> **chili555 said:**
> Here you go: [https://askubuntu.com/questions/1070593/lenovo-thinkpad-e480-no-wifi-adaptor-found-in-ubuntu-18-04/1070645#1070645](https://askubuntu.com/questions/1070593/lenovo-thinkpad-e480-no-wifi-adaptor-found-in-ubuntu-18-04/1070645#1070645)

:p=d> thank you very much ! i had some problems affecting the commands but eventually it worked ! thank you again !

---

### Post by chili555 on 2018-11-13
Glad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

