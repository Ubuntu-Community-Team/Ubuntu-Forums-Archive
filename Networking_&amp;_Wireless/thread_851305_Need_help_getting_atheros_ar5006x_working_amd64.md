---
title: "Need help getting atheros ar5006x working amd64"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Jdurr0613 on 2008-07-06
I have a compaq presario a900 with an internal wifi card, atheros ar5006x. Upon a fresh install of XUBUNTU 8.06 AMD 64. The restricted drivers are in use upon install and a lspci responds with:

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig responds

lo        no wireless extensions.

eth0      no wireless extensions.

gui net config utility does not recognize the wifi card

what am i missing here?

---

### Post by argosreality on 2008-07-06
I'm having the same issue except with a dv6745us running x86. My dmesg also shows this:

```
[   36.329133] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   36.509231] wlan: 0.8.4.2 (0.9.4)
[   36.574631] ath_pci: disagrees about version of symbol _ath_hal_attach
[   36.574636] ath_pci: Unknown symbol _ath_hal_attach
[   36.574756] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   36.574758] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   36.574996] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   36.574998] ath_pci: Unknown symbol ath_hal_computetxtime
[   36.575226] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   36.575228] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   36.575444] ath_pci: Unknown symbol _ath_hal_detach
[   36.576382] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   36.576384] ath_pci: Unknown symbol ath_hal_init_channels
[   36.576558] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   36.576560] ath_pci: Unknown symbol ath_hal_getwirelessmodes
```

---

