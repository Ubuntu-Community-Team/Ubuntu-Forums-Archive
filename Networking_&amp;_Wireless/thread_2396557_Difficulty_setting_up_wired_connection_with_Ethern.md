---
title: "Difficulty setting up wired connection with Ethernet to USB adapter"
date: 2018-07-17
forum: Networking &amp; Wireless
---

### Post by nat9 on 2018-07-17
Hi,

I'm using a Dell laptop with Ubuntu 16.04 (no dual-boot). My laptop does not have an Ethernet port so I bought a Tecknet USB 3.0 hub with Ethernet adapter. I connected it to my computer and to my modem, unfortunately it does not work (the wireless still works perfectly).

I tried to solve the problem, but could not. I figured out the followings:
- Form my modem configuration I can see the adapter with an assigned IP address. 
- I tried to set up a wired connection in Network Connections with a static IP address (need it for port forwarding). In the Ethernet tab in the Device section nothing shows up. I suppose that is not good. 
- The command ```
sudo lshw -C network
``` gives me the following:

```
  *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 83
       serial: f4:06:69:7d:24:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-130-generic firmware=17.948900127.0 ip=192.168.1.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f7100000-f7101fff

```

So there is no wired interface, that is a problem, but I do not know how to deal with it. 

Any help would be appreciated.

---

### Post by wyliecoyoteuk on 2018-07-18
try 
lsusb 

which will give you info about the device

---

### Post by nat9 on 2018-07-18
Yes I tried, sorry forgot to post it. So I got:
```
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 012: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 003 Device 011: ID 0bda:0411 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 04f3:0387 Elan Microelectronics Corp. 
Bus 002 Device 003: ID 1bcf:2b8a Sunplus Innovation Technology Inc. 
Bus 002 Device 016: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 025: ID 0bda:5411 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The adapter has an USB hub with three USB port, the three **Realtek Semiconductor Corp.** in the lsusb output.

The hub works, I can connect any USB device to it and my modem sees the adapter so it is not a hardware issue.

---

### Post by wyliecoyoteuk on 2018-07-18
obda:8153 is the ethernet adapter, the others are the USB controller and hub

rtl8153 chipset is not always detected properly

[https://www.pcsuggest.com/install-rtl8153-driver-linux/](https://www.pcsuggest.com/install-rtl8153-driver-linux/)

---

### Post by nat9 on 2018-07-19
wyliecoyoteuk, thanks for the help!

I went to the link, tried to install the trl8152 driver but run into a problem. While compiling it complained about a variable (BMCR_SPEED10) not being defined, so I went to investigate and figured out that my kernel (4.4) does not define this variable, so I went to upgrade my kernel (it was long due) and now the adapter works perfectly. (My touchpad also works, which was the main reason I wanted to upgrade my kernel for a while.) So great, it solved both of my problems :-D=d> Thanks again! \\:D/

---

