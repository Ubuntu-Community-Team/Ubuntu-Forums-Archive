---
title: "Ethernet interface no sleep at all times"
date: 2019-09-05
forum: Networking &amp; Wireless
---

### Post by toby99 on 2019-09-05
i am hibernating / sleeping my pc after 10 min. while in hibernation I can see that the ethernet interface port LEDs are not on or blinking as an indication for "on" or standby mode. How to prevent the ethernet interface to sleep at all times in ubuntu? My main goal is to utilize the WoL feature to wake up my PC remotely. Some information:

$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 06
       serial: XX:XX:XX:XX:XX:XX
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=XXX.XXX.XXX.XXX latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
#############################

$ ifconfig -a
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet XXX.XXX.XXX.XXX  netmask XXX.XXX.XXX.X  broadcast XXX.XXX.XXX.XXX
        inet6 XXXX::XXXX:XXXX:XXXX:XXXX  prefixlen 64  scopeid 0x20<link>
        ether XX:XX:XX:XX:XX:XX  txqueuelen 1000  (Ethernet)
        RX packets 105479  bytes 15854955 (15.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11389  bytes 1383817 (1.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2284  bytes 237460 (237.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2284  bytes 237460 (237.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

###########

$ sudo ethtool enp4s0
Settings for enp4s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
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

---

### Post by toby99 on 2019-09-09
Follow up -- additional information: I can inform that when the pc is in  normal operation the two LEDs at the network interface are blinking.  When the pc is in sleep/hibernation mode, the LEDs are off.

---

