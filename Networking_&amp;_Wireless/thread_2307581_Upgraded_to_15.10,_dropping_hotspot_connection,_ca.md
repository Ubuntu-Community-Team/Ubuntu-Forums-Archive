---
title: "Upgraded to 15.10, dropping hotspot connection, can't connect eth0"
date: 2015-12-26
forum: Networking &amp; Wireless
---

### Post by l6griffin on 2015-12-26
This is a continuing problem from 15.04. I have 2 HP 2000 laptops, I now have both running version 15.10. I have not been able to connect them to my router with eth0. The hotspot connection is dropping if I don't use it for 2-5 minutes.

---

### Post by praseodym on 2015-12-26
Check if there is a MAC-address filter activated. Also show
```

sudo apt-get install ethtool
sudo ethtool eth0
lsmod | grep r8
| dmesg | egrep 'eth|r8'
```without being connected via WLAN

---

### Post by l6griffin on 2015-12-26
> **praseodym said:**
> Check if there is a MAC-address filter activated. Also show
```

sudo apt-get install ethtool
sudo ethtool eth0
lsmod | grep r8
| dmesg | egrep 'eth|r8'
```without being connected via WLAN

Where do I check for "MAC-address filter activated"

```
sudo apt-get install ethtool
[sudo] password for larry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
larry@hp-2k-4id2:~$ 
larry@hp-2k-4id2:~$ sudo ethtool eth0
Settings for eth0:
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
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no
larry@hp-2k-4id2:~$ 
larry@hp-2k-4id2:~$ lsmod | grep r8
r8169                  81920  0
mii                    16384  2 r8169,usbnet
larry@hp-2k-4id2:~$ 
larry@hp-2k-4id2:~$ | dmesg | egrep 'eth|r8'
bash: syntax error near unexpected token `|'
larry@hp-2k-4id2:~$ 

```

---

### Post by praseodym on 2015-12-26
Lets try:

```
sudo ethtool -s eth0 speed 100 autoneg off
sudo ethtool eth0
dmesg | egrep 'eth|r8'
```
If there is no connection at all, revert it via
```

sudo ethtool -s eth0 speed 10 autoneg on
```

---

### Post by l6griffin on 2015-12-26
I ran the commands, then disconnected from the hotspot, then tried to connect to eth0, no connect. Then reconnected to the hotspot. I then made the reply and didn't check to see if I was still connected before I hit submit. I wasn't connected and networking locked up, even after getting the server not found error. The icon (wifi signal) in the task did nothing when I clicked on it. Had to reboot and start over.
```

 sudo ethtool -s eth0 speed 100 autoneg off
[sudo] password for larry: 
larry@hp-2k-4id2:~$ 
larry@hp-2k-4id2:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
larry@hp-2k-4id2:~$ 
larry@hp-2k-4id2:~$ 
larry@hp-2k-4id2:~$ dmesg | egrep 'eth|r8'
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880106c00000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    0.280760] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.281113] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.459026] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.538722] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.549471] r8169 0000:03:00.0 eth0: RTL8105e at 0xffffc90000766000, a0:d3:c1:cb:49:d0, XID 00c00000 IRQ 26
[   27.328168] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.769210] r8169 0000:03:00.0 eth0: link down
[   27.769335] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  302.705246] usbcore: registered new interface driver cdc_ether
[ 7273.109290] r8169 0000:03:00.0 eth0: link down
[ 7274.131826] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7274.323298] r8169 0000:03:00.0 eth0: link down
[ 7274.324513] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7322.069812] r8169 0000:03:00.0 eth0: link down
[ 7323.110775] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7323.305081] r8169 0000:03:00.0 eth0: link down
[ 7323.305419] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[41402.917166] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[41403.120703] r8169 0000:03:00.0 eth0: link down
[41403.124124] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[41433.881959] r8169 0000:03:00.0 eth0: link up
[41433.882000] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

---

### Post by l6griffin on 2016-02-08
I changed routers (bricked the old one) and most of my problems seem to be solved. I bought a Asus RT-68u/w almost worked out of the box. Once the WIFI was setup I've had no problems with it and it's faster.

---

