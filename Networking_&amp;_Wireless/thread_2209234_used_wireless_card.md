---
title: "used wireless card?"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by papahonk2 on 2014-03-04
Hello,
 My original card started dropping me. so i bought a card online it was a used [COLOR=#000000]Intel Pro/Wireless Iwl-4965agn. but from what i read it worked on my laptop (latitude d820) and it seemed to work with linux from the few post i read. i installed it, it also had a extra plug on the card. my computer just so happened to have a extra wire, so i plugged it in. once booted it fired up and showed networks i clicked mine added password and got bars  saying i was online. but couldnt do anything. so i pulled out my trusty old linksys usb g  plugged it in but had disconnect the 4965 from the network to get the usb to get a web page to load. I did noticed when i click on the wireless icon  it shows the 4965 as a intel vaio VGN-SZ79SN C could it be set to another computer


```
 sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan2
       version: 61
       serial: 00:21:5c:10:5c:83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.11.0-17-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:ecffe000-ecffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:08:0a:9f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:ecef0000-ecefffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:22:6b:a6:4e:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.11.0-17-generic firmware=1.7 ip=192.168.2.34 link=yes multicast=yes wireless=IEEE 802.11bg
papahonk@papahonk-Latitude-D820:~$ 


```
```


    *************** info trace ***************


    ***** uname -a *****


    Linux papahonk-Latitude-D820 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux


    ***** lsb_release *****


    Distributor ID: Ubuntu
    Description: Ubuntu 13.10
    Release: 13.10
    Codename: saucy


    ***** lspci *****


    09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Device [1028:01cc]
    Kernel driver in use: tg3
    0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
    Kernel driver in use: iwl4965


    ***** lsusb *****


    Bus 001 Device 005: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 002: ID 1bcf:053e Sunplus Innovation Technology Inc.
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 003: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
    Bus 003 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 006: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
    Bus 002 Device 005: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
    Bus 002 Device 004: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
    Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
    Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


    ***** PCMCIA Card Info *****


    PRODID_1=""
    PRODID_2=""
    PRODID_3=""
    PRODID_4=""
    MANFID=0000,0000
    FUNCID=255 


```

```
***** iwconfig *****


wlan0 IEEE 802.11bg ESSID:"bgca"
Mode:Managed Frequency:2.437 GHz Access Point: <MAC address removed>
Bit Rate=54 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn
Link Quality=48/70 Signal level=-62 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:207 Missed beacon:0


wlan2 IEEE 802.11abgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=14 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff



***** rfkill *****


0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
1: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
2: phy1: Wireless LAN
Soft blocked: no
Hard blocked: no


***** iw reg get *****




***** route -n *****


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.2.1 0.0.0.0 UG 0 0 0 wlan0
192.168.2.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan0


***** lsmod *****


rt73usb 26890 0
rt2x00usb 20041 1 rt73usb
rt2x00lib 48933 2 rt73usb,rt2x00usb
iwl4965 106818 0
iwlegacy 88016 1 iwl4965
mac80211 517444 4 iwl4965,iwlegacy,rt2x00lib,rt2x00usb
cfg80211 401762 4 iwl4965,iwlegacy,mac80211,rt2x00lib
crc_itu_t 12627 2 rt73usb,firewire_core 
```

```
***** nm-tool *****

NetworkManager Tool


State: connected (global)


- Device: wlan0 [bgca 1] ------------------------------------------------------
Type: 802.11 WiFi
Driver: rt73usb
State: connected
Default: yes
HW Address: <MAC address removed>


Capabilities:
Speed: 54 Mb/s


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Points (* = current AP)
*bgca: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 56 WPA


IPv4 Settings:
Address: 192.168.2.34
Prefix: 24 (255.255.255.0)
Gateway: 192.168.2.1


DNS: 192.168.7.254




- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: tg3
State: unavailable
Default: no
HW Address: <MAC address removed>


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off




- Device: wlan2 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: iwl4965
State: disconnected
Default: no
HW Address: <MAC address removed> 
```

```
- Device: wlan2 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: iwl4965
State: disconnected
Default: no
HW Address: <MAC address removed>


Capabilities:


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Points
bgca: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0 Scan completed :
Cell 01 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=50/70 Signal level=-60 dBm
Encryption keyn
ESSID:"bgca"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000026bfbfbda5e
Extra: Last beacon: 24ms ago
IE: Unknown: 000462676361
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: 2D1A0E101EFFFF000000000000000000000000000000000000 000000
IE: Unknown: 3D1606050300000000000000000000000000000000000000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F 00
IE: Unknown: DD1E00904C330E101EFFFF0000000000000000000000000000 00000000000000
IE: Unknown: DD1A00904C3406050300000000000000000000000000000000 000000
IE: Unknown: DD0600E04C020120


wlan2 Scan completed :
Cell 01 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=65/70 Signal level=-45 dBm
Encryption keyn
ESSID:"bgca"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000026bfbfd3768
Extra: Last beacon: 52ms ago
IE: Unknown: 000462676361
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: Unknown: 2D1A0E101EFFFF000000000000000000000000000000000000 000000
IE: Unknown: 3D1606050300000000000000000000000000000000000000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F 00
IE: Unknown: DD1E00904C330E101EFFFF0000000000000000000000000000 00000000000000
IE: Unknown: DD1A00904C3406050300000000000000000000000000000000 000000
IE: Unknown: DD0600E04C020120 
```

```
***** resolv.conf *****


nameserver 127.0.1.1


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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename: /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license: GPL
firmware: rt73.bin
description: Ralink RT73 USB Wireless LAN driver.
version: 2.3.0
author: http://rt2x00.serialmonkey.com
srcversion: 79088AB6F8FA9AA591F582B
alias: usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends: rt2x00lib,rt2x00usb,crc-itu-t
intree: Y
vermagic: 3.11.0-17-generic SMP mod_unload modversions 686
parm: nohwcryptisable hardware encryption. (bool)
***** resolv.conf *****

nameserver 127.0.1.1

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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

filename: /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license: GPL
firmware: rt73.bin
description: Ralink RT73 USB Wireless LAN driver.
version: 2.3.0
author: http://rt2x00.serialmonkey.com
srcversion: 79088AB6F8FA9AA591F582B
alias: usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends: rt2x00lib,rt2x00usb,crc-itu-t
intree: Y
vermagic: 3.11.0-17-generic SMP mod_unload modversions 686
parm: nohwcryptisable hardware encryption. (bool) 
```

```
filename: /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license: GPL
description: rt2x00 usb library
version: 2.3.0
author: http://rt2x00.serialmonkey.com
srcversion: 5CFE65EA16A08E63C627D96
depends: rt2x00lib,mac80211
intree: Y
vermagic: 3.11.0-17-generic SMP mod_unload modversions 686


filename: /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license: GPL
description: rt2x00 library
version: 2.3.0
author: http://rt2x00.serialmonkey.com
srcversion: EB7C454417ADECB5D8A7F2A
depends: mac80211,cfg80211
intree: Y
vermagic: 3.11.0-17-generic SMP mod_unload modversions 686


filename: /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware: iwlwifi-4965-2.ucode
alias: iwl4965
license: GPL
author: Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version: in-tree:
description: Intel(R) Wireless WiFi 4965 driver for Linux
srcversion: C007F7FFBC37A981E9A87E5
alias: pci:v00008086d00004230sv*sd*bc*sc*i*
alias: pci:v00008086d00004229sv*sd*bc*sc*i*
depends: iwlegacy,cfg80211,mac80211
intree: Y
vermagic: 3.11.0-17-generic SMP mod_unload modversions 686
parm: swcrypto:using crypto in software (default 0 [hardware]) (int)
parm: queues_num:number of hw queues. (int)
parm: 11n_disable:disable 11n functionality (int)
parm: amsdu_size_8K:enable 8K amsdu size (int)
parm: fw_restart:restart firmware in case of error (int)


filename: /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license: GPL
author: Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version: in-tree:
description: iwl-legacy: common functions for 3945 and 4965
srcversion: BC2DEA74DD4DC4E093C27BE
depends: mac80211,cfg80211
intree: Y
vermagic: 3.11.0-17-generic SMP mod_unload modversions 686
parm: led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm: bt_coex_active:enable wifi/bluetooth co-exist (bool)




***** udev rules *****


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x13b1:0x0020 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x8086:0x4229 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2" 
```

```
***** dmesg *****


[ 21.199400] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[ 21.199405] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[ 21.199460] iwl4965 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 21.199642] iwl4965 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[ 21.242481] iwl4965 0000:0c:00.0: device EEPROM VER=0x36, CALIB=0x5
[ 21.242529] iwl4965 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 21.242637] iwl4965 0000:0c:00.0: irq 45 for MSI/MSI-X
[ 21.349524] iwl4965 0000:0c:00.0: loaded firmware version 228.61.2.24
[ 21.581456] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[ 28.047557] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 28.048072] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[ 31.575465] wlan2: authenticate with <MAC address removed>
[ 31.593507] wlan2: send auth to <MAC address removed> (try 1/3)
[ 31.597973] wlan2: authenticated
[ 31.598235] iwl4965 0000:0c:00.0 wlan2: disabling HT/VHT due to WEP/TKIP use
[ 31.600083] wlan2: associate with <MAC address removed> (try 1/3)
[ 31.607856] wlan2: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[ 31.637026] wlan2: associated
[ 31.637073] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 34.387971] iwl4965 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000000.
[ 34.387981] iwl4965 0000:0c:00.0: Loaded firmware version: 228.61.2.24
[ 34.388048] iwl4965 0000:0c:00.0: Start IWL Error Log Dump:
[ 34.388052] iwl4965 0000:0c:00.0: Status: 0x000213E4, count: 5
[ 34.388312] iwl4965 0000:0c:00.0: Desc Time data1 data2 line
[ 34.388318] iwl4965 0000:0c:00.0: FH49_ERROR (0x000C) 2324854622 0x00000008 0x03130000 208
[ 34.388321] iwl4965 0000:0c:00.0: pc blink1 blink2 ilink1 ilink2 hcmd
[ 34.388325] iwl4965 0000:0c:00.0: 0x0046C 0x0A332 0x004C2 0x006DE 0x0A386 0x443004E
[ 34.388329] iwl4965 0000:0c:00.0: FH register values:
[ 34.388366] iwl4965 0000:0c:00.0: FH49_RSCSR_CHNL0_STTS_WPTR_REG: 0X03737900
[ 34.388387] iwl4965 0000:0c:00.0: FH49_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00308c40
[ 34.388408] iwl4965 0000:0c:00.0: FH49_RSCSR_CHNL0_WPTR: 0X00000070
[ 34.388429] iwl4965 0000:0c:00.0: FH49_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819000
[ 34.388450] iwl4965 0000:0c:00.0: FH49_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
[ 34.388472] iwl4965 0000:0c:00.0: FH49_MEM_RSSR_RX_STATUS_REG: 0X03130000
[ 34.388493] iwl4965 0000:0c:00.0: FH49_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 34.388514] iwl4965 0000:0c:00.0: FH49_TSSR_TX_STATUS_REG: 0X07ff0002
[ 34.388535] iwl4965 0000:0c:00.0: FH49_TSSR_TX_ERROR_REG: 0X00000000
[ 170.638164] ieee80211 phy1: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[ 170.666187] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[ 170.687080] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[ 170.765182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 170.765856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 173.192818] wlan0: authenticate with <MAC address removed>
[ 173.251490] wlan0: send auth to <MAC address removed> (try 1/3)
[ 173.276916] wlan0: authenticated
[ 173.277258] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 173.280115] wlan0: associate with <MAC address removed> (try 1/3)
[ 173.287295] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 173.298135] wlan0: associated
[ 173.298184] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 283.432077] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 284.744778] wlan0: authenticate with <MAC address removed>
[ 284.785353] wlan0: send auth to <MAC address removed> (try 1/3)
[ 284.988071] wlan0: send auth to <MAC address removed> (try 2/3)
[ 284.992775] wlan0: authenticated
[ 284.993078] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 284.996074] wlan0: associate with <MAC address removed> (try 1/3)
[ 285.011770] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 285.022138] wlan0: associated
[ 337.576073] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 345.064757] wlan0: authenticate with <MAC address removed>
[ 345.105102] wlan0: send auth to <MAC address removed> (try 1/3)
[ 345.122174] wlan0: authenticated
[ 345.122460] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 345.124100] wlan0: associate with <MAC address removed> (try 1/3)
[ 345.328068] wlan0: associate with <MAC address removed> (try 2/3)
[ 345.532057] wlan0: associate with <MAC address removed> (try 3/3)
[ 345.736060] wlan0: association with <MAC address removed> timed out
[ 353.260231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 359.404819] wlan0: authenticate with <MAC address removed>
[ 359.445567] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 359.648071] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 359.852071] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 360.056068] wlan0: authentication with <MAC address removed> timed out
[ 361.352844] wlan0: authenticate with <MAC address removed>
[ 361.393299] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 361.596073] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 361.800070] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 362.004042] wlan0: authentication with <MAC address removed> timed out
[ 363.304845] wlan0: authenticate with <MAC address removed>
[ 363.344784] wlan0: send auth to <MAC address removed> (try 1/3)
[ 363.350698] wlan0: authenticated
[ 363.350975] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 363.352073] wlan0: associate with <MAC address removed> (try 1/3)
[ 363.357937] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 363.369051] wlan0: associated
[ 363.369070] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 379.052551] wlan2: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2423.508077] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2430.992831] wlan0: authenticate with <MAC address removed>
[ 2431.035819] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2431.236075] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2431.440086] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2431.644070] wlan0: authentication with <MAC address removed> timed out
[ 2432.940832] wlan0: authenticate with <MAC address removed>
[ 2432.981050] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2433.184065] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2433.388069] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2433.592048] wlan0: authentication with <MAC address removed> timed out
[ 2439.274258] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2597.408841] wlan0: authenticate with <MAC address removed>
[ 2597.450460] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2597.461125] wlan0: authenticated
[ 2597.461409] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2597.464073] wlan0: associate with <MAC address removed> (try 1/3)
[ 2597.470872] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 2597.481605] wlan0: associated
[ 2597.481652] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2722.508079] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2723.812800] wlan0: authenticate with <MAC address removed>
[ 2723.853513] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2723.861695] wlan0: authenticated
[ 2723.861987] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2723.864088] wlan0: associate with <MAC address removed> (try 1/3)
[ 2723.870428] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 2723.882173] wlan0: associated
[ 2772.508079] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2773.820841] wlan0: authenticate with <MAC address removed>
[ 2773.861269] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2774.064055] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2774.268081] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2774.472056] wlan0: authentication with <MAC address removed> timed out
[ 2775.768833] wlan0: authenticate with <MAC address removed>
[ 2775.809109] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2776.012078] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2776.216069] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2776.420048] wlan0: authentication with <MAC address removed> timed out
[ 2777.716870] wlan0: authenticate with <MAC address removed>
[ 2777.756837] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2777.960072] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2777.983381] wlan0: authenticated
[ 2777.983731] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2777.984059] wlan0: associate with <MAC address removed> (try 1/3)
[ 2778.006547] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 2778.018002] wlan0: associated
[ 2795.504079] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2796.812805] wlan0: authenticate with <MAC address removed>
[ 2796.853487] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2797.056073] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2797.260068] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2797.464064] wlan0: authentication with <MAC address removed> timed out
[ 2798.760850] wlan0: authenticate with <MAC address removed>
[ 2798.800950] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2798.804508] wlan0: authenticated
[ 2798.804777] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2798.808115] wlan0: associate with <MAC address removed> (try 1/3)
[ 2798.813904] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 2798.824861] wlan0: associated
[ 2815.492080] ieee80211 phy1: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[ 2816.800838] wlan0: authenticate with <MAC address removed>
[ 2816.841157] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2817.044087] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2817.248074] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2817.452056] wlan0: authentication with <MAC address removed> timed out
[ 2824.916852] wlan0: authenticate with <MAC address removed>
[ 2824.956860] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2825.160072] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2825.364049] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2825.568047] wlan0: authentication with <MAC address removed> timed out
[ 2826.868906] wlan0: authenticate with <MAC address removed>
[ 2826.908900] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2827.112062] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2827.316076] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 2827.520075] wlan0: authentication with <MAC address removed> timed out
[ 2831.273614] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3997.408853] wlan0: authenticate with <MAC address removed>
[ 3997.449599] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3997.452399] wlan0: authenticated
[ 3997.452697] rt73usb 1-5:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3997.456099] wlan0: associate with <MAC address removed> (try 1/3)
[ 3997.462410] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=9)
[ 3997.473630] wlan0: associated
[ 3997.473680] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ****************** 
```


[/COLOR]

i ran the wireless info test but dont know how to get the info to you as it said i had 10 images and the max was 8

[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385) from this page

---

### Post by papahonk2 on 2014-03-04
i tried to do this with the usb off  and just the internal card running but, i didnt understand what he wanted  with the code he wanted us to load for the offline machine

---

### Post by chili555 on 2014-03-04
I suggest you reboot with the USB detached. Try to connect with the internal Intel. Run the wireless info again. Then attach the USB and post the wireless info, which was run unencumbered by the conflicting USB, here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Give us the link in your reply.

We'll try to figure this little gem out:> iwl4965 0000:0c:00.0: Microcode SW error detected. Restarting 0x82000000.

---

### Post by papahonk2 on 2014-03-12
sorry it took so long  

[http://paste.ubuntu.com/7082045](http://paste.ubuntu.com/7082045)

thanks for any help

---

### Post by chili555 on 2014-03-12
We see about 40% of the wireless_info file and we also see all the drivers loaded for the USB which probably conflict. Please detach the USB and any ethernet. Reboot so we have a clean slate. Run:```
dmesg | grep iwl > wifi.txt
```Hook up the USB or even better, the ethernet and find the file wifi.txt and paste it as above.

---

### Post by papahonk2 on 2014-03-16
that was a a clean boot i was hard wired in for it no usb attached

---

### Post by chili555 on 2014-03-16
> **papahonk2 said:**
> that was a a clean boot i was hard wired in for it no usb attachedWhy are these all loaded? > rt73usb                26890  0 
rt2x00usb              20041  1 rt73usb
rt2x00lib              48933  2 rt73usb,rt2x00usbAre they called in /etc/modules? Please post:```
cat /etc/modules
```

---

