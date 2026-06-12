---
title: "Ubuntu 15.04 network, UbuntuGnome 15.04 no network"
date: 2015-05-18
forum: Networking &amp; Wireless
---

### Post by Tuumke on 2015-05-18
Hello guys, 

Been looking for a few days now. I'm having troublews with Ubuntu Gnome 15.04
This is the situation:

Laptop: HP Probook 650 G1
Software: Windows 7 and Ubuntu Gnome 15.04
Problem description:
When using Windows, i can do anything without problems. But when switching to UbuntuGnome 15.04, i do have wired network but im not getting DHCP ip adress.
On a different 650 laptop with Ubuntu 15.04, i do have wired and wireless network with the same network drivers etc...

Now, while typing this, the wired connection came up. So i got an IP adress.. thank god

Now my wireless is still not working. When using: Additional Drivers, i can say that the system needs to use Sourcode from Broadcom 802.11 Linux STA-driver from bcmwl-kernel-source, but when applying, it just gets stuck somehow.
Help?

>   *-network       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: a0:d3:c1:9c:b8:81
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.12-3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:28 memory:d0700000-d071ffff memory:d073f000-d073ffff ioport:3080(size=32)
  *-network
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:18 memory:d0500000-d0503fff

> tijmen@LT12118:~$ dmesg | grep iwltijmen@LT12118:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2015-05-18
> Now my wireless is still not working. When using: Additional Drivers, i can say that the system needs to use Sourcode from Broadcom 802.11 Linux STA-driver from bcmwl-kernel-source, but when applying, it just gets stuck somehow.It would be most helpful to see how it gets stuck. Please try to install the driver from the terminal so you can see and then post the result:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Thanks.

---

### Post by Tuumke on 2015-05-18
Fixed it with:
```

sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source

```

---

