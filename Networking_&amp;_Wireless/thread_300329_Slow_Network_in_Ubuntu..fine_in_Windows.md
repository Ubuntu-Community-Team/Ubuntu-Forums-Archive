---
title: "Slow Network in Ubuntu..fine in Windows"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by chrisg631 on 2006-11-15
I have a problem with my network while using Linux.  Here is my network card:
```
# lspci | grep Ethernet
00:09.0 Ethernet controller: MYSON Technology Inc SURECOM EP-320X-S 100/10M Ethernet PCI Adapter
```

The fealnx module is loaded.  Verified by using lsmod and I am online, but download speeds are REALLY slow ~ 15kB/s.  However, in Windows I am getting normal speeds of ~ 500kB/s.

Both mii-tool and ethtool report that the "link" is down, but I am still online.  The NIC is the only network device attached to this PC. 
```
# ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: off
        Current message level: 0x00000000 (0)
        Link detected: no

# mii-tool -v
eth0: 10 Mbit, half duplex, no link
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   10 Mbit, half duplex
  basic status: no link
  capabilities:
  advertising: 

```

I have disabled IPV6 by putting "alias net-pf-10 off" instead of "alias net-pf-10 ipv6" in the /etc/modprobe.d/aliases.  The card is 10/100 Full Duplex but it's reported at only 10mb Half Duplex.  I am current running Ubuntu 6.10, although I have also tried other distros using live-cd's with the same problem.  Anyone have any suggestions?

---

