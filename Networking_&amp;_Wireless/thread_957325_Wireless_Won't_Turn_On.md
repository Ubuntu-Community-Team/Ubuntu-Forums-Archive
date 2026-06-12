---
title: "Wireless Won't Turn On"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by Chary on 2008-10-24
Hello all.

Yet another wireless issue to add to the masses. Basically, my laptop (like most, if not all?) has a switch to enable and disable the wireless capabilities on the laptop. So, it's currently switched off (the amber light indicates it, it should be blue when on) and nothing I do can make it come on. I've flicked the switch in all directions and positions, the light still staying amber. I've restarted each time I've changed it's position, no joy. My information is as follows:

OS: Ubuntu (Latest 64bit)
Laptop: HP Pavilion dv9821ea

Command outputs:

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

**lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:a0:e6:10
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=10.0.0.5 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```

I've read through most stickies and how to threads as well as searched the forums and nothing helped. I've tried disabling and re-enabling ipv6 as suggested in the documentation to no avail.

Now I'm no expert but I can clearly see that wireless isn't within the capabilities. The wireless network is definitely functionable because the windows laptop can pick it up and go on it fine.

I've played with nearly every network setting I can find under system >> Admin etc. The card works fine on wired so the network card itself is installed.

I noticed my network card wasn't on this list: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) but I was kind of hoping that since one type has managed to work for HP hardware hopefully mine can too. Do you suggest I try what's recommended for the "Pavilion zv5000"?

Any help / advice / comments on this would be greatly appreciated.

Best regards,

Chary.

---

