---
title: "RaLink RT2561/RT61 on Intrepid"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by drberg1000 on 2008-11-04
I installed the 64bit Intrepid on my box a few days ago, but can't seem to get my wireless to work.  It appears the card is detected and drivers are loaded, but I can't bring the interface up with ifup and no AP's are found with 'iwlist scanning'.   If I tell the network manager to look specifically for my AP, it fails and goes right back to the wired connection.

Some details are below.  Any suggestion?



dberg@dberg-desktop:~$ lspci | grep RaLink
```
03:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```


dberg@dberg-desktop:~$ sudo lshw -C network
```
  *-network DISABLED
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wmaster0
       version: 00
       serial: 00:1c:10:6a:ec:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
```


dberg@dberg-desktop:~$ modinfo rt61pci
```
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.1.8
author:         http://rt2x00.serialmonkey.com
srcversion:     8F4EE2C062AC0B948F1F3AD
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
```

---

### Post by radel on 2008-11-04
I had the same problem this afternoon with a pcmcia card with rt2561 firmware.
After booting the live-cd and seeing that it was working, I figured out that was a problem with the kernel i was using.

Installing linux-backport-modules-intrepid and linux-image-generic (which needed linux-firmware) solved for me.

---

### Post by drberg1000 on 2009-01-21
radel:  thanks for the suggestions but they don't seem to help at all.  There don't seem to be any RT61 modules I can load. 

Trying to build the RT61 module is giving me trouble too.

I don't have a lot of time to work on this and it works fine when I load a 32bit live CD.  Is there an easy way for me to convert convert my system to a 32 bit install?

Thanks much.

--Dave

---

### Post by drberg1000 on 2009-01-21
Just noticed I've been trying to load the wrong driver name today.  When I use modprobe rp61pci I get...


```
dberg@dberg-desktop:~/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo modprobe rt61pci
[sudo] password for dberg: 
WARNING: Error inserting rt2x00lib (/lib/modules/2.6.27-9-generic/updates/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00pci (/lib/modules/2.6.27-9-generic/updates/rt2x00pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt61pci (/lib/modules/2.6.27-9-generic/updates/rt61pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dberg@dberg-desktop:~/RT61_Linux_STA_Drv1.1.0.0/Module$
``` 


Seeing dmesg as instructed:

```
[10131.201601] rt61pci: Unknown symbol rt2x00mac_config_interface
[10131.201850] rt61pci: Unknown symbol rt2x00pci_remove
[10131.202026] rt61pci: Unknown symbol rt2x00mac_remove_interface
[10131.202203] rt61pci: Unknown symbol rt2x00lib_txdone
[10131.202380] rt61pci: Unknown symbol rt2x00mac_config
[10131.202557] rt61pci: Unknown symbol rt2x00queue_get_queue
[10131.202734] rt61pci: Unknown symbol rt2x00mac_conf_tx
[10131.203060] rt61pci: Unknown symbol rt2x00mac_start
[10131.203238] rt61pci: Unknown symbol rt2x00mac_stop
[10131.203471] rt61pci: Unknown symbol rt2x00mac_configure_filter
[10131.203648] rt61pci: Unknown symbol rt2x00mac_tx
[10131.203825] rt61pci: Unknown symbol rt2x00pci_resume
[10131.204064] rt61pci: Unknown symbol rt2x00pci_probe
[10131.204241] rt61pci: Unknown symbol rt2x00mac_get_tx_stats
[10131.204607] rt61pci: Unknown symbol rt2x00pci_rxdone
[10131.204811] rt61pci: Unknown symbol rt2x00mac_bss_info_changed
[10131.204989] rt61pci: Unknown symbol rt2x00pci_write_tx_data
dberg@dberg-desktop:~$ 
```

This is just the tail end.

---

