---
title: "wired and wifi connections do not work in 14.04.1"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by PIerre_Viel on 2015-01-04
I need help my wired and wifi connections don't work since I installed 14.04.1

*-network
        description: Network controller
        product: BCM4311 802.11a/b/g [14E4:4312]
        vendor: Broadcom Corporation  [14E4]
        physical id: 0
        bus info: pci@0000:0b:00.0
        version: 01
        width: 32 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list
        configuration: driver=wl latency=0
        resources: irq:17 memory:fe8fc000-fe8fffff
*-network UNCLAMED
        description: Ethernet controller
        product: BCM4401-B0 100Base-TX [14E4:170C]
        vendor: Broadcom Corporation [14E4]
        physical id:0
        bus info: pci@0000:03:00.0
        version: 02
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list
        configuration: latency=64
        resources: memory:fe5fe000-fe5fffff

---

### Post by praseodym on 2015-01-04
Hi,

download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. WLAN should work. What about LAN?
```

sudo modprobe -v b44
```

---

### Post by Hadaka on 2015-01-04
Hi,since you have no internet access, Let's get you some,,
please open a terminal ctrl/alt/t  and make sure your wired
cable is connected. then COPY and paste,,
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot
you should now have wired internet service, with your now working
wired connection,,,do Praseodym's instructions to download the firmware
you need for wireless.
Ignore any offer to load additional drivers or proprietary drivers.

---

