---
title: "Overriding built-in wireless w/ PCCard (upgrading)"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by ben.s on 2008-08-16
Hi Folks,

I'm tearing my hair out about this one.  I have a Thinkpad T40p with a built-in 802.11ab card (Atheros AR5211) -- it works fine, but I would like to take advantage of the Draft N network I've installed at home, so I bought a D-Link DWA-642 (Atheros AR5416).  The card is fully supported by MadWifi, according to their site.

I can see both cards in lspci:
```
02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
03:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)

```

And I can see them with 'lshw -C network':
```

  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:2e:25:6d
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:41:ea:af
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.201 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b
  *-network UNCLAIMED
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0

```

But try as I might I can't figure out the magic modprobe incantation to get the AR5416 recognized by iwconfig... I have ath0 (the AR5211), but no ath1.

Anyone have any advice?  There's no option in the BIOS to disable the on-board card.

---

