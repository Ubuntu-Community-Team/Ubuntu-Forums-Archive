---
title: "no wifi on ThinkPad Edge E145 Ubuntu 14.04 LTS"
date: 2016-08-14
forum: Networking &amp; Wireless
---

### Post by neil44 on 2016-08-14
[ATTACH]270691[/ATTACH]

Suddenly (it seems) wifi has disappeared!

I have this as a result of running the wifi info script:
```

########## wireless info START ##########

Report from: 14 Aug 2016 19:37 BST +0100

Booted last: 14 Aug 2016 19:10 BST +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-93-generic #140-Ubuntu SMP Mon Jul 18 21:21:05 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:510c]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 04f2:b2fe Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04ca:2007 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              496328  0 
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4513181 (4.5 MB)  TX bytes:486658 (486.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       759     1  0 19:10 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/OrtCafe]] (600 root)
[connection] id=OrtCafe | type=802-11-wireless
[802-11-wireless] ssid=OrtCafe | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IHB]] (600 root)
[connection] id=IHB | type=802-11-wireless
[802-11-wireless] ssid=IHB | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Impact Hub Birmingham]] (600 root)
[connection] id=Impact Hub Birmingham | type=802-11-wireless | permissions=user:claire:; | autoconnect=false
[802-11-wireless] ssid=Impact Hub Birmingham | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SKY76476_EXT]] (600 root)
[connection] id=SKY76476_EXT | type=802-11-wireless
[802-11-wireless] ssid=SKY76476_EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKYB5FFB]] (600 root)
[connection] id=SKYB5FFB | type=802-11-wireless
[802-11-wireless] ssid=SKYB5FFB | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOB-WSTU]] (600 root)
[connection] id=HOB-WSTU | type=802-11-wireless
[802-11-wireless] ssid=HOB-WSTU | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/PLUSNET-P8XC9T]] (600 root)
[connection] id=PLUSNET-P8XC9T | type=802-11-wireless
[802-11-wireless] ssid=PLUSNET-P8XC9T | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM784481-2G]] (600 root)
[connection] id=VM784481-2G | type=802-11-wireless
[802-11-wireless] ssid=VM784481-2G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Impact Hub Birmingham Members]] (600 root)
[connection] id=Impact Hub Birmingham Members | type=802-11-wireless
[802-11-wireless] ssid=Impact Hub Birmingham Members | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/The Kitchen Garden_xt]] (600 root)
[connection] id=The Kitchen Garden_xt | type=802-11-wireless
[802-11-wireless] ssid=The Kitchen Garden_xt | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKY06C45]] (600 root)
[connection] id=SKY06C45 | type=802-11-wireless
[802-11-wireless] ssid=SKY06C45 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/mac-public]] (600 root)
[connection] id=mac-public | type=802-11-wireless
[802-11-wireless] ssid=mac-public | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SKY76476_EXT 1]] (600 root)
[connection] id=SKY76476_EXT 1 | type=802-11-wireless
[802-11-wireless] ssid=SKY76476_EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM291887-2G]] (600 root)
[connection] id=VM291887-2G | type=802-11-wireless
[802-11-wireless] ssid=VM291887-2G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOB-WADM]] (600 root)
[connection] id=HOB-WADM | type=802-11-wireless
[802-11-wireless] ssid=HOB-WADM | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Kitchen Garden-2G]] (600 root)
[connection] id=Kitchen Garden-2G | type=802-11-wireless
[802-11-wireless] ssid=Kitchen Garden-2G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BCU-Wireless]] (600 root)
[connection] id=BCU-Wireless | type=802-11-wireless
[802-11-wireless] ssid=BCU-Wireless | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/mac birmingham]] (600 root)
[connection] id=mac birmingham | type=802-11-wireless
[802-11-wireless] ssid=mac birmingham | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-93-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-93-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D5:FC:C7:F0:EC:19:47:73:D0:56:65:94:89:35:93:1E:3B:13:36:A9
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   23.242757] r8169 0000:03:00.0 eth0: link down (repeated 2 times)
[   23.242857] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   25.635860] r8169 0000:03:00.0 eth0: link up
[   25.635884] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

Can anyone help? I've tried following this: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)
But it doesn't seem to have helped.

---

### Post by neil44 on 2016-08-14
Actually, I seem to have fixed it! I had to disable the secure boot thing to add the new driver. Will this stop my (additional) problem of wifi dropping off and coming back randomly?

---

### Post by jeremy31 on 2016-08-14
You likely have secure boot enabled in BIOS and newer kernels are enforcing a restriction on drivers if they are not signed, the wl driver is not signed so the kernel will not load it.
You can check with ```
sudo modprobe -v wl
```

You found it, post a new result for the wireless script after ```
./wireless-info
```

---

