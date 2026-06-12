---
title: "Broadcom Wake-on-Lan Not Working (Dell Inspiron 6400 / 1505)"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by ben103 on 2014-08-26
Hi all,

I have been unsuccessfully trying to get Wake-on-Lan working on my Dell Inspiron laptop with onboard Broadcom Ethernet controller on ubuntu 14.04.
Here is what I have tried so far:
[LIST]
[*]Enable WOL in BIOS does not seem possible as there is no such entry
[*]ethtool eth0 gives me:
[/LIST]
```
[FONT=Menlo]Settings for eth0:[/FONT]
[FONT=Menlo]    Supported ports: [ MII ][/FONT]
[FONT=Menlo]    Supported link modes:   10baseT/Half 10baseT/Full [/FONT]
[FONT=Menlo]                            100baseT/Half 100baseT/Full [/FONT]
[FONT=Menlo]    Supported pause frame use: No[/FONT]
[FONT=Menlo]    Supports auto-negotiation: Yes[/FONT]
[FONT=Menlo]    Advertised link modes:  10baseT/Half 10baseT/Full [/FONT]
[FONT=Menlo]                            100baseT/Half 100baseT/Full [/FONT]
[FONT=Menlo]    Advertised pause frame use: Symmetric Receive-only[/FONT]
[FONT=Menlo]    Advertised auto-negotiation: Yes[/FONT]
[FONT=Menlo]    Speed: 100Mb/s[/FONT]
[FONT=Menlo]    Duplex: Full[/FONT]
[FONT=Menlo]    Port: Twisted Pair[/FONT]
[FONT=Menlo]    PHYAD: 1[/FONT]
[FONT=Menlo]    Transceiver: internal[/FONT]
[FONT=Menlo]    Auto-negotiation: on[/FONT]
[FONT=Menlo]    MDI-X: Unknown[/FONT]
[FONT=Menlo]    Supports Wake-on: g[/FONT]
[FONT=Menlo]    Wake-on: g[/FONT]
[FONT=Menlo]    Current message level: 0x000000ff (255)[/FONT]
[FONT=Menlo]                   drv probe link timer ifdown ifup rx_err tx_err[/FONT]
[FONT=Menlo]    Link detected: yes[/FONT]

```
[LIST]
[*]cat /proc/acpi/wakeup gives me the following, so my network card (PCIE) should be able to wake the system
[/LIST]
```
[FONT=Menlo]cat /proc/acpi/wakeup[/FONT]
[FONT=Menlo]Device    S-state      Status   Sysfs node[/FONT]
[FONT=Menlo]LID      S3    *enabled [/FONT]
[FONT=Menlo]PBTN      S4    *enabled [/FONT]
[FONT=Menlo]MBTN      S5    *disabled[/FONT]
[FONT=Menlo]PCI0      S3    *disabled  no-bus:pci0000:00[/FONT]
[FONT=Menlo]USB0      S3    *enabled   pci:0000:00:1d.0[/FONT]
[FONT=Menlo]USB1      S3    *enabled   pci:0000:00:1d.1[/FONT]
[FONT=Menlo]USB2      S3    *enabled   pci:0000:00:1d.2[/FONT]
[FONT=Menlo]USB3      S3    *enabled   pci:0000:00:1d.3[/FONT]
[FONT=Menlo]EHCI      S3    *enabled   pci:0000:00:1d.7[/FONT]
[FONT=Menlo]AZAL      S3    *disabled  pci:0000:00:1b.0[/FONT]
[FONT=Menlo]PCIE      S4    *enabled   pci:0000:00:1e.0[/FONT]
[FONT=Menlo]RP01      S4    *disabled  pci:0000:00:1c.0[/FONT]
[FONT=Menlo]RP02      S3    *disabled[/FONT]
[FONT=Menlo]RP03      S3    *disabled[/FONT]
[FONT=Menlo]RP04      S3    *disabled  pci:0000:00:1c.3[/FONT]
[FONT=Menlo]RP05      S3    *disabled[/FONT]
[FONT=Menlo]RP06      S3    *disabled[/FONT]

```
[LIST]
[*]I have the following lines of code in rc.local to ensure that wol is always on and that PCIE can always wake the system:
[/LIST]
```

[FONT=Menlo]ethtool [/FONT][COLOR=#34BD26][FONT=Menlo]-s[/FONT][/COLOR][FONT=Menlo] eth0 wol g
[/FONT][COLOR=#000000][FONT=Menlo]sh -c [/FONT][/COLOR][B]"echo PCIE > /proc/acpi/wakeup"
[/B]
```

[LIST]
[*]I am using a static ip address:
[/LIST]
```
[FONT=Menlo]ifconfig[/FONT][FONT=Menlo]eth0      Link encap:Ethernet  HWaddr 00:15:c5:af:2b:8d  [/FONT]
[FONT=Menlo]          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT]
[FONT=Menlo]          inet6 addr: fe80::215:c5ff:feaf:2b8d/64 Scope:Link[/FONT]
[FONT=Menlo]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=Menlo]          RX packets:3013 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=Menlo]          TX packets:1904 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=Menlo]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=Menlo]          RX bytes:999610 (999.6 KB)  TX bytes:213900 (213.9 KB)[/FONT]
[FONT=Menlo]          Interrupt:17[/FONT]
```
[LIST]
[*]I am using the following ethernet card
[/LIST]
```
[FONT=Menlo]lshw -class network[/FONT][FONT=Menlo]  *-network               [/FONT]
[FONT=Menlo]       description: Ethernet interface[/FONT]
[FONT=Menlo]       product: BCM4401-B0 100Base-TX[/FONT]
[FONT=Menlo]       vendor: Broadcom Corporation[/FONT]
[FONT=Menlo]       physical id: 0[/FONT]
[FONT=Menlo]       bus info: pci@0000:03:00.0[/FONT]
[FONT=Menlo]       logical name: eth0[/FONT]
[FONT=Menlo]       version: 02[/FONT]
[FONT=Menlo]       serial: 00:15:c5:af:2b:8d[/FONT]
[FONT=Menlo]       size: 100Mbit/s[/FONT]
[FONT=Menlo]       capacity: 100Mbit/s[/FONT]
[FONT=Menlo]       width: 32 bits[/FONT]
[FONT=Menlo]       clock: 33MHz[/FONT]
[FONT=Menlo]       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT]
[FONT=Menlo]       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.10 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s[/FONT]
[FONT=Menlo]       resources: irq:17 memory:efbfe000-efbfffff[/FONT]
```

[LIST]
[*]I am powering off using sudo pm-suspend or sudo pm-suspend-hybrid
[/LIST]

When trying to wake-up using wakeonlan and the MAC address from a different computer, nothing happens and the computer continues sleeping.
Using wakeonlan on my Synology NAS everything works fine.

Do you have any idea what I am missing?

Thanks!

---

