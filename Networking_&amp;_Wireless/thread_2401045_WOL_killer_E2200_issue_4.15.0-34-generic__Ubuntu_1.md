---
title: "WOL killer E2200 issue 4.15.0-34-generic // Ubuntu 18.04.1 LTS"
date: 2018-09-12
forum: Networking &amp; Wireless
---

### Post by manilaboy1vic on 2018-09-12
Hello team,

I cant seem to enable WOL for this NIC.  I enabled it in the BIOS.

Here is the modinfo for the nic driver.

```

vic@bickle:~$ modinfo alxfilename:       /lib/modules/4.15.0-34-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
license:        GPL
description:    Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     DDD52B7257E572D121505EB
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E0B1sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E0A1sv*sd*bc*sc*i*
alias:          pci:v00001969d0000E091sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        mdio
retpoline:      Y
intree:         Y
name:           alx
vermagic:       4.15.0-34-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           enable_wol:Enable Wake on Lan feature (bool)

```
Ethtool claims operation not supported:

```


root@bickle:~# ethtool -s enp3s0 wol g
Cannot set new wake-on-lan settings: Operation not supported
  not setting wol
root@bickle:~# 



vic@bickle:~$ sudo ethtool enp3s0 
Settings for enp3s0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: d
    Wake-on: d
    Current message level: 0x000060e4 (24804)
                   link ifup rx_err tx_err hw wol
    Link detected: yes

```

TIA

---

### Post by chili555 on 2018-09-13
> root@bickle:~# ethtool -s enp3s0 wol g
Cannot set new wake-on-lan settings: Operation not supported
  not setting wolIs there any improvement with:```
[COLOR="#FF0000"]sudo[/COLOR] ethtool -s enp3s0 wol g
sudo ethtool enp3s0
```

---

