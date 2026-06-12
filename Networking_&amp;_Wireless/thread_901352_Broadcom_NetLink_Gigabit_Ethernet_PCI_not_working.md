---
title: "Broadcom NetLink Gigabit Ethernet PCI not working"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by mstipanov on 2008-08-26
Can someone please help?

I have a problem with my network adapter.

lshw -C reports:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

There is no network card in windows...

I tried removing and adding tg3 module, but it didn't help.

I'm struggling with this for 4 days now, and I don't have any more ideas.

Oh yes .... I'm using Ubuntu 8.04, and the card worked fine until last week.

I also tried Xubuntu and Ubuntu versions 6.06 and 8.04 with same results.

I read that it may be a faulty NIC ROM, and that I should try to flash it, but b57udiag utility didn't recognize any cards ...   

Thanks.

---

