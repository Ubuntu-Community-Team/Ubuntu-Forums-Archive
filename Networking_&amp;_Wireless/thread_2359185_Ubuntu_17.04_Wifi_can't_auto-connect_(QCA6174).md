---
title: "Ubuntu 17.04 Wifi can't auto-connect (QCA6174)"
date: 2017-04-21
forum: Networking &amp; Wireless
---

### Post by benjsec on 2017-04-21
I'm having trouble with my wifi since installing 17.04. I was previously on Mint 18 and it worked fairly well, but would give up every few hours.

Now it will not connect automatically on start-up or when resuming from sleep. If I wait for the auto-attempts to fail and then select the network manually it will connect. Once connected it seems as stable as it was on Mint. There is also a long delay on start-up which seems to be caused by the wifi, although I'm not 100% sure of this.

I have tried replacing the firmware with the version from [[https://github.com/kvalo/ath10k-firmware]](https://github.com/kvalo/ath10k-firmware]) but that hasn't had any effect. I've also linked `firmware-4.bin` to `firmware-5.bin` which has removed the warning but nothing more.

I've also tried disabling the power management as per [[https://askubuntu.com/questions/884922/wifi-on-lenovo-ideapad-running-ubuntu-16-04/884987#884987]](https://askubuntu.com/questions/884922/wifi-on-lenovo-ideapad-running-ubuntu-16-04/884987#884987]). This has made it fail faster after login (which at least means less time waiting before manually selecting the network) but hasn't fixed the issue.

Sources:
 * [[https://ubuntuforums.org/showthread.php?t=2358669]](https://ubuntuforums.org/showthread.php?t=2358669])
 * [[https://askubuntu.com/questions/770897/problems-with-qualcomm-atheros-qca6174-in-ubuntu-16-04]](https://askubuntu.com/questions/770897/problems-with-qualcomm-atheros-qca6174-in-ubuntu-16-04])

Wireless-info script output:
```

########## wireless info START ##########

Report from: 21 Apr 2017 08:41 BST +0100

Booted last: 21 Apr 2017 00:00 BST +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
	Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter [11ad:0807]
	Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 001 Device 009: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 008: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 006: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:56c1 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04ca:3016 Lite-On Technology Corp. 
Bus 001 Device 002: ID 04f2:1558 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0
ath10k_pci             45056  0
ath10k_core           344064  1 ath10k_pci
ath                    28672  1 ath10k_core
mac80211              782336  1 ath10k_core
cfg80211              602112  3 mac80211,ath,ath10k_core
sparse_keymap          16384  2 acer_wmi,intel_vbtn
wmi                    16384  1 acer_wmi
video                  40960  2 acer_wmi,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       975     1  7 08:40 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.10.0-19-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00088-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/0000:01:00.0/net/wlp1s0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5bcf1dc4-1e43-47f2-96ea-bfdbfa84a63d | Abarat

SSID                           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Virgin Media                   <MAC 'Virgin Media' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
VM-guest-2976694               <MAC 'VM-guest-2976694' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
VM-guest-2976694               <MAC 'VM-guest-2976694' [AN3]>  Infra  48    5240 MHz  54 Mbit/s  54      &#9602;&#9604;__  --           no        
Abarat                         <MAC 'Abarat' [AN4]>  Infra  48    5240 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2         no        
Virgin Media                   <MAC 'Virgin Media' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2 802.1X  no        
VM6915386                      <MAC 'VM6915386' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2    no        
Abarat                         <MAC 'Abarat' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2         no        
VM6915386                      <MAC 'VM6915386' [AN8]>  Infra  36    5180 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2         no        
TALKTALKF75505                 <MAC 'TALKTALKF75505' [AN9]>  Infra  9     2452 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2    no        
VM900304-5G                    <MAC 'VM900304-5G' [AN10]>  Infra  36    5180 MHz  54 Mbit/s  27      &#9602;___  WPA2         no        
TALKTALK-A8919B                <MAC 'TALKTALK-A8919B' [AN11]>  Infra  4     2427 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2    no        
SKY1AB04                       <MAC 'SKY1AB04' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA2         no        
KeySurf                        <MAC 'KeySurf' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  20      &#9602;___  --           no        
DIRECT-97-HP ENVY 4520 series  <MAC 'DIRECT-97-HP ENVY 4520 series' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA2         no        
Virgin Media                   <MAC 'Virgin Media' [AN15]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  WPA2 802.1X  no        
VM900304-2G                    <MAC 'VM900304-2G' [AN16]>  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2    no        
Virgin Media                   <MAC 'Virgin Media' [AN17]>  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA2 802.1X  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Abarat]] (600 root)
[connection] id=Abarat | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Abarat
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

wlp1s0    Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     50E531406EF702B9976A8A9
depends:        ath10k_core
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     1B2C9C18ACF805C04DCA414
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     4B8612B6FF71DD27AE8CE67
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6FCDB39CB1DCCA0C9A450B2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0ADFC23D0B6BCD6916160E7
depends:        
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.693926] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[    4.693944] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    4.699973] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
[    4.699975] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.700487] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.2.0-00088-QCARMSWPZ-1 api 5 features ignore-otp crc32 4dcf5871
[    4.772964] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8c15898f
[    7.018269] ath10k_pci 0000:01:00.0: htt-ver 3.14 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    7.103456] ath: EEPROM regdomain: 0x6c
[    7.103457] ath: EEPROM indicates we should expect a direct regpair map
[    7.103457] ath: Country alpha2 being used: 00
[    7.103458] ath: Regpair used: 0x6c
[    7.108852] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   94.304598] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 5 times)
[  104.108672] wlp1s0: authenticate with <MAC 'Abarat' [AN4]>
[  104.152645] wlp1s0: send auth to <MAC 'Abarat' [AN4]> (try 1/3)
[  104.153646] wlp1s0: authenticated
[  104.154842] wlp1s0: associate with <MAC 'Abarat' [AN4]> (try 1/3)
[  104.158144] wlp1s0: RX AssocResp from <MAC 'Abarat' [AN4]> (capab=0x411 status=0 aid=1)
[  104.164040] wlp1s0: associated
[  104.164114] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  104.169424] ath: EEPROM regdomain: 0x833a
[  104.169426] ath: EEPROM indicates we should expect a country code
[  104.169427] ath: doing EEPROM country->regdmn map search
[  104.169429] ath: country maps to regdmn code: 0x37
[  104.169430] ath: Country alpha2 being used: GB
[  104.169431] ath: Regpair used: 0x37
[  104.169432] ath: regdomain 0x833a dynamically updated by country IE
[  104.208738] wlp1s0: Limiting TX power to 20 (23 - 3) dBm as advertised by <MAC 'Abarat' [AN4]>
[  104.778021] wlp1s0: deauthenticating from <MAC 'Abarat' [AN4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  104.790090] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[  104.846393] wlp1s0: authenticate with <MAC 'Abarat' [AN4]>
[  104.888119] wlp1s0: send auth to <MAC 'Abarat' [AN4]> (try 1/3)
[  104.889152] wlp1s0: authenticated
[  104.890885] wlp1s0: associate with <MAC 'Abarat' [AN4]> (try 1/3)
[  104.892823] wlp1s0: RX AssocResp from <MAC 'Abarat' [AN4]> (capab=0x411 status=0 aid=1)
[  104.896816] wlp1s0: associated
[  104.896877] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  104.901882] ath: EEPROM regdomain: 0x833a
[  104.901883] ath: EEPROM indicates we should expect a country code
[  104.901885] ath: doing EEPROM country->regdmn map search
[  104.901886] ath: country maps to regdmn code: 0x37
[  104.901888] ath: Country alpha2 being used: GB
[  104.901889] ath: Regpair used: 0x37
[  104.901891] ath: regdomain 0x833a dynamically updated by country IE
[  104.925561] wlp1s0: Limiting TX power to 20 (23 - 3) dBm as advertised by <MAC 'Abarat' [AN4]>
[  105.294940] wlp1s0: deauthenticating from <MAC 'Abarat' [AN4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  105.306820] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[  110.059048] wlp1s0: authenticate with <MAC 'Abarat' [AN4]>
[  110.100308] wlp1s0: send auth to <MAC 'Abarat' [AN4]> (try 1/3)
[  110.101293] wlp1s0: authenticated
[  115.105709] wlp1s0: aborting authentication with <MAC 'Abarat' [AN4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  115.263402] wlp1s0: authenticate with <MAC 'Abarat' [AN7]>
[  115.321209] wlp1s0: send auth to <MAC 'Abarat' [AN7]> (try 1/3)
[  115.324044] wlp1s0: authenticated
[  120.322662] wlp1s0: aborting authentication with <MAC 'Abarat' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  125.113949] wlp1s0: authenticate with <MAC 'Abarat' [AN4]>
[  125.155384] wlp1s0: send auth to <MAC 'Abarat' [AN4]> (try 1/3)
[  125.156429] wlp1s0: authenticated
[  130.156387] wlp1s0: aborting authentication with <MAC 'Abarat' [AN4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  131.013272] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[  135.743825] wlp1s0: authenticate with <MAC 'Abarat' [AN7]>
[  135.801095] wlp1s0: send auth to <MAC 'Abarat' [AN7]> (try 1/3)
[  135.803635] wlp1s0: authenticated
[  140.802678] wlp1s0: aborting authentication with <MAC 'Abarat' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  141.867385] wlp1s0: authenticate with <MAC 'Abarat' [AN4]>
[  141.908756] wlp1s0: send auth to <MAC 'Abarat' [AN4]> (try 1/3)
[  141.912013] wlp1s0: authenticated
[  156.013427] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)

########## wireless info END ############

```

Does anyone have any more suggestions to try?

---

### Post by UbuntuWho on 2017-04-24
> **benjsec said:**
> I'm having trouble with my wifi since installing 17.04. I was previously on Mint 18 and it worked fairly well, but would give up every few hours.
Now it will not connect automatically on start-up or when resuming from sleep. If I wait for the auto-attempts to fail and then select the network manually it will connect. Once connected it seems as stable as it was on Mint. There is also a long delay on start-up which seems to be caused by the wifi, although I'm not 100% sure of this.

I've been having a similar problem for months since upgrading to Ubuntu 16.04. When I was on 14.04, I didn't notice a lot of WiFi problems, but ever since upgrading to the next stable release, I've been having a heck of a time.

Usually, whenever I reboot, Network Manager will give a status of being connected to my wireless, but I won't have internet access until I manually disconnect and reconnect to the same provider. I've been having more and more issues with connecting lately, and my other devices are able to connect! What can I do? :confused:

---

### Post by UbuntuWho on 2017-05-13
Here's my network controller also:
```
$ lspci -nnk | grep 0280 -A2
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc AR9485 Wireless Network Adapter [11ad:6617]
    Kernel driver in use: ath9k

```

---

### Post by UbuntuWho on 2017-05-19
**Bump!** :-\"

---

