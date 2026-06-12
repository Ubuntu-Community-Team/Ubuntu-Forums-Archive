---
title: "Turn on Wifi hardware in MSI windpad 110 w"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by saeb2 on 2017-03-20
hi there I Installed Ubuntu 16.10 in my MSI windpad 110w tablet pc
Tablet detail is available here:
```
https://www.msi.com/product/tablet/WindPad-110W.html
```
in Windows I can turn on wifi with application named MSI O-Easy
[IMG]https://www.msi.com/pic/image/product_img/other/nb/110w/110w_24.jpg[/IMG]

but I don't know how I can turn Wifi on in Ubuntu
my details:
```

########## wireless info START ##########


Report from: 20 Mar 2017 14:14 IRST +0330


Booted last: 20 Mar 2017 00:00 IRST +0330


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description: Ubuntu 16.10
Release: 16.10
Codename: yakkety


##### kernel ############################


Linux 4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:15:00 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0037] (rev 01)
 Subsystem: AzureWave AW-NB100H 802.11n Wireless Mini PCIe Card [1a3b:2100]
 Kernel driver in use: ath9k


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 002: ID 12d1:1404 Huawei Technologies Co., Ltd. EM770W miniPCI WCDMA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0cf3:3008 Atheros Communications, Inc. Bluetooth (AR3011)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 1770:ff00  
Bus 004 Device 003: ID 0eef:72fa D-WAV Scientific Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
 Soft blocked: no
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes


##### lsmod #############################


ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k,ath9k_common
ath                    32768  3 ath9k_hw,ath9k,ath9k_common
mac80211              757760  1 ath9k
ath3k                  20480  0
cfg80211              581632  4 mac80211,ath9k,ath,ath9k_common
bluetooth             552960  32 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 11176  bytes 675040 (675.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 11176  bytes 675040 (675.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


 NetworkManager


Running:


root       576     1  0 14:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         ttyUSB2
GENERAL.TYPE:                           gsm
GENERAL.NM-TYPE:                        NMDeviceModem
GENERAL.VENDOR:                         HUAWEI Technology
GENERAL.PRODUCT:                        HUAWEI MOBILE WCDMA EM770W
GENERAL.DRIVER:                         option1
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /org/freedesktop/ModemManager1/Modem/0
GENERAL.IP-IFACE:                       
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9485 Wireless Network Adapter (AW-NB100H 802.11n Wireless Mini PCIe Card)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.8.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
WirelessEnabled=true
NetworkingEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/TOR-ROUTER]] (600 root)
[connection] id=TOR-ROUTER | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TOR-ROUTER
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SAEB]] (600 root)
[connection] id=SAEB | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=SAEB
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Tehran (based on set time zone)


country 00: DFS-UNSET
 (2402 - 2472 @ 40), (N/A, 20), (N/A)
 (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
 (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
 (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
 (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
 (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
 (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
 (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


wlp2s0    14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz


##### iwlist scan #######################


wlp2s0    Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7DD7AE5764B41812C31660E
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     C1094862B67773C0C7822B7
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D15742225CC828FEB319976
depends:        ath
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ath3k]
filename:       /lib/modules/4.8.0-22-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     822A166EB22C0577CB2ED55
depends:        bluetooth
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 


[cfg80211]
filename:       /lib/modules/4.8.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-22-generic SMP mod_unload modversions 
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


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   11.157014] ath: phy0: ASPM enabled: 0x43
[   11.157023] ath: EEPROM regdomain: 0x60
[   11.157025] ath: EEPROM indicates we should expect a direct regpair map
[   11.157031] ath: Country alpha2 being used: 00
[   11.157033] ath: Regpair used: 0x60
[   12.684463] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   12.843745] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)


########## wireless info END ############





```

---

### Post by chili555 on 2017-03-20
I'm sure this is the problem:```
##### rfkill ############################


0: hci0: Bluetooth
 Soft blocked: no
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: no
[COLOR="#FF0000"] Hard blocked: yes[/COLOR]
```The system thinks that the wireless switch is set to airplane mode to turn off the wireless. Do you have a wireless button or switch? No? I didn't think so.

Are there any clues here?```
dmesg | grep -i msi
lsmod | grep -e wmi -e msi
```

---

