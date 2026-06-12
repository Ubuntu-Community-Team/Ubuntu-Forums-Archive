---
title: "Ubuntu 15.10 - dpkg: error: requested operation requires superuser privilege"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by vijay_shankar on 2015-11-11
I am trying to install two packages to enable my ethernet and wifi, the commands seems to fail. 

```
sudo dpkg -i b43-fwcutter_019-2_1386* && dpkg -i firmware-b43-installer_019-2_all*
```

I am getting the below error: 
> [B]dpkg: error: requested operation requires superuser privilege

[/B]

Below is my network information: 

```
[COLOR=#000000]sudo lshw -C network

[/COLOR]
```

```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0
       version: 02
       serial: 00:23:ae:38:7e:45
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:29 ioport:de00(size=256) memory:f0010000-f0010fff memory:f0000000-f000ffff memory:f6800000-f681ffff



```

---

### Post by matt_symes on 2015-11-11
Hi

Try this

```
sudo dpkg -i b43-fwcutter_019-2_1386* && **sudo **dpkg -i firmware-b43-installer_019-2_all*
```

Both dpkg commands require elevated privileges.

Kind regards

---

### Post by vijay_shankar on 2015-11-11
Thanks, it worked but why is it asking for internet connection to install the package, "some problem occured during the firmware download. Please check your internet connection". I am not connected to internet while using the ubuntu [No Ethernet or No Wifi]

---

### Post by matt_symes on 2015-11-11
Hi

> **vijay_shankar said:**
> Thanks, it worked but why is it asking for internet connection to install the package, "some problem occured during the firmware download. Please check your internet connection". I am not connected to internet while using the ubuntu [No Ethernet or No Wifi]

First things first, i'm going to move your question to the **Network and Wireless** subforum.

Is this package *firmware-b43-installer_019-2_all...* trying to download the firmware ? 
Do you need both packages ?
What tutorial are you trying to follow ? Do you have a link ?

I'm not the best person to help you with your question as i have never used those two packages but be patient and someone will come along to help you.

Kind regards

---

