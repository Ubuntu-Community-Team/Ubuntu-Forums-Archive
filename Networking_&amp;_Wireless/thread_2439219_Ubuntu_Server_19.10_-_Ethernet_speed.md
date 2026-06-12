---
title: "Ubuntu Server 19.10 - Ethernet speed"
date: 2020-03-24
forum: Networking &amp; Wireless
---

### Post by kayltsanten on 2020-03-24
Good afternoon all,
i'm here to ask help to us about my ethernet interface.

below, you can see information about card, kernel and driver installed:
```
Ethernet controller: 
Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)    
Subsystem: ASRock Incorporation Motherboard (one of many)    
Kernel driver in use: r8168    
Kernel modules: r8168
```

```
[COLOR=#005400][FONT=Monaco]enp2s0 =====================
driver: r8168
version: 8.047.04-NAPI
firmware-version: expansion-rom-version: bus-info: 0000:02:00.0supports-statistics: yessupports-test: nosupports-eeprom-access: nosupports-register-dump: yessupports-priv-flags: nolo =====================[/FONT][/COLOR]
```

```

[COLOR=#005400][FONT=Monaco]Settings for enp2s0:    
Supported ports: [ TP ]    
Supported link modes:   
10baseT/Half 10baseT/Full                             
100baseT/Half 100baseT/Full
1000baseT/Full     
Supported pause frame use: Symmetric Receive-only    
Supports auto-negotiation: Yes    
Supported FEC modes: Not reported    
Advertised link modes:  
10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised pause frame use: 
Symmetric Receive-only    
Advertised auto-negotiation: Yes    
Advertised FEC modes: Not reported    
Link partner advertised link modes:  
10baseT/Half 10baseT/Full                                          
100baseT/Half 100baseT/Full                                          
1000baseT/Half 1000baseT/Full     
Link partner advertised pause frame use: Symmetric Receive-only    
Link partner advertised auto-negotiation: Yes    
Link partner advertised FEC modes: Not reported    
Speed: 100Mb/s    
Duplex: Full    
Port: Twisted Pair    
PHYAD: 0    
Transceiver: internal    
Auto-negotiation: on    
MDI-X: Unknown    
Supports Wake-on: pumbg    
Wake-on: g    
Current message level: 0x00000033 (51)                   
drv probe ifdown ifup    
Link detected: yes[/FONT][/COLOR]
```


now, this is a problem: i can't setup speed to 1000.
if i do it by ethtool, connection go down and i can't restart it.. only way is to setup again speed to 100 FULL.

can you help me?

Thanks all!
Lorenzo

---

### Post by kayltsanten on 2020-03-25
after 1 week test, after 5 different driver and 3 different cable.. now connection is up to 1000 and trasnfer rate is near teoric 120MB/s.
thanks all

---

### Post by ajgreeny on 2020-03-25
That's  great news but do please  tell us how you managed to get it  working and also mark as solved from the Thread Tools up top.

---

### Post by kayltsanten on 2020-03-26
i have change cable 3 times and i have re-install driver.
i think, the mail problem was cable: first cable CAT.6 changed with an older used cable cat. 5e.

---

### Post by ajgreeny on 2020-03-26
Great! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 

It is a great help to other users searching the forum.

---

