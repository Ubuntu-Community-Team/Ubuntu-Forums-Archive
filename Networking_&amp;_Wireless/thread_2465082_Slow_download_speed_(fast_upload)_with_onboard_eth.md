---
title: "Slow download speed (fast upload) with onboard ethernet only"
date: 2021-07-21
forum: Networking &amp; Wireless
---

### Post by drakesiard on 2021-07-21
My laptop has slow download speeds (compared to upload speeds) when using the onboard (gigabit) ethernet controller versus using a USB3.0 (gigabit) dongle.

The onboard ethernet gives me a download ~50Mbps, but the upload goes up to ~400 Mbps.
The same cable plugged into the USB ethernet dongle gives upload and download of 400Mbps.

I know it's not the systemd/ECN issue because I tested sysctl net.ipv4.tcp_ecn=0 with no effect, and it only happens on the one interface anyway.

Update: it's not the r8168/r8169 issue ([https://itectec.com/ubuntu/ubuntu-r8168-r8169-realtek-driver-module-troubles/](https://itectec.com/ubuntu/ubuntu-r8168-r8169-realtek-driver-module-troubles/)), because I installed r8168-dkms and checked the right module was loaded, but the speed difference remains.

[HR][/HR]

lspci on the onboard ethernet shows:

```
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)
```

ethtool enp2s0 (the onboard controller) shows:

```
 Settings for enp2s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
```



lsusb on the dongle shows:
```
 Bus 002 Device 006: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
```

ethtool enx00ee22aa659a (the usb dongle) shows:
```
 Settings for enx00ee22aa659a:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 3
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes
```

---

### Post by drakesiard on 2021-07-21
It's not a wireless issue, but here are the two wireless info dumps:

---

