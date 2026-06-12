---
title: "Killer E3000 lan card only negotiating 100mb/s"
date: 2022-12-05
forum: Networking &amp; Wireless
---

### Post by mike430 on 2022-12-05
Have Ubuntu 22.04.1. Machine is new and switch it's connected to indicates 1000mb/s. 

Have set to auto negotiate, checked multiple cables to no avail. 

Removed the driver and compiled and installed r8169 driver from RealTek and it works, but still is capped at 100mb/s.

Below is output on my nic:
```
Settings for enp46s0:    Supported ports: [ TP     MII ]
    Supported link modes:   10baseT/Half 10baseT/Full
                            100baseT/Half 100baseT/Full
                            1000baseT/Full
                            2500baseT/Full
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full
                            100baseT/Half 100baseT/Full
                            1000baseT/Full
                            2500baseT/Full
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                         100baseT/Half 100baseT/Full
                                         1000baseT/Full
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 1000Mb/s
    Duplex: Full
    Auto-negotiation: on
    master-slave cfg: preferred slave
    master-slave status: slave
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: external
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: d
    Link detected: yes
```

Thanks for any help. Mike

---

### Post by mike430 on 2022-12-06
[COLOR=#111111][FONT=Arial]I figured this. The settings in KDE under system settings > connection has 100mpbs with auto neg. However, as you can see I manually installed a driver and set at 1000mbs. My machine was only pulling in 100mbps upon a speed test.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]In /etc/default/grub there is a kernel setting (GRUB_CMDLINE_LINUX_DEFAULT="splash") I added this to the end (pcie_aspm=off) then updated grub.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]Although KDE still indicates i am capped at 100mbps, but upon conducting a speed test it works and pulling in the top speed of my internet which 250mbps.[/FONT][/COLOR]

---

