---
title: "Help getting Netgear GA311 working"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by luken8r on 2007-02-06
Just like the tile says:  I need some assistance getting a new Netgear NIC using the Realtek RTL-8169 chipset working on my desktop
Here is where I stand right  now. Card is installed and System->Networking shows that the card on eth1 is active.

Problems:
1) If I move the ethernet cable from eth0 (working port) to eth1 the system locks up and reboots on me
2) If I boot with the cable in the new Netgear card, the lights DATA and 100M LEDs the back are illuminated, but I dont get an IP if I do a ifconfig eth1 down + up and if I look at the route table its empty.  If I try to add a route, it just says "network unreachable"

Here is some data from my system:

from dmesg |grep eth1:
> [17179589.456000] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179664.876000] r8169: eth1: link up
[17179676.508000] eth1: no IPv6 routers present
[17179880.804000] r8169: eth1: link up
[17179891.292000] eth1: no IPv6 routers present


from lspci:
> 0000:02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller (LOM)
0000:03:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


from ethtool
> Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000033 (51)
        Link detected: yes

The duplex changes from half to full if I have the cable connected....

Ive downloaded the opensource drivers this morning from Realtek's website, but got the following:

> make -C src/ clean
make[1]: Entering directory `/home/ld/Desktop/r1000_v1.05/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Leaving directory `/home/ld/Desktop/r1000_v1.05/src'
make -C src/ modules
make[1]: Entering directory `/home/ld/Desktop/r1000_v1.05/src'
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/ld/Desktop/r1000_v1.05/src modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ld/Desktop/r1000_v1.05/src'
make: *** [modules] Error 2



apparently, I dont have the build directory in  /lib/modules/2.6.15-27-386/ 

So, any suggestions?  Keep in  mind I am  not too swift at Linux yet so please elaborate on any commands I should run 

thx

---

### Post by luken8r on 2007-02-07
:confused:

---

