---
title: "ubuntu 20.04 WIFI not showing"
date: 2020-12-04
forum: Networking &amp; Wireless
---

### Post by petewatcharawit on 2020-12-04
After installing Ubuntu 20.04 for a week, the WIFI icon has disappeared. Using this command: ```
lspci | grep Wireless

```
returns
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter

I have updated the software using: ```
sudo apt update
``` ```
sudo apt upgrade
```  and restart but the WIFI icon is still missing. My home WIFI works fine.

Any idea on how to solve the internet connection?

---

### Post by wildmanne39 on 2020-12-04
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by praseodym on 2020-12-04
If LAN works, run
```

sudo apt install build-essential dkms rtl8821ce-dkms
```
Reboot and turn off SecureBoot

---

### Post by petewatcharawit on 2020-12-05
**I get this message**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.8.1-5ubuntu1).
build-essential is already the newest version (12.8ubuntu1.1).
rtl8821ce-dkms is already the newest version (5.5.2.1-0ubuntu4~20.04.2).
The following package was automatically installed and is no longer required:
  libfprint-2-tod1
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**Then I disabled SecureBoot via BIOS setting. No WIFI still. Help please?**

Note that running the command: ```
sudo lshw -C network 
```returns
*-network UNCLAIMED       
       description: Network controller
       product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:f000(size=256) memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: bnep0
       serial: 8c:c8:4b:10:8f:68
       capabilities: ethernet physical
       configuration: broadcast=yes ip=192.168.44.74 multicast=yes

---

### Post by petewatcharawit on 2020-12-05
Problem solved. 

I ran: [```
sudo apt-get remove rtl8821ce-dkms
```

and then reinstall it: ```
sudo apt-get install rtl8821ce-dkms
```

---

