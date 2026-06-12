---
title: "lacp not being sent on bond interfaces"
date: 2024-08-13
forum: Networking &amp; Wireless
---

### Post by scott-w-reeve on 2024-08-13
No LACP being sent out eno2 or eno3.
LACP IS being received from the other side.

LLDP is going out eno2 and eno3.

Not sure what I'm missing.

FWIW:
root@dl380rack1:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04 LTS
Release:        24.04
Codename:       noble




root@dl380rack1:~#cat /etc/netplan/50-cloud-init.yaml

network:
    ethernets:
        eno1:
            dhcp4: true
        eno2:
            dhcp4: false
            dhcp6: false
        eno3:
            dhcp4: false
            dhcp6: false
        eno4:
            dhcp4: true
        ens2f0np0:
            dhcp4: true
        ens2f1np1:
            dhcp4: true
    bonds:
      bond0:
        interfaces:
          - eno2
          - eno3
        parameters:
          mode: 802.3ad
          lacp-rate: slow
          mii-monitor-interval: 100
    version: 2
~              




root@dl380rack1:~# cat /proc/net/bonding/bond0
Ethernet Channel Bonding Driver: v6.8.0-39-generic


Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0
Peer Notification Delay (ms): 0


802.3ad info
LACP active: on
LACP rate: slow
Min links: 0
Aggregator selection policy (ad_select): stable
System priority: 65535
System MAC address: 02:5f:a1:a0:2d:01
Active Aggregator Info:
        Aggregator ID: 1
        Number of ports: 1
        Actor Key: 9
        Partner Key: 1
        Partner Mac Address: 00:00:00:00:00:00


Slave Interface: eno2
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 98:f2:b3:e7:5e:bd
Slave queue ID: 0
Aggregator ID: 1
Actor Churn State: none
Partner Churn State: churned
Actor Churned Count: 0
Partner Churned Count: 1
details actor lacp pdu:
    system priority: 65535
    system mac address: 02:5f:a1:a0:2d:01
    port key: 9
    port priority: 255
    port number: 1
    port state: 77
details partner lacp pdu:
    system priority: 65535
    system mac address: 00:00:00:00:00:00
    oper key: 1
    port priority: 255
    port number: 1
    port state: 1


This doesn't look quite right:

root@dl380rack1:~# ethtool bond0
Settings for bond0:
        Supported ports: [  ]
        Supported link modes:   Not reported
        Supported pause frame use: No
        Supports auto-negotiation: No
        Supported FEC modes: Not reported
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
        Speed: 1000Mb/s
        Duplex: Full
        Auto-negotiation: off
        Port: Other
        PHYAD: 0
        Transceiver: internal
        Link detected: yes

---

### Post by The Cog on 2024-08-13
Yaml is indentation sensitive, and this forum normally strips indentation from posts. Please can you repost, and put code tags round the file contents to preserve indentation. The easiest way is to click Go Advanced, and then the editor gives you a # button at the top - highlicht the code secments and click #.

---

