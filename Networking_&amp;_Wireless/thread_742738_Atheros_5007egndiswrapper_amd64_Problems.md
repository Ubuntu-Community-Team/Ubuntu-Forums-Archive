---
title: "Atheros 5007eg/ndiswrapper amd64 Problems"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by mdramige on 2008-04-02
I'm running Hardy amd64 and am having a strange issue with an Atheros 5007eg. I'm using ndiswrapper with the windows xp amd64 driver.

The card works fine if I insert the ndiswrapper module manually, but when it loads via /etc/modules, I can't connect after booting.

Even if I keep it in /etc/modules, I can simply remove the module after boot and reload it. The card works fine after doing that. I'm trying to find a difference between kernel messages when the card is loaded at boot vs. loading manually.

I should also mention that if I let the module load at boot, I can still do a "iwlist wlan0 scan" and get a bunch of access points returned. When I try to connect to an access point, however, I get "ADDRCONF(NETDEV_UP): wlan0: link is not ready" every time it tries to connect.

**At boot:**
```

[   29.996474] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   30.448157] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   30.449832] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[   30.450484] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   30.450497] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   30.450556] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[   30.450690] PCI: Setting latency timer of device 0000:03:00.0 to 64

[   30.862656] ndiswrapper: using IRQ 19
[   30.863218] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   30.863230] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   30.863366] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   31.106733] wlan0: ethernet device 00:1e:4c:a8:9d:61 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   31.110912] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   31.111636] usbcore: registered new interface driver ndiswrapper
```


**After removing and reloading the ndiswrapper modules:**
```
[  155.806517] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  155.832896] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[  155.834583] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[  155.834838] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[  155.834883] ndiswrapper (ZwClose:2227): closing handle 0x0 not implemented
[  155.835040] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  156.198164] ndiswrapper: using IRQ 19
[  156.400170] wlan0: ethernet device 00:1e:4c:a8:9d:61 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[  156.404345] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  156.404423] usbcore: registered new interface driver ndiswrapper
```

Any ideas?

---

### Post by kevdog on 2008-04-02
How are you trying to connect after boot?  With Network Manager?  If so can you post your /etc/network/interfaces file?

---

### Post by mdramige on 2008-04-02
> **kevdog said:**
> How are you trying to connect after boot?  With Network Manager?  If so can you post your /etc/network/interfaces file?

I was originally using Network Manager, but am now using Wicd so that I can set different IP addresses for different networks. The problem hasn't changed since switching to Wicd. I can still connect fine after removing/inserting the module.

I just checked /etc/network/interfaces and nothing is listed for wlan0. Where is the config information for Wicd stored?

```

auto lo
iface lo inet loopback
```

---

