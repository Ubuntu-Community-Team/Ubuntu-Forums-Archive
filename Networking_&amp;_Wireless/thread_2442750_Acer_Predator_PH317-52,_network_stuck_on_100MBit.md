---
title: "Acer Predator PH317-52, network stuck on 100MBit"
date: 2020-05-07
forum: Networking &amp; Wireless
---

### Post by vangoda on 2020-05-07
Hi,

I have an Acer Predator PH317-52 machine with Kubuntu 18.04 installed.
Kernel version is 5.3.0-51-generic.
The problem is the speed of Ethernet, it is stuck at 100Mbps and should be 1Gbps.
The card in question, as stated by output of lspci, is:[INDENT]Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
[/INDENT]
I am not sure if the card is RTL8111, RTL8168 or the RTL8411, this is very confusing. From googling it seems to be RTL8168.

I am certain that this card supports 1 Gbit and have also confirmed that all the other network gear is ok, I can get 1Gbit from Windows OS.
I have tried manually setting the value to 1000 Mbps from network manager, but it wouldn't connect at all when i did this.
I have also tried setting the autonegotiation on in network manager. I have tried both the steps below with ethtool too.
All the settings apply successfully but autonegotiation always sets speed to 100Mbps and setting it to 1Gbit always fails to connect.
I have tried installing the r8168-dkms package from apt-get but the results are the same (installation finished with no problems).
Here is the output of ethtool:
```

ethtool enp7s0f1
Settings for enp7s0f1
        Supported ports: [ TP ]
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
        Link partner advertised pause frame use: Symmetric
        Link partner advertised auto-negotiation: Yes
        Link partner advertised FEC modes: Not reported
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes
```

I don't know what to do next and I'm not even sure what the problem is.
I would be grateful for any advice on how to proceed.

Edit:
With an USB3.0 ethernet adapter i get full 1Gbit connection speed.

---

### Post by slickymaster on 2020-05-07
Thread moved to **Networking & Wireless** for a better fit

---

