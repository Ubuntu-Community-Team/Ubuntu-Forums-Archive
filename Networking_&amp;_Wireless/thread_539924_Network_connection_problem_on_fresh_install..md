---
title: "Network connection problem on fresh install."
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by kellyjosephprice on 2007-08-31
This roommate of mine complained about his computer running slow.  It was bogged down with a town of spyware.  So I installed kubuntu for him, but now it won't connect to the internet.  I'm behind a dsl modem/router and it has an Intel 82801db PRO/100 ve Ethernet controller.
Please help.

---

### Post by noob12 on 2007-09-01
I  think the e100 driver should claim the device.  If there are problems, the most likely causes are the prom checksum or some issue with PCI routing.
We need to see what's going on.

Can you post the output of these (if possible, use a USB drive to transfer text off the host) and to the machine from which you are posting.

```

lspci -nn

sudo lshw -C network

dmesg

```

UPDATE:  I've stopped watching this thread.  PM me if you want help.

---

