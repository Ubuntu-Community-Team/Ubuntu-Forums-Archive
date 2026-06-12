---
title: "Can't connect to the internet wirelessly through xUbuntu"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by frank39 on 2014-03-22
Hi all,

Complete beginner here. Have installed ubuntu through vmware player on my laptop. Can connect to the internet fine on windows but not through ubuntu. I have been trying to follow this guide "http://docs.xubuntu.org/1304/internet-networks.html#network-troubleshoothing-wifi-on". The network icon allows me to check "enable networking" but there is no "enable wireless" coming up at all. I followed the "check if the device is recognized" and got this output:

 *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:ee:f3:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes
       resources: irq:19 ioport:2000(size=128) memory:e7b00000-e7b0ffff


It doesn't say enabled, disabled, claimed or unclaimed anywhere.

I also attempted the "chechking for connection to the router" section and got:

lo        no wireless extensions.


eth0      no wireless extensions.

Any advice? I'm slowly losing it here.


Cheers

---

### Post by PartisanEntity on 2014-03-22
*Moved thread to Networking & Wireless Forum.*

---

### Post by Vladlenin5000 on 2014-03-22
Are you talking about a virtual machine ((...) *installed ubuntu through vmware player* (...))?
If so no wonder it hasn't recognized any other network device than the Ethernet and even that depends on how the network/internet access has been configured to that VM.

---

### Post by frank39 on 2014-03-22
> **Vladlenin5000 said:**
> Are you talking about a virtual machine ((...) *installed ubuntu through vmware player* (...))?
If so no wonder it hasn't recognized any other network device than the Ethernet and even that depends on how the network/internet access has been configured to that VM.

Yes I'm running it through a virtual machine. Do you know how I can set up wireless internet through this?

---

### Post by Vladlenin5000 on 2014-03-22
The first question is why so you want to do that? Assuming there's already an internet connection of some sort in the host OS the usual default is for the VM to have the same access the host has via a virtual network adapter. This can be changed according to specific needs but if you just need internet/LAN connection for the VM the defaults are fine.

In order to use a physical device and have a different network connection configured with it in the VM the said device will become unavailable to the host OS. So, if the WiFi device is already in use by the host you can't use in the VM. VMWare lets you "assign" USB devices to the VM and then they should be installed and configured the same way they would in a natively installed OS.

---

