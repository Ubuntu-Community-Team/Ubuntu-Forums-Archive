---
title: "trying to set up a WPA secured wireless network with ndiswrapper"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by analyzer92 on 2008-07-31
Okay where do I begin.

For the past 2 days I have been trying to set up my wireless network and things aren't looking very good. My wireless adapter has a BCM4306 chipset. I first tried getting wireless with the b43 driver. After installing b43-fwcutter and I was able to see wireless networks in my nm-applet as well as when I typed in ```
iwlist scan
```. However, whenever I tried to connect to my network, it would either not connect or connect and say at 0%. So I decided that ndiswrapper is supposed to faster anyway so I tried to do that. I installed the driver did a whole bunch of things all these tutorials tell me to do and I did what I could with disabling the b43 driver. Now my computer doesn't think wlan0 doesn't exist. When I type in ```
lshw -C network
```, this is what I get:

```
martin@martin-desktop:~/broadcom$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:03:47:a1:90:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

```

One thing I noticed was that the driver and module were not ndiswrapper. Could this be the problem.

Also, I tried using wpa_supplicant and it wouldn't work but I am guessing that is because the b43 driver wouldn't work and the ndiswrapper driver isn't currently working.

Thanks in advance.

---

