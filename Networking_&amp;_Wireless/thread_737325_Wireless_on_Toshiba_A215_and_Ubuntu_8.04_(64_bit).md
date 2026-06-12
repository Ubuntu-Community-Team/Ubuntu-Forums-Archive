---
title: "Wireless on Toshiba A215 and Ubuntu 8.04 (64 bit)"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by soofsoof on 2008-03-27
Hi all,

I have Toshiba A215-4697 (64 bit AMD) with and Atheros wireless card. I installed Ubuntu 8.04 (64 bit version).

lshw says:
 *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

And under system->administration->hardware drivers I have:
Atheros hardware access layer (HAL) - Enabled and in use
Support for Atheros 802.11 wireless lan card - Enabled and in use.

So the "system knows" about my card, but nothing is working. In network manager I don't see any wireless interface or networks.

Any ideas?

---

### Post by siafulinux on 2008-03-27
I am having the same problem with a Toshiba P205D-S7802 system.

---

### Post by lalelu on 2008-03-28
This may help you:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
It worked for me. (Asus X50R)

But "At this time, AR5007 support is limited to x86 (32bit)!"

---

### Post by scottro on 2008-03-28
[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

It's my page, and that will tell you how to determine if it's the card referenced by the Madwifi trouble ticket.  It also has a link to a thread on these forums where someone got that card working in 64 bit.

---

### Post by lalelu on 2008-03-28
> Running the command /sbin/lspci -nn should show, however a vendor ID of 168c:001c.
I don't know if this is Ubuntu specific, but i think it's:
```
/bin/lspci
```
or
```
/usr/bin/lspci
```

Edit: Or just lspci

---

### Post by scottro on 2008-03-28
Thank you.  That was originally written for Fedora, and will be changed in a few minutes. 

(By the time I played with Ubuntu on the machine, I already knew that it was an AR5007EG, which is no excuse for putting up inaccurate information.)

---

