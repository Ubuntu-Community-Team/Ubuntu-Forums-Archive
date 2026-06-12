---
title: "wired 10 MB card - reset command?"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by thor111 on 2007-11-11
I had this 100 MB card running at 10 MB (because of my old cabling), by using the following commands
  sudo ethtool -s eth0 autoneg off
  sudo ethtool -s eth0 speed 10
I could then just reset my connection, and everything would work.  Now the card doesn't respond to anything.  Is there a generic reset command for the nic card?  All of my expertise (poor choice of words) is on the MS side (sorry).  I'd like to convert, but it's a lot more intimidating than it should be.  Thanks in advance for any support.

-Mark

---

### Post by noob12 on 2007-11-13
Can you post the output of these commands
```

lspci -nn

sudo lshw -C network

sudo ethtool eth0

```

---

### Post by thor111 on 2007-11-18
It's working now, but I'm not sure why.  Here are the listings you requested.

kelly@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440LX/EX - 82443LX/EX Host bridge [8086:7180] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge [8086:7181] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 01)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 01)
00:0e.0 Multimedia audio controller [0401]: Ensoniq ES1370 [AudioPCI] [1274:5000]
00:12.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)
kelly@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 10
       serial: 00:05:5d:46:41:75
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.15.103 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:de00-deff iomemory:efffff00-efffffff irq:10
kelly@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes
kelly@ubuntu:~$ 

Your help is appreciated!

---

### Post by noob12 on 2007-11-18
OK.  If the problem recurs check this thread as well:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

