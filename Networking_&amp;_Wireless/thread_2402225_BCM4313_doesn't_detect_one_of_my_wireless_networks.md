---
title: "BCM4313 doesn't detect one of my wireless networks, it's slow and bad connection"
date: 2018-09-27
forum: Networking &amp; Wireless
---

### Post by rcrdo on 2018-09-27
Hi there.

I'm having some issues with my wireless adapter that haven't been solved by upgrading to Ubuntu 18.04.1
I can't see one of my wireless networks, the one I use to print, because it's the local network, when every other device can (phones, computers).

And even if I can connect to another network, my wireless connection is also pretty slow (compared to that of other devices connected to the same network), and it randomly disconnects and reconnects, which can be pretty frustrating if you're downloading something or trying to watch a video or similar things.

I've tried installing wicd, but it does nothing.
I don't know what to do and I'd like your advice.

This is the output of lshw -C network for my wireless adapter:

```
description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0b1
       version: 01
       serial: 00:1b:b1:a3:0e:3d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.15.0-34-generic firmware=610.812 ip=10.2.118.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fc600000-fc603fff

```

Please, tell me if you need any other information.

Thanks.

---

