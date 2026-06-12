---
title: "HP Pavilion dv6000+ Atheros wifi"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Manji on 2008-03-02
I just got a HP dv6700 laptop with AMD 64bit anthlonx2. *Everything* is working fine out of the box for Ubuntu "except for the wifi". It happens to be using the Atheros chip sets, and I'm not having much luck of coming to a solution and finding on anything on the web about this. Anyone has a suggestion about this problem???

> description: Ethernet controller
       
product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       
vendor: Atheros Communications, Inc.
       
physical id: 0
       
bus info: pci@0000:03:00.0
       
version: 01
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress msix cap_list
       
configuration: latency=0



---

### Post by Fuzey on 2008-03-07
I just got the same laptop and I'm having the same issue. Were you able to figure it out?

---

### Post by petri.p on 2008-03-10
> **Fuzey said:**
> I just got the same laptop and I'm having the same issue. Were you able to figure it out?

I have an HP Pavilion dv6732, and the Ubuntu madwifi driver does not work with it... because the chip is actually an Atheres 5007eg, not Atheros 5006eg. lspci reports it incorrectly.

There is an experimental driver for it which works with 32 bit kernels, I followed the directions from this link, and it works for me:

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")

---

### Post by eks on 2008-05-22
I've got the same problem as well.

But I'm not too fond of using a wrapper to be able to use wifi... has anyone tried the ath5k driver?

[http://madwifi.org/wiki/About/ath5k](http://madwifi.org/wiki/About/ath5k)

I will, but maybe only tomorrow when I get some free time...



eks

---

