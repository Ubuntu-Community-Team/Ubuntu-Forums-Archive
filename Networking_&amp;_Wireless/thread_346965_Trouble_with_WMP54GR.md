---
title: "Trouble with WMP54GR"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by Cronosin on 2007-01-26
I'm trying to get my wireless working and keep running into trouble. I'm using 128-bit WEP (thanks to having a Nintendo DS), and my SSID has a space in it. Now, I don't know if that's causing the trouble, but let me go on.

When I look at iwconfig, I see the following:
```

lo               no wireless extensions.

wmaster0    IEEE 802.11g  Frequency:2.412 GHz
                  RTS thr:off     Fragment thr=2348 B

wlan0          IEEE 802.11g    ESSID:""
                  Mode:Managed  Frequency:2.412 GHz Access Point: Not-Associated
                  RTS thr:off        Fragment thr=2348 B

eth0            no wireless extensions // onboard wired port not in use

sit0             no wireless extensions // ????
```

When I run *sudo lshw*, I get the following (cut for brevity):
```

*-network:1 DISABLED
    description: Wireless interface
    product: Ralink RT2600 802.11 MIMO
    vendor: RaLink
    physical id: b
    bus info: pci@00:0b.0
    logical name: wmaster0
    version: 00
    serial: ##:##:##:##:##:##
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list logical wireless ethernet physical
    configuration: broadcast=yes driver=rt61pci driverversion=CVS firmware=.bin link=yes multicast=yes wireless=IEEE 802.11g
    resources: iomemory:e4800000-e4807fff irq:201
```

If I try to assign wmaster0 an SSID, it fails with the following error:
```

Error for wireless request "SET ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
```

I'm not terribly new to Ubuntu, but I am to the wireless scene. My wireless router is an Apple Airport Extreme.

Thanks for all the help!

---

### Post by anvo on 2007-02-01
I have the same wireless card but I get the same error output even after I tried "ndiswrapper".  Have you tried "ndiswrapper", too?  And what about "madwifi"...?

---

