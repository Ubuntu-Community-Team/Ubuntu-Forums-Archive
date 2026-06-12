---
title: "[SOLVED] ath_pci symbol unknown? known only to the Lone Ranger"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-21
Card/Software not speaking to each other

Output of dmesg 

[  163.888136] wlan: 0.8.4.2 (0.9.3.1)
[  163.963545] ath_pci: Unknown symbol _ath_hal_attach
[  163.964019] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  163.965405] ath_pci: Unknown symbol ath_hal_computetxtime
[  163.966595] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  163.967039] ath_pci: Unknown symbol ath_hal_detach
[  163.969046] ath_pci: Unknown symbol ath_hal_probe
[  163.971595] ath_pci: Unknown symbol ath_hal_init_channels
[  163.972569] ath_pci: Unknown symbol ath_hal_getwirelessmodes

How do I introduce the ath_pci to the various _hal_?

---

### Post by Mark_in_Hollywood on 2007-07-25
THREAD CLOSED.

I have reinstalled Feisty. This is not so much a solution as it is a time saving measure. After 2 weeks of "fooling around' with various modprobe, lsmod and assorted commands, i want something that works.

---

