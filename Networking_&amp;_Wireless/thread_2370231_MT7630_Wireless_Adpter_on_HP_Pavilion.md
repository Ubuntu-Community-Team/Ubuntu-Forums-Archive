---
title: "MT7630 Wireless Adpter on HP Pavilion"
date: 2017-08-31
forum: Networking &amp; Wireless
---

### Post by simajinid on 2017-08-31
I installed Ubuntu 16.4 LTS on a USB drive for HP pavilion 15. The wifi adapter (Mediatek MT7630e) was working with Windwos 10. But on Ubuntu the Adapter is not recognized.
How can I make it work? Are drivers for HP pavilion laptops for Mediatek MT7630 available?

---

### Post by praseodym on 2017-09-02
Driver can be installed afterwards via LAN:

[https://github.com/neurobin/MT7630E/](https://github.com/neurobin/MT7630E/)

Installation
```

sudo apt-get install git build-essential
git clone https://github.com/neurobin/MT7630E.git
cd MT7630E/
chmod +x install test uninstall
sudo ./install
```

or via dkms:
```

sudo apt-get install git dkms build-essential
git clone https://github.com/neurobin/MT7630E.git
cd MT7630E/
sudo make dkms
```
[https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working](https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working)

Driver info wireless

modinfo mt7630e```

filename:       /lib/modules/4.4.0-93-generic/updates/dkms/mt7630e.ko
license:        GPL
description:    rt2x00 library
version:        2.3.8
author:         http://rt2x00.serialmonkey.com
license:        GPL
description:    rt2x00 7630 library
version:        2.3.8
author:         http://rt2x00.serialmonkey.com
license:        GPL
description:    rt2x00 mmio library
version:        2.3.8
author:         http://rt2x00.serialmonkey.com
license:        GPL
firmware:       MT7650E234.bin
description:    Mediatek MT7630 PCI Wireless LAN driver.
version:        2.3.8
author:         http://rt2x00.serialmonkey.com
license:        GPL
description:    Ralink RT2800 library
version:        2.3.8
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
license:        GPL
description:    rt2x00 pci library
version:        2.3.8
author:         http://rt2x00.serialmonkey.com
srcversion:     F8B691AE2F721FE1A2079D3
alias:          pci:v000014C3d00007650sv*sd*bc*sc*i*
alias:          pci:v000014C3d00007630sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,eeprom_93cx6,crc-ccitt
vermagic:       4.4.0-93-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

Driver mt76xx Bluetooth
```

modinfo mt76xx 
filename:       /lib/modules/4.4.0-93-generic/updates/dkms/mt76xx.ko
firmware:       mt76x2.bin
firmware:       mt76x0.bin
license:        GPL
version:        2.0.4
description:    Mediatek Bluetooth USB driver ver 2.0.4
srcversion:     0F8BC23AD4290355A0CADA0
alias:          usb:v0489pE080d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0489pE080d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v0489pE069d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0489pE069d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v0E8Dp7632d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v0E8Dp7662d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v0E8Dp763Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp763Ed*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7650d*dc*dsc*dp*icE0isc01ip01in*
depends:        
vermagic:       4.4.0-93-generic SMP mod_unload modversions
```

---

