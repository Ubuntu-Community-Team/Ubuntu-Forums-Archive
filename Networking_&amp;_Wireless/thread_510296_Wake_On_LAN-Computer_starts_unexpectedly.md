---
title: "Wake On LAN-Computer starts unexpectedly"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by ltcmdata on 2007-07-26
Hello!
I have been trying to make wake on lan work for some time now.I am using Kubuntu Feisty with an Elitegroup PM800-M2 motherboard and a Realtek RTL8139D NIC.I did the following steps:
1) Enabled wol with ethtool- no problem there.
```
data@enterprise:/etc/modprobe.d$ sudo ethtool eth0
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
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

```
2)enabled "wake on pci" in the BIOS.I also enabled an option in the BIOS called "PCI master" which I do not entirely understand.My motherboard manual said:"When set to off any PCI device set as the Master will not power on the system".:confused:

After reboot I wasn't any more able to shut down the computer, it acted as on normal reboot.Tried it on WinXP and it was the same. Even by pressing the power button at boot it restarted.So I assumed a PCI card must wake it directly after shut down.It seems that the problem was my CMI8738 sound card, because after I removed it the problem disappeared.

3)Removed the -i option from the halt script.

After that my computer waked on a sent magic packet, but it started turning on at random without any packets sent.I coudn't actually be perfectly sure  if the magic packet did the trick as I did the waking over the Internet, which I assume would take a couple of seconds, but the timing was more or less the same.

So I have a system, that can be waken, but it also wakes unexpectedly, which doesn't do much good.Can anyone help?

---

