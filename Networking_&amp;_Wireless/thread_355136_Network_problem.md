---
title: "Network problem"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by spiked79 on 2007-02-06
I have just installed Xubuntu on my laptop.  The problen that I am having is that I can not get my network card to be reconized.  It is a Xircim Realport Cardbus Ethernet 10/100.  Does anyone know of a site to get a driver for it?

Thanks.

---

### Post by spd106 on 2007-02-07
It should be supported out of the box.
Can you post the output you get from entering the following at a terminal. ```
lshw -C network
```
Most of the cardbus drivers are available from [http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html)

---

### Post by spiked79 on 2007-02-07
Hardware Lister (lshw) - B.02.06
usage: lshw [ -format ] [ -options ...]
           lshw -version
           
           -version  print program version (B.02.06)

format can be
          -html       output hardware tree as HTML
          -xml        output hardware tree as XML
          -short      output hardare paths
          -businfo   output bus information

options can be
          -classClass       only show a certian class of hardware
          - c Class           same sa '-class CLASS'
          -disable TEST    disable a yeat (like pci, isapnp, cpuid, etc.)
          -enable TEST     enable a test (like pci, isapnp, cpuid, etc.)

Hope this help.

Thanks,
Spiked79

---

### Post by spd106 on 2007-02-08
Can you try that again with a capital C, or copy/paste if you can. It should look something like this, though not wireless.
```
~$ sudo lshw -C network
*-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@01:0a.0
       logical name: wlan0
       version: 03
       serial: 00:11:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=10.x.x.x multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e7000000-e7001fff irq:209

```

---

### Post by spiked79 on 2007-02-08
Every time I try that it tells me:
"WARNING: you should run this program as a supers user."
How do I switch to be a super user?

Thanks,
Spiked79

---

