---
title: "No WiFi in new user of Persistent USB"
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-11-18
I am using a 250GB SSD as a persistent USB with xubuntu. I have a stable Internet connection (The is being written using it).

I want to password the login so have made a new sudoer user. When I logout of the live xubuntu into the new user I am unable to connect to the Internet. The error I get when I try to edit the connection is:

Error Initializing editor

No such interface
'org.freedesktop.NetworkManager.Settings.Connection' on object at path/org/freedesktop.NetworkManager/Settings/2

The information I get when in the live xubuntu is:

```


EDIT: On rebooting and returning to the live xubuntu I have also lost internet there now. In fact I don't see any available networks.
xubuntu@xubuntu:~$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: cb
       serial: 34:e6:ad:ba:1f:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-21-generic firmware=16.242414.0 ip=192.168.2.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:55 memory:b6300000-b6301fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 0c
       serial: 2c:60:0c:8a:6e:27
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:4000(size=256) memory:b6200000-b6200fff memory:b6000000-b6003fff
xubuntu@xubuntu:~$

xubuntu@xubuntu:~$ lspci | grep -i wireless
07:00.0 Network controller: Intel Corporation Wireless 3160 (rev cb)
xubuntu@xubuntu:~$

```

Any help here?

EDIT: I am using 16.04

In fact after rebooting and returning to the live xubuntu, I don't have internet access there now.. A pastebinit from the same machine when attempting to get a stable connection with 17.04:

[http://paste.ubuntu.com/25865847/](http://paste.ubuntu.com/25865847/)

---

### Post by makem2 on 2017-11-18
I have now idea why but I have Internet in both the live xubuntu and the new live user. Now I can remove the xubuntu user and be able to login securely.

---

### Post by C.S.Cameron on 2017-11-18
With a 250GB drive it is probably much better to use a Full install rather than a Persistent install.
More stable, better security, faster boot, etc,etc.

---

### Post by makem2 on 2017-11-19
I agree. I was experimenting to first be sure I could deal with xubuntu. The intention was to see if I could also have windows 10 on the same SSD. It appears possible but fraught with problems.

---

