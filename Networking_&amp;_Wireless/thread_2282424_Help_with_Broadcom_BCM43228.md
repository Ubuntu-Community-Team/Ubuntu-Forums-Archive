---
title: "Help with Broadcom BCM43228"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by noebondone on 2015-06-13
Hi! I'need help! I'm not espeak englhish!!! But understand...

Go...

```
########## wireless info START ##########

Report from: 12 Jun 2015 21:15 ART -0300

Booted last: 12 Jun 2015 21:03 ART -0300

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge

0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 003: ID 0a5c:21f3 Broadcom Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              484040  0 
bcma                   52096  0 
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       666     1  0 21:03 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/673/hci0/dev_6C_9B_02_69_17_55
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7c7ce47a-eb83-41f5-bfb7-7f3d380d678b | Red Noé

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:0c:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/LAYUNTA]] (600 root)
[connection] id=LAYUNTA | type=802-11-wireless
[802-11-wireless] ssid=LAYUNTA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INTERNET DEL COLE]] (600 root)
[connection] id=INTERNET DEL COLE | type=802-11-wireless
[802-11-wireless] ssid=INTERNET DEL COLE | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Fidel]] (600 root)
[connection] id=Fidel | type=802-11-wireless
[802-11-wireless] ssid=Fidel | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TURISTAS]] (600 root)
[connection] id=TURISTAS | type=802-11-wireless
[802-11-wireless] ssid=TURISTAS | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FliaA]] (600 root)
[connection] id=FliaA | type=802-11-wireless
[802-11-wireless] ssid=FliaA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FLORENCIA*]] (600 root)

[[/etc/NetworkManager/system-connections/La Guardia 2]] (600 root)
[connection] id=La Guardia 2 | type=802-11-wireless
[802-11-wireless] ssid=La Guardia 2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WIFICASA]] (600 root)
[connection] id=WIFICASA | type=802-11-wireless
[802-11-wireless] ssid=WIFICASA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Claro Internet]] (600 root)
[connection] id=Claro Internet | type=802-11-wireless
[802-11-wireless] ssid=Claro Internet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-Arnet-2001]] (600 root)
[connection] id=WiFi-Arnet-2001 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-2001 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Lucy]] (600 root)
[connection] id=Lucy | type=802-11-wireless
[802-11-wireless] ssid=Lucy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KUALKIERA 2]] (600 root)
[connection] id=KUALKIERA 2 | type=802-11-wireless
[802-11-wireless] ssid=KUALKIERA 2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-Arnet-4wk4]] (600 root)
[connection] id=WiFi-Arnet-4wk4 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-4wk4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-Arnet-4133]] (600 root)
[connection] id=WiFi-Arnet-4133 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-4133 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tenda]] (600 root)
[connection] id=Tenda | type=802-11-wireless
[802-11-wireless] ssid=Tenda | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/eliana wifi]] (600 root)
[connection] id=eliana wifi | type=802-11-wireless
[802-11-wireless] ssid=eliana wifi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CRISTINA CAPITANA]] (600 root)
[connection] id=CRISTINA CAPITANA | type=802-11-wireless
[802-11-wireless] ssid=CRISTINA CAPITANA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-Arnet-2453]] (600 root)
[connection] id=WiFi-Arnet-2453 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-2453 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/G2 mini_3283]] (600 root)
[connection] id=G2 mini_3283 | type=802-11-wireless
[802-11-wireless] ssid=G2 mini_3283 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-Arnet-b1c4]] (600 root)
[connection] id=WiFi-Arnet-b1c4 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-b1c4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Fibertel WiFi541]] (600 root)
[connection] id=Fibertel WiFi541 | type=wifi
[wifi] ssid=Fibertel WiFi541 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/88754]] (600 root)
[connection] id=88754 | type=802-11-wireless
[802-11-wireless] ssid=88754 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HP-Print-B8-LaserJet 1102]] (600 root)
[connection] id=HP-Print-B8-LaserJet 1102 | type=802-11-wireless
[802-11-wireless] ssid=HP-Print-B8-LaserJet 1102 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WiFi-Arnet-hzgw]] (600 root)
[connection] id=WiFi-Arnet-hzgw | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-hzgw | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Kafka]] (600 root)
[connection] id=Kafka | type=802-11-wireless
[802-11-wireless] ssid=Kafka | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IPEM 167]] (600 root)
[connection] id=IPEM 167 | type=802-11-wireless
[802-11-wireless] ssid=IPEM 167 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ap01]] (600 root)
[connection] id=ap01 | type=802-11-wireless
[802-11-wireless] ssid=ap01 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Argentina/Cordoba (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     22618C9A8AD682CBE73FFF2
depends:        
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9A:AC:90:0A:BD:02:20:FB:93:C8:BE:10:F2:0D:69:73:DA:B8:29:F5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.13.0-53-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9A:AC:90:0A:BD:02:20:FB:93:C8:BE:10:F2:0D:69:73:DA:B8:29:F5
sig_hashalgo:   sha512

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4359 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    9.252910] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[    9.252962] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[    9.252987] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[    9.265578] bcma: bus0: Bus registered
[   10.183449] usb 1-1.3: Direct firmware load failed with error -2
[   10.183904] Bluetooth: can't load firmware, may not work correctly

########## wireless info END ############

```

Thanks!

---

### Post by chili555 on 2015-06-13
> 03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
Subsystem: Broadcom Corporation Device [14e4:0607]
Kernel driver in use: bcma-pci-bridgeThe correct driver for your device is bcmwl-kernel-source. Please obtain a temporary internet connection by ethernet or whatever means possible and open a terminal:```
sudo apt-get install  --reinstall bcmwl-kernel-source
```After it finishes, detach the ethernet, reboot and tell us if it's working as expected.

---

### Post by Bucky Ball on 2015-06-14
*Post moved to own thread.*

(Also, please use code tags for terminal output. See the last link in my signature. I have added them to your first post.)

---

### Post by praseodym on 2015-06-14
Hi,

obviously, there was an upgrade to 15.04? The kernel 3.13 is from 14.04! Lets check
```

sudo apt-get update
sudo apt-get install --reinstall linux-generic build-essential dkms linux-headers-generic
```

---

