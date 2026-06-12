---
title: "Need to scan before running wpa_supplicant on RT2500"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by glutinous on 2008-06-20
Hi,

I have managed to get my RT2500 wireless networking card working with my WPA/WPA2 access point. But it requires some funny steps so I was wondering if anyone had any suggestions on how I can better automate it. Right now I need to do the following:

[LIST=1]
[*]modprobe -r rt2500pci
[*]modprobe rt2500pci
[*]iwlist wlan0 scanning
**(Successfully finds wireless network and prints it out)**
[*]wpa_supplicant -c./wpa-psk-tkip.conf -iwlan0 -d
**(Successfully associates with AP)**
[*]dhclient wlan0
**(Successfully gets IP address from DHCP server)**
[/LIST]

If I skip the iwlist part, or adding/removing modules then it doesn't work.

Any ideas on how I can get this working from just the /etc/networking/interfaces config file?

I am running Hardy, with kernel, linux-image-2.6.24-19-generic (version 2.6.24-19.33), and the backport modules, linux-backports-modules-2.6.24-19-generic (version 2.6.24-19.17).

My wifi card (output from lspci -v):

```

01:07.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: Unknown device 18eb:5310
	Flags: bus master, slow devsel, latency 32, IRQ 20
	Memory at e8000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

```

The wpa_supplicant config I am using:

```

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="jungle"
	key_mgmt=WPA-PSK
	proto=WPA2
	pairwise=TKIP
	group=TKIP
	psk="SECRET"
}

```

modinfo of the rt2500pci kernel module I am using:

```

filename:       /lib/modules/2.6.24-19-generic/updates/wireless/rt2x00/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.1.4
author:         http://rt2x00.serialmonkey.com
srcversion:     C6C39A4D25E3DC3C2D47678
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
vermagic:       2.6.24-19-generic SMP mod_unload 586

```

Right now, I am using the following for my /etc/networking/interfaces, but it doesn't work. I need to manually setup the network using the steps I described above.

```

auto wlan0
iface wlan0 inet dhcp
wpa-ssid jungle
wpa-proto WPA2
wpa-key-mgmt WPA-PSK
wpa-psk "SECRET"

```

-Glutinous

---

