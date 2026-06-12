---
title: "Linksys WMP54G not recognised"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by JebusWankel on 2006-08-31
I just installed a Linksys WMP54G PCI wireless card on my computer running Dapper. When I turned it on after I put the card in it wouldn't boot to harddrive, it showed the Dell screen and stood there. The third restart I put in the Dapper live cd and told it to boot to harddrive and that fixed it. Now it seems that the card isn't fully recognized. sudo lshw comes up with this:

*-network:0 UNCLAIMED
                description: Network controller
                product: RaLink
                vendor: RaLink
                physical id: 8
                bus info: pci@01:08.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:ff8e0000-ff8e7fff irq:11

Device Manager shows

Vendor: RaLink
Device: Unknown (0x0301)
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown
OEM Vendor: Linksys
OEM Product: Unknown (0x0055)

Doesn't show up in iwconfig. ifconfig shows

eth0      Link encap:Ethernet  HWaddr 00:04:76:B9:00:58
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1656 (1.6 KiB)  TX bytes:1656 (1.6 KiB)


Network Settings doesn't show it under Connections.

I don't think the card is being recognized as ra0, so anything requiring that probably won't work, but I'll give it a shot.

Do I just need a driver? I searched Synaptic and the two drivers that showed, the rt2400 and rt2500 were only available as source, which I'd rather not compile myself if there's an easier way.

In the online documentation it seemed like the card would work once I pointed it to the network. That's why I picked this card. My experience and what I've read in the forums suggest otherwise.

I love Ubuntu and the friendly atmosphere on the forums. Thank you for reading this post even if you don't respond. If you do, thank you doubly so.

---

### Post by bionnaki on 2006-09-01
try this: [http://www.ubuntuforums.org/showthread.php?t=241565](http://www.ubuntuforums.org/showthread.php?t=241565)

---

### Post by JebusWankel on 2006-09-02
Update: card recognized and working fine under Dapper live CD

---

