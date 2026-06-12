---
title: "Intrepid Fresh Install - Sees Radio, Driver, But Still No Wireless"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by N00bB00b on 2008-11-12
Noob here.

I did a fresh install of Intrepid on an Acer Aspire 3680.

It has an Atheros AR5BXB63 Radio.

I have no idea what I'm doing.  However, I have done the following:
1) Booted into Windows and made sure the radio was functioning and turned on.
2) Went to System->Administration->Hardware Drivers shows "Support for Atheros 802.11 wireless LAN cards.", and has a green light.  This is the driver that Intrepid installed.

3) ```
[B]lshw -C network
[/B]
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:fc:44:db:98:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

4)```
**lspci**

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

5)```
**lsmod**

wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci

```

6)```
**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by N00bB00b on 2008-11-13
bumping thread so hopefully someone sees it

---

