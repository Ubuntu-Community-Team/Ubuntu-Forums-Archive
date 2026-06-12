---
title: "Problem with WiFi detecting anything."
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by derpyforever21 on 2018-08-08
This is everything i got if anyone needs anything more let me know. Also i am still pretty new to ubuntu.


```
########## wireless info START ##########

Report from: 08 Aug 2018 00:36 EDT -0400

Booted last: 08 Aug 2018 00:00 EDT -0400

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-131-generic #157-Ubuntu SMP Thu Jul 12 15:51:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1179:ff66]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Askey Computer Corp. WLL6080 802.11bgn Wireless Mini PCIe Card [AR9281] [144f:7141]
    Kernel modules: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              565248  0
wmi                    20480  1 toshiba_acpi

##### interfaces ########################

[/etc/network/interfaces]

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:10.0.0.220  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          inet6 addr: 2601:980:c200:e042:<IP6 'eth0' [IF1]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23594352 (23.5 MB)  TX bytes:3348659 (3.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:14196 (14.1 KB)  TX bytes:14196 (14.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 75.75.75.75
nameserver 75.75.76.76
search hsd1.pa.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      3644     1  0 00:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.ADDRESS[1]:                         10.0.0.220/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         2601:980:c200:e042:<IP6 'eth0' [IF1]>/64
IP6.ADDRESS[2]:                         fe80::<IP6 'eth0' [IF1]>/64
IP6.GATEWAY:                            fe80::5e8f:e0ff:fec0:175b

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-131-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0138430EFA92759AB09DF26
depends:        
retpoline:      Y
intree:         Y
vermagic:       4.4.0-131-generic SMP mod_unload modversions retpoline 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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
blacklist acer_wmi
blacklist acer_wmi

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.527918] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   20.160070] ath: EEPROM regdomain: 0x65
[   20.160075] ath: EEPROM indicates we should expect a direct regpair map
[   20.160079] ath: Country alpha2 being used: 00
[   20.160081] ath: Regpair used: 0x65
[   24.447862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.820159] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   24.820290] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.404887] r8169 0000:02:00.0 eth0: link up
[   26.404901] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  180.824658] r8169 0000:02:00.0 eth0: link down
[  226.315119] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  236.820050] r8169 0000:02:00.0 eth0: link up
[  555.624581] ath9k: ath9k: Driver unloaded

########## wireless info END ############
```

---

### Post by wildmanne39 on 2018-08-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

