---
title: "Slow wired internet speeds"
date: 2018-02-16
forum: Networking &amp; Wireless
---

### Post by mrfox321 on 2018-02-16
The internet on this new install is very slow. 

Chip: Intel 8700K Coffee Lake
   Motherboard:  ASUS z370-a 

 Additionally, if I try to switch to 100Mbps full duplex, I lose connectivity completely.  The router should be able to handle those speeds... 

 relevant terminal outputs: 
```

lspci -nnk | grep 0200 -A2 
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]     
Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]     
Kernel driver in use: e1000e 

```

```

lsb_release -a 
No LSB modules are available. 
Distributor ID:    Ubuntu 
Description:    Ubuntu 16.04.3 LTS Release:    16.04 
Codename:    xenial 

```

```

dmesg | grep e100 
[    1.019777] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k 
[    1.019778] e1000e: Copyright(c) 1999 - 2015 Intel Corporation. 
[    1.088854] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode 
[    1.293851] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock 
[    1.361854] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) b0:6e:bf:30:35:17 
[    1.361855] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection 
[    1.361933] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF 
[    1.362258] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0 
[   63.485234] e1000e: enp0s31f6 NIC Link is Up 10 Mbps Full Duplex, Flow Control: Rx/Tx 
[   63.485239] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO 
[10810.250430] e1000e: enp0s31f6 NIC Link is Down 
[10876.654579] e1000e: enp0s31f6 NIC Link is Up 10 Mbps Full Duplex, Flow Control: Rx/Tx 
[10876.654585] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO 
[10921.757898] e1000e: enp0s31f6 NIC Link is Down 
[10970.293392] e1000e: enp0s31f6 NIC Link is Up 10 Mbps Full Duplex, Flow Control: Rx/Tx 
[10970.293397] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO 

```

```

sudo ethtool enp0s31f6 
Settings for enp0s31f6:     
Supported ports: [ TP ]     
Supported link modes:   10baseT/Half 10baseT/Full                              100baseT/Half 100baseT/Full                              1000baseT/Full      
Supported pause frame use: No     
Supports auto-negotiation: Yes     
Advertised link modes:  10baseT/Half 10baseT/Full                              100baseT/Half 100baseT/Full                              1000baseT/Full      
Advertised pause frame use: No     
Advertised auto-negotiation: Yes     
Speed: 10Mb/s     
Duplex: Full     
Port: Twisted Pair     
PHYAD: 1     
Transceiver: internal    
Auto-negotiation: on    
MDI-X: on (auto)     
Supports Wake-on: pumbg    
Wake-on: g     
Current message level: 0x00000007 (7)                    drv probe link     
Link detected: yes

```

---

### Post by oldfred on 2018-02-16
Please delete & repost your terminal output. It is unintelligible. 

Use code tags, which are easy to add using Forum's advanced editor and # icon.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by mrfox321 on 2018-02-16
Apologies, the formatting was destroyed by the slow internet speeds, haha.  Formatted

---

