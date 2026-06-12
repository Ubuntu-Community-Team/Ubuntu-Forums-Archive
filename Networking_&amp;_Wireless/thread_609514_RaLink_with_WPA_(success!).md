---
title: "RaLink with WPA (success!)"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by yaidiot! on 2007-11-11
I finally got around to upgrading to Gutsy this morning. I'd been putting it off because my wireless card had been a bit fickle with Feisty and browsing the forum posts it didn't look like Gutsy would be any better. Actually, it worked out of the box! After futzing for a bit I realized I needed just two lines --

```
sudo rm /etc/network/interfaces
sudo /etc/init.d/dbus restart
```

This is the info on the device, ra0:
```
04:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: RaLink Unknown device 2560
        Flags: bus master, slow devsel, latency 64, IRQ 23
        Memory at faafc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
```

Modules:
```
~$ lsmod |grep rt2
rt2500pci              19072  0 
rt2x00pci              11520  1 rt2500pci
rt2x00lib              19584  2 rt2500pci,rt2x00pci
rfkill                  8208  2 rt2x00lib
mac80211              171016  4 rc80211_simple,rt2500pci,rt2x00pci,rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
eeprom_93cx6            3200  1 rt2500pci
```

Wireless WPA out of the box, and faster boot time as well! Ubuntu just keeps getting better!

---

