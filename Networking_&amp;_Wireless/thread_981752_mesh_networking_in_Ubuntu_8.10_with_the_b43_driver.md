---
title: "mesh networking in Ubuntu 8.10 with the b43 driver"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by gradedcheese on 2008-11-14
I wanted to mention that Intrepid Ibex pretty much supports draft-802.11s mesh networking out of the box with the b43 driver (ie: most Broadcom wireless cards).  

If you have two or more PCs or laptops with that chipset (and the b43 driver working) and are interested in setting up a mesh, give it a shot.  I wrote up a quick [HOWTO]("http://andrey.thedotcommune.com/2008/11/mesh-networking-in-ubuntu-810.html") about it that I hope will be helpful.

---

### Post by pevir on 2009-02-10
I'd like to give mesh a try with my IBM Thinkpad T40. I was wondering is it even possible to try out mesh with the following network devices (result of lspci -v | less) :

02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation Unknown device 2551
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
        Subsystem: IBM ThinkPad R40
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at c0201000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8000 [size=64]
        Capabilities: <access denied>

It seems that there isn't mesh supported drivers for Intel network adapters according to [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers) 

So I need to get a Broadcomm card or ZyDAS based adapter in order to get mesh working?

---

