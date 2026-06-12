---
title: "Can't turn on wifi."
date: 2010-11-24
forum: New to Ubuntu
---

### Post by card0124 on 2010-11-24
I am using Ubuntu 10.04, and everything has been working great so far, with one big issue. I am unable to activate my wifi. when I right click the icon on the dock bar enable wireless is checked, but the hardware button on my laptop still shows that it is off. The hardware button is not working to turn it on. The button still works in windows. I want to use Ubuntu as my primary, but with no wifi there is no way that i can use it.

  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:f3:89:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

this is what shows up when I followed the troubleshooting instructions. Please help me here I don't know what to do. I am using an ethernet connection now and still nothing. If it helps my laptop is an hp entertainment pc.

---

### Post by ptn107 on 2010-11-24
Can you post the output of:

```
sudo lshw -c network
lspci -v
```

you should probably post in [_pastebin_]("http://paste.ubuntu.com/") and post the link.

---

### Post by card0124 on 2010-11-24
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by yankysunny on 2010-11-24
> **card0124 said:**
> Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

There is a typo is i might think of
sudo lshw -C network

---

### Post by card0124 on 2010-11-24
PCI (sysfs)  
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
       resources: irq:18 memory:d8500000-d8503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:ab:58:09
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:3000(size=256) memory:d2410000-d2410fff memory:d2400000-d240ffff memory:d2420000-d243ffff

---

### Post by 3rdalbum on 2010-11-24
With your Ethernet connection, go to System > Administration > Synaptic Package Manager. Go to Settings > Repositories. Make sure the first four checkboxes are ticked (this will mean that you'll have access to all Ubuntu software).

Close this window and click the Reload button in Synaptic Package Manager. When it's done doing its thing, close Synaptic and go to System > Administration > Hardware Drivers (it might be called "Additional Drivers" depending on your version of Ubuntu). If all goes well, you will be offered a driver to use.

---

### Post by card0124 on 2010-11-24
Installing the driver worked thank you very much. There was a few that popped up, but I was able to find the right one. Thank you for all your help.

---

