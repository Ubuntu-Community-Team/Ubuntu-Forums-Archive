---
title: "Qualcomm Atheros QCA9565/AR9565 Wireless Network Adapter Drops Connection"
date: 2023-09-24
forum: Networking &amp; Wireless
---

### Post by wyattwhiteeagle on 2023-09-24
I've done all I know to do, resetting the wireless adapter, and the modem, router and/or access point in Windows.
I have no clue how to do those things in *buntu.


This started happening when I had to replace the internal HDD.
I replaced it with a Western Digital Blue internal HDD.
I'm thinking that could also be contributing to the problem.


Can ya'll please have a look at the following "wireless-info script" output and help me identify and resolve the problem?


```
########## wireless info START ##########


Report from: 24 Sep 2023 10:52 EDT -0400


Booted last: 24 Sep 2023 00:00 EDT -0400


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy


##### kernel ############################


Linux 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


sed: can't read /root/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


01:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57786 Gigabit Ethernet PCIe [14e4:16b3] (rev 01)
	Subsystem: Acer Incorporated [ALI] NetXtreme BCM57786 Gigabit Ethernet PCIe [1025:0775]
	Kernel driver in use: tg3


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0642]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b3f6 Chicony Electronics Co., Ltd HD WebCam (Acer)
Bus 002 Device 005: ID 04ca:300b Lite-On Technology Corp. Atheros AR3012 Bluetooth
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


ath9k                 253952  0
ath9k_common           49152  1 ath9k
ath9k_hw              663552  2 ath9k_common,ath9k
ath3k                  24576  0
ath                    40960  3 ath9k_common,ath9k,ath9k_hw
mac80211             1617920  1 ath9k
cfg80211             1241088  4 ath9k_common,ath9k,ath,mac80211
bluetooth            1036288  35 btrtl,btmtk,btintel,btbcm,bnep,ath3k,btusb,rfcomm
libarc4                16384  1 mac80211
acer_wmi               36864  0
sparse_keymap          16384  1 acer_wmi
wmi_bmof               16384  0
video                  73728  2 acer_wmi,i915
wmi                    40960  3 video,acer_wmi,wmi_bmof


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'enp1s0f0' [IF1]> brd <MAC address>
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>


##### iwconfig ##########################


lo        no wireless extensions.


enp1s0f0  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad
search .


##### network managers ##################


Installed:


	NetworkManager


Running:


root         568       1  0 09:36 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 6.2.0-26-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.PATH:                           pci-0000:02:00.0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               yes
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         p2p-dev-wlp2s0
GENERAL.TYPE:                           wifi-p2p
GENERAL.NM-TYPE:                        NMDeviceWifiP2P
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/4
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         (unknown)
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.PATH:                           --
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     no
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         enp1s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Broadcom Inc. and subsidiaries
GENERAL.PRODUCT:                        NetXtreme BCM57786 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 6.2.0-26-generic
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'enp1s0f0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0f0
GENERAL.PATH:                           pci-0000:01:00.0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               off
IP4.GATEWAY:                            --
IP6.GATEWAY:                            --
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WIN_201145.nmconnection]] (600 root)
[connection] id=WIN_201145 | type=wifi
[wifi] ssid=WIN_201145
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


enp1s0f0  no frequency information.


wlp2s0    13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp1s0f0  Interface doesn't support scanning.


wlp2s0    No scan results


##### module infos ######################


[ath9k]
filename:       /lib/modules/6.2.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
parm:           use_msi:Use MSI instead of INTx if possible (int)


[ath9k_common]
filename:       /lib/modules/6.2.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
depends:        ath9k_hw,ath,cfg80211
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/6.2.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 


[ath3k]
filename:       /lib/modules/6.2.0-26-generic/kernel/drivers/bluetooth/ath3k.ko
license:        GPL
description:    Atheros AR30xx firmware driver
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           ath3k
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 


[ath]
filename:       /lib/modules/6.2.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 


[mac80211]
filename:       /lib/modules/6.2.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/6.2.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       6.2.0-26-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0
use_msi: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 4561.157099] ath: phy0: Chip reset failed
[ 4561.157102] ath: phy0: Unable to reset channel, reset status -22
[ 4561.168244] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4561.340550] ath: phy0: Chip reset failed
[ 4561.340553] ath: phy0: Unable to reset channel, reset status -22
[ 4561.351685] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4561.523866] ath: phy0: Chip reset failed
[ 4561.523869] ath: phy0: Unable to reset channel, reset status -22
[ 4561.535003] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4561.707164] ath: phy0: Chip reset failed
[ 4561.707168] ath: phy0: Unable to reset channel, reset status -22
[ 4561.718316] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4561.890491] ath: phy0: Chip reset failed
[ 4561.890495] ath: phy0: Unable to reset channel, reset status -22
[ 4561.901643] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4562.073826] ath: phy0: Chip reset failed
[ 4562.073830] ath: phy0: Unable to reset channel, reset status -22
[ 4562.085009] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4562.257313] ath: phy0: Chip reset failed
[ 4562.257316] ath: phy0: Unable to reset channel, reset status -22
[ 4562.268444] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4562.440613] ath: phy0: Chip reset failed
[ 4562.440615] ath: phy0: Unable to reset channel, reset status -22
[ 4562.451834] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4562.624042] ath: phy0: Chip reset failed
[ 4562.624046] ath: phy0: Unable to reset channel, reset status -22
[ 4562.635243] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4562.807444] ath: phy0: Chip reset failed
[ 4562.807447] ath: phy0: Unable to reset channel, reset status -22
[ 4562.818626] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4562.990835] ath: phy0: Chip reset failed
[ 4562.990838] ath: phy0: Unable to reset channel, reset status -22
[ 4563.002004] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4563.174331] ath: phy0: Chip reset failed
[ 4563.174335] ath: phy0: Unable to reset channel, reset status -22
[ 4563.185502] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4563.357705] ath: phy0: Chip reset failed
[ 4563.357708] ath: phy0: Unable to reset channel, reset status -22
[ 4563.368873] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4563.541077] ath: phy0: Chip reset failed
[ 4563.541081] ath: phy0: Unable to reset channel, reset status -22
[ 4563.552246] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4563.724455] ath: phy0: Chip reset failed
[ 4563.724458] ath: phy0: Unable to reset channel, reset status -22
[ 4563.735622] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4563.907844] ath: phy0: Chip reset failed
[ 4563.907848] ath: phy0: Unable to reset channel, reset status -22
[ 4563.919031] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4564.091364] ath: phy0: Chip reset failed
[ 4564.091368] ath: phy0: Unable to reset channel, reset status -22
[ 4564.102517] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4564.274741] ath: phy0: Chip reset failed
[ 4564.274744] ath: phy0: Unable to reset channel, reset status -22
[ 4564.285897] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4564.458090] ath: phy0: Chip reset failed
[ 4564.458092] ath: phy0: Unable to reset channel, reset status -22
[ 4564.469266] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4564.641484] ath: phy0: Chip reset failed
[ 4564.641487] ath: phy0: Unable to reset channel, reset status -22
[ 4564.652671] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4564.824872] ath: phy0: Chip reset failed
[ 4564.824875] ath: phy0: Unable to reset channel, reset status -22
[ 4564.836123] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4565.008452] ath: phy0: Chip reset failed
[ 4565.008455] ath: phy0: Unable to reset channel, reset status -22
[ 4565.019647] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4565.191830] ath: phy0: Chip reset failed
[ 4565.191833] ath: phy0: Unable to reset channel, reset status -22
[ 4565.203008] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4565.375212] ath: phy0: Chip reset failed
[ 4565.375215] ath: phy0: Unable to reset channel, reset status -22
[ 4565.386382] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4565.558595] ath: phy0: Chip reset failed
[ 4565.558599] ath: phy0: Unable to reset channel, reset status -22
[ 4565.569760] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4565.741934] ath: phy0: Chip reset failed
[ 4565.741937] ath: phy0: Unable to reset channel, reset status -22
[ 4565.753108] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4565.925448] ath: phy0: Chip reset failed
[ 4565.925451] ath: phy0: Unable to reset channel, reset status -22
[ 4565.936628] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4566.108806] ath: phy0: Chip reset failed
[ 4566.108809] ath: phy0: Unable to reset channel, reset status -22
[ 4566.119974] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4566.292176] ath: phy0: Chip reset failed
[ 4566.292179] ath: phy0: Unable to reset channel, reset status -22
[ 4566.303352] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4566.475672] ath: phy0: Chip reset failed
[ 4566.475675] ath: phy0: Unable to reset channel, reset status -22
[ 4566.486836] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4566.659043] ath: phy0: Chip reset failed
[ 4566.659047] ath: phy0: Unable to reset channel, reset status -22
[ 4566.670215] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4566.842430] ath: phy0: Chip reset failed
[ 4566.842434] ath: phy0: Unable to reset channel, reset status -22
[ 4566.869512] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[ 4567.042029] ath: phy0: Chip reset failed
[ 4567.042036] ath: phy0: Unable to reset channel, reset status -22
[ 4567.253117] ath: phy0: RX failed to go idle in 10 ms RXSM=0xffffffff
[ 4567.264228] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff


########## wireless info END ############
```

---

### Post by jeremy31 on 2023-09-24
In terminal ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Power it off and try a cold boot up

---

### Post by wyattwhiteeagle on 2023-09-24
i made a few statements in my original post here that I recently learned aren't true.

It is my old 80gb HDD that is the Western Digital Blue.

The HDD that is in the laptop when the report was ran is a Seagate Thin 1tb internal HDD that I had bought on Ebay.

While waiting for a response here, I switched from the Ebay Seagate to the 80gb WD Blue and it seems the wireless connection is good and stable.

Should I run the mentioned command?
I would also need guidance on how to do a cold boot in *buntu.

I do realize that at some point very soon I'll want to do a fresh clean install on the 80gb WD Blue to make sure everything is properly installed and properly synced.
That is unless there's CLI commands to do that without doing the fresh clean install.
I don't currently have any real backup's to rely on...just all my stuff saved in another location.

---

### Post by jeremy31 on 2023-09-24
Run the command.  A cold boot is shutting off the computer rather than just doing a reboot

---

### Post by wyattwhiteeagle on 2023-09-24
> **jeremy31 said:**
> In terminal ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Power it off and try a cold boot up
I ran the command and did the "cold boot".

What's my next step?

Re-run the wireless info script?
Give it a little time and observe?

---

### Post by jeremy31 on 2023-09-24
You could run the script again and post results.  I wonder if it isn't working you may want to power it off, remove power cord and battery, then hold the power button for 20 seconds.  Put it back together and boot

---

### Post by wyattwhiteeagle on 2023-09-24
> **jeremy31 said:**
> You could run the script again and post results. I wonder if it isn't working you may want to power it off, remove power cord and battery, then hold the power button for 20 seconds. Put it back together and boot


It seems to be a good and stable connection.
In fact, I mentioned that in the following quote.


It seems to be good enough that I'm on it now without issue's.


> **wyattwhiteeagle said:**
> ...While waiting for a response here, I switched from the Ebay Seagate to the 80gb WD Blue and it seems the wireless connection is good and stable.


Should I run the mentioned command?
I would also need guidance on how to do a cold boot in *buntu.

---

### Post by jeremy31 on 2023-09-24
I am not sure how a hard drive could affect it unless it was drawing a lot of power

---

### Post by wyattwhiteeagle on 2023-09-24
I'm thinking the Seagate Thin that I bought off Ebay was a corrupt hard drive.
It was doing the same thing in Windows 7 Home SP1 too.

There may be more wrong with that Hard Drive than we know.
I mean...it's Ebay...it's a reseller's auction database.
Even I...a low-end user...could sell something on there.
Just choose something to sell...say all the good stuff everyone wants to see, including free returns...before long I have something sold then refuse the return after it's sold.
Sad thing is, it costed me about $60 and I been working on this so long that it's easily past the free return and refund time frame.
I very well could've read good stuff about the HDD...order it...and find out it don't work properly.

The point about selling on Ebay...
My brother's father-in-law is trying to sell a 1982 penny for $200 on there simply because the year on it is the same as the title of the song made famous by Randy Travis.
Of course he ain't gonna say that in the description or remarks sections for that coin.
Plus, who in their right mind is gonna buy some random cent for $200?
Even a coin collector...someone in it not only for the collection of coin's but also for the money among other reasons...won't buy that penny.

I could see it if the song title or lyrics were inspired by that same exact penny and the proof of that would need to be with that coin, but that coin has no documented history with it.

---

### Post by praseodym on 2023-09-29
Which country do you live? iwlist chan shows 13 channels, for the US, only 11 are allowed

If you are in the US run

```
sudo sed -i "s/REGDOMAIN=/REGDOMAIN=[COLOR="#FF0000"]US[/COLOR]/g" /etc/default/crda 
```
and reboot

For other countries check you country code here

[https://en.wikipedia.org/wiki/ISO_3166-1](https://en.wikipedia.org/wiki/ISO_3166-1)

---

