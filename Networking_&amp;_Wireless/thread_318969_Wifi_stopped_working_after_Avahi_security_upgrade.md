---
title: "Wifi stopped working after Avahi security upgrade"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by alarik on 2006-12-14
With Edgy, after accepting the [latest security patch]("http://ubuntuforums.org/showthread.php?t=318561&highlight=avahi") for Avahi to version 0.6.13-2ubuntu2.3, my Wifi just stopped working.  I'm using gnome network-manager on a Lenovo X60.

I see the following in /var/log/messages which I never used to see:
> 
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_rate_tx_complete
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol _ath_hal_attach
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_rate_attach
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_rate_newassoc
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_hal_computetxtime
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_rate_dynamic_proc_register
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_hal_mhz2ieee
Dec 14 21:07:02 localhost kernel: [17179599.304000] ath_pci: Unknown symbol ath_hal_detach
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_hal_probe
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_rate_node_cleanup
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_rate_detach
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_rate_node_init
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_rate_findrate
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_hal_init_channels
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_rate_newstate
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
Dec 14 21:07:02 localhost kernel: [17179599.308000] ath_pci: Unknown symbol ath_hal_getwirelessmodes


Any help would be greatly appreciated.  I am considering just going back to the version that shipped with Edgy. The strange thing is that the note for the security patch indicates:

> Previous patch broke operation with network-manager

...whereas for me the exact opposite seems to be true.

Alarik

---

### Post by alarik on 2006-12-14
Alas, reverting the libraries to the original Edgy versions didn't help either.  For a brief moment I thought perhaps the problem was that I had somehow switched off the wifi via the hardware switch on the laptop, but that's not it either.

Any help very gratefully appreciated,

Alarik

---

### Post by alarik on 2006-12-14
If I boot to the generic kernel (not the 386 kernel I use for the SMP support) then Wifi works again.  Hooray!  I guess I can probably figure it out from here.

Alarik

---

