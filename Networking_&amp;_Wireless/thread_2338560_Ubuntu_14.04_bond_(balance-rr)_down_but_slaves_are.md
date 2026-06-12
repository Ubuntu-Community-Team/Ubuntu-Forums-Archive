---
title: "Ubuntu 14.04 bond (balance-rr) down but slaves are up"
date: 2016-09-29
forum: Networking &amp; Wireless
---

### Post by fenichelar on 2016-09-29
I am trying to setup balance-rr on my Ubuntu 14.04 server. I have a USB 3.0 dual NIC adapter (eth1 and eth2). It is direct connected to my NAS. It was working and then I rebooted and now it isn't working. I can't seem to get it to work now and I don't see anything wrong. Here are all of the files I can think that are relevant. Both of the slave interfaces appear to be working correctly but the bond is down. Is there something I am missing? Thanks!

cat /etc/modules

[HTML]
    lp
    rtc
    bonding
    
    # Chip drivers
    coretemp
[/HTML]

cat /etc/network/interfaces

[HTML]
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# eth1 configuration
auto eth1
iface eth1 inet manual
bond-master bond0

# eth2 configuration
auto eth2
iface eth2 inet manual
bond-master bond0

# Bonding eth1 & eth2 to create bond0 NIC
auto bond0
iface bond0 inet static
address 172.16.0.101
netmask 255.255.255.0
bond-mode balance-rr
bond-miimon 100
bond-slaves none
[/HTML]

cat /proc/net/bonding/bond0

[HTML]
Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: load balancing (round-robin)
MII Status: down
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0
[/HTML] 

sudo ethtool bond0

[HTML]
Settings for bond0:
Supported ports: [ ]
Supported link modes: Not reported
Supported pause frame use: No
Supports auto-negotiation: No
Advertised link modes: Not reported
Advertised pause frame use: No
Advertised auto-negotiation: No
Speed: Unknown!
Duplex: Unknown! (255)
Port: Other
PHYAD: 0
Transceiver: internal
Auto-negotiation: off
Link detected: no
[/HTML] 

sudo ethtool eth1

[HTML]
Settings for eth1:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Link partner advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Link partner advertised pause frame use: Symmetric Receive-only
Link partner advertised auto-negotiation: Yes
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
[/HTML] 

sudo ethtool eth2

[HTML]
Settings for eth1:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Link partner advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Link partner advertised pause frame use: Symmetric Receive-only
Link partner advertised auto-negotiation: Yes
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
[/HTML] 

dmesg | grep "eth1"

[HTML]
[ 6.259558] ax88179_178a 2-4.1:1.0 eth1: register 'ax88179_178a' at usb-0000:00:14.0-4.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0a:cd:2b:c9:14
[ 6.893683] bond0: Adding slave eth1
[ 10.219344] ax88179_178a 2-4.1:1.0 eth1: ax88179_178a - Link status is: 1
[ 10.220703] ax88179_178a 2-4.1:1.0 eth1: Write medium type: 0x013b
[ 10.221713] ax88179_178a 2-4.1:1.0 eth1: link up, 1000Mbps, full-duplex, lpa 0xCDE1
[/HTML] 

dmesg | grep "eth2"

[HTML]
[ 6.588030] ax88179_178a 2-4.2:1.0 eth2: register 'ax88179_178a' at usb-0000:00:14.0-4.2, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:0a:cd:2b:c9:15
[ 6.894174] bond0: Adding slave eth2
[ 10.603356] ax88179_178a 2-4.2:1.0 eth2: ax88179_178a - Link status is: 1
[ 10.604551] ax88179_178a 2-4.2:1.0 eth2: Write medium type: 0x013b
[ 10.605743] ax88179_178a 2-4.2:1.0 eth2: link up, 1000Mbps, full-duplex, lpa 0xCDE1
[/HTML] 

dmesg | grep "bond0"

[HTML]
[ 6.664913] bond0: Setting MII monitoring interval to 100
[ 6.893683] bond0: Adding slave eth1
[ 6.894174] bond0: Adding slave eth2
[/HTML] 

Originally posted here: [http://serverfault.com/questions/805987/ubuntu-14-04-bond-balance-rr-down-but-slaves-are-up](http://serverfault.com/questions/805987/ubuntu-14-04-bond-balance-rr-down-but-slaves-are-up)

---

### Post by fenichelar on 2016-09-30
The issue was hardware/driver related. I purchased a different USB 3.0 to dual gigabit adapter and installed the supplied drivers. Using the config above it works perfectly.


StarTech USB 3.0 to Dual Gigabit Ethernet Adapter (USB32000SPT) - does not work
Vantec USB 3.0 to Dual Gigabit Ethernet Network Adapter (CB-U320GNA) - works

---

