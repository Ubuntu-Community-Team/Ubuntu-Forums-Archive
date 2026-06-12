---
title: "Hotplug Problems with USB Ethernet Adapter"
date: 2005-08-05
forum: Networking &amp; Wireless
---

### Post by Edozien on 2005-08-05
OBJECTIVE

I hope the following issue and workaround is useful to someone in the forum. 

I set up an x86 Linux router with six Ethernet interfaces. I used an EPIA-CL Mini-ITX motherboard with a DC power supply. The board has certain features required for my application. The board has two Ethernet ports and four USB ports. The major shortcoming of this mother board is that it has only one PCI slot.

I used an Intel PRO/1000 dual port server adapter. The quad port version does not work with the EPIA's 3.3V PCI slot.

I used two Linksys USB Ethernet adapters to complete the six Ethernet ports. 

I used Ubuntu Linux Hoary Hedgehog 5.04 as the operating system. 

I used quagga as the dynamic routing daemon. 

All software was properly installed. The system was configured to detect all devices using the Linux hotplug subsystem. 


THE PROBLEM

The issue I wish to submit concerns an apparent incompatibility with the USB Ethernet adapters. 

The system boots up properly when the USB adapters are not plugged in. Once the system has booted up, the USB adapters can be plugged in. The USB adapters and all six Ethernet ports are then correctly initialized by the hotplug subsystem. 

The two on-board Ethernet ports are assigned eth0 and eth1. The two ports of the Intel PRO/1000 are assigned eth2 and eth3. The USB adapters are assigned eth4 and eth5. They all work properly thereafter. 

Unfortunately my application requires occasional remote reboots of the system so it is not practical to have to remove the USB adapters before a reboot and then re-insert them after the system completes rebooting.

However if the system is booted up with the USB adapters plugged in, the system hangs while "Starting hotplug subsystem". I was able to enable verbose mode to narrow down the problem to execution of /etc/hotplug/usb.rc. The specific problem seems to be in maybe_stop_usb ().


THE WORKAROUND

To get around this problem, I decided to configure the interfaces manually rather than using the hotplug subsystem. 

I edited /etc/network/interfaces to disable hotplug configuration of the interfaces. The resulting /etc/network/interfaces file does not configure any interfaces besides the lo interface.

I created /etc/rcS.d/S99manual-interfaces which uses ifconfig to set up the six interfaces manually. 

With this arrangement I can reboot the system with the USB adapters plugged in and the manual configuration script configures all interfaces correctly. However the interfaces are numbered differently. The two on-board Ethernet ports are still assigned eth0 and eth1. The two ports of the Intel PRO/1000 are now assigned eth4 and eth5. The USB adapters are now assigned eth2 and eth3. They all work properly.


REQUEST

I wonder if someone can explain the behaviour I encoutered. I also wonder if there is a more elegant solution to this problem that preserves hotplug configuration of all devices and interfaces. 

Edozien

---

