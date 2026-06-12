---
title: "ethernet cards renamed - I am lost"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by wsw70 on 2007-08-16
Greetings,

I am brand new to ubuntu (and quite aged in linux :)) and completely lost in how the ethernet cards are named and renamed.
I am on 7.04, my two ethernet cards (one built-in, the other one PCI) are recognized by lspci and the appropriate modules are loaded. With appropriate configuration they work fine.

**Summary of the issue**: there are three interfaces discovered during boot (eth0, eth1, and eth2) and of these only eth1 and eth2 exist after the boot process
**Question**: how do the dicovery work in ubuntu? Why teh PCI card is first recognized as eth0 and then renamed to eth2 (and eth0 dissapears)

/etc/networks/interfaces:
```

auto lo eth1 eth2
iface lo inet loopback
iface eth2 inet static
    (address, mask, gateway for eth2)
iface eth1 inet static
    (address, mask, gateway for eth1)

```

The output of "grep eth /var/log/dmesg":

```

eth0: RealTek RTL8139 at 0xf886cf00, 00:05:5d:50:df:c7, IRQ 16
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
eth1: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 
eth1: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
eth1: dma_rwctrl[76180000] dma_mask[64-bit]
eth2: link up, 100Mbps, full-duplex, lpa 0x41E1

```

I would appreciate any help here. The built-in card is systematically assigned eth1, so my understanding is that the PCI card is discovered forst, assigned eth0, then comes the buil-in one, and then some magic happens (maybe due to the /etc/network/interfaces content? I am widly guessing here) and it gets renamed to eth2.

Thanks!
Wojtek

---

### Post by noob12 on 2007-08-16
Take a look at **/etc/iftab**.  Make sure that any mapping for eth0 has the mac address 00:05:5d:50:df:c7 for the card that you want to be eth0.  If it has a different one, it will get renamed by udev to avoid the name collision.

It sounds like what is happening is that the driver is picking eth0 as its name, which holds until udev comes around and renames it eth2.  Seems consistent with the logs anyway.

If you are doing funny things with mac cloning try to avoid using the mac addr as the basis of the iftab mapping.  Instead use one of the alternatives.  See **man iftab** and **man udev** for more info.

---

### Post by wsw70 on 2007-08-17
> **noob12 said:**
> Take a look at **/etc/iftab**.  Make sure that any mapping for eth0 has the mac address 00:05:5d:50:df:c7 for the card that you want to be eth0. 


You are correct. /etc/iftab had en entry for eth0. no idea how it was generated, probably automatically during the installation.

> It sounds like what is happening is that the driver is picking eth0 as its name, which holds until udev comes around and renames it eth2. 

Very likely. Now that I know about iftab I will investigate further.

THANKS a lot for the help.

Wojtek

---

