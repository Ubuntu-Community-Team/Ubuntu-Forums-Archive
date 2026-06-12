---
title: "Issue with TG3 driver + BCM5705 NIC"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by m0unds on 2006-10-11
I picked up a Broadcom NetXtreme 5705 ethernet NIC to replace a problematic Intel NIC. 

I installed the new nic, powered up the box, expecting to have to adjust iftab to indicate the new card. 

lspci:
0000:00:10.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 01)

ifconfig only shows the loopback device. modprobe shows the tg3 module is loaded

i changed iftab to show the mac address of the new card, but no joy. tried removing and readding the tg3 module with no luck.

i reinstalled the intel nic so i could run in a terminal (easier on me) 

running ethtool on the device shows this:

Settings for eth1:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: Unknown! (0)
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: no

Anyone have any insight as to what I might be doing wrong to be causing this to happen?

---

### Post by m0unds on 2006-10-11
i fixed the issue, but it's kind of ridiculous how.

i had eth0 still present because i reinstalled the intel nic. i verified that there was an entry in /etc/network/interfaces for eth1 (new nic) and there was. there was an entry in /etc/iftab for it also. i rmmmod'd the tg3 mod and reinserted it again (as i've done 20 times today..), device came up and i was able to ping google.com-- but not any local stuff. took down eth0, and everything was passing through eth1 without any issues.

go figure. it's late.. maybe that's my problem :)

---

