---
title: "Trying to get wireless on IBM R51 with ubuntu- already tried going through help guide"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by azneinstein on 2006-09-13
Hi guys, this is my first time working with linus, so please be gentle. I can't seem to connect to the internet, I don't think my driver was installed. It's a IBM R51, with the Intel Pro/Wirelles 3300BG card.

when I typed sudo lshw -C network, it comes up with:
description: Wireless Interface
product: Pro/Wireless 2200BG
vendor: Intel Corporation
physical id: 2
bus info: pci@02:02.0
logical name: eth0
version: 05
serial: 00:12:f0:d3:c9:be
width: 32 bits
clock: 33mhz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver-ipw3300 driverversion=1.1.1 firmware:ABG:9.0.2.6 (Mar 22 2005) link: no multicast-yes wireless=unassociated
resources: iomemory: d0200000-d0200fff irq:11

When I type- sudo iwconfig
it lists lo, irda0, eth0, and sit0 with "no wireless extensions"

What steps are needed now to get the proper drivers loaded? Thanks a lot. -Ken

*Let me know if I'll need to use windows drivers with wine... and how to do that as well, thanks.

---

