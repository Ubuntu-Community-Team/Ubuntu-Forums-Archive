---
title: "Atheros not working"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by jlindgren on 2007-04-16
i've loaded all the drivers and such, but i can't seem to get it to work. the modules are loading, ect...but still no luck. any help?
ubuntu 6.10

relevant dmesg output:
[17179588.404000] wlan: 0.8.4.2 (0.9.2.1)
[17179588.512000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.680000] ath_rate_sample: 1.2 (0.9.2.1)
[17179588.684000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179588.684000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 233
[17179588.684000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179588.684000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13) <<----problem - but unaware of how to fix it...

relevant lsmod:
ath_pci                97184  0 
ath_rate_sample        15616  1 ath_pci
wlan                  204764  2 ath_pci,ath_rate_sample
ath_hal               192080  2 ath_pci,ath_rate_sample

kernel:
2.6.17-11-386

any ideas?

---

### Post by spd106 on 2007-04-16
Consider downloading and installing the newest version of madwifi (currently 0.9.3), it may have support for your device.

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

