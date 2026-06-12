---
title: "Ubuntu 15.04 &amp; Broadcom 4352"
date: 2015-07-27
forum: Networking &amp; Wireless
---

### Post by Vormeph on 2015-07-27
A month ago I got a dell xps 13 and installed Ubuntu 15.04. Getting the wireless was a pain as it involved tethering my phone to the laptop and then installing the broadcom proprietary drivers. Today, the wireless connection seems to hang from time to time for no apparent reason. I thought it was a problem with my router but it doesn't look like it because my phone (with mobile data switched off) can browse the web just fine with no problems at all, no hangs or nothing. Here is some info regarding the hardware:

```

  *-network               
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: c4:8e:8f:f5:c8:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.64 latency=0 multicast=yes wireless=IEEE 802.11abg

```

I don't know what's causing the internet to hang, but I also found out that while the internet hangs if I click on my SSID (causing it to dc and reconnect) then the system freezes. Thus, I can only derive a conclusion that it has something to do with the driver. I don't know what else I could do, so I'm here asking for help as to how I can solve the internet freezes, and maybe forward the bug that my system freezes (I have to cold reboot; the caps lock flashing asks for it!) in order to resolve the said issue.

---

### Post by kerry_s on 2015-07-27
when the caps lock flashes, that means the kernel crashed.

for your future knowledge, the drivers are in/on the installer iso. so say you boot up live, just run additional drivers & you will have working wifi. if you select install third party during install it will install the drivers at the same time so after reboot wifi should work.

click on the network icon-> edit connections, delete the wifi & set it up again like you do a fresh install.

---

### Post by kerry_s on 2015-07-27
sorry, forum hiccup
kept giving error, so i just clicked reload & that happened.

---

### Post by Vormeph on 2015-07-28
> **kerry_s said:**
> when the caps lock flashes, that means the kernel crashed.

for your future knowledge, the drivers are in/on the installer iso. so say you boot up live, just run additional drivers & you will have working wifi. if you select install third party during install it will install the drivers at the same time so after reboot wifi should work.

click on the network icon-> edit connections, delete the wifi & set it up again like you do a fresh install.

But, you see, that's not what happened with me. I did select third party during the install but when I rebooted from the live install into the actual install the wifi was just disabled, hence the big process in trying to get it all back up again. If there's a kernel crash, then it must be something to do with the driver itself.

---

