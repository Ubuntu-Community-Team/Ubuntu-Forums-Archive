---
title: "Problem with Gigabyte GA_965P_DS3 (Marvell Tech Group) on board ethernet"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by xenomorph99 on 2007-04-22
Hi,

I have a problem with this motherboard and 7.04. I can acquire an IP address via DHCP but accessing the net is good for about 10 seconds.

infocentre reports a "Ethernet controller: Marvell Technology Group Unknown Device 4364 (rev12)
Subsystem: Gigabyte Tech....... Unknown device e000
etc

I'm assuming that this on board LAN controller is not supported (maybe incorrectly). Is there a workaround for this?

I do have another PCI network card that I can use but I'd like to get the onboard one working.

Ta,
Xeno

---

### Post by chili555 on 2007-04-22
I think this adapter is using the sky2 module which you can verify with ```
lsmod | grep sky2
```I believe it's a known bug in the sky2 module. Check here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009)

There is a fix described about 3/4 of the way down.

---

