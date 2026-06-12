---
title: "Gutsy - bcm43xx.ko - Invalid module format"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by ts-onlyfree on 2007-12-27
hiho,

i got my bcm43xx working with ndiswrapper  ( fsc amilo-pro v8010d ), but there is no monitoring-mode, so i tried the berlios drivers

have a look what happens...

sudo modprobe bcm43xx
WARNING: Error inserting ieee80211softmac (/lib/modules/2.6.22-14-386/kernel/net/ieee80211/softmac/ieee80211softmac.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting bcm43xx (/lib/modules/2.6.22-14-386/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko): Invalid module format

cya
tso

---

### Post by ts-onlyfree on 2007-12-27
dmesg | grep bcm
[  119.476000] bcm43xx: no version for "struct_module" found: kernel tainted.
[  119.476000] bcm43xx: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.22-14-386 mod_unload 486 '
[  125.992000] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[  126.392000] wlan0: ethernet device 00:90:4b:de:8f:8c using NDIS driver: bcmwl5a, version: 0x3642e00, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[  666.172000] bcm43xx: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.22-14-386 mod_unload 486 '
[10561.124000] bcm43xx: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.22-14-386 mod_unload 486 '

any ideas? seems that i need the right bcm43xx.ko for my kernel... but how can i create it?

---

