---
title: "AR5007 on amilo Li17178"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by tartaro on 2008-10-05
[(Edit.)Wrong typing on title it is Li1718 not 17178]
I was trying to install my Atheros wifi internal card (AR5007) on my Amilo Li17178 following this guide [http://ubuntuforums.org/archive/index.php/t-644899.html](http://ubuntuforums.org/archive/index.php/t-644899.html).
I've installed the madwifi drivers with the latest version
```
$ modinfo ath_pci | grep version 
version:        svn r3861
srcversion:     53828DCE2B2CEC52C9E9103

```
And the acerhk support for the button activation.
But when i try to load the ath_pci module it says:
```
$ sudo modprobe ath_pci 
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

this is some from dmesg
```
[  439.894723] ath_hal: module license 'Proprietary' taints kernel.
[  439.896944] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  440.156556] ath_pci: disagrees about version of symbol _ath_hal_attach
[  440.156568] ath_pci: Unknown symbol _ath_hal_attach
[  440.156690] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  440.156694] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  440.157166] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  440.157171] ath_pci: Unknown symbol ath_hal_computetxtime
[  440.157483] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  440.157488] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  440.157752] ath_pci: Unknown symbol _ath_hal_detach
[  440.158461] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  440.159142] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  440.159146] ath_pci: Unknown symbol ath_hal_init_channels
[  440.159438] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  440.159442] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  554.832575] ath_pci: disagrees about version of symbol _ath_hal_attach
[  554.832590] ath_pci: Unknown symbol _ath_hal_attach
[  554.832907] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  554.832914] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  554.834013] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  554.834020] ath_pci: Unknown symbol ath_hal_computetxtime
[  554.834474] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  554.834476] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  554.834747] ath_pci: Unknown symbol _ath_hal_detach
[  554.835454] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  554.836133] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  554.836138] ath_pci: Unknown symbol ath_hal_init_channels
[  554.836489] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  554.836493] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[ 1029.292143] ath_pci: disagrees about version of symbol _ath_hal_attach
[ 1029.292159] ath_pci: Unknown symbol _ath_hal_attach
[ 1029.292443] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[ 1029.292449] ath_pci: Unknown symbol ath_hal_process_noisefloor
[ 1029.293555] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[ 1029.293565] ath_pci: Unknown symbol ath_hal_computetxtime
[ 1029.294292] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[ 1029.294300] ath_pci: Unknown symbol ath_hal_mhz2ieee
[ 1029.294834] ath_pci: Unknown symbol _ath_hal_detach
[ 1029.296476] ath_pci: Unknown symbol ath_hal_print_decoded_register
[ 1029.298071] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 1029.298079] ath_pci: Unknown symbol ath_hal_init_channels
[ 1029.298763] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 1029.298772] ath_pci: Unknown symbol ath_hal_getwirelessmodes

```
Please, can someone help me?

regards
tartaro

---

### Post by Ghadi Rayess on 2008-10-16
I just faced the same problem.
It was working fine before, until i made an apt-get update and it stopped working :S.
Some new lib/package must have messed up the madwifi libraries....

---

