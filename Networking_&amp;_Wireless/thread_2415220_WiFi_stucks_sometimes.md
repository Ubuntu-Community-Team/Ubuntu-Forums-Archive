---
title: "WiFi stucks sometimes"
date: 2019-03-22
forum: Networking &amp; Wireless
---

### Post by abylikhsanov on 2019-03-22
I have recently installed Ubuntu 18.04 on my laptop and WiFi sometimes starts to work very poor and the download speed drops dramatically. Then, I have to restart the wifi:
```
sudo service network-manager restart
```

After whcih, I get my normal speed.

Some information about my WiFi card:

```
[COLOR=#333333][FONT=monospace]lshw -C network[/FONT][/COLOR]
```:

```
 *-network                 
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 30
       serial: 48:a4:72:62:0f:39
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.18.0-16-generic firmware=38.c0e03d94.0 ip=192.168.86.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:a1310000-a1313fff



```

As my drivers are installed, I can't understand what might be wrong.

---

