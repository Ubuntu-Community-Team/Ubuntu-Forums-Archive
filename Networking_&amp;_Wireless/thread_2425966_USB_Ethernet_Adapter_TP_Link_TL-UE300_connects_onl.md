---
title: "USB Ethernet Adapter TP Link TL-UE300 connects only at 10MBit to 100MBit ethernet"
date: 2019-09-02
forum: Networking &amp; Wireless
---

### Post by meise21 on 2019-09-02
Hi,
I am using an USB ethernet adapter on an old i-Mac running Xubuntu 18.04.2LTS. It manages to connect to my 100MBit ethernet but only at slow speed 10MBit.

If I do an ethtool on my adapter I get the following:

```
Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
   ** Advertised link modes:  10baseT/Half 10baseT/Full **
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 10Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00007fff (32767)
                   drv probe link timer ifdown ifup rx_err tx_err tx_queued intr tx_done rx_status pktdata hw wol
    Link detected: yes

```

For some reason the advertised link modes are set to 10baseT/Half and 10baseT/Full only. I tried to manually set the advertised modes to also include 100MBit (half and full duplex) but if I do that the connection stops working. Any idea what is going wrong or how I could get more info?
Thanks in advance!
Markus

---

### Post by pcfan1234 on 2019-09-06
Check your switch/modem/router. Important are the speeds supported by the device the computer is connected to.

---

### Post by meise21 on 2019-09-08
The switch is a gigabit switch the router to the internet is 100MBit only. I thought this is the reason why "Link partner advertised link modes" shows 100MBit in ethtool.
 Connections between other computers on the network are 100Mbit so this shouldn't be the problem.

---

### Post by pcfan1234 on 2019-09-08
The advertised link modes are only between 2 directly connected devices. If your computer has a Gigabit NIC and the switch too (and the cable is ok and 8 wires), they can connect with Gigabit, regardless which speed is used between switch and router.
Check your cable. Is it able to connect with Gigabit on another computer/switch?

---

### Post by meise21 on 2019-09-08
I played around some more and noticed a strange thing. If I connect both my PC not via my switch to my internet router but directly to my router I get a 100 MBit connection. Interestingly this changes also the values for "Advertised link modes" there I get 10, 100 and 1000MBit when I connect my PC to the router, but only 10MBit when i connect it to my switch (which is at least advertised as gigabit ethernet switch). I'll try more the next days.

---

### Post by meise21 on 2019-09-10
Thanks for your tips. The problem was my apparently defective switch. I got a new one yesterday and everything works like a treat now...
Thanks,
Markus

---

