---
title: "Wireless lights blinking(red and blue) on COMPAQ PRESARIO A933TU"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by sindhav.ravi on 2011-05-05
I have installed UBUNTU 11.04 on Comaq Presario A933tu laptop.I was able to connect to wireless network.BUt after connecting to wireless networks the adapter lights started blinking nd it blinks continously..

here is the detail of my network adapter which i got using lspci  -vv

```````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
Network controller : Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection(rev 02)

Subsystem: Hewlett-Packard company device 135b

Control: I/O- Mem+ BusMaster+ SpecCycle- MeWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

Latency:0
Interrupt:  pin A route to IRQ 42
Region 0: Memory at d1300000 (32-bit, non-prefetchable) [size=4k]
Capabilities:<access denied>
Kernel driver in use : iwl3945
Kernel modules: iwl3945

``````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
I fear if that blinking may damage my laptop.

please help me out.....

---

### Post by josephmills on 2011-05-05
could we see a ```
lsmod | grep iwl
```
thanks

---

### Post by sindhav.ravi on 2011-05-06
```
lsmod | grep iwl

iwl3945               130113  0 
iwlcore               148965  1 iwl3945
mac80211              257001  2 iwl3945,iwlcore
cfg80211              156212  3 iwl3945,iwlcore,mac80211

```

---

