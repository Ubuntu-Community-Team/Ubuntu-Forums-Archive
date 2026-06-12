---
title: "Getting WOL to work with 3Com NIC"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by bennierex on 2007-02-22
Hi there,

I've been trying for some time now to get WOL to work on my Ubuntu (6.10) home server. Everything is set-up for this to work (BIOS, cable, NIC), but for some reason the system does not boot when the magic packet is sent. I checked with a packet sniffer that the actual package gets broadcasted, so the problem must lie with the server itself.

After spending some time searching goole and these forums, I figured the problem must be with the WOL settings on the card. I tried to change these with ethtool, but thusfar this is not working. Maybe there is a problem with the actual driver of my NIC which prevents me from setting the WOL-parameter. I hope anyone here can help me out with this.

Some additional info;
```
>sudo lsmod
Module                  Size  Used by
ipv6                  271136  14
af_packet              24584  2
lp                     12964  0
3c59x                  47912  0
mii                     6912  1 3c59x
hw_random               7320  0
floppy                 62916  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
evdev                  11392  0
psmouse                41352  0
serio_raw               8452  0
intel_agp              26012  1
agpgart                35016  1 intel_agp
i2c_i810                6276  0
i2c_algo_bit           10376  1 i2c_i810
i2c_core               23424  1 i2c_algo_bit
pcspkr                  4352  0
parport_pc             37796  1
parport                39368  2 lp,parport_pc
ext3                  142344  1
jbd                    62100  1 ext3
uhci_hcd               25096  0
usbcore               134656  2 uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  3
piix                   11780  1
generic                 6276  0
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41376  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

>sudo mii-tool eth0
  No MII transceiver present!.

>sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

>sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol

>lspci | grep Eth
01:0c.0 Ethernet controller: 3Com Corporation 3c980-TX Fast Etherlink XL Server Adapter [Cyclone] (rev 30)

>lsmod | grep mii
mii                     6912  1 3c59x
```

---

