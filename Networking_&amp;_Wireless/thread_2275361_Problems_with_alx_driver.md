---
title: "Problems with alx driver?"
date: 2015-04-25
forum: Networking &amp; Wireless
---

### Post by malch2 on 2015-04-25
I have a Lenovo Y480 laptop running Xubuntu 15.04.

Wireless works great :-) But I am having big problems with the wired Ethernet connection.

After booting up (or physically disconnecting or reconnecting the Ethernet port) everything works for maybe 10-20 seconds.

Then all network activity just hangs until whatever app times out. No errors reported in syslog.

This machine is dual-boot with Windows 7 which works just fine -- same hardware, cable, router.

The problem seems to be related to receive overruns (see ifconfig below).

Details from lspci, ethtool and ifconfig:

```
sudo lspci -kv
02:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 08)
    Subsystem: Lenovo Device 3979
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at d3a00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable+ Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-f1-29-ac-dc-0e-a1-ff
    Kernel driver in use: alx

sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Current message level: 0x000060e4 (24804)
                   link ifup rx_err tx_err hw wol
    Link detected: yes

ifconfig
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:f1:29:ac  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5903 errors:5034 dropped:0 overruns:5034 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58875 (58.8 KB)  TX bytes:36873 (36.8 KB)
          Interrupt:16 
```

I did try forcing the thing to run at 10MHz and flipping between half and full duplex but that didn't have any effect.

I'm kinda stuck but willing to try anything within my capabilities.

---

### Post by malch2 on 2015-04-26
This was the problem:

[https://bugzilla.kernel.org/show_bug.cgi?id=70761](https://bugzilla.kernel.org/show_bug.cgi?id=70761)

A suggested workaround (setting MTU to 8192) appears to be working for me.

---

### Post by przemek9 on 2015-05-08
Don't work for me :(

---

