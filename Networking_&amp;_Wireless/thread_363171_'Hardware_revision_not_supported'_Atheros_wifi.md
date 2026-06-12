---
title: "'Hardware revision not supported' Atheros wifi"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by hearty on 2007-02-16
[LIST=1]
```

root@mesh-two:~# dmesg

[ 1045.647072] wlan: 0.8.4.2 (0.9.2.1)
[ 1182.901276] ath_rate_sample: 1.2 (0.9.2.1)
[ 1232.760956] ath_rate_sample: unloaded
[ 1235.076072] ath_hal: driver unloaded
[ 1260.472059] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[ 1275.285229] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1293.335065] ath_rate_sample: 1.2 (0.9.2.1)
[ 1303.753441] ath_pci: 0.9.4.5 (0.9.2.1)
[ 1303.753986] PCI: Enabling device 0000:01:02.0 (0001 -> 0003)
[ 1303.758126] [COLOR="Red"]wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)[/COLOR]

```
[/LIST]
[LIST=2]
```

root@mesh-two:~# uname -a

Linux mesh-two 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

```
[/LIST]
[LIST=3]
```

root@mesh-two:~# lspci

0000:01:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


```
[/LIST]
:confused:

---

### Post by Floppyjoe on 2007-02-16
This Url may help:

[http://www.ubuntuforums.org/showthread.php?t=339810&highlight=AR5212](http://www.ubuntuforums.org/showthread.php?t=339810&highlight=AR5212)

---

