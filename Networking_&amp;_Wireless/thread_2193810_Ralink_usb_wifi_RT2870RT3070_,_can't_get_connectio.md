---
title: "Ralink usb wifi RT2870/RT3070 , can't get connection"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by oscar.danielm on 2013-12-14
Hello all, 

i'm new in linux and i need help..

i have a problem with my connection, i can't get network, i don't know what to do..

acording with Additional drive r- the usb driver is install but not in use, why happen this?  :confused:
[ATTACH=CONFIG]248610[/ATTACH]

somebody can help me.. 

thanks


ok,,

here is the output:


```
*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 040b:2011 Weltrend Semiconductor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.76
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search lan

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address  removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"

***** dmesg *****


****************** done ******************
```

---

### Post by varunendra on 2013-12-15
Welcome to the forums oscar.danielm !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by oscar.danielm on 2013-12-19
some one can help me with my issue..

---

### Post by varunendra on 2013-12-19
> **oscar.danielm said:**
> some one can help me with my issue..

Hello oscar.danielm,

You should post updates in new posts, otherwise your thread won't come up in our search results as "unread" and we can't know you have posted an update.

I am currently travelling and mostly out of signal to connect to internet (and low on laptop battery too), so may not be able to reply back quickly. But as per the report you posted, neither the proprietary, nor the native driver is loaded for your adapter.

For now, please try (while the usb adapter is plugged in) -
```
sudo modprob -v rt2800usb
```

Then check -
```
lsmod | grep rt2
iwconfig
sudo iwlist scan
dmesg | grep rt2
```

Please post back the result of the above commands, and I'll try to reply back as soon as possible. :)

---

### Post by oscar.danielm on 2013-12-23
thank varun..

i made somthing and crash the system... and re-install again.. :) but here are the output..

```

*************** info trace ***************

***** uname -a *****

Linux daniel-HP-dv6000 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 040b:2011 Weltrend Semiconductor 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****

rt2800usb              22773  0 
rt2800lib              58967  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20808  1 rt2800usb
rt2x00lib              55382  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506862  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search gateway.2wire.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     97DFE1D97D1F82B1A0E6405
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.2.0-57-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     5EABEA0AE546B2B7B7EBC1A
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.2.0-57-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D537DA9342A12F9A4C96005
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.2.0-57-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E604D2DEC4141A1B32A11E7
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-57-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[   20.510480] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[   20.510532] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.

****************** done ******************

```

and the output for the last comman:

```

root@daniel-HP-dv6000:/home/daniel# sudo modprob -v rt2800usb
sudo: modprob: command not found

root@daniel-HP-dv6000:/home/daniel# lsmod | grep rt2
rt2800usb              22773  0 
rt2800lib              58967  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20808  1 rt2800usb
rt2x00lib              55382  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              506862  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211


root@daniel-HP-dv6000:/home/daniel# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@daniel-HP-dv6000:/home/daniel# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


root@daniel-HP-dv6000:/home/daniel# dmesg | grep rt2
[   20.510480] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[   20.510532] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   20.510654] usbcore: registered new interface driver rt2800usb


```

---

### Post by chili555 on 2013-12-23
Since Varun may be traveling, I'll respectfully lend a little hand, if I may.> [   20.510480] phy0 -> rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected.
[   20.510532] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.That means, roughly, although the driver rt2800usb is supposed to drive your device 148f:3070, guess what; it doesn't. Boo hoo.

Let's try a newer version of rt2800usb that, hopefully, works better. With a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic
```Detach the ethernet, reboot and let us hear your report.

We now return you to your regularly scheduled guru.

---

### Post by oscar.danielm on 2013-12-23
thanks for you time chili but still same thing..

```

***** dmesg *****

[   21.456718] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   21.523719] ieee80211 phy0: rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected
[   21.523772] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device


```


i downloaded suppose the driver from the ralink page rt2870/3070.. but it doesn't work..

in windows vista it works fine, but in ubuntu i can't make work the usb wifi..

---

### Post by varunendra on 2013-12-26
> **chili555 said:**
> Since Varun may be traveling, I'll respectfully lend a little hand, if I may.
Thank you so much for the helping hand Sir !
Unfortunately, I have got indulged in something which seems to be going to keep me full time busy for a long time (unless I didn't like it and got rid of it). Although not sure it can really keep me away from the forums. :P

@oscar.danielm,

You may try an even newer driver. Please follow the instructions in this post : [http://ubuntuforums.org/showthread.php?t=2194870&p=12883518#post12883518](http://ubuntuforums.org/showthread.php?t=2194870&p=12883518#post12883518)

Just replace the command "make defconfig-rtlwifi" with "**make defconfig-wifi**" in the above post, and it will become an instruction set for your issue (of course installing a different driver than rtl8723ae which that post is originally written for).

---

### Post by oscar.danielm on 2013-12-27
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]thanksvarun for u support,

but i still have the problem, suppose thedriver is installer but i don't have wifi signal, the usb adapter is"dead" any light is on...
a cording with the result ofyour wifi script this is the output, the error disappeared..
[/SIZE][/FONT][/COLOR]

```

*************** info trace ***************


***** uname -a *****


Linux daniel-HP-dv6000 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


***** lspci *****


00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 040b:2011 Weltrend Semiconductor 


***** PCMCIA Card Info *****




***** iwconfig *****


ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0




***** rfkill *****




***** lsmod *****


rt5572sta             802219  0 


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.85
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


lo        Interface doesn't support scanning.


ra0       Interface doesn't support scanning.


eth0      Interface doesn't support scanning.




***** resolv.conf *****


nameserver 127.0.0.1
search lan


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-local.conf]
blacklist rt5572sta


***** modinfo *****


filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt5572sta.ko
version:        2.6.1.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     0437D721DA31F3109C8F9D3
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1875p7733d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-57-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)




***** udev rules *****


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   28.038804] rtusb init rt2870 --->


****************** done ******************

```

			[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]idon't know what else do.. 
i hope u have a little time tohelp us..[/SIZE][/FONT][/COLOR]

or if you know where i can read info to fix this...

saludos!!
Daniel

---

### Post by chili555 on 2013-12-27
The driver he suggested is not what you have installed if your interface is ra0. ra0 is usually a result of a file downloaded directly from Ralink. I suggest you remove it. Follow the same procedure:```
cd ~/Desktop/downloaded_file  [COLOR="#FF0000"]<--or wherever you extracted it[/COLOR]
sudo su
make uninstall
exit
```Then try the process Varun linked again. After it is finished, reboot.

---

### Post by oscar.danielm on 2013-12-28
Chili555,
 i made what you said, but it didn't work, still same..

i unistalled the ralink driver and install the backports..

check the output:

```

************** info trace ***************


***** uname -a *****


Linux daniel-HP-dv6000 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
	Kernel driver in use: forcedeth


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 040b:2011 Weltrend Semiconductor 


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.85
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.




***** resolv.conf *****


nameserver 127.0.0.1
search lan


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****




***** udev rules *****


# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****




****************** done ******************

```

can i do other thing?

saludos
Daniel

---

### Post by varunendra on 2013-12-29
As you can see yourself in the report, there is nothing to see or verify about the driver in it, since it is neither loaded nor are there any messages about it in dmesg.

Please try -
```
sudo modprobe -v rt2800usb
```
And check -
```
dmesg | grep rt28
```
Do you see any errors? Please post them back if you do. If not, can you scan wireless networks now? -
```
sudo iwlist scan
```

---

### Post by oscar.danielm on 2013-12-29
thanks for your help varun..

many error.. here is the output:

```

root@daniel-HP-dv6000:/home/daniel# sudo modprobe -v rt2800usb
insmod /lib/modules/3.2.0-57-generic/updates/net/wireless/cfg80211.ko 
WARNING: Error inserting cfg80211 (/lib/modules/3.2.0-57-generic/updates/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-57-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg WARNING: Error inserting crc_ccitt (/lib/modules/3.2.0-57-generic/kernel/lib/crc-ccitt.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2800lib (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2800usb (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2800usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@daniel-HP-dv6000:/home/daniel# dmesg | grep rt28
root@daniel-HP-dv6000:/home/daniel# sudo iwlist scan
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.

```

can u tell me what other thing can i do?

saludos
Daniel

---

### Post by varunendra on 2013-12-29
Please run the same commands again, then as the error messages suggest to do, take a look at dmesg -
```
dmesg | tail -40
```
Please post back the output of the dmesg command above after running the "sudo modprobe -v rt2800usb" command.

---

### Post by oscar.danielm on 2013-12-30
here is the output with the new command:
```

daniel@daniel-HP-dv6000:~$ sudo modprobe -v rt2800usb
insmod /lib/modules/3.2.0-57-generic/updates/net/wireless/cfg80211.ko 
WARNING: Error inserting cfg80211 (/lib/modules/3.2.0-57-generic/updates/net/wireless/cfg80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-57-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00lib (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2x00usb (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting crc_ccitt (/lib/modules/3.2.0-57-generic/kernel/lib/crc-ccitt.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rt2800lib (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rt2800usb (/lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2800usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
daniel@daniel-HP-dv6000:~$ dmesg | grep rt28
daniel@daniel-HP-dv6000:~$ dmesg | tail -40
[ 1239.912119] PM: resume of drv:usb dev:1-1:1.0 complete after 117.358 msecs
[ 1239.912138] PM: resume of drv: dev:ep_00 complete after 117.097 msecs
[ 1239.912146] PM: resume of drv: dev:ep_81 complete after 117.355 msecs
[ 1239.912153] PM: resume of drv: dev:ep_01 complete after 117.329 msecs
[ 1239.912161] PM: resume of drv: dev:ep_02 complete after 117.283 msecs
[ 1239.912167] PM: resume of drv: dev:ep_03 complete after 117.257 msecs
[ 1239.912175] PM: resume of drv: dev:ep_04 complete after 117.233 msecs
[ 1239.912182] PM: resume of drv: dev:ep_05 complete after 117.208 msecs
[ 1239.912189] PM: resume of drv: dev:ep_06 complete after 117.180 msecs
[ 1239.912985] PM: resume of drv:uvcvideo dev:1-4:1.0 complete after 117.753 msecs
[ 1239.912993] PM: resume of drv:uvcvideo dev:1-4:1.1 complete after 117.702 msecs
[ 1239.912999] PM: resume of drv: dev:ep_00 complete after 117.678 msecs
[ 1239.913006] PM: resume of drv: dev:ep_83 complete after 117.744 msecs
[ 1239.941076] PM: resume of drv:usbhid dev:2-2:1.0 complete after 145.673 msecs
[ 1239.941084] PM: resume of drv: dev:ep_81 complete after 145.648 msecs
[ 1239.941090] PM: resume of drv: dev:ep_00 complete after 145.622 msecs
[ 1239.972345] ata3.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 1239.972350] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 1239.972362] ata3: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[ 1239.988302] ata3.00: configured for MWDMA2
[ 1240.080279] PM: resume of drv:battery dev:PNP0C0A:00 complete after 287.103 msecs
[ 1240.260062] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1240.268224] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 1240.284326] ata1.00: configured for UDMA/133
[ 1240.296418] PM: resume of drv:sd dev:0:0:0:0 complete after 501.342 msecs
[ 1240.296430] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 501.269 msecs
[ 1240.316486] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 524.660 msecs
[ 1240.442226] firewire_core: rediscovered device fw0
[ 1240.442884] PM: resume of drv:nvidia dev:0000:00:05.0 complete after 651.407 msecs
[ 1240.443491] PM: resume of devices complete after 652.095 msecs
[ 1240.443668] PM: resume devices took 0.652 seconds
[ 1240.443704] PM: Finishing wakeup.
[ 1240.443706] Restarting tasks ... done.
[ 1240.451375] video LNXVIDEO:00: Restoring backlight state
[ 1240.516974] ata2: SATA link down (SStatus 0 SControl 300)
[ 1253.184054] eth0: no IPv6 routers present
[ 1365.838716] cfg80211: Unknown symbol backport_genl_unregister_family (err 0)
[ 1365.839165] cfg80211: Unknown symbol __backport_genl_register_family (err 0)
[ 1425.653211] cfg80211: Unknown symbol backport_genl_unregister_family (err 0)
[ 1425.653651] cfg80211: Unknown symbol __backport_genl_register_family (err 0)

```

saludos
Daniel

---

### Post by varunendra on 2014-01-01
Hi again !

The errors are unexpected. Even though your kernel is a bit old now, the backports are supposed to fully support all the supported kernels. Now the 'supported' part can be a key here, possibly causing the errors.

Anyway, since you already tried the sta driver from Ralink's official site earlier, with no change in performance, I guess the only other thing we can try with your current kernel is to try a slightly older backported driver package instead of the latest. Try this one : [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2)

Please download it and use the same method as suggested in post #8.

Alternatively, we can try the proprietary sta driver (rt5572sta) again, properly this time (I don't know how you installed it earlier, and it was blacklisted too) and hope it would work. But for that, it may help a lot if you can give us the link to the guide you followed to install it, so we can see if you missed any important step.

If none of that works, can you do a fresh install of 12.04.3? If not, we can upgrade just the kernel, but a fresh install of the latest point release would be best to rule out any doubts about configuration/dependency issues.

---

### Post by oscar.danielm on 2014-01-03
thanks again Varun..

this is what i made.. more or less..

[http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage](http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage)

i downloaded the drivers for ralink and backported..
extract the files..
i went to the folder.. and made the next commands

make
sudo make install
sudo modprobe rt2870sta

or i followed your post#8

by the way i tried to install differents backports..

backports-3.10-2
backports-3.13-rc2-1

and the last you mentioned..
backports-3.12-1
this is the output: (according with u wifi-script i have ubuntu 12.04.3)

```

*************** info trace ***************

***** uname -a *****

Linux daniel-HP-dv6000 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 002: ID 040b:2011 Weltrend Semiconductor 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****

rt2800usb              22843  0 
rt2800lib              88613  1 rt2800usb
crc_ccitt              12707  1 rt2800lib
rt2x00usb              20742  1 rt2800usb
rt2x00lib              55065  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              569081  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              567517  2 rt2x00lib,mac80211
compat                 30258  4 rt2800usb,rt2x00lib,mac80211,cfg80211

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2800usb.ko
version:        backported from Linux (v3.12-0-g5e01dc7) using backports v3.12-1-0-g9ae6b6c
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     15E60061680AE27D19A3BEF
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2800lib,rt2x00usb,compat
vermagic:       3.2.0-57-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     0D90A441E5E3AD7E88361B3
depends:        rt2x00lib,mac80211,crc-ccitt
vermagic:       3.2.0-57-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     3FB557481D528590192EF77
depends:        rt2x00lib,mac80211
vermagic:       3.2.0-57-generic SMP mod_unload modversions 

filename:       /lib/modules/3.2.0-57-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     797CC4241FB07974BD524B2
depends:        mac80211,compat,cfg80211
vermagic:       3.2.0-57-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****
[B]
[   35.639670] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   35.668054] ieee80211 phy0: rt2800_init_eeprom: Error - Invalid RF chipset 0x3070 detected
[   35.668074] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device[/B]

****************** done ******************

```

and other thing, i tried to install the ralink driver rt2870, but this one has a problem,
when i made "make"..
this is what i get:
```

root@daniel-HP-dv6000:/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1# make
make -C tools
make[1]: Entering directory `/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/3.2.0-57-generic/build SUBDIRS=/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-57-generic'
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_md5.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1408 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1408 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1616 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_UNWRAP&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:2348:1: warning: the frame size of 1152 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:895:2: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:895:2: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c: In function &#8216;BssTableSetEntry&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:5739:39: warning: operation on &#8216;Tab->BssOverlapNr&#8217; may be undefined [-Wsequence-point]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/mlme.c:6100:1: warning: the frame size of 1728 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_wep.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/action.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_data.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_aes.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_sync.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/eeprom.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_info.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/dfs.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/spectrum.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/spectrum.c:1977:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rt_channel.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_profile.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_asic.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/assoc.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1764:1: warning: the frame size of 1328 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:764:1: warning: the frame size of 1264 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sync.c:1094:1: warning: the frame size of 1328 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sanity.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/connect.c:355:1: warning: the frame size of 1760 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/wpa.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/ags.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ba_action.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/ba_action.c:1531:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocUsbBulkBufStruct&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52:2: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217; [-Werror=implicit-function-declaration]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52:13: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeUsbBulkBufStruct&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78:3: error: implicit declaration of function &#8216;usb_buffer_free&#8217; [-Werror=implicit-function-declaration]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitRecv&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:745:30: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:849:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:932:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:949:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:975:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:982:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:997:12: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:1015:11: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:1150:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:1157:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:1194:11: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
cc1: some warnings being treated as errors
[B]make[2]: *** [/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/daniel/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-57-generic'
make: *** [LINUX] Error 2[/B]

```

and the ralink driver rt5572sta, this one more or less works, due to i can see the driver in 
"Additional Drivers menu" but the usb doesn't work.. (same as the picture in the post#1)
this is the output:

```

*************** info trace ***************

***** uname -a *****

Linux daniel-HP-dv6000 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 002 Device 002: ID 040b:2011 Weltrend Semiconductor 

***** PCMCIA Card Info *****


***** iwconfig *****

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


***** rfkill *****


***** lsmod *****

rt5572sta             802219  0 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.89
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search lan

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/rt5572sta.ko
version:        2.6.1.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     0437D721DA31F3109C8F9D3
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1875p7733d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0067d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-57-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[   34.165882] rtusb init rt2870 --->

****************** done ******************

```

any idea what is happening with this..

saludos
Daniel

---

### Post by varunendra on 2014-01-04
> **oscar.danielm said:**
> this is what i made.. more or less..

[http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage](http://ubunturt2870.pbworks.com/w/page/8928776/FrontPage)
That guide is way outdated and so is the driver suggested on that page. So I would disregard it altogether.

> by the way i tried to install differents backports..
..and based on the last one's output, it is clear that your chip is properly supported by none yet. So let's move on to the latest proprietary one available..

> and the ralink driver rt5572sta, this one more or less works, due to i can see the driver in 
"Additional Drivers menu" but the usb doesn't work.. (same as the picture in the post#1)
..let's try compiling the one directly downloaded from Ralink's official website. Please make sure the required packages for compiling the driver are installed beforehand -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Once the above packages are installed/updated, follow the instructions as follows :

[INDENT]**1)** Download the RT5572 USB driver package from this page : [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501) . This will be a tar.bz2 package *(currently DPO_RT5572_LinuxSTA_2.6.1.3_20121022.tar.bz2)* of 835.8 KB (816.2 KiB) size.

**2)** Copy this file to your desktop > Right-click > "Extract here"

**3)** Open the file **os/linux/config.mk** from the extracted directory. Change the values of lines 26 and 35 from "**n**" to "**y**", so that they become -
```
HAS_WPA_SUPPLICANT=**[COLOR="#800000"]y[/COLOR]**
```
and ```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#800000"]y[/COLOR]**
``` respectively. Proofread, save and close the file.

**4)** Now open a terminal (Ctrl-Alt-T) and run the following commands one-by-one :
```
cd Desktop/DPO_RT5572_LinuxSTA_2.6.1.3_20121022
make
sudo make install
```
Watch out for errors, especially during 'make', and report back if there are any. Warnings can usually be safely ignored, as well as a typical error about "/tftpboot" in the last.

**5)** Blacklist the native driver so that it doesn't even try to load -
```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

**6)** Reboot and check lsmod to make sure the compiled driver loaded and not the native one -
```
lsmod | egrep 'rt28|rt55'
```
You should see only rt5572sta in the output, not the rt2800usb.[/INDENT]

If all of this goes smoothly, can you scan networks and connect to them? If not, my next advice would be to upgrade the kernel and try compiling the driver again as suggested above. Is a fresh install of 12.04.3 an easy option for you? That is usually better than upgrading the kernel manually.

---

### Post by oscar.danielm on 2014-01-04
the usb-wifi is working now..

thanks a lot, dude!!  for your time and u help!!

Saludos
Daniel

---

### Post by varunendra on 2014-01-05
Aha! Such a sweet clause that [FONT=Comic Sans MS]"working now"[/FONT] is! :)

Please mark the thread as [Solved] now. It helps us and the users by indicating that the thread contains a possible solution to the problem.

---

### Post by oscar.danielm on 2014-03-07
Varun, can you help me again..

yesterday i had a upgrade (i saw somthing about kernel).... and after install and restart the wifi connection didn't work..

i already trayed the last command, but i can get the connection..

i ran your script:
```


*************** info trace ***************

***** uname -a *****

Linux daniel-HP-Pavilion-dv6000 3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.71
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2800usb
blacklist rt2800usb

[/etc/modprobe.d/blacklist-local.conf]
blacklist rt5572sta

***** modinfo *****


***** udev rules *****

# PCI device 0x10de:/sys/devices/pci0000:00/0000:00:14.0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****


****************** done ******************


```

thanks

Daniel

---

### Post by varunendra on 2014-03-07
Hello Daniel !

Yes, the drawback of using a manually compiled driver is that you'll have to do that each time a kernel upgrade happens.

But which of the commands did you try? The ones in post #18 or some other one?

Did you also follow some other method in the meanwhile? Because the driver we used in post #18 is showing up as blacklisted in the report -
> **oscar.danielm said:**
> 
```

[/etc/modprobe.d/blacklist-local.conf]
blacklist rt5572sta
```

Assuming you have already compiled and installed the driver correctly again (you don't need to follow all the steps by the way, just step 3,4), please remove the blacklist file -
```
sudo rm /etc/modprobe.d/blacklist-local.conf
```
Then load the driver -
```
sudo modprobe -v rt5572sta
```
If you haven't installed the driver again, or if it wasn't installed properly for some reason, please follow steps 2-3-4 again from post #8 to install it. If it gives any errors during installation, please post back the errors.

---

### Post by oscar.danielm on 2014-03-08
it's working now..

by the way.. every time that i make a upgrade in the kernel..

i need to do the same thing.. install, and use the last two command that you posted..

thanks a lot dude!!

saludos
Daniel

---

### Post by varunendra on 2014-03-08
Glad I could help. :)

I hope you won't need these manual fixes after upgrading to 14.04, and its native driver should be good enough to handle your wireless card. But I'd also recommend to _NOT_ upgrade immediately when it is released. Give it some time to iron out its initial bugs, and preferably upgrade in May last or early June.

When the time comes and you decide to upgrade, try the OS in live mode first to make sure it supports the wifi and other hardware properly. Install it only when satisfied.

**PS:**
Please mark the thread as [SOLVED] using "Thread Tools" link above the top post on the page.

---

