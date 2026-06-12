---
title: "Broadcom BCM4312 / HP Pavilion dv6"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by stcline on 2014-01-03
Just installed 13.10 on an HP Pavilion dv6.  Ethernet works but wireless does not.  I have run all updates but I am not sure where to go from here.  I am somewhat new to Ubuntu but can generally figured these things out if pointed in the right direction.  Thanks in advance for any guidance.

---

### Post by Bucky Ball on 2014-01-03
Welcome. Post the output of:
```

sudo lshw -C network
```

Thanks.

Do you have anything in 'Additional Drivers'?

---

### Post by stcline on 2014-01-03
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:c6:26:c0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff


Additional Drivers says: Broadcom Corporation: U98Z049.00 Wireless Mini PCle Card (device not working)

---

### Post by Bucky Ball on 2014-01-04
Ok, try these three commands one after the other in a terminal (hit return between each). You will need to be online with a cable for it work:

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get purge b43-fwcutter firmware-b43-installer b43-pci-bridge bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*
```

At the moment you have the b43-pci-bridge driver installed. That is wrong.

---

### Post by stcline on 2014-01-04
I tried those.  I does not look like it worked.  I restarted and still no effect.  Here is the terminal results:

[COLOR=#000000][FONT=Arial]sudo apt-get remove bcmwl-kernel-source[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Package 'bcmwl-kernel-source' is not installed, so not removed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
sudo apt-get purge b43-fwcutter firmware-b43-installer b43-pci-bridge bcmwl*


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'bcmwl-kernel-source' for regex 'bcmwl*'
Note, selecting 'bcmwl-modaliases' for regex 'bcmwl*'
Package 'bcmwl-modaliases' is not installed, so not removed
E: Unable to locate package b43-pci-bridge


[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*

[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Note, selecting 'bcmwl-kernel-source' for regex 'bcmwl*'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Note, selecting 'bcmwl-modaliases' for regex 'bcmwl*'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Package firmware-b43-lpphy-installer is not available, but is referred to by another package.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This may mean that the package is missing, has been obsoleted, or[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]is only available from another source[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]However the following packages replace it:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  firmware-b43-installer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-01-04
Try:

```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

Reboot. If still no result, please post the output of these two commands (the second will show a file):

```
sudo lshw -C network
nano /etc/modprobe.d/blacklist.conf
```

---

### Post by stcline on 2014-01-04
That did it!  Thanks for the help.

---

### Post by Bucky Ball on 2014-01-04
I like it when a plan works out! Good news. Enjoy the OS, the forums and the learning curve. ;)

---

