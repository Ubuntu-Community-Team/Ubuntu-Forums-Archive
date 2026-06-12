---
title: "New install of 16.04 - wireless ok bu ethernet says not connected"
date: 2016-09-26
forum: Networking &amp; Wireless
---

### Post by nfshirley on 2016-09-26
Hi

I am a newbie.  I have just installed 16.04 on a HP 620 laptop.  The network was working in Windows but I am unable to get it working in Ubuntu 16.04.

lspci - k gives

```
Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet Controller (rev 02)
Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet Controller
Kernel driver in use: r8169
Kernel modules: r8169
```

```
dmesg | grep ens5 gives
r8169 0000:85:00.0 ens5: renamed from eth0
IPv6: ADDRCONF(NETDEV_UP): ens5: link is not ready
r8169 0000:85:00.0 ens5: link down
IPv6: ADDRCONF(NETDEV_UP): ens5: link is not ready
```

ethtool ens gives:
```
Settings for ens5:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no
```

ifconfig
```
ens5      Link encap:Ethernet  HWaddr 64:31:50:74:70:37  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I am not sure what other information people might need to assist me.

I do know the network cable definitely works as I have used it in another computer fine.

Any help / advice / pointers will be very much appreciated.

Many thanks

Neil

---

