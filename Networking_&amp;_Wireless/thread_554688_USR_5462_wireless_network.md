---
title: "USR 5462 wireless network"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Richard Hunt on 2007-09-19
I have had Ubuntu 7.0.4. installed for 3 days now for the first time - i.e. this is my first experience with any form of Linux.  My PC is an AMD Athlon 64 3500+ CPU with dual boot now working with Win XP Pro.  Installation went fine and all appears to be well under Ubuntu - except networking (so far).  I have a USB connection to my router which acts as internet gateway.  It is a USR5462 wireless router with a USB USR5422 adapter.

I have successfully connected to the internet after about an hour of tinkering with the settings undar a) Network and b) Network settings.  I think I know the correct configuration now and saved them under a 'location'.  However every time I restart Ubuntu even recalling this location, the network does not connect and it takes upwards of half an hour to tinker again, and eventually get back to the same settings.  This is a major frustration and will shorten experimentation with Ubuntu if I cannot get it sorted.  

I have since visited the USR site and ugraded the router firmware and this seems to have stopped access altogther to the router from Ubuntu (works fine in Win XP).  I can ping 192.168.2.0 but no other address, when the settings are for Static IP address.

I'd appreciate some help so that the network starts correctly each time I start Ubuntu.

I am completely new to the world of Linux and therefore have no knowledge of any of its jargon yet. Please give any response to this in plain English!

---

### Post by Richard Hunt on 2007-09-21
I may have found the answer to this myself.  A phone call to USR technical support indicates that the USB adapter (model 5422) is not compatible with Linux.

This may explain later inability to connect, but seems not to explain why I actually managed to connect on 2 occasions.

---

### Post by bjd on 2007-09-21
It's not supported by USR anyway, but that does not mean it is impossible to get your USB device to work with linux
Especially since it sort of worked before...

Might be handy if you also post output of *sudo lshw -C network* and *lsusb* with the device plugged in.
That way people can see what hardware exactly you have and may be able to better help you out...

---

### Post by Richard Hunt on 2007-09-23
Thank you.

Output shown below:

lsusb
Bus 003 Device 008: ID 0471:0329 Philips 
Bus 003 Device 009: ID 07b5:0312 Mega World International, Ltd 
Bus 003 Device 006: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 003 Device 005: ID 14aa:0225 AVerMedia (again) or C&E 
Bus 003 Device 004: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0aec:3050 Neodio Technologies Corp. ND3050 8-in-1 Card Reader
Bus 001 Device 004: ID 04b4:5500 Cypress Semiconductor Corp. HID->COM RS232 Adapter
Bus 001 Device 003: ID 0461:0340 Primax Electronics, Ltd Colorado 9600 Scanner
Bus 001 Device 001: ID 0000:0000  

sudo lshw etc
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:11:09:ba:13:7b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:de00-deff iomemory:fdefe000-fdefe0ff irq:20

*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:49:55:42:17
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.0 multicast=yes wireless=IEEE 802.11g

I think this shows that the system can see the USB device.  The network configuration shows a static IP address above, but I have found that automatic seems to produce a connection.  However at present it does not and I cannot even ping the router.  Uisng the IP address shown I can at least ping it.

---

