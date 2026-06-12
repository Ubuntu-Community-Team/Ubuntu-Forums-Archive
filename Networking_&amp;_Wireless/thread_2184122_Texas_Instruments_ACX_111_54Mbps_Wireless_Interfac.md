---
title: "Texas Instruments ACX 111 54Mbps Wireless Interface"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by maxcar on 2013-10-27
Hi, I can't connect with this card.

Here is the code result. Thanks in advance.


*************** info trace ***************

***** uname -a *****

Linux cris-desktop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

***** lspci *****

00:0b.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
    Kernel driver in use: uhci_hcd
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

***** lsusb *****

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****

wl1251_sdio             1990  0 
wl1251                 75002  1 wl1251_sdio
mac80211              205402  2 wl1251_sdio,wl1251
cfg80211              126144  2 wl1251,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.50
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.81.16.164
    DNS:             62.81.16.213



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

***** NetworkManager.conf *****

nm-system-settings.conf (used up to 10.04):

[main]
plugins=ifupdown,keyfile

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 62.81.16.164
nameserver 62.81.16.213

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/wl12xx/wl1251_sdio.ko
author:         Kalle Valo <kalle.valo@nokia.com>
license:        GPL
srcversion:     1979679AECE051400A9BA2F
alias:          sdio:c*v104Cd9066*
depends:        mac80211,wl1251
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 

filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/wl12xx/wl1251.ko
alias:          spi:wl12xx
author:         Kalle Valo <kalle.valo@nokia.com>
license:        GPL
description:    TI wl1251 Wireles LAN Driver Core
srcversion:     F629647BCE8CF1FBAFBB938
depends:        mac80211,cfg80211
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 


***** udev rules *****

# PCI device 0x1106:0x3065 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[   14.072779] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin

****************** done ******************

---

### Post by varunendra on 2013-10-27
> **maxcar said:**
> 
Linux cris-desktop **[COLOR="#FF0000"]2.6.32-33-generic[/COLOR]** #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    **[COLOR="#FF0000"]Ubuntu 10.04.3 LTS[/COLOR]**

10.04 desktop has reached its EOL ([End Of Life]("https://wiki.ubuntu.com/Releases")). Please upgrade to 12.04.3 that uses a much newer kernel and has better support for hardware. Either your card should work without any tweaks on it, or it would make more sense to troubleshoot it on a supported version.

I would recommend to download its ISO via torrent to ensure integrity of the download, and choose 64 bit if your system supports that : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

Burn a CD or create a live USB with the above downloaded ISO and test it in live mode first (use "Test" option when prompted). If it seems to work nicely, do a fresh install overwriting the current one. If you want to save something from the current installation, or otherwise need help with that, please start a new thread with relevant title in a relevant section (e.g. Installation & Upgrades).

---

### Post by Iowan on 2013-10-27
Moved to new thread

---

### Post by caesar753 on 2013-11-09
welcome in the club ...

---

