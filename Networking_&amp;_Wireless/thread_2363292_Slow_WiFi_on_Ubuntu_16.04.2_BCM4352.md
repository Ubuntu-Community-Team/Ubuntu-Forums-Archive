---
title: "Slow WiFi on Ubuntu 16.04.2 BCM4352"
date: 2017-06-08
forum: Networking &amp; Wireless
---

### Post by s3bax on 2017-06-08
Hey guys!

A few days ago I installed Ubuntu 16.04.2 LTS on a secondary HDD, so I'm new to Ubuntu.

So to begin with my WiFi Card is an Asus PCE-AC56 Dual-Band Wireless-AC1300 PCI-E Adapter :
```
*-network       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlp9s0
       version: 03
       serial: 08:62:66:bc:78:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.0.155 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7400000-f7407fff memory:f7200000-f73fffff



```

I had some trouble to install the driver for it but I finally managed to do so.

[IMG]http://i.imgur.com/IYnumdf.png[/IMG]

Everything works ok for a while then from times to times my internet speed drop, I can't load any page, in the System Monitor shows that I barely get a few KB/s speed, but this only happens on this SO, because if I test my speed on my phone it works perfectly.
Also, it only happens on this SO since I have Windows 10 x64 on a SSD and there no WiFi slowdowns.

Any help that someone could provide is appreciated.

Thanks you!

---

### Post by howefield on 2017-06-08
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by s3bax on 2017-06-08
> **howefield said:**
> Thread moved to the "*Networking & Wireless*" forum for a better fit.

Thanks you!

---

