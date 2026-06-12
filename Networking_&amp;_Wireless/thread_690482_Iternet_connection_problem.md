---
title: "Iternet connection problem"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by tentel on 2008-02-07
I've been browsing through threads for a couple days now, and i simply cannot get my  bcm43xx card to work.

when i type in sudo lshw -C  network

i get back

 *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0




and i used ndisgtk to install the bcmwl5.inf, and it worked fine.  it tells me the driver is installed.


when i use the resticted drivers  manager, and put the same command into the terminal, it gives me much more information including the driver that is installed and whatnot, and it tells me it is eth1, but every time i have the restricted manager running my entire system becomes extremely laggy and unusable.


does anyone have any idea what might be wrong?  or any possible solution?


i'm at my wits end.

---

### Post by Hightide on 2008-02-07
HI tentel

There is a problem with driver installation as it states '*-network UNCLAIMED'. Have a look at Kevdogs wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188") for more information 

regards

:)

---

