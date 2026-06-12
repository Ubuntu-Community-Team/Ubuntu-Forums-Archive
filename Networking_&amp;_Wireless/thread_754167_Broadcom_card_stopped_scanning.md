---
title: "Broadcom card stopped scanning"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by Julolidine on 2008-04-13
Well I just restarted my computer, and my Broadcom card, which had been working perfectly decided to stop scanning.

This is a Brodcom 4306 with ndiswrapper.

```

david@david-dell:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


```

```

david@david-dell:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:2f:d3:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,03/23/2006, 4.40.1 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


```

I tried completely removing the card, and then reran ndiswrapper to get it going, but no luck.  Tried rmmod ndiswrapper, and then reinserted, still nothing.  Any ideas?  :confused:

---

### Post by Julolidine on 2008-04-13
^

---

### Post by Julolidine on 2008-04-14
Don't have much more new info, still doesn't work.  Have tried a couple different things - like going back to fwcutter, but it didn't work.

---

